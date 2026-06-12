---
title: "Toshiba A205-S4567 ubuntu 7.10 no sound"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by mathew_davis on 2007-12-17
.Ok I have run through a lot of tutorials but still have not found anything that works.  I had installed ubuntu 7.4 a while ago but had to take it off because of wireless drivers but ubuntu 7.10 fixed that.  As best as I can remember the audio worked in 7.4 but is not working in 7.10.  So here is what I get when I do an aplay -l
[INDENT]
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/INDENT]

when I run aplay it seems to be working just fine, except for the lack of sound.  I then tried going into the alsa sound mixer opening everything and making sure nothing was muted and it all checked out.  As far as I know I have the latest alsa drivers although I am not opposed to trying again.  Really any link would be helpful.  When I go to System>Sound and try all the Test buttons they seem to be working except for the lack of sound.  When I go to the bottom it allows me to switch devices.  I can choose the HDA intel (ALSA mixer) or I can choose the Realtek ALC268(Oss Mixer) To choose from.  Either one I pick it behaves the same way. 

What am I missing here.  At first I thought well maybe my sound card or speakers died.  So I booted up into Vista(Sorry to mention that name here) and tested them out.  They seemed to be functioning just fine.  Any help here would be great. 

Thanks,
Matt

---

### Post by rmdec on 2007-12-22
I have a Toshiba A135-S4656 Ubuntu 7.10 upgraded from 7.04 and I have a very similar, if not exactly the same problem. Unfortunately I have not found an easy fix yet. I heard it might have something to do with an unclean upgrade, but a fix that doesn't involve reinstallation would be nice.

---

### Post by NoEsAlAzar on 2007-12-28
Hi,

I've got a Toshiba Satellite A205-S4577 with ubuntu 7.10 and I had the same problem. Finally I could make it work with information in the link below:

[http://taufanlubis.wordpress.com/2007/11/26/fix-no-sound-for-ubuntu-in-toshiba-satellite-a205-s4707/](http://taufanlubis.wordpress.com/2007/11/26/fix-no-sound-for-ubuntu-in-toshiba-satellite-a205-s4707/)

But there are some things I learned the hard way. So here are my notes about this link. I strongly suggest you take these notes into consideration to fix the issue faster:

1. The command "./configure" wont work unless build-essential package is installed (via synaptic or apt-get)
2. The compilation of alsa-utils-1.0.15 will give an error unless package libncurses5-dev is installed
3. Sometimes a Warning is generated when trying to use modprobe command. I found that in that case, "/etc/modules" has to be open to add all the modules that would need to be added via modprobe command.
4. When running "./configure –with-cards=hda-intel –with-sequencer=yes ; make ; make install" command, make sure to use double hyphen (--) or it wont work.

I hope this helps you!

---

