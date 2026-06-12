---
title: "ALSA Sound Slow and Muffled with New Sound Card"
date: 2009-03-08
forum: Multimedia Software
---

### Post by helliewm on 2009-03-08
I bought a sound card 

lspci -v shows:  Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CM8738
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 20
	I/O ports at c000 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: C-Media PCI
	Kernel modules: snd-cmipci

Checking the ALSA web site before I bought the card revealed its compatible with ALSA. The reason for buying the Sound Card is my on board sound is not support my ALSA.

I have worked through the Sticky on Sound Solutions/Guide in the guide in the Sticky of this forum, to no avail.

OSS works beautifully a big improvement from my on board sound. So yes the Sound Card is correctly installed and does work with OSS.

However if I change to ALSA (by going to System, Preferences, Sound) the sound is very very slow and muffled. I have also checked by ALSA setting in ALSA Setting, that I installed, as well as right clicking on Volume Control to ensure that is set up correcting and nothing is muted.   

I have also checked Pulse Audio.

I have googled but that is no help. 
 
Does anyone have any ideas? Once again if I use OSS the sound is fantastic so its not the Sound Card that is the problem. The Sound Card is supported by ALSA. 

Helen

---

### Post by markbuntu on 2009-03-08
Unless you remove the alsa packages and reinstall them old drivers may be in use


(1) Remove the ALSA packages
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```

(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```


Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

``` 

(3) Reboot

---

### Post by helliewm on 2009-03-08
Thank you so much, that worked:D Clearly you need to reinstall ALSA if have new sound card.

Many thanks,

Helen

---

