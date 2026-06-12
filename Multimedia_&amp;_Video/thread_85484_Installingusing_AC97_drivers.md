---
title: "Installing/using AC97 drivers"
date: 2005-11-02
forum: Multimedia &amp; Video
---

### Post by Diod on 2005-11-02
Hey, im trying to install AC97 drivers (since these are the ones i used when i had windows). To do this i downloaded realtek-linux-audiopack-3.4-6.tar.bz2, unpacked it and ran ./install it all went fine, it said it installed itself. So i reboot but i still dont have sound ingame.
I always had sound out of games, when listening to music and watching movies and hearing those sounds when clicking the mouse. But i still don't have sound when playing games(Americas Army, enemy territory)
When in AA i look at the sound modes it only says OpenAL

---

### Post by Kirzzy_Boy on 2005-11-02
Have you tried changing your Multimedia settings?
If not, try System > Preferences > Multimedia Systems Selector
Under Default Sink select ALSA and under Default Source select OSS
I hope this sorts it out;)

---

### Post by Diod on 2005-11-02
nope, doesnt work :(

---

### Post by Diod on 2005-11-03
Tried doing it with the help of [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Nvidia&card=.&chip=nForce&module=intel8x0](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Nvidia&card=.&chip=nForce&module=intel8x0) but i cant make it work :(

---

### Post by eddye on 2005-11-03
Sorry cant help

---

### Post by pizzach on 2005-11-03
I don't play many games, but my laptop uses a AC97 chipset.  As a general rule of thumb since Hoary I've had to update my audio driver to get any sound at all.  I never touched the realtek stuff personally.

The newest audio driver my mic and speakers finally seem to work totally without hitch. [http://www.alsa-project.org/](http://www.alsa-project.org/)  > Driver 10.0.10r2

All I do is the general 
./configure
make
sudo make install

In any case, have you updated your alsa drivers?  It seems you have been to the site but I'm just trying to make sure.

---

### Post by Diod on 2005-11-03
When i do ./configure this is what it says:

> checking for gcc... gcc checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/diod/alsa-driver-1.0.10rc2
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).


i cant find the dir with "my" kernel source

---

### Post by porsher_puddles on 2005-11-03
yeh i got similar sound problems to diod, i get sound with music,system sounds but games like frozen bubble or battleships i can't get sound.when i go into multimedia settings and run the sound test i get sound with the first test but not with the second

---

### Post by codejunkie on 2005-11-03
[quote=Diod]When i do ./configure this is what it says:



i cant find the dir with "my" kernel source[/quote] try ```
sudo apt-get update
``` 
```
sudo apt-get install build-essential linux-headers-`uname -r`
``` this will install the kernel source and basic compliers and such to install most software.

---

### Post by Diod on 2005-11-04
Driver 10.0.10r2 didnt work. I did compile it and made it and installed it(thx for that codejunkie :)), but its still the same. Could it have something to do with midi cause i cant hear midi when i test that. Anyway, ill be installing the newest alsa utils and alsa libs and check if that makes a diff.

---

### Post by Diod on 2005-11-05
I have also posted this on another forum, there are some replies that may give hints or something to help you help me?
[http://www.linuxhelp.ca/forums/index.php?act=ST&f=10&t=7139&st=0&#entry24747](http://www.linuxhelp.ca/forums/index.php?act=ST&f=10&t=7139&st=0&#entry24747)

---

### Post by Diod on 2005-11-05
I now have sound in wine while playing games. i had to pick aRts as sound provider instead of OSS, but still havent got sound in native linux games to work :(

---

### Post by Diod on 2005-11-07
bump

---

### Post by jomofrodo on 2005-11-27
Did you make sure that the on-board pci sound is enabled in your machine's BIOS.  I just spent a couple of days jumping through all of these hoops. At the end the module was compiled and loading (as verified by lsmod). But I was still getting "no device" errors from sound applications like XMMS. Then I did a *very* careful review of the lshw output and realized that the AC'97 device was not showing up at all. That's when I went into the BIOS settings and found that the on-board audio driver was disabled.  If you are like me, somewhere in the process of loading up the OS you may have gone into the BIOS and selected "load failsafe presets" or something similar. I believe that is when my on-board audio got disabled.  Anyway -- worth a check. Look at your lshw output to verify that the audio device is showing up. Also, make sure the soundcore is enabled (modprobe soundcore -- should show up in lsmod).

---

