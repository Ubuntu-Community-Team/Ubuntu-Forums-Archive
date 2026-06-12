---
title: "how to play dvd on laptop"
date: 2008-10-19
forum: Multimedia Software
---

### Post by AGSzabo on 2008-10-19
help,

i installed ubuntu to my laptop and noticed that it cant play dvd. i searched this froum for "play dvd" but did not find anything usefull. however the start-screen of my dvd is showing, but i cant click start. i guess a codec is missing. can you help  me?

regards,
AGS

---

### Post by linuxisfree on 2008-10-19
You should probably Install libdvdread (libdvdread3, i think)and libdvdnav (AFAIK, libdvdnav4). They should be in the repositories. Hope that'll help!:)

And, just what player do you use?

---

### Post by forger on 2008-10-19
Try this in terminal:
```
sudo apt-get install ubuntu-restricted-extras
```
It will install the most common restricted packages a desktop might need :) (java, flash, codecs etc)

You probably need the medibuntu third-party repository codecs too:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Be sure to read [this part]("https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs")!

---

### Post by AGSzabo on 2008-10-19
> And, just what player do you use?

totem


> (libdvdread3, i think)and libdvdnav (AFAIK, libdvdnav4)

these packages are allready installed. i try what forger told (download in progress :).

---

### Post by AGSzabo on 2008-10-19
i installed the restricted modules and (except java) now ist still does not work. in addition the install killed my synaptics manager that now either does not start anymore or when typing something into the search box it hangs and its window gets darker. whats up?

---

### Post by forger on 2008-10-19
Did you install the medibuntu reporsitory correctly as described at the link in the previous post?

It shouldn't be the packages fault.. try logging out and logging back in
If that doesn' fix it, try rebooting.

If it still isn't fixed, reply with the output of these commands:
```
apt-cache policy libdvdcss2
cat /etc/apt/sources.list*
sudo apt-get -f install
sudo apt-get update
```

---

### Post by AGSzabo on 2008-10-19
```
calla@sunny:~$ apt-cache policy libdvdcss2
libdvdcss2:
  Installiert: (keine)
  Kandidat: (keine)
  Versions-Tabelle:
calla@sunny:~$

calla@sunny:~$ cat /etc/apt/sources.list*
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Beta i386 (20081001)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://de.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://de.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://de.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://de.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
cat: /etc/apt/sources.list.d: Is a directory
calla@sunny:~$ 


calla@sunny:~$ sudo apt-get -f install
[sudo] password for calla: 
E: Konnte Lock /var/lib/dpkg/lock nicht bekommen - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

calla@sunny:~$ sudo apt-get update
OK   http://de.archive.ubuntu.com intrepid Release.gpg
OK   http://de.archive.ubuntu.com intrepid/main Translation-de
OK   http://de.archive.ubuntu.com intrepid/restricted Translation-de
OK   http://de.archive.ubuntu.com intrepid/universe Translation-de
OK   http://de.archive.ubuntu.com intrepid/multiverse Translation-de
OK   http://de.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://de.archive.ubuntu.com intrepid-updates/main Translation-de
Ign http://de.archive.ubuntu.com intrepid-updates/restricted Translation-de
Ign http://de.archive.ubuntu.com intrepid-updates/universe Translation-de
OK   http://security.ubuntu.com intrepid-security Release.gpg
Ign http://security.ubuntu.com intrepid-security/main Translation-de
Ign http://de.archive.ubuntu.com intrepid-updates/multiverse Translation-de
OK   http://de.archive.ubuntu.com intrepid Release   
OK   http://de.archive.ubuntu.com intrepid-updates Release
Ign http://security.ubuntu.com intrepid-security/restricted Translation-de
Ign http://security.ubuntu.com intrepid-security/universe Translation-de
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-de
OK   http://security.ubuntu.com intrepid-security Release
OK   http://de.archive.ubuntu.com intrepid/main Packages
OK   http://security.ubuntu.com intrepid-security/main Packages
OK   http://security.ubuntu.com intrepid-security/restricted Packages
OK   http://security.ubuntu.com intrepid-security/main Sources
OK   http://security.ubuntu.com intrepid-security/restricted Sources
OK   http://de.archive.ubuntu.com intrepid/restricted Packages
OK   http://de.archive.ubuntu.com intrepid/main Sources
OK   http://de.archive.ubuntu.com intrepid/restricted Sources
OK   http://de.archive.ubuntu.com intrepid/universe Packages
OK   http://de.archive.ubuntu.com intrepid/universe Sources
OK   http://de.archive.ubuntu.com intrepid/multiverse Packages
OK   http://de.archive.ubuntu.com intrepid/multiverse Sources
OK   http://de.archive.ubuntu.com intrepid-updates/main Packages
OK   http://de.archive.ubuntu.com intrepid-updates/restricted Packages
OK   http://de.archive.ubuntu.com intrepid-updates/main Sources
OK   http://de.archive.ubuntu.com intrepid-updates/restricted Sources
OK   http://security.ubuntu.com intrepid-security/universe Packages
OK   http://security.ubuntu.com intrepid-security/universe Sources
OK   http://security.ubuntu.com intrepid-security/multiverse Packages
OK   http://security.ubuntu.com intrepid-security/multiverse Sources
OK   http://de.archive.ubuntu.com intrepid-updates/universe Packages
OK   http://de.archive.ubuntu.com intrepid-updates/universe Sources
OK   http://de.archive.ubuntu.com intrepid-updates/multiverse Packages
OK   http://de.archive.ubuntu.com intrepid-updates/multiverse Sources
E: Konnte Lock /var/lib/dpkg/lock nicht bekommen - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
calla@sunny:~$ 

```

---

### Post by forger on 2008-10-19
Try this:
**[COLOR="Red"]WARNING! Use at your own risk - Could break the packaging system - backup is recommended[/COLOR]**

```

cat /etc/apt/sources.list.d/*
sudo rm /var/lib/dpkg/lock
sudo apt-get -f install
sudo apt-get update
sudo apt-get install libdvdcss2
```

Post back with the output again :)

---

### Post by AGSzabo on 2008-10-20
```

calla@sunny:~$ cat /etc/apt/sources.list.d/*
cat: /etc/apt/sources.list.d/*: No such file or directory
calla@sunny:~$

calla@sunny:~$ sudo rm /var/lib/dpkg/lock
[sudo] password for calla: 
calla@sunny:~$ 

calla@sunny:~$ sudo apt-get -f install
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
calla@sunny:~$

calla@sunny:~$ sudo apt-get update
OK   http://security.ubuntu.com intrepid-security Release.gpg
Ign http://security.ubuntu.com intrepid-security/main Translation-de         
Hole:1 http://de.archive.ubuntu.com intrepid Release.gpg [189B]               
OK   http://de.archive.ubuntu.com intrepid/main Translation-de                
OK   http://de.archive.ubuntu.com intrepid/restricted Translation-de
OK   http://de.archive.ubuntu.com intrepid/universe Translation-de
OK   http://de.archive.ubuntu.com intrepid/multiverse Translation-de
OK   http://de.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://de.archive.ubuntu.com intrepid-updates/main Translation-de
Ign http://de.archive.ubuntu.com intrepid-updates/restricted Translation-de
Ign http://de.archive.ubuntu.com intrepid-updates/universe Translation-de
OK   http://archive.canonical.com intrepid Release.gpg
Ign http://archive.canonical.com intrepid/partner Translation-de
Ign http://security.ubuntu.com intrepid-security/restricted Translation-de
Ign http://security.ubuntu.com intrepid-security/universe Translation-de
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-de
Ign http://de.archive.ubuntu.com intrepid-updates/multiverse Translation-de
Hole:2 http://de.archive.ubuntu.com intrepid Release [65,9kB]
OK   http://archive.canonical.com intrepid Release                          
OK   http://security.ubuntu.com intrepid-security Release                   
OK   http://archive.canonical.com intrepid/partner Packages                
OK   http://security.ubuntu.com intrepid-security/main Packages
OK   http://security.ubuntu.com intrepid-security/restricted Packages
OK   http://security.ubuntu.com intrepid-security/main Sources
OK   http://security.ubuntu.com intrepid-security/restricted Sources
OK   http://security.ubuntu.com intrepid-security/universe Packages
OK   http://security.ubuntu.com intrepid-security/universe Sources
OK   http://security.ubuntu.com intrepid-security/multiverse Packages
OK   http://security.ubuntu.com intrepid-security/multiverse Sources
OK   http://de.archive.ubuntu.com intrepid-updates Release
Hole:3 http://de.archive.ubuntu.com intrepid/main Packages [1260kB]
Hole:4 http://de.archive.ubuntu.com intrepid/restricted Packages [7248B]       
Hole:5 http://de.archive.ubuntu.com intrepid/main Sources [503kB]              
Hole:6 http://de.archive.ubuntu.com intrepid/restricted Sources [2623B]        
Hole:7 http://de.archive.ubuntu.com intrepid/universe Packages [4525kB]        
Hole:8 http://de.archive.ubuntu.com intrepid/universe Sources [1978kB]         
Hole:9 http://de.archive.ubuntu.com intrepid/multiverse Packages [201kB]       
Hole:10 http://de.archive.ubuntu.com intrepid/multiverse Sources [95,6kB]      
OK   http://de.archive.ubuntu.com intrepid-updates/main Packages               
OK   http://de.archive.ubuntu.com intrepid-updates/restricted Packages         
OK   http://de.archive.ubuntu.com intrepid-updates/main Sources                
OK   http://de.archive.ubuntu.com intrepid-updates/restricted Sources          
OK   http://de.archive.ubuntu.com intrepid-updates/universe Packages           
OK   http://de.archive.ubuntu.com intrepid-updates/universe Sources            
OK   http://de.archive.ubuntu.com intrepid-updates/multiverse Packages         
OK   http://de.archive.ubuntu.com intrepid-updates/multiverse Sources          
Es wurden 8640kB in 1min19s geholt (108kB/s)                                   
Paketlisten werden gelesen... Fertig
calla@sunny:~$ 

calla@sunny:~$ sudo apt-get install libdvdcss2
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
Paket libdvdcss2 ist nicht verfügbar, wird aber von einem anderen
Paket referenziert. Das kann heißen, dass das Paket fehlt, dass es veraltet
ist oder nur aus einer anderen Quelle verfügbar ist.
E: Paket libdvdcss2 hat keinen Installationskandidaten
calla@sunny:~$ 

```

---

### Post by forger on 2008-10-20
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get install medibuntu-keyring
sudo apt-get update
sudo apt-get install libdvdcss2 ubuntu-restricted-extras w32codecs

```
(in that order)

Reply with the output once more :)

---

### Post by teeny on 2008-10-20
I am going to be suggest to that 's relevant website which will hopefully guide you if your matter is just relevant to CD,DVD or videos,audios, movies and etc anything relevant to those topics just contact there and visit this website make sure you will
get some satisfactory answers.
[http://orbisdigital.co.uk/](http://orbisdigital.co.uk/)
Thanks

---

### Post by AGSzabo on 2008-10-20
```
calla@sunny:~$ sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
[sudo] password for calla: 
--2008-10-20 21:18:09--  http://www.medibuntu.org/sources.list.d/intrepid.list
Auflösen des Hostnamen »www.medibuntu.org«.... 87.98.242.110
Verbindungsaufbau zu www.medibuntu.org|87.98.242.110|:80... verbunden.
HTTP Anforderung gesendet, warte auf Antwort... 200 OK
Länge: 230 [text/plain]
In »/etc/apt/sources.list.d/medibuntu.list« speichern.

100%[======================================>] 230         --.-K/s   in 0s      

2008-10-20 21:18:10 (14,8 MB/s) - »/etc/apt/sources.list.d/medibuntu.list« gespeichert [230/230]

calla@sunny:~$ sudo apt-get update
Hole:1 http://packages.medibuntu.org intrepid Release.gpg [189B]
OK   http://security.ubuntu.com intrepid-security Release.gpg                  
Ign http://security.ubuntu.com intrepid-security/main Translation-de           
OK   http://archive.canonical.com intrepid Release.gpg                         
Ign http://archive.canonical.com intrepid/partner Translation-de               
Hole:2 http://de.archive.ubuntu.com intrepid Release.gpg [189B]                
OK   http://de.archive.ubuntu.com intrepid/main Translation-de                 
OK   http://de.archive.ubuntu.com intrepid/restricted Translation-de           
OK   http://de.archive.ubuntu.com intrepid/universe Translation-de             
OK   http://de.archive.ubuntu.com intrepid/multiverse Translation-de           
OK   http://de.archive.ubuntu.com intrepid-updates Release.gpg                 
Ign http://de.archive.ubuntu.com intrepid-updates/main Translation-de          
Ign http://de.archive.ubuntu.com intrepid-updates/restricted Translation-de    
Ign http://de.archive.ubuntu.com intrepid-updates/universe Translation-de      
Ign http://security.ubuntu.com intrepid-security/restricted Translation-de     
Ign http://security.ubuntu.com intrepid-security/universe Translation-de       
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-de
OK   http://archive.canonical.com intrepid Release                            
Ign http://de.archive.ubuntu.com intrepid-updates/multiverse Translation-de   
Ign http://packages.medibuntu.org intrepid/free Translation-de                 
Hole:3 http://de.archive.ubuntu.com intrepid Release [65,9kB]                 
OK   http://security.ubuntu.com intrepid-security Release                      
OK   http://archive.canonical.com intrepid/partner Packages                    
OK   http://security.ubuntu.com intrepid-security/main Packages                
Ign http://packages.medibuntu.org intrepid/non-free Translation-de             
OK   http://security.ubuntu.com intrepid-security/restricted Packages
OK   http://security.ubuntu.com intrepid-security/main Sources                 
OK   http://security.ubuntu.com intrepid-security/restricted Sources           
OK   http://de.archive.ubuntu.com intrepid-updates Release                     
OK   http://security.ubuntu.com intrepid-security/universe Packages           
OK   http://security.ubuntu.com intrepid-security/universe Sources          
OK   http://security.ubuntu.com intrepid-security/multiverse Packages       
OK   http://security.ubuntu.com intrepid-security/multiverse Sources        
Hole:4 http://packages.medibuntu.org intrepid Release [11,7kB]              
Hole:5 http://de.archive.ubuntu.com intrepid/main Packages [1261kB]
Ign http://packages.medibuntu.org intrepid Release          
Hole:6 http://packages.medibuntu.org intrepid/free Packages [5077B]            
Hole:7 http://packages.medibuntu.org intrepid/non-free Packages [10,5kB]       
Hole:8 http://de.archive.ubuntu.com intrepid/restricted Packages [7248B]       
Hole:9 http://de.archive.ubuntu.com intrepid/main Sources [503kB]              
Hole:10 http://de.archive.ubuntu.com intrepid/restricted Sources [2623B]       
Hole:11 http://de.archive.ubuntu.com intrepid/universe Packages [4525kB]       
Hole:12 http://de.archive.ubuntu.com intrepid/universe Sources [1979kB]        
Hole:13 http://de.archive.ubuntu.com intrepid/multiverse Packages [201kB]      
Hole:14 http://de.archive.ubuntu.com intrepid/multiverse Sources [95,6kB]      
OK   http://de.archive.ubuntu.com intrepid-updates/main Packages               
OK   http://de.archive.ubuntu.com intrepid-updates/restricted Packages         
OK   http://de.archive.ubuntu.com intrepid-updates/main Sources                
OK   http://de.archive.ubuntu.com intrepid-updates/restricted Sources          
OK   http://de.archive.ubuntu.com intrepid-updates/universe Packages           
OK   http://de.archive.ubuntu.com intrepid-updates/universe Sources            
OK   http://de.archive.ubuntu.com intrepid-updates/multiverse Packages         
OK   http://de.archive.ubuntu.com intrepid-updates/multiverse Sources          
Es wurden 8668kB in 1min18s geholt (111kB/s)                                   
Paketlisten werden gelesen... Fertig
W: GPG error: http://packages.medibuntu.org intrepid Release: Die folgenden Signaturen konnten nicht überprüft werden, weil ihr öffentlicher Schlüssel nicht verfügbar ist: NO_PUBKEY 2EBC26B60C5A2783
W: Probieren Sie »apt-get update«, um diese Probleme zu korrigieren.
calla@sunny:~$ sudo apt-get install medibuntu-keyring
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
Die folgenden NEUEN Pakete werden installiert:
  medibuntu-keyring
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 14 nicht aktualisiert.
Es müssen 3448B an Archiven heruntergeladen werden.
Nach dieser Operation werden 49,2kB Plattenplatz zusätzlich benutzt.
WARNUNG: Die folgenden Pakete können nicht authentifiziert werden!
  medibuntu-keyring
Diese Pakete ohne Überprüfung installieren [j/N]? J
Hole:1 http://packages.medibuntu.org intrepid/free medibuntu-keyring 2008.04.20 [3448B]
Es wurden 3448B in 0s geholt (13,6kB/s) 
Wähle vormals abgewähltes Paket medibuntu-keyring.
(Lese Datenbank ... 121227 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke medibuntu-keyring (aus .../medibuntu-keyring_2008.04.20_all.deb) ...
Richte medibuntu-keyring ein (2008.04.20) ...
OK

calla@sunny:~$

calla@sunny:~$ sudo apt-get update
OK   http://de.archive.ubuntu.com intrepid Release.gpg
OK   http://de.archive.ubuntu.com intrepid/main Translation-de
OK   http://de.archive.ubuntu.com intrepid/restricted Translation-de
OK   http://de.archive.ubuntu.com intrepid/universe Translation-de
OK   http://de.archive.ubuntu.com intrepid/multiverse Translation-de
OK   http://de.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://de.archive.ubuntu.com intrepid-updates/main Translation-de
Ign http://de.archive.ubuntu.com intrepid-updates/restricted Translation-de   
Ign http://de.archive.ubuntu.com intrepid-updates/universe Translation-de     
Ign http://de.archive.ubuntu.com intrepid-updates/multiverse Translation-de    
OK   http://archive.canonical.com intrepid Release.gpg                         
Ign http://archive.canonical.com intrepid/partner Translation-de               
OK   http://security.ubuntu.com intrepid-security Release.gpg                  
Ign http://security.ubuntu.com intrepid-security/main Translation-de           
Ign http://security.ubuntu.com intrepid-security/restricted Translation-de     
Hole:1 http://packages.medibuntu.org intrepid Release.gpg [189B]               
OK   http://de.archive.ubuntu.com intrepid Release                             
OK   http://de.archive.ubuntu.com intrepid-updates Release                     
OK   http://archive.canonical.com intrepid Release                             
Ign http://security.ubuntu.com intrepid-security/universe Translation-de       
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-de     
OK   http://security.ubuntu.com intrepid-security Release                      
OK   http://de.archive.ubuntu.com intrepid/main Packages                       
OK   http://archive.canonical.com intrepid/partner Packages                    
OK   http://security.ubuntu.com intrepid-security/main Packages               
Ign http://packages.medibuntu.org intrepid/free Translation-de                
OK   http://security.ubuntu.com intrepid-security/restricted Packages          
OK   http://security.ubuntu.com intrepid-security/main Sources                 
OK   http://security.ubuntu.com intrepid-security/restricted Sources           
OK   http://de.archive.ubuntu.com intrepid/restricted Packages                 
OK   http://de.archive.ubuntu.com intrepid/main Sources                        
OK   http://de.archive.ubuntu.com intrepid/restricted Sources                  
OK   http://de.archive.ubuntu.com intrepid/universe Packages                   
OK   http://de.archive.ubuntu.com intrepid/universe Sources                    
OK   http://de.archive.ubuntu.com intrepid/multiverse Packages                 
OK   http://de.archive.ubuntu.com intrepid/multiverse Sources                  
OK   http://de.archive.ubuntu.com intrepid-updates/main Packages               
OK   http://de.archive.ubuntu.com intrepid-updates/restricted Packages        
OK   http://de.archive.ubuntu.com intrepid-updates/main Sources               
OK   http://de.archive.ubuntu.com intrepid-updates/restricted Sources         
OK   http://security.ubuntu.com intrepid-security/universe Packages           
OK   http://security.ubuntu.com intrepid-security/universe Sources            
OK   http://security.ubuntu.com intrepid-security/multiverse Packages         
OK   http://security.ubuntu.com intrepid-security/multiverse Sources          
Ign http://packages.medibuntu.org intrepid/non-free Translation-de            
OK   http://de.archive.ubuntu.com intrepid-updates/universe Packages
OK   http://de.archive.ubuntu.com intrepid-updates/universe Sources
OK   http://de.archive.ubuntu.com intrepid-updates/multiverse Packages
OK   http://de.archive.ubuntu.com intrepid-updates/multiverse Sources
Hole:2 http://packages.medibuntu.org intrepid Release [11,7kB]
OK   http://packages.medibuntu.org intrepid/free Packages
OK   http://packages.medibuntu.org intrepid/non-free Packages
Es wurden 11,9kB in 1s geholt (6106B/s)
Paketlisten werden gelesen... Fertig
calla@sunny:~$ 
calla@sunny:~$ sudo apt-get install libdvdcss2 ubuntu-restricted-extras w32codecs
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
ubuntu-restricted-extras ist schon die neueste Version.
Die folgenden zusätzlichen Pakete werden installiert:
  libstdc++5
Vorgeschlagene Pakete:
  mplayer
Die folgenden NEUEN Pakete werden installiert:
  libdvdcss2 libstdc++5 w32codecs
0 aktualisiert, 3 neu installiert, 0 zu entfernen und 14 nicht aktualisiert.
Es müssen 14,6MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 35,5MB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? J
Hole:1 http://de.archive.ubuntu.com intrepid/universe libstdc++5 1:3.3.6-17ubuntu1 [296kB]
Hole:2 http://packages.medibuntu.org intrepid/free libdvdcss2 1.2.10-0.2medibuntu1 [36,8kB]
Hole:3 http://packages.medibuntu.org intrepid/non-free w32codecs 20071007-0medibuntu3 [14,3MB]
Es wurden 14,6MB in 2min24s geholt (101kB/s)                                   
Wähle vormals abgewähltes Paket libdvdcss2.
(Lese Datenbank ... 121231 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke libdvdcss2 (aus .../libdvdcss2_1.2.10-0.2medibuntu1_i386.deb) ...
Wähle vormals abgewähltes Paket libstdc++5.
Entpacke libstdc++5 (aus .../libstdc++5_1%3a3.3.6-17ubuntu1_i386.deb) ...
Wähle vormals abgewähltes Paket w32codecs.
Entpacke w32codecs (aus .../w32codecs_20071007-0medibuntu3_i386.deb) ...
Richte libdvdcss2 ein (1.2.10-0.2medibuntu1) ...

Richte libstdc++5 ein (1:3.3.6-17ubuntu1) ...

Richte w32codecs ein (20071007-0medibuntu3) ...
Verarbeite Trigger für libc6 ...
ldconfig deferred processing now taking place
calla@sunny:~$ 


```

nah, it still does not work.. in totem. but in gxine and kaffeien it now works!

---

### Post by forger on 2008-10-22
try log out and log back in, maybe it will work then.. otherwise.. use xine/kaffeine :)

---

### Post by AGSzabo on 2008-10-22
relogging in and rebooting did not help... at least my synapcis does no more hang after the last update.

---

