---
title: "USB Soundcard not working"
date: 2009-03-09
forum: Multimedia Software
---

### Post by saralk on 2009-03-09
Hi. I've been using Linux as my main OS for a few months now, and I really do like it, every so often a problem comes along but i'm more than willing to take the time to find out what is wrong and fix it.

However, I have been trying for a few weeks to get a USB soundcard working and I can't figure it out at all.

The jack on my internal soundcard has come loose so now sound only comes out of one speaker and even that is starting to break, very soon i'll have no sound if I can't get this to work. :(

I've got a USB soundcard from Trust (SC-5500P) and I can't get it to work. When I plug it in, the mute button on the soundcard does enable mute on the computer so I know something is happening, but there is no option is System > Preferences > Sound for USB Audio.

Any help would be greatly appreciated. :)

---

### Post by markbuntu on 2009-03-09
Try this

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by saralk on 2009-03-09
> **markbuntu said:**
> Try this

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

I tried that, but my usb sound card does not show up

---

### Post by markbuntu on 2009-03-09
Ok, what do you get with

lsusb

---

### Post by saralk on 2009-03-09
```
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 145f:0143  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by saralk on 2009-03-11
Anyone have any ideas?

---

### Post by markbuntu on 2009-03-11
Does the blue light come on when you plug it in?

---

### Post by saralk on 2009-03-12
> **markbuntu said:**
> Does the blue light come on when you plug it in?

yes, and if you push it, everything gets muted

---

### Post by markbuntu on 2009-03-12
Well, it should not be controlling your on board sound at all so that is weird. You should probably talk to the alsa devs on chat or on one of the mailing lists about this.

[http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)

---

### Post by adrien214 on 2009-06-19
Hi,
did you disable your onboard audio ?
I remember when I first plugged-in my Trust SS550P, there would be the ubuntu login sound coming out but nothing else.
Then I managed to get sound but nothing more than stereo.

when I type in the command : 
```
cat /dev/sndstat 
```

I get :
```
[SIZE="2"]Sound Driver:3.8.1a-980706 (ALSA v1.0.18rc3 emulation code)
Kernel: Linux satellite 2.6.28-6-generic #16-Ubuntu SMP Mon Jan 26 20:16:00 UTC 2009 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
USB Sound Device at usb-0000:00:13.0-2, full speed

Audio devices:
1: USB Audio (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
1: USB Mixer[/SIZE]
```

do you see anything yourself there ?

I'll try to look into this because I really would like to have my soundcard working with linux as well... (all speakers and the subwoofer).

btw - is your machine a laptop ?

---

### Post by erikthedrink on 2009-09-08
Being your system does not recognize your USB audio card, this is not likely to work.:confused:  However, go to Applications, then Accessories, then Terminal.  In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.

---

