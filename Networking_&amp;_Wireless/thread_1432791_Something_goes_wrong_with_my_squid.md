---
title: "Something goes wrong with my squid"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by Hitsugaya81 on 2010-03-18
Hello every one.

I have a squid server running since 4 month but...
yesterday, around 11 PM, my server have reboot (probably due to a general power shutdown)
now, squid refuse all connection... i don't know why...

This is my squid.conf
```
http_port 192.168.0.201:3128

hierarchy_stoplist cgi-bin ?
acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY

# Taille maximum de mémoire vive utilisée pour stocker du cache
cache_mem 64 MB

# Taille maximum des objets stockés dans le cache
maximum_object_size 1 MB

# Ici vous définissez les répertoires du cache, vous pouvez définir plusieurs répertoires, l'intêret est de définir des répertoires sur des disques différents afin de gagner en vitesse.

# Chemin des fichiers de cache
cache_dir ufs /media/works/webfolder/Squid/DataBase 1024 16 256

# Format des logs :
# -> Avec off, squid utilise son propre format de logs,
#    mais la date et l'heure ne sont pas lisibles.

# -> Avec on, squid utilise le format standard CLF
emulate_httpd_log on

# Ces deux lignes permettent d'intégrer le plugin SquidGuard
# redirect_program /usr/bin/squidGuard
# redirect_children 4

# Pas d'infos sur ces lignes
refresh_pattern ^ftp:                1440        20%        10080
refresh_pattern ^gopher:        1440        0%        1440
refresh_pattern .                0        20%        4320


# Liste des acl par défaut -> A conserver
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563        # https, snews

# Cette partie définit les ports auquels certains utilisateurs auront droits d'accès, ici ils auront accès à http (port 80), https (port 443), msn (1863). Vous pouvez bien entendu interdire les accès en commentant ou supprimant les lignes correspondantes.

#acl SSL_ports port 873                 # rsync
acl Safe_ports port 80                     # http
acl Safe_ports port 21                     # ftp
acl Safe_ports port 22                     # ssh
acl Safe_ports port 443 563            # https, snews
acl Safe_ports port 1863                 # msn
acl Safe_ports port 70                  # gopher
#acl Safe_ports port 210                # wais
acl Safe_ports port 1025-65535      # unregistered ports
#acl Safe_ports port 280                # http-mgmt
#acl Safe_ports port 488                # gss-http
#acl Safe_ports port 591                # filemaker
acl Safe_ports port 777                # multiling http
#acl Safe_ports port 631                # cups
#acl Safe_ports port 873                # rsync
#acl Safe_ports port 901                # SWAT

# Enfin on définit les accès
# Les règles sont lues dans l'ordre et s'arretent à la première interdiction correspondant au critère de l'utilisateur, un peu comme un firewall, l'ordre des règles est donc important !
# Dans l'exemple, ci dessous, localhost a tous les droits.
# On permet grâce à la ligne http_access deny !Safe_ports d'interdire la connexion à tous les ports exceptés ceux définis par les lignes acl Safe_ports

acl purge method PURGE
acl CONNECT method CONNECT

# Ici on définit les ACL, ceci vous permet de définir des groupes afin de leur attribuer des droits différents.
# Cette ligne définit les adresses IP des utilisateurs du réseau. Vous devez la personnaliser selon votre configuration réseau.
# ACL qui définit le réseau utilisant le cache
acl MonReseau src 192.168.0.0/255.255.255.0

# Accès fournis par squid
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports

# On donne ensuite accès au WEB au localhost et au réseau "Mon réseau" définit plus haut.
#donne accès au proxy à mon réseau
http_access allow MonReseau
http_access allow localhost

# On interdit le reste. Important car sinon votre proxy sera un "open proxy" il pourra être utilisé par n'importe quel via internet, notamment pour faire des choses malintentionnées.
# Interdit tout le reste
# http_access deny all

# Autorise les réponses pour tout le monde (par défaut)
http_reply_access allow all

# Autorise le protocole icp pour tout le monde (par défaut)
icp_access allow all

coredump_dir /var/spool/squid

# Ces lignes sont importantes dans le cas d'un proxy transparents ne les oublier pas.
# pour le proxy transparent

# Vous devez indiquer les serveurs DNS de votre FAI
dns_nameservers 192.168.0.1

# Si vous désirez effectuer des statistiques WEB notamment avec MRTG ou rrdtool, Squid peut faire serveur SNMP
# on active le SNMP sur squid pour les stats mrtg :)
acl snmppublic snmp_community public
snmp_port 3401
snmp_access allow snmppublic all

# Vous définissez ensuite l'host de votre proxy et le mail de l'administrateur.
visible_hostname portails-anc.com
cache_mgr chansigaudyann.anc@orange.fr

# fichier log
logfile_rotate    30
access_log    /media/works/webfolder/logs/Squid/Squid-access.log squid
cache_log    /media/works/webfolder/logs/Squid/Squid-cache.log
cache_store_log    /media/works/webfolder/logs/Squid/Squid-store.log
```In syslog, squid haven't any access to him log :
Cannot open '/media/works/webfolder/logs/Squid/Squid-store.log' for writing
I think this is the problem but I don't how to resolve it.

All help will be welcome.

I hope my English spelling will no hurt you... ;)

Thanks everyone

---

### Post by Hitsugaya81 on 2010-03-19
31 users have viewed my post but... No one to help?

---

### Post by Hitsugaya81 on 2010-03-22
53 overview but...

no one to help ?
no one knowing something about ?
no one interesting by ?

---

### Post by Hitsugaya81 on 2010-03-26
I'm looking for solution since 6 days ago... but I found nothing.
95 persons have read my post but no one have give me a answer...

Is there no one who know the use of Squid?

Please someone help me.

Thanks a lot.

---

