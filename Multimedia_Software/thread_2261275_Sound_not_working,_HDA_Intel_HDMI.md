---
title: "Sound not working, HDA Intel HDMI"
date: 2015-01-17
forum: Multimedia Software
---

### Post by chronic2 on 2015-01-17
Hi,


I am trying to get my new HTPC to work. I chose to install ubuntu 14.04 server edition and run Kodi on it, as I don't really have the need for a full desktop environment.
However, I have not been able to sound working completely. After following several guides, hints, explanations and random notices it seemed to be about time to open up my own thread to seek help...


Starting with the hardware and problem: I am trying to get sound over HDMI. The board is an ASRock H97M-ITX boad (H97M chipset).
In order to troubleshoot the issue, I have already tried a couple of different debian flavours and desktops (which I installed in the hope that they would provide some packages that helped fix the problem)


The best results so far have been with a gnome 3 core installation, where I got sound for a couple of videos, but not all, and not from the browser (flash/HTML5).
After messing around with the settings and plugins, I decided to start on a new ubuntu server installation. Here I installed a LXDE to use some pulse audio tools that were recommended on the internet.
I have also installed a Linux Mint 17 to verifiy the issue here, and I face the same problems.


Drivers seem to be installed correctly and the hardware is detected (seemingly) correctly:
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```





If I interpret the problem correctly, applications seem to be able to access the drivers, and I can see the amplitude in pavucontrol, but the signal doesn't seem to be sent to the correct subdevice (?)
[[IMG]http://www.pictr.com/thumbs/q5ribqsujv.png[/IMG]]("http://www.pictr.com/?v=q5ribqsujv.png")


I checked the subdevices with 
```
aplay -D plughw:0,X /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

```

using 3, 7 and 8 as X (for the subdevices of card 0). I got a sound playing for subdevice 8, but only after the first try (so, the first attempt resulted in silence, the following played the testsound)


I have tried a couple of ways to set card 0, subdevice 8 as the default device for alsa and pulse, but most of the advice resulted in the pulse daemon crashing...


I am out of my wits now, maybe somebody can tell me what the 2015 way of setting the default devices is or can help me with any further ideas...
Any help is welcome :)


PS: 
kernel version: 3.16.0-28-generic (had to upgrade, as the stock kernel 14.04 ships with brings a kernel panic when a graphical frontend is started o.O)


alsa-info: [http://www.alsa-project.org/db/?f=e90e5a7b348cc48c49302470a1a7893fec847247](http://www.alsa-project.org/db/?f=e90e5a7b348cc48c49302470a1a7893fec847247)

---

### Post by Kevin_Delaney on 2015-02-11
I am having this EXACT same problem. My ALSA config is here:

[http://www.alsa-project.org/db/?f=0e092cddeff28681a216e9d6f73757c966fb7b81](http://www.alsa-project.org/db/?f=0e092cddeff28681a216e9d6f73757c966fb7b81)

Did you ever get this figured out? I have tried seemingly everything.

---

### Post by chronic2 on 2015-02-15
Sadly not... I also do not have a lot of time on my hands recently to tinker around the system :/
My last straw was a post that I read, that there was a bug in the kernel starting in version 3.11 that caused trouble with Intel HDA devices over HDMI. So yesterday I tried to downgrad my kernel to 3.10.24 (that was the latest patch version at the time of the post), but to no avail...
Maybe it helps you... 

I'm going to install a windows on the machine and check the sound there and run some linux vm ontop of it :/

FYI: I tried the whole thing with Arch linux just to be sure (kernel 3.18), but same problem...

---

