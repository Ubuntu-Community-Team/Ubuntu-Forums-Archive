---
title: "installation of VLC"
date: 2011-09-17
forum: Multimedia Software
---

### Post by moijdikssekool on 2011-09-17
i try to install VLC. So i follow the advices found on Videolan:
apt-get update -> OK
and
apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc -> not OK, it returns:
> 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Aucune version du paquet mozilla-plugin-vlc n'est disponible, mais il existe dans la base
de données. Cela signifie en général que le paquet est manquant, qu'il est devenu obsolète
ou qu'il n'est disponible que sur une autre source

E: Impossible de trouver le paquet vlc
E: Impossible de trouver le paquet vlc-plugin-pulse
E: Le paquet « mozilla-plugin-vlc » n'a pas de version susceptible d'être installée

it's in french, it's written the packages are not found

---

### Post by dniMretsaM on 2011-09-17
What happens if you just do this:
```
sudo apt-get update
sudo apt-get install vlc
```
And do you have the multiverse repositories enabled (although I don't think that should matter)?

---

### Post by moijdikssekool on 2011-09-17
i added
> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe multiverse
from [http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html](http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html)to /etc/apt/sources.list. Now i have
> root@ubuntu:~# apt-get install vlc
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Certains paquets ne peuvent être installés. Ceci peut signifier
que vous avez demandé l'impossible, ou bien, si vous utilisez
la distribution unstable, que certains paquets n'ont pas encore
été créés ou ne sont pas sortis d'Incoming.
L'information suivante devrait vous aider à résoudre la situation : 

Les paquets suivants contiennent des dépendances non satisfaites :
 vlc : Dépend: libcucul0 (>= 0.99.beta13b-1) mais ne sera pas installé
       Dépend: libwxgtk2.6-0 (>= 2.6.3.2.2) mais ne sera pas installé
E: Paquets défectueuxdo you want me to translate? it says some pkg can't be installed -> not created yet. defective Pkg
my ubuntu is brand new, kubuntu 11, i did the test with Ubunbu too

---

### Post by howefield on 2011-09-18
Why are you root ?

You shouldn't need to add "hardy" (8.04) repositories to an 11.04 installation.

Remove them and try again. 

```
sudo apt-get update
sudo apt-get install vlc
```

---

### Post by moijdikssekool on 2011-09-18
here is the result
> ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty InRelease
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main TranslationIndex
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted TranslationIndex
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Translation-en
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main i386 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted i386 Packages          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main TranslationIndex             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted TranslationIndex       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vlcthe update loads some translations but if i go to langage support, english is the only proposed langage and whatever i do in the windows, i cant change langage but dont care, the problem is VLC, dont care about that (i change my kubuntu to ubuntu thanks to the usb drive install method and apparently it forgets some langage problems)

---

### Post by dniMretsaM on 2011-09-18
Search for it in KPackageKit and see what the results are.

---

### Post by moijdikssekool on 2011-09-18
it's ok
just before, i have tried apt-get install vlc, and it was OK... the pkg was temporary unavailable?

---

### Post by mc4man on 2011-09-18
open up your software sources (or whatever that is in kubuntu) and if the Cdrom is enabled (pretty sure it is) then disable & update your sources again
screen show SS in ubuntu and what I'm referring to

---

### Post by dniMretsaM on 2011-09-18
> **moijdikssekool said:**
> it's ok
just before, i have tried apt-get install vlc, and it was OK... the pkg was temporary unavailable?

Glad it worked! Mark the thread as solved please.

---

