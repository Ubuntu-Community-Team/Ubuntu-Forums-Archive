---
title: "Flash Player killed after upgrade to Firefox 3.6.8"
date: 2010-08-04
forum: Multimedia Software
---

### Post by AstroPhysik on 2010-08-04
Hello,
I'm running ubuntu 9.04 AMD64 Bit

last week i did the upgrade to the new Mozilla Firefox 3.6.8, and now my Flashplayer ist not working anymore. (e.g. myspace) I have the flashplugin-installer and flashplugin-nonfree, each 10.1.53.64

The downloads, the new Firefox gives me are not working..  Any Idea?

I already tried the new downloaded file with: 

> sudo rm /usr/lib/mozilla/plugins/libflashplayer.so
sudo cp ~/Desktop/libflashplayer.so /usr/lib/mozilla/plugins
 but it did not work..

Thanx A.P.

---

### Post by AstroPhysik on 2010-08-04
regarding to:
[http://ubuntuforums.org/showthread.php?t=1484202](http://ubuntuforums.org/showthread.php?t=1484202)

i installed the first aid plugin and it solved my problem.

greetz AP

> 
Please wait...DON'T CLOSE THIS TERMINAL!
[sudo] password for user: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht länger benötigt:
  libaccess-bridge-java gstreamer0.10-plugins-ugly libswfdec-0.8-0
  libswt-gtk-3.4-jni libswt-cairo-gtk-3.4-jni libswt-gtk-3.4-java
  ttf-telugu-fonts gstreamer0.10-ffmpeg ttf-bengali-fonts cdrdao
  libswt-mozilla-gtk-3.4-jni libsidplay1 rhino ttf-kannada-fonts
  ttf-wqy-zenhei ttf-oriya-fonts
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.
Die folgenden Pakete werden ENTFERNT:
  swfdec-mozilla*
0 aktualisiert, 0 neu installiert, 1 zu entfernen und 0 nicht aktualisiert.
Nach dieser Operation werden 315kB Plattenplatz freigegeben.
(Lese Datenbank ... 200319 Dateien und Verzeichnisse sind derzeit installiert.)
Entferne swfdec-mozilla ...
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
Paket mozilla-plugin-gnash ist nicht installiert, wird also auch nicht entfernt
Die folgenden Pakete wurden automatisch installiert und werden nicht länger benötigt:
  libaccess-bridge-java gstreamer0.10-plugins-ugly libswfdec-0.8-0 libswt-gtk-3.4-jni libswt-cairo-gtk-3.4-jni
  libswt-gtk-3.4-java ttf-telugu-fonts gstreamer0.10-ffmpeg ttf-bengali-fonts cdrdao libswt-mozilla-gtk-3.4-jni
  libsidplay1 rhino ttf-kannada-fonts ttf-wqy-zenhei ttf-oriya-fonts
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
E: Konnte Paket adobe-flashplugin nicht finden
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht länger benötigt:
  libaccess-bridge-java nspluginwrapper gstreamer0.10-plugins-ugly libswfdec-0.8-0 libswt-gtk-3.4-jni
  libswt-cairo-gtk-3.4-jni libswt-gtk-3.4-java ttf-telugu-fonts gstreamer0.10-ffmpeg ttf-bengali-fonts
  flashplugin-installer cdrdao libswt-mozilla-gtk-3.4-jni libsidplay1 rhino ttf-kannada-fonts ttf-wqy-zenhei
  ttf-oriya-fonts
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.
Die folgenden Pakete werden ENTFERNT:
  flashplugin-nonfree*
0 aktualisiert, 0 neu installiert, 1 zu entfernen und 0 nicht aktualisiert.
Nach dieser Operation werden 41,0kB Plattenplatz freigegeben.
(Lese Datenbank ... 200303 Dateien und Verzeichnisse sind derzeit installiert.)
Entferne flashplugin-nonfree ...
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht länger benötigt:
  libaccess-bridge-java nspluginwrapper gstreamer0.10-plugins-ugly libswfdec-0.8-0 libswt-gtk-3.4-jni
  libswt-cairo-gtk-3.4-jni libswt-gtk-3.4-java ttf-telugu-fonts gstreamer0.10-ffmpeg ttf-bengali-fonts cdrdao
  libswt-mozilla-gtk-3.4-jni libsidplay1 rhino ttf-kannada-fonts ttf-wqy-zenhei ttf-oriya-fonts
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.
Die folgenden Pakete werden ENTFERNT:
  flashplugin-installer*
0 aktualisiert, 0 neu installiert, 1 zu entfernen und 0 nicht aktualisiert.
Nach dieser Operation werden 180kB Plattenplatz freigegeben.
(Lese Datenbank ... 200300 Dateien und Verzeichnisse sind derzeit installiert.)
Entferne flashplugin-installer ...
Lösche Konfigurationsdateien von flashplugin-installer ...
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht länger benötigt:
  libaccess-bridge-java gstreamer0.10-plugins-ugly libswfdec-0.8-0 libswt-gtk-3.4-jni libswt-cairo-gtk-3.4-jni
  libswt-gtk-3.4-java ttf-telugu-fonts gstreamer0.10-ffmpeg ttf-bengali-fonts cdrdao libswt-mozilla-gtk-3.4-jni
  libsidplay1 rhino ttf-kannada-fonts ttf-wqy-zenhei ttf-oriya-fonts
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.
Die folgenden zusätzlichen Pakete werden installiert:
  flashplugin-installer
Vorgeschlagene Pakete:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
Die folgenden NEUEN Pakete werden installiert:
  flashplugin-installer flashplugin-nonfree
0 aktualisiert, 2 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen noch 0B von 21,1kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 221kB Plattenplatz zusätzlich benutzt.
Vorkonfiguration der Pakete ...
Wähle vormals abgewähltes Paket flashplugin-installer.
(Lese Datenbank ... 200293 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke flashplugin-installer (aus .../flashplugin-installer_10.1.53.64ubuntu0.9.04.1_amd64.deb) ...
Wähle vormals abgewähltes Paket flashplugin-nonfree.
Entpacke flashplugin-nonfree (aus .../flashplugin-nonfree_10.1.53.64ubuntu0.9.04.1_amd64.deb) ...
Richte flashplugin-installer ein (10.1.53.64ubuntu0.9.04.1) ...
Downloading...
--2010-08-04 15:24:37--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz)
Auflösen des Hostnamen »archive.canonical.com«.... 91.189.88.33
Verbindungsaufbau zu archive.canonical.com|91.189.88.33|:80... verbunden.
HTTP Anforderung gesendet, warte auf Antwort... 200 OK
Länge: 4739416 (4,5M) [application/x-gzip]
In »./adobe-flashplugin_10.1.53.64.orig.tar.gz« speichern.

     0K .......... .......... .......... .......... ..........  1%  449K 10s
    50K .......... .......... .......... .......... ..........  2% 1,68M 6s
   100K .......... .......... .......... .......... ..........  3% 1,18M 5s
   150K .......... .......... .......... .......... ..........  4% 3,51M 4s
   200K .......... .......... .......... .......... ..........  5% 1,93M 4s
   250K .......... .......... .......... .......... ..........  6% 11,3M 3s
   300K .......... .......... .......... .......... ..........  7% 3,36M 3s
   350K .......... .......... .......... .......... ..........  8% 3,84M 3s
   400K .......... .......... .......... .......... ..........  9% 11,6M 2s
   450K .......... .......... .......... .......... .......... 10% 2,47M 2s
   500K .......... .......... .......... .......... .......... 11% 10,9M 2s
   550K .......... .......... .......... .......... .......... 12% 11,4M 2s
   600K .......... .......... .......... .......... .......... 14% 11,5M 2s
   650K .......... .......... .......... .......... .......... 15% 9,25M 2s
   700K .......... .......... .......... .......... .......... 16% 3,69M 2s
   750K .......... .......... .......... .......... .......... 17% 11,7M 1s
   800K .......... .......... .......... .......... .......... 18% 10,8M 1s
   850K .......... .......... .......... .......... .......... 19% 11,3M 1s
   900K .......... .......... .......... .......... .......... 20% 11,0M 1s
   950K .......... .......... .......... .......... .......... 21% 11,7M 1s
  1000K .......... .......... .......... .......... .......... 22% 6,75M 1s
  1050K .......... .......... .......... .......... .......... 23% 11,3M 1s
  1100K .......... .......... .......... .......... .......... 24% 10,9M 1s
  1150K .......... .......... .......... .......... .......... 25% 11,6M 1s
  1200K .......... .......... .......... .......... .......... 27% 1,23M 1s
  1250K .......... .......... .......... .......... .......... 28% 9,34M 1s
  1300K .......... .......... .......... .......... .......... 29% 16,4M 1s
  1350K .......... .......... .......... .......... .......... 30% 15,9M 1s
  1400K .......... .......... .......... .......... .......... 31% 15,1M 1s
  1450K .......... .......... .......... .......... .......... 32% 15,2M 1s
  1500K .......... .......... .......... .......... .......... 33% 6,03M 1s
  1550K .......... .......... .......... .......... .......... 34% 13,4M 1s
  1600K .......... .......... .......... .......... .......... 35% 14,4M 1s
  1650K .......... .......... .......... .......... .......... 36% 11,1M 1s
  1700K .......... .......... .......... .......... .......... 37% 12,9M 1s
  1750K .......... .......... .......... .......... .......... 38% 14,6M 1s
  1800K .......... .......... .......... .......... .......... 39% 12,7M 1s
  1850K .......... .......... .......... .......... .......... 41% 2,12M 1s
  1900K .......... .......... .......... .......... .......... 42% 6,22M 1s
  1950K .......... .......... .......... .......... .......... 43% 2,78M 1s
  2000K .......... .......... .......... .......... .......... 44% 9,13M 1s
  2050K .......... .......... .......... .......... .......... 45% 11,2M 1s
  2100K .......... .......... .......... .......... .......... 46% 3,03M 1s
  2150K .......... .......... .......... .......... .......... 47% 8,81M 1s
  2200K .......... .......... .......... .......... .......... 48% 5,07M 1s
  2250K .......... .......... .......... .......... .......... 49% 30,7M 1s
  2300K .......... .......... .......... .......... .......... 50% 29,1M 1s
  2350K .......... .......... .......... .......... .......... 51% 4,48M 1s
  2400K .......... .......... .......... .......... .......... 52% 17,4M 0s
  2450K .......... .......... .......... .......... .......... 54% 12,6M 0s
  2500K .......... .......... .......... .......... .......... 55% 5,60M 0s
  2550K .......... .......... .......... .......... .......... 56% 13,7M 0s
  2600K .......... .......... .......... .......... .......... 57% 11,0M 0s
  2650K .......... .......... .......... .......... .......... 58% 11,1M 0s
  2700K .......... .......... .......... .......... .......... 59% 11,3M 0s
  2750K .......... .......... .......... .......... .......... 60% 11,3M 0s
  2800K .......... .......... .......... .......... .......... 61% 4,99M 0s
  2850K .......... .......... .......... .......... .......... 62% 13,3M 0s
  2900K .......... .......... .......... .......... .......... 63% 14,2M 0s
  2950K .......... .......... .......... .......... .......... 64% 11,4M 0s
  3000K .......... .......... .......... .......... .......... 65% 11,2M 0s
  3050K .......... .......... .......... .......... .......... 66% 4,62M 0s
  3100K .......... .......... .......... .......... .......... 68% 15,0M 0s
  3150K .......... .......... .......... .......... .......... 69% 12,1M 0s
  3200K .......... .......... .......... .......... .......... 70% 11,2M 0s
  3250K .......... .......... .......... .......... .......... 71% 11,5M 0s
  3300K .......... .......... .......... .......... .......... 72% 11,1M 0s
  3350K .......... .......... .......... .......... .......... 73% 6,58M 0s
  3400K .......... .......... .......... .......... .......... 74% 9,46M 0s
  3450K .......... .......... .......... .......... .......... 75% 11,3M 0s
  3500K .......... .......... .......... .......... .......... 76% 9,84M 0s
  3550K .......... .......... .......... .......... .......... 77% 12,8M 0s
  3600K .......... .......... .......... .......... .......... 78% 11,0M 0s
  3650K .......... .......... .......... .......... .......... 79% 5,54M 0s
  3700K .......... .......... .......... .......... .......... 81% 14,9M 0s
  3750K .......... .......... .......... .......... .......... 82% 11,4M 0s
  3800K .......... .......... .......... .......... .......... 83% 11,3M 0s
  3850K .......... .......... .......... .......... .......... 84% 11,4M 0s
  3900K .......... .......... .......... .......... .......... 85% 5,70M 0s
  3950K .......... .......... .......... .......... .......... 86% 11,7M 0s
  4000K .......... .......... .......... .......... .......... 87% 12,8M 0s
  4050K .......... .......... .......... .......... .......... 88% 10,9M 0s
  4100K .......... .......... .......... .......... .......... 89% 11,0M 0s
  4150K .......... .......... .......... .......... .......... 90% 11,6M 0s
  4200K .......... .......... .......... .......... .......... 91% 3,57M 0s
  4250K .......... .......... .......... .......... .......... 92% 42,2M 0s
  4300K .......... .......... .......... .......... .......... 93% 29,3M 0s
  4350K .......... .......... .......... .......... .......... 95% 8,60M 0s
  4400K .......... .......... .......... .......... .......... 96% 16,7M 0s
  4450K .......... .......... .......... .......... .......... 97% 11,1M 0s
  4500K .......... .......... .......... .......... .......... 98% 3,75M 0s
  4550K .......... .......... .......... .......... .......... 99% 15,9M 0s
  4600K .......... .......... ........                        100% 12,0M=0,8s

2010-08-04 15:24:38 (5,89 MB/s) - »./adobe-flashplugin_10.1.53.64.orig.tar.gz« gespeichert [4739416/4739416]

Download done.
Flash Plugin installed.

Richte flashplugin-nonfree ein (10.1.53.64ubuntu0.9.04.1) ...
Finished! You can close this terminal. You must restart Firefox now.


---

