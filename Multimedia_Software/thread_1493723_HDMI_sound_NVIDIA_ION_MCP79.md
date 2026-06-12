---
title: "HDMI sound NVIDIA ION MCP79"
date: 2010-05-26
forum: Multimedia Software
---

### Post by JJJJoke on 2010-05-26
Have a fresh install of Ubuntu 10.04 on my mini 311 (NVIDIA ION).
Everything works fine except sound through HDMI. Trying different things, but still no luck.

So the question is whether the HDMI Sound Problem is due to NVIDIA driver 195.36.15? (That was stated in some posts. Previous driver 185 has now hdmi issue, but causes poor graphic performance)

Why official Ubuntu Repos don't use newest NVIDIA driver (195.32.24)? Could the hdmi audio be fixed only with new NVIDIA driver update?

or the problem could be due to incorrect alsa/... setting?

The output of aplay, uname etc
```
$ uname -a
Linux **** 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 24 2010 for kernel 2.6.32-22-generic (SMP).
$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD81B1X5

==> /proc/asound/card0/codec#3 <==
Codec: Nvidia MCP79/7A HDMI 

5/26/10
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 
$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=NVidia
    HDA NVidia, STAC92xx Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output 
```

---

### Post by JJJJoke on 2010-05-26
Solved!
The problem was actually in NVIDIA Driver 195.32.15(24)
Installing new driver (beta) 250... will solve issue
Here is code with adding new repository and installing latest driver:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install nvidia-current
```

---

### Post by farbird on 2010-05-26
no thanks to me?
heheh

---

### Post by JJJJoke on 2010-05-28
> **farbird said:**
> no thanks to me?
heheh

Thank you!!! :)

---

### Post by JJJJoke on 2010-05-29
> **JJJJoke said:**
> Solved!
The problem was actually in NVIDIA Driver 195.32.15(24)
Installing new driver (beta) 250... will solve issue
Here is code with adding new repository and installing latest driver:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install nvidia-current
```

The solution works only couple of days. After that the sound again down!!! 
Should waiting for stable driver from NVIDIA????

---

### Post by farbird on 2010-06-01
try doing another apt-get update

---

### Post by dblegend on 2010-06-02
I just got basic, HDMI, stereo sound under 10.04 64bit on my Zotac ION 9300 box via the Avenard nVidia 195 drivers.  I followed the instructions to get the repos added here:

[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

I used synaptic to pull the glx-195 packages, then I used alsamixer on the command line to unmute all three SPDIF options.  At that point, running a quick speaker test ("speaker-test -Dhdmi -C2 -r48000 -FS32_LE") proved successful.  I haven't gotten to test it under myth or boxee yet, but I have high hopes that things will go well when I get to that point.

I hope that helps.

Dave

---

### Post by farbird on 2010-06-05
mine still works fine...

---

### Post by JJJJoke on 2010-06-09
> **farbird said:**
> try doing another apt-get update

This helps. Having sound through HDMI again.

---

### Post by JJJJoke on 2010-06-10
After one day of full work sound down again :(
Apt-get update do not help this time. I don't know what happens here.
May be problems with hardware?
HP MINI 311-1000, Nvidia ION, Atom 270

---

### Post by tmette on 2010-06-10
> **JJJJoke said:**
> After one day of full work sound down again :(
Apt-get update do not help this time. I don't know what happens here.
May be problems with hardware?
HP MINI 311-1000, Nvidia ION, Atom 270

I saw that farbird posted [this]("http://forum.xbmc.org/showthread.php?t=69479") link in a different thread in UF.  I'm going to try it out when I get home and see if it helps out my nettop.  Maybe it can solve your problem too?

---

### Post by jonasg on 2010-06-10
I'm also having trouble getting sound over HDMI to work on my ubuntu system using MCP79.

Maybe a little bit of output would help:

[http://www.alsa-project.org/db/?f=9faeb71819e9676d7b9bd4bef4ae46e3546921ed](http://www.alsa-project.org/db/?f=9faeb71819e9676d7b9bd4bef4ae46e3546921ed)

---

### Post by JJJJoke on 2010-06-15
> **JJJJoke said:**
> After one day of full work sound down again :(
Apt-get update do not help this time. I don't know what happens here.
May be problems with hardware?
HP MINI 311-1000, Nvidia ION, Atom 270

Got it!
Found the problem: the software, I guess, works properly! It's my HDMI device - monitor DELL 2709w - get down sometimes after entering/restoring from powersafe mode. The video was fine, but sound was absent. The solution is to power off/on the monitor.

---

### Post by psunix on 2010-07-17
hi

I just installed ubuntu 10.04 on my media center... everything works perfect except of the hdmi audio output. I tried to fix the problem but after some hours still no success ...

what I already tried:

1. Installing nvidia graphic current driver
2. Installing nvidia graphic 173 driver
3. Downloading and installing newest nvidia graphic driver from website (256.35)
4. Compiling and installing the newest alsa driver ([http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)) (1.0.23)

all output channels are unmuted (alsamixer)

before there was ubuntu 9.10 on this machine and HDMI audio out worked perfectly. I just reinstalled ubuntu because I messed up some other things ...

Hardware: nvidia Geforce 7050 PV / nForce 630a

uname -a
> Linux saturn 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

aplay -l

> **** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

also in the gnome sound menu there are many different profiles to select ... Digital Stereo (HDMI) Output, Digital Stereo Duplex ( IEC958 ), ...

is there anything else I might try to fix the audio output over HDMI?

Thanks for any help

---

### Post by psunix on 2010-07-18
...

ok, I*almost gave it up ... and then with

> aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav

I can here some sound :)

I found this command in this thread

[http://forums.debian.net/viewtopic.php?f=7&t=33277&start=15](http://forums.debian.net/viewtopic.php?f=7&t=33277&start=15)

I also created the file /etc/asound.conf
> pcm.!default {
     type plug
     slave.pcm {
             type hw
             card 0
             device 3
     }
}

but I still don't know how to configure my system to play sound from other applications ... any hints ?

...

---

