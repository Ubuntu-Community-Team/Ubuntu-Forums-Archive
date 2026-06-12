---
title: "Confused with JACK and JACK RACK as a simple effects unit for guitar"
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by renzokuken on 2006-10-01
hi,

I've been reading the Ubuntu Studio wiki and threads here and have to say i'm very impressed. I'm currently following the studio setup guide on the wiki.

Anyways, i want to use JACK-RACK or Creox as an effects unit for playing guitar. i@m not looking to record anything or go anywhere hi-tech, i just wanna make my guitar sound cool.

Is it as simple as installing Jack and Jack-Rack/Creox, pluging my guitar into my Line-In port and playing? I cant find a tutorial anywhere specifically explaining this.

Thanks

---

### Post by monnezzaio on 2006-10-01
here is my experience 

PC Laptop Compaq R4100 (AMD Sempron 3200 RAM 1GB)
audio: edirol UA-25 (USB with mic-preampli and Hi-Zi Impedance switch)
guitar: hohner G3T

problems are xruns in jack (buffer under run o over run) that locks all sounds

1)use blackbox as windows manager 
2) stop all service processes or modules unuseful
3) qjackctl
4)jack-rack

for a big distorced guitar


use 
qjackctl  (jack gui)
jack-rack
LADSA caps

48 Khz 11 ms latency 


script to stop almost all is stopable (run it with sudo two o three times for dependecies of modules)

/etc/init.d/networking stop
/etc/init.d/ssh stop
/etc/init.d/samba stop
/etc/init.d/dbus stop
/etc/init.d/cupsys stop
/etc/init.d/powernowd stop
/etc/init.d/crond stop
/etc/init.d/atd stop
/etc/init.d/hplip stop
killall gam_server
killall artsd
killall ssh-agent
killall pdflush
killall dbus-daemon
killall dbus-launch
killall syslogd
killall cron
killall klogd
killall dcopserver
killall gconfd-2
killall bonobo-activation-server
swapoff -a
umount /dev/sda1
umount /dev/hda1
umount /dev/hda5
rmmod b2c2_flexcop_pci
rmmod b2c2_flexcop
rmmod stv0297
rmmod stv0299
rmmod mt312
rmmod mt352
rmmod lgdt330x
rmmod nxt200x
rmmod dvb_core
rmmod dvb_pll
rmmod snd_ac97_codec
rmmod snd_intel8x0
rmmod joydev
rmmod 8139too
rmmod 8139cp
rmmod mii
rmmod snd_atiixp
rmmod snd_ac97
rmmod snd_atiixp_modem
rmmod snd_ac97_codec
rmmod snd_ac97_bus
rmmod ntfs
rmmod ipv6


 
jack-rack preset (copy and paste in a file e load in jack-rack)

CAPS_compress
CAPS AMPV
CAPS Stereo chorus II
CAPS Cabinet II
CAPS Stereo Spazializer

---

### Post by monnezzaio on 2006-10-15
midi controlled jack-rack realtime effetcs stack for great guitar

low latency on the road tips here is my experience

hardware:  
PC Laptop Compaq R4100 (AMD Sempron 3200 RAM 1GB)
audio: edirol UA-25 (USB with mic-preampli and Hi-Zi Impedance switch)
guitar: hohner G3T
midi controller : behringer fbc1010 midi foot controller

problems are xruns in jack (buffer under run o over run) that locks all sounds

follow this steps

0)on cpu with variable frequency (like Inel centrin, amd sempron ....)set cpu frequncy to highest
    0a) install cpu freq utils package : sudo aptitude install         cpufrequtils
    0a) read the current frequency  :  sudo cpufreq-info
    0b) set the frquency (for example on my CPU 1800Mhz)   
                                    :  sudo cpufreq-set -f 1800MHz

1) Add midi controll to jack-rack
  1a) remove stadard jack-rack : sudo aptitude remove jack-rack
  1b) download jack-rack-1.4.4. sources from site 
  1c) install all libraries needed by jack-rack to rcompile
       1cI)  sudo aptitude install libxml2-dev
       1cII) sudo aptitude install liblrdf0-dev
       1cIII) sudo aptitude install libjack0.100.0-dev
       1cIV) sudo aptitude install libasound2-dev
       1cV) sudo aptitude install libgtk2-dev (or libgtk+2.0-directfb-dev)
  1d) tar xvfz jack-rack-1.4.4.tar.gz
  1e) cd jack-rack-1.4.4
  1f) ./configure
  1g) make
  1h) sudo make install


2) use realtime kernel (try ubuntumusique realtime kernel) 
3) use blackbox as windows manager
4) stop all service processes or modules unuseful
5) qjackctl
6) /usr/local/bin/jack-rack

connect audioin to jack-rack (audio)
connect jack-rack audio-out to pcmaudioout(audio)
connect midiin to jack-rack
now you can right click on each slider to add a midi controll for that parameter (note that midi controls are in the range 0-127 but midi control window of jack-rack use 1-128.So remap your assignements like volume 7 --> 8 expression 27-->28)

use
qjackctl (jack gui)
jack-rack
LADSA caps

48 Khz 11 ms latency


script to stop almost all is stopable (run it with sudo two o three times for dependecies of modules)

/etc/init.d/networking stop
/etc/init.d/ssh stop
/etc/init.d/samba stop
/etc/init.d/dbus stop
/etc/init.d/cupsys stop
/etc/init.d/powernowd stop
/etc/init.d/crond stop
/etc/init.d/atd stop
/etc/init.d/hplip stop
killall gam_server
killall artsd
killall ssh-agent
killall pdflush
killall dbus-daemon
killall dbus-launch
killall syslogd
killall cron
killall klogd
killall dcopserver
killall gconfd-2
killall bonobo-activation-server
swapoff -a
umount /dev/sda1
umount /dev/hda1
umount /dev/hda5
rmmod b2c2_flexcop_pci
rmmod b2c2_flexcop
rmmod stv0297
rmmod stv0299
rmmod mt312
rmmod mt352
rmmod lgdt330x
rmmod nxt200x
rmmod dvb_core
rmmod dvb_pll
rmmod snd_ac97_codec
rmmod snd_intel8x0
rmmod joydev
rmmod 8139too
rmmod 8139cp
rmmod mii
rmmod snd_atiixp
rmmod snd_ac97
rmmod snd_atiixp_modem
rmmod snd_ac97_codec
rmmod snd_ac97_bus
rmmod ntfs
rmmod ipv6



for a big distorced guitar
 jack-rack effects 

caps effects used
CAPS_compress
CAPS AMPV
CAPS Stereo chorus II
CAPS Cabinet II
CAPS Stereo Spazializer

---

### Post by hendrikwout on 2006-10-25
I must say, I have very good experience with effects processing under ubuntu., but it needs some tweaking (like using realtime-lsm-module and activating preemptive kernel option). If you've done the job, you can get latency times under 5 ms. You can do the trick also with ardour instead of jack-rack (it uses the same ladspa plugins) and you can record you guitar at the same time.

---

### Post by dolson on 2006-10-26
You do not use the realtime-lsm-module on Ubuntu Dapper or Ubuntu Edgy. Use the built-in PAM. It's in the wiki: [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by Schoappied on 2007-11-26
Hi,.

I've Jack finaly working now! :)

Bu I do not understand how I can make JAck-rack work. I want to use it to add some (realtime/ live) effects to my guitar. Can somebody help me out?

here is a screenshot:

[http://img90.imageshack.us/img90/412/jackracket2.png](http://img90.imageshack.us/img90/412/jackracket2.png)

---

