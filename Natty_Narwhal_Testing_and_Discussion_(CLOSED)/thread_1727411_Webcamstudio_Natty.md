---
title: "Webcamstudio Natty"
date: 2011-04-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by DMKryl on 2011-04-12
Hi i've trying to install webcamstudio, and i can't make it work,

at first i downloaded the debs in the main page 
[http://www.ws4gl.org/download/installing-on-ubuntu](http://www.ws4gl.org/download/installing-on-ubuntu)
**[http://code.google.com/p/webcamstudio/downloads/list](http://code.google.com/p/webcamstudio/downloads/list)**

but all packages tell me something like this
```
Lintian check results for /media/sda3/Installers/Programs/Debs/webcamstudio_0.57alpha2_all.deb:
E: webcamstudio: control-file-has-bad-owner postinst patrick/patrick != root/root 
E: webcamstudio: wrong-file-owner-uid-or-gid etc/ 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid etc/init.d/ 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid etc/init.d/webcamstudio 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid etc/rc2.d/ 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid etc/rc2.d/S99webcamstudio 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid etc/rc3.d/ 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid etc/rc3.d/S99webcamstudio 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid etc/rc4.d/ 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid etc/rc4.d/S99webcamstudio 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid etc/rc5.d/ 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid etc/rc5.d/S99webcamstudio 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/ 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/bin/ 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/bin/webcamstudio 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/lib/ 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/lib/webcamstudio/ 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/lib/webcamstudio/README.TXT 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/lib/webcamstudio/WebcamStudio.jar 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/lib/webcamstudio/lib/ 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/lib/webcamstudio/lib/AbsoluteLayout.jar 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/lib/webcamstudio/lib/appframework-1.0.3.jar 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/lib/webcamstudio/lib/commons-cli-1.2.jar 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/lib/webcamstudio/lib/commons-codec-1.2.jar 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/lib/webcamstudio/lib/commons-httpclient-3.1.jar 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/lib/webcamstudio/lib/dbus.jar 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/lib/webcamstudio/lib/gstreamer-java-1.4.jar 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/lib/webcamstudio/lib/jcl104-over-slf4j-1.4.2.jar 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/lib/webcamstudio/lib/jna-3.2.4.jar 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/lib/webcamstudio/lib/jtwitter.jar 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/lib/webcamstudio/lib/mail.jar 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/lib/webcamstudio/lib/netty-3.1.5.GA.jar 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/lib/webcamstudio/lib/swing-worker-1.1.jar 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/ 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/applications/ 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/applications/webcamstudio.desktop 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/pixmaps/ 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/pixmaps/webcamstudio.png 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/ 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/ 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/Alert.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/Lights.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/Rain.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/Snow1.0.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/TuxPeek1.0.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/WS4GLBlinkingLogo.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/WavingHand.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/bars.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/big_flames.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/coin_roll.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/ducks.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/electric_fence.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/fire.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/ghost.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/gold_gold-n-silver_sparkle.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/gold_sparkle_frame.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/pumpkin.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/slow_moon_transit.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/sparkles.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/webcamstudio_coin.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/webcamstudio_coin2.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/animations/wipers.anm 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/webcamstudio-src/ 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/webcamstudio-src/Makefile 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/webcamstudio-src/README 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/webcamstudio-src/comp.sh 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/webcamstudio-src/libwebcamstudio.c 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/webcamstudio-src/webcamstudio.c 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/widgets/ 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/widgets/NY_Daily_News-Photo.xml 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/widgets/USA_National_Debt_Clock.xml 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/widgets/USA_Threat_Level.xml 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/widgets/Weatherbug-Beauport.xml 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/widgets/Weatherbug-LosAngeles.xml 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/widgets/Weatherbug-Mexico.xml 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/widgets/Weatherbug-Montreal.xml 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/widgets/Weatherbug-NewYork.xml 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/widgets/Weatherbug-Paris.xml 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/widgets/Weatherbug-PuertoRico-Argentina.xml 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/widgets/Weatherbug-Washington-DC.xml 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/widgets/osnews-rss.xml 1000/1000 
E: webcamstudio: wrong-file-owner-uid-or-gid usr/share/webcamstudio/widgets/ubuntu-rss.xml 1000/1000 

```

So i've tried to compile and manual install the program with the page instructions
[http://www.ws4gl.org/download/compiling](http://www.ws4gl.org/download/compiling)
[http://www.ws4gl.org/download/manual-installation](http://www.ws4gl.org/download/manual-installation)

i've compiled correctly the program, but i can't install it or make the devices to make it work the make file in the directions output me this

```
ledah@Sasha:~/webcamstudio-read-only/trunk/vloopback$ sudo make install
make -C /lib/modules/`uname -r`/build M=/home/ledah/webcamstudio-read-only/trunk/vloopback modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  INSTALL /home/ledah/webcamstudio-read-only/trunk/vloopback/webcamstudio.ko
  DEPMOD  2.6.38-8-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
depmod -ae
WARNING: -e needs -E or -F

```

uname -r= 2.6.38-8-generic

this is the makefile [http://pastebin.com/CcXuLrFz](http://pastebin.com/CcXuLrFz)

thx in advance for any help

---

### Post by uRock on 2011-04-12
Moved to Natty Narwhal Testing & Discussion.

---

