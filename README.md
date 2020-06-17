# Le document de déploiement
### Installation du dépôt de docker-ce 
###### Mise à jour l’index des packages « apt »

    $ sudo apt-get update

###### Installation des packages qui permettent à « apt » d’utiliser un référentiel en HTTPS.
    $ sudo apt-get install \
        apt-transport-https \
        ca-certificates \
        curl \
        software-properties-common

###### Ajouter la clé GPG officielle 
    $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

### Installation de docker-ce
###### Mise à jour l’index des packages « apt »
    $ sudo apt-get update

###### Ajouter le dépôt de docker

    $ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

###### Mise à jour l’index des packages « apt »
    $ sudo apt-get update
    
###### Vérification du dépôt de docker 

    $ apt-cache policy docker-ce
###### Installation docker-ce
    $ sudo apt-get install docker-ce
    
    $ sudo usermod -aG docker ${USER}
    
    $ su - ${USER}
    
    $ id -nG
    
    $ sudo bash
    
    $ exit

###### Vérification 

    $ sudo docker run hello-world


### Déploiement du serveur lamp(Linux, Apache, MySQL, PHP5.6) en utilisant le docker.


###### le répertoire des sources de l’application


    $ /home/user-camacte/web/src


L’application est emballé dans deux containeur différents.

1. Le conteneur d’Apache-PHP qui gère les requêtes de http/https.
3. Le conteneur de Mysql. 
Les scripts de l’application sont stockés dans le host, vous pouvez modifier les fichiers directement sans modifier / redémarrer les conteneurs/images.


### Compiler et exécuter 

Tout d’abord, nous devons installer le docker-compose qui nous facilite le montage des conteneurs.

###### Télécharger le docker-compose 

    $ sudo curl -L https://github.com/docker/compose/releases/download/1.21.0/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose

###### Application des autorisation d’exécution
    $ sudo chmod +x /usr/local/bin/docker-compose
 

###### Pour avoir plus d’information, vous pouvez exécuter la commande ci-dessous :

    $ docker-compose --help

    
###### Démarrer les conteneurs, nous devons indiquer le nom du fichier
    
    $ docker-compose -f docker-compose-prod.yml up -d
    

###### Arrêter les conteneurs
    
    $ docker-compose down    

###### Supprimer les conteneurs
    
    $ docker-compose rm       
    
### Vérifier les statuts des conteneurs
    
    $ docker ps -a   
    
    ### test pull request
