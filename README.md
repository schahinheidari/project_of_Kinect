# project_of_Kinect
<h1 align="center"> wish sport </h1> <br>
<div id="haut"></div>
<p align="center">
  <a href="https://youtu.be/dQw4w9WgXcQ">
    <img alt="LogoWish" title="LogoWish" src="./src/main/resources/logo.png" width="366">
  </a>
</p>

<p align="center">
  <i>Le sport, c'est bien, mais en version wish c'est mieux !</i>
</p>

<hr/>

<h2> Sommaire </h2>

<ul id="Sommaire">
<li><a href="#intro">Introduction</a></li>
<li><a href="#fonctionnalité">Fonctionnalités</a></li> 
<li><a href="#installation">Installation</a></li>
<ul><a href="#prerequis">Prérequis</a> </ul>
<ul><a href="#demarrage">Démarrage de l'application</a> </ul>
<li><a href="#utilisation">Comment utiliser wish sport ?</a></li>
<ul><a href="#accueil">Page d'accueil</a></ul>
<ul><a href="#creation">Page de création</a></ul>
<ul><a href="#visualisation">Page de visualisation</a></ul>
<ul><a href="#verification">Page de vérification</a></ul>
<li><a href="#limite">Les limites de l'application</a></li>
<li><a href="#évolution">Les perspectives d'évolution</a></li>
</ul>

<hr/>

<div id="intro"></div>
<h2> Introduction </h2><br/>

<p class="alinea">wish sport est une application de gestion d'exercices sportifs. Grâce à l'utilisation d'une kinect,
les mouvements du sportif sont capturés et enregistrés sur l'ordinateur.</p>
<p><a href="#haut">haut de page</a></p>

<hr/>
<div id="fonctionnalité"></div>
<h2> Fonctionnalités </h2><br/>
<li>Enregistrement d'un exercice,</li>
<li>Enregistrement d'un mouvement de référence en lien à une catégorie,</li>
<li>Visualisation d'un exercice,</li>
<li>L'importation et l'exportation d'un exercice,</li>
<li>Vérification d'un exercice avec un mouvement de référence.</li>

<p><a href="#haut">haut de page</a></p>
<hr/>
<div id="installation"></div>
<h2> Installation </h2><br/>
<div id="prerequis"></div>
<h3>Prérequis</h3>
<li>Bibliothèques pour faire fonctionner la kinect : <a href="https://docs.microsoft.com/en-us/azure/kinect-dk/sensor-sdk-download">cliquez-ici</a> </li>
<li>Bibliothèque pour le websocket : <a href="https://github.com/uNetworking/uWebSockets">cliquez-ici</a> </li>
<li>Bibliothèque pour la kinect si besoin  <a href="https://github.com/Microsoft/vcpkg">cliquez-ici</a> </li>
<li>Bibliothèque pour du JSON en c++ : <a href="https://github.com/open-source-parsers/jsoncpp">cliquez-ici</a> </li>
<li>Docker (ainsi que docker-compose)</li>
<li>Maven</li>
<br/>
<div id="demarrage"></div>
<h3>Démarrage de l'application</h3>
<p><i>Il faut d'abord cloner le projet git puis exécuter les commandes ci-dessous.</i></p>
<h4>La base de données</h4>
<p><i>Pour démarrer la base de données, il faut utiliser les lignes de commande suivante :</i></p>
<p style="padding: 10px; border: 2px solid;">docker compose up</p>
<p><i>Pour remplir la base de données :</i></p>
<p style="padding: 10px; border: 2px solid;">docker cp ./wish-sport-app/src/main/resources/scripts/ wish-sport-app-app-1:/scripts</p>
<p style="padding: 10px; border: 2px solid;">docker exec -it wish-sport-app-app-1 psql -U kinect kinect \
-f /scripts/create_db.sql \
-f /scripts/categorie.sql \
-f /scripts/enregistrement.sql \
-f /scripts/frame.sql \
-f /scripts/jointure.sql \
-f /scripts/mouvementref.sql \
-f /scripts/sequence.sql</p>
<h4>Le serveur</h4>
<p><i>Pour démarrer le serveur, il faut utiliser les lignes de commande suivante :</i></p>
<p style="padding: 10px; border: 2px solid;">cd serveur_cpp</p>
<p style="padding: 10px; border: 2px solid;">make</p>
<p style="padding: 10px; border: 2px solid;">sudo ./WsServer</p>
<h4>L'application générale</h4>
<p><i>Pour démarrer l'application, il faut utiliser les lignes de commande suivante :</i></p>
<p><i><b>Avec Maven</b></i></p>
<p style="padding: 10px; border: 2px solid;">mvn clean package</p>
<p style="padding: 10px; border: 2px solid;">mvn javafx:run</p>
<p><i><b>Sans Maven</b> (il faut se mettre à la racine du dossier)</i></p>
<p style="padding: 10px; border: 2px solid;">java -cp target/WishSport-1.0.0-jar-with-dependencies.jar univ.tln.i243.groupe1.Main</p>

<p><a href="#haut">haut de page</a></p>
<hr/>

<div id="utilisation"></div>
<h2> Comment utiliser wish sport ? </h2><br/>
<div id="accueil"></div>
<h3>Page d'accueil</h3>
<p align="center">
    <img alt="p-accueil" title="p-accueil" src="./src/main/resources/readme-resources/page-accueil.png" width="920">
</p>
<li><b>Enregistrer</b> : Permet l'accès aux fonctionnalités de création d'exercice et de catégorie</li>
<li><b>Visualiser</b> : Permet d'accéder à la page des exercices enregistrés sur la base de données</li>
<li><b>Comparer</b> : Permet d'aller sur la page de vérification des exercices</li>
<p><a href="#haut">haut de page</a></p>
<hr/>
<div id="creation"></div>
<h3>Page de création</h3>

<p align="center">
    <img alt="p-creation" title="p-creation" src="./src/main/resources/readme-resources/page-creation.png" width="920">
</p>
<li><b>Créer une catégorie</b> : Pour créer une catégorie où ranger des exercices,</li>
<li><b>Créer un enregistrement</b> : Pour créer une fiche d'exercice sur lequel on va rajouter un enregistrement de mouvement soit par importation soit via la kinect,</li>
<li><b>Créer un exercice référent</b> : Pour créer un mouvement de référence à la catégorie voulue.</li>
<br/>
<p><a href="#haut">haut de page</a></p>
<h4>Créer une catégorie</h4>
<p align="center">
    <img alt="p-cat" title="p-cat" src="./src/main/resources/readme-resources/formulaire-categorie.png" width="920">
</p>
<br/>
<p><a href="#haut">haut de page</a></p>
<h4>Créer un enregistrement</h4>
<p align="center">
    <img alt="p-enregistrement" title="p-enregistrement" src="./src/main/resources/readme-resources/formulaire-exercice.png" width="920">
</p>
<p class="alinea"><i>La catégorie et le nom sont obligatoires.</i></p>
<br/>
<p><a href="#haut">haut de page</a></p>
<h4>Créer un exercice référent</h4>
<p align="center">
    <img alt="p-referent" title="p-referent" src="./src/main/resources/readme-resources/formulaire-referent.png" width="920">
</p>
<p class="alinea"><i>Pour créer un mouvement de référence, il faut d'abord sélectionner la catégorie à laquelle il correspond (un seul mouvement par catégorie).
Ensuite, il faut sélectionner un trio de jointures donnant les angles importants. La vérification d'exercice va utiliser les angles choisies comme
moyen de comparaison avec d'autres exercices de la même catégorie.</i></p>
<br/>
<p><a href="#haut">haut de page</a></p>
<hr/>
<div id="visualisation"></div>
<h3>Visualiser</h3>
<p align="center">
    <img alt="p-visualisation" title="p-visualisation" src="./src/main/resources/readme-resources/page-visualisation.png" width="920">
</p>
<p class="alinea"><i>Il faut sélectionner d'abord une catégorie pour afficher les exercices de celle-ci.</i></p>
<li><b>Supprimer l'exercice</b> : Supprime l'exercice de la base de données</li>
<li><b>Exporter en JSON</b> : Exporte un exercice sous un format JSON reconnu par l'application</li>
<li><b>Voir l'exercice</b> : Ouvre une fenêtre jMonkey pour afficher un squelette qui exécute le mouvement</li>
<br/>
<p><a href="#haut">haut de page</a></p>
<hr/>
<h3>Page de vérification</h3>
<div id="verification"></div>
<h4>Page de choix de l'exercice à vérifier</h4>
<p align="center">
    <img alt="p-visualisation" title="p-visualisation" src="./src/main/resources/readme-resources/page-verification.png" width="920">
</p>
<p class="alinea"><i>Seuls les exercices de la catégorie sont affichés.</i></p>
<br/>
<p><a href="#haut">haut de page</a></p>
<h4>Retour visuel</h4>
<p align="center">
    <img alt="exemple" title="p-visualisation" src="./src/main/resources/readme-resources/exemple-verif.png" width="920">
</p>
<p class="alinea"><i>Une fenêtre externe s'ouvre pour afficher un squelette qui exécute l'exercice. Des couleurs s'affichent au niveau des jointures pour indiquer le degré de précision du mouvement.</i></p>
<li><b>Rouge</b> : le mouvement est mal fait,</li>
<li><b>Orange</b> : le mouvement est en partie mal fait,</li>
<li><b>Vert</b> : le mouvement est bien fait.</li>


<br/>
<p><a href="#haut">haut de page</a></p>
<hr/>
<div id="limite"></div>
<h2> Les limites de l'application </h2><br/>

<li>L'application ne peut gérer qu'une seule personne devant la kinect,</li>
<li>L'application ne peut gérer qu'une seule kinect,</li>
<li>Les exercices sont enregistrés d'un bloc (problème de taille en mémoire),</li>
<li>Les exercices mettent du temps à s'enregistrer (problème juste au-dessus),</li>
<li>Les exercices sont limités en temps et en répétition (il n'y a pas de combinaisons possibles).</li>

<p><a href="#haut">haut de page</a></p>
<hr/>
<div id="évolution"></div>
<h2> Les perspectives d'évolution </h2><br/>
<p><i>(du + important au - important)</i></p>

<li>Amélioration de la vérification de mouvement notamment la rotation des jointures et la synchronisation des gestes (fonctionnalité faisable),</li>
<li>Améliorer de la communication entre la kinect et l'application (coûteux en temps),</li>
<li>Ajout de la fonctionnalité de comparaison en live (faisable si la communication entre la kinect et l'application est améliorée),</li>
<li>Commander par des gestes le démarrage d'un enregistrement et sa fin (faisable si la communication entre la kinect et l'application est améliorée)</li>
<li>Ajout de profils d'utilisateurs pour des programmes personnalisés (faisable),</li>
<li>Utiliser l'exportation d'un exercice en JSON pour le convertir en C3D (coûteux en temps).</li>

<p><a href="#haut">haut de page</a></p>
<hr/>
