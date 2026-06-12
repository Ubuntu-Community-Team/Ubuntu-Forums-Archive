---
title: "ubuntu(7.10) alsa drivers and emu 0404 HELP"
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by redhairfreerider on 2008-02-09
Newbie on ubuntu and linux in general,I installed version 7.1 4days ago.Installation package had alsa initial setup installed.Having no sound from emu 0404 I used Synaptic System Manager to get alsa drivers up to date.My card needs ver 1.0.16 and automatic update olny goes up to ver 1.0.14!So I downloaded alsa-drivers alsa-utils and alsa-lib and tried to install manually!First problem comes from dev/snd where I only have seq and timer files.When I run "./snddevices" a bunch of files are written under /dev/snd but upon rebot I only have the first 2 files I mentioned!2 problem I have is upon following alsa tutorial for installing drives when I run "make" under alsa-utils I get the following error message:

make[1]: Entering directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/include'
make all-am
make[2]: Entering directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/include'
make[2]: Leaving directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/include'
make[1]: Leaving directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/include'
Making all in alsactl
make[1]: Entering directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/alsactl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/alsactl'
Making all in alsaconf
make[1]: Entering directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/alsaconf'
Making all in po
make[2]: Entering directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/redhairfreerider/downloads/alsa-utils-1.0.16/alsaconf'
make: *** [all-recursive] Error 1

Can somebody please help me!!

---

### Post by perixx on 2008-02-09
Look here: [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+guide]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+guide")

regards, 
perixx

---

### Post by redhairfreerider on 2008-02-09
Tried the whole afternoon but nothing happened.It seem that I dont have snd moudules?Also Ubuntu sees my card as Sb audigy!What can I do?

---

### Post by perixx on 2008-02-09
Hello again...

I can't guarantee, but here are the alsa-packages installed in my system; perhaps you can find any that's missing in your system:
> dpkg -l *alsa*
Gewünscht=Unbekannt/Installieren/R=Entfernen/P=Säubern/Halten
| Status=Nicht/Installiert/Config/U=Entpackt/Fehlgeschl. Konf./Halb install.
|/ Fehler?=(kein)/Halten/R=Neuinst notw/X=beide (Status, Fehler: GROSS=schlecht)
||/ Name           Version        Beschreibung
+++-==============-==============-============================================
un  alsa           <keine>        (keine Beschreibung vorhanden)
ii  alsa-base      1.0.13-3ubuntu ALSA driver configuration files
ii  alsa-oss       1.0.12-1       ALSA wrapper for OSS applications
ii  alsa-tools     1.0.13-1       Console based ALSA utilities for specific ha
ii  alsa-tools-gui 1.0.13-1       GUI based ALSA utilities for specific hardwa
ii  alsa-utils     1.0.13-1ubuntu ALSA utilities
ii  alsamixergui   0.9.0rc2-1-9   graphical soundcard mixer for ALSA soundcard
un  alsaplayer-com <keine>        (keine Beschreibung vorhanden)
ii  alsaplayer-jac 0.99.76-9      PCM player designed for ALSA (JACK output mo
un  alsaplayer-out <keine>        (keine Beschreibung vorhanden)
ii  gstreamer0.10- 0.10.12-0ubunt GStreamer plugin for ALSA
ii  libalsaplayer0 0.99.76-9      PCM player designed for ALSA (interface libr
un  libarts-alsa   <keine>        (keine Beschreibung vorhanden)
un  libclalsadrv   <keine>        (keine Beschreibung vorhanden)
ii  libclalsadrv1  1.0.1-3ubuntu1 ALSA driver C++ access library
un  libclalsadrvc2 <keine>        (keine Beschreibung vorhanden)
ii  libesd-alsa0   0.2.36-3ubuntu Enlightened Sound Daemon (ALSA) - Shared lib
ii  libsdl1.2debia 1.2.11-7ubuntu Simple DirectMedia Layer (with X11 and ALSA 
un  vlc-plugin-als <keine>        (keine Beschreibung vorhanden)
ii  xfce4-mixer-al 4.4.0-0ubuntu1 Xfce4 Mixer ALSA backend  
There are some packages that you won't need for sure, like alsaplayer-jack and xfce4...(unless you use Xubuntu). But check for the other packages, like alsa-base, -tools, -utils and so on. If in doubt, reinstall them - perhaps it helps. You could also check on the alsa-homepage about your audio chip, if it's supported at all: 
[http://www.alsa-project.org/main/index.php/Matrix:Main]("http://www.alsa-project.org/main/index.php/Matrix:Main")

You also can install 'modconf', a CLI-UI for browsing and configuring your system modules:  ```
sudo apt-get install modconf
```It's possible to simply add/remove missing/superfluous kernel modules with it - very convenient, but be careful not to change anything unless you're sure what you're doing! 

Should Alsa not support your soundchip, OSSv3 (standard Ubunutu) or OSSv4  might fill the gap - check out the infos in this thread: 
[http://ubuntuforums.org/showpost.php?p=4205399&postcount=9]("http://ubuntuforums.org/showpost.php?p=4205399&postcount=9")

Good luck!

perixx

---

