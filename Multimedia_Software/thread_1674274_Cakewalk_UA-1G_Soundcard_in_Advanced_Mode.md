---
title: "Cakewalk UA-1G Soundcard in Advanced Mode?"
date: 2011-01-23
forum: Multimedia Software
---

### Post by HeyMelvin on 2011-01-23
[SIZE=2]Hi, my first post, please help! Just bought the Roland UA-1G Soundcard.

Has any one got this Sound card to work in Advanced mode: i.e 96KHz / 24 bit[/SIZE] [SIZE=2]

It works as a plug and play soundcard at 44Hz 16bit - but Alsa doesn't seem to support the "advanced mode"[/SIZE] [SIZE=2]

There is a kernel module driver here[/SIZE] [SIZE=2]

[http://michaelminn.com/linux/mmusbaudio/](http://michaelminn.com/linux/mmusbaudio/)[/SIZE]  [SIZE=2]

Couldn't get it to work though, I wonder if anyone else has??[/SIZE] [SIZE=2]

When I perform 
**$ sudo make**
I get this error
[/SIZE]> make -C /lib/modules/`uname -r`/build SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  CC [M]  /home/rhid/mmusbaudio/mmusbaudio.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "register_sound_midi" [/home/rhid/mmusbaudio/mmusbaudio.ko] undefined!
WARNING: "register_sound_mixer" [/home/rhid/mmusbaudio/mmusbaudio.ko] undefined!
WARNING: "unregister_sound_dsp" [/home/rhid/mmusbaudio/mmusbaudio.ko] undefined!
WARNING: "register_sound_dsp" [/home/rhid/mmusbaudio/mmusbaudio.ko] undefined!
WARNING: "unregister_sound_mixer" [/home/rhid/mmusbaudio/mmusbaudio.ko] undefined!
WARNING: "unregister_sound_midi" [/home/rhid/mmusbaudio/mmusbaudio.ko] undefined!
  CC      /home/rhid/mmusbaudio/mmusbaudio.mod.o
  LD [M]  /home/rhid/mmusbaudio/mmusbaudio.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
g++ -O0 -g3 -Wall -o mmusbplay mmusbplay.cpp
make: g++: Command not found
make: *** [mmusbplay] Error 127[SIZE=2]
I'm running Ubuntu 10.10, [/SIZE] [SIZE=2]
Kernel 2.6.35-24-generic
Alsa 1.0.23

Need help badly,[/SIZE] [SIZE=2]

Thanks[/SIZE] [SIZE=2]

Rhid[/SIZE]

---

### Post by HeyMelvin on 2011-01-24
I seem to be making 'a mountain out of a molehill'. Just tested the soundcard using audacity and it works in advanced mode and at all the different sample rates.

How I tested is....keep souncard in advanced mode and change the sample rates on the soundcard using the sample rate switch configuration panel located on the back of the soundcard.....NOTE: you must unplug soundcard between sample rate change or between basic and advance mode changes for the computer to detect new settings

Then in Audacity change the project sample rate according to the sample rate set on the soundcard....then record something...I just plugged a mp3 player into the mic in socket...
If Audacity and soundcard bitrates match you should be able to record at 96KHz....Using my system anyway...and I did update ALSA prior to testing so don't know about older versions..

Seems to have worked anyway....Will see how it goes

---

### Post by cchhrriiss121212 on 2011-01-24
The driver up there should not be necessary as it is for OSS which is not used by Ubuntu. If you need any more info, you may want to bookmark this:
[http://alsa.opensrc.org/index.php/Cakewalk_UA-1G](http://alsa.opensrc.org/index.php/Cakewalk_UA-1G)

---

### Post by teddy92 on 2011-02-18
Hi i have the same issue with mmusbaudio.
I'm using Ubuntu studio 10.10 and i'm trying to install the driver to use the advanced mode on roland um-g2 because so there is less latency.
can anyone help me please?
my error is the same of melvin's :
teddy@ubuntu-studio:~/mmusbaudio$ sudo make
make -C /lib/modules/`uname -r`/build SUBDIRS=`pwd` modules
make[1]: ingresso nella directory "/usr/src/linux-headers-2.6.35-25-generic"
  CC [M]  /home/teddy/mmusbaudio/mmusbaudio.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "register_sound_midi" [/home/teddy/mmusbaudio/mmusbaudio.ko] undefined!
WARNING: "register_sound_mixer" [/home/teddy/mmusbaudio/mmusbaudio.ko] undefined!
WARNING: "unregister_sound_dsp" [/home/teddy/mmusbaudio/mmusbaudio.ko] undefined!
WARNING: "register_sound_dsp" [/home/teddy/mmusbaudio/mmusbaudio.ko] undefined!
WARNING: "unregister_sound_mixer" [/home/teddy/mmusbaudio/mmusbaudio.ko] undefined!
WARNING: "unregister_sound_midi" [/home/teddy/mmusbaudio/mmusbaudio.ko] undefined!
  CC      /home/teddy/mmusbaudio/mmusbaudio.mod.o
  LD [M]  /home/teddy/mmusbaudio/mmusbaudio.ko
make[1]: uscita dalla directory "/usr/src/linux-headers-2.6.35-25-generic"
g++ -O0 -g3 -Wall -o mmusbplay mmusbplay.cpp
make: g++: comando non trovato
make: *** [mmusbplay] Errore 127

thanks in advance

---

