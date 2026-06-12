---
title: "Could us poor Gateway Notebook owners form a soundcard support group?"
date: 2007-08-17
forum: Multimedia &amp; Video
---

### Post by morelostthanfound on 2007-08-17
Could somebody who has successfully made sound come out of the speakers on a MT series Gateway laptop post a how to? 

I have a MT3422 with Ubuntu 7.04.  aplay -l sees HDA NVidia STAC92xx Analog and I can run alsamixer and have the sound icon on my desktop. To the best of my knowledge nothing is muted and I don't have an option to turn of an external amplifier.

I have read all of the posts I can find on this topic and have tried everything short the stuff that requires compiling code. 

If the ALSA drivers don't work from doing a sudo modprobe snd-hda-intel don't work, whats left for me to try?

---

### Post by gils0040 on 2007-08-21
I've got an MT3423 and am also getting no sound. I have the Sigmatel Stac9200 card. The motherboard uses the Nforce 430 chipset. Anyone get this working?!

---

### Post by netron on 2007-08-22
same deal here.  gateway notebook.

anyone got a solution?


cat /proc/asound/cards


"HDA-Intel   - HDA Nvidia"

---

### Post by FuturePilot on 2007-08-22
If you have an HDA-Intel sound card, you might want to look here
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by netron on 2007-08-22
> **FuturePilot said:**
> If you have an HDA-Intel sound card, you might want to look here
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

that didnt work for me.

compiling and installing the alsa drivers went ok.  

it did say something about the channels being muted by default - but when i look at alsamixer the master channel is unmuted (green 00)

still no sound...

grrrrr...

](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by netron on 2007-08-22
here's the output of an alsa diagnostic script that i ran on my laptop:

[http://pastebin.ca/666902](http://pastebin.ca/666902)


i got the script from here:
[http://bulletproof.servebeer.com/alsa/scripts/alsa-info.sh](http://bulletproof.servebeer.com/alsa/scripts/alsa-info.sh)

---

### Post by netron on 2007-08-22
ran "alsaconf" and it reports the card  as being

hda-intel nVidia Corporation MCP51 HIgh Definition Audio (rev a2)

this ran ok.  no errors.
still no sound.

---

### Post by gils0040 on 2007-08-22
netron, I havent run that script but it looks as though i have the same exact card as you. Post back if you manager to get it working please!

---

### Post by netron on 2007-08-22
>aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


>lspci

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

>cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xb0000000 irq 20

came across an interesting thread here:
[http://www.nvnews.net/vbulletin/showthread.php?t=78913&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=78913&page=2)

---

### Post by netron on 2007-08-22
i'm going to compile and download the alsa-oss library

path on the alsa wiki is wrong. its

[ftp://ftp.alsa-project.org/pub/oss-lib/alsa-oss-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/oss-lib/alsa-oss-1.0.14.tar.bz2)

---

### Post by netron on 2007-08-22
getting somewhere...  alsa-oss compile/install resulted in 

/proc/asound/card0/oss_mixer

being created

contents:
VOLUME "Master" 0
BASS "" 0
TREBLE "" 0
SYNTH "" 0
PCM "" 0
SPEAKER "" 0
LINE "" 0
MIC "" 0
CD "" 0
IMIX "" 0
ALTPCM "" 0
RECLEV "" 0
IGAIN "Capture" 0
OGAIN "" 0
LINE1 "" 0
LINE2 "" 0
LINE3 "" 0
DIGITAL1 "IEC958" 0
DIGITAL2 "" 0
DIGITAL3 "" 0
PHONEIN "" 0
PHONEOUT "" 0
VIDEO "" 0
RADIO "" 0
MONITOR "" 0

interesting....  the mixing levels are all zero.


> /etc/init.d/alsasound restart
Shutting down sound driver: done
Starting sound driver: snd-hda-intel done
Starting sound driver: snd-hda-intel done
XXX write TLV...

(hmmm... whats "XXX write TLV"??)

still no sound.. ill reboot now.

---

### Post by netron on 2007-08-22
no sound after reboot.

but that oss_mixer output in /proc is interesting....
i wonder what thats all about..

---

### Post by netron on 2007-08-22
found this bug report about it:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117246](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117246)

seems as if lots of people are affected.

mepis is also affected, so its not specific to ubuntu:
[http://www.mepislovers.org/forums/showthread.php?t=8443](http://www.mepislovers.org/forums/showthread.php?t=8443)

i'm also finding threads from various distros going back to 2006 of last year. 
i would love to know what the hell is going on here.  completely stumped. 

maddening thing about it is that an mp3 player like Beep or XMMS works just fine - the oscilloscopes move in time with the music BUT I CANT HEAR ANYTHING!

---

### Post by netron on 2007-08-24
bump.  no update to that launchpad entry linked above

---

### Post by gils0040 on 2007-09-10
It works!!! Download the patch and instructions here [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948)
Good luck!

---

### Post by KenMac on 2007-09-20
Hi guys.  I have a Gateway MT3423 running 7.04 and like many, I am not getting sound.  I was happy to see the Gils0040 was ably to get sound from an MT3423.  However, when I ran the patch that Gils0040 linked to on #15 I was greeted with many error messages and no sound.  Could Gils0040 or anyone that has made sound come out of the MT3423 give me a step by step of how it is accomplished?  Thanks very much in advance.

---

### Post by KenMac on 2007-09-20
Please disregard my prior post.  I re-ran the patch and I now have sound!  Thank you to everyone who contributed to the patch.  I have been wanting to hear what Mandela had to say for weeks! :)

---

### Post by themadhatter on 2007-09-23
I've got problems too - sound is the only thing that I haven't got working. When i run Aplay I get:

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Now I don't care about the modem (we have cable), but the lack of sound is getting annoying. When I run Alsamixer I get:

alsamixer: function snd_mixer_load failed: Invalid argument
wayne@the-mad-hatter-laptop:~$


so I think that something is wrong with Alsamixer, but I don't know what.

Wayne

---

### Post by Paradoxfox93 on 2007-11-19
Hi I'm D and I'm a deaf/dumb gateway owner. I need support! LMAO  Also have any of you gotten wirelss workng? I've found the most sucess with feisty as far as system stability (Gusty crashed all the time and Drake wouldn't even recognize wired).

---

### Post by gils0040 on 2008-01-02
wireless works with native linux drivers now too! The kernel patch is available here [https://sourceforge.net/tracker/index.php?func=detail&aid=1833847&group_id=186406&atid=917159](https://sourceforge.net/tracker/index.php?func=detail&aid=1833847&group_id=186406&atid=917159)

---

### Post by Apotheosis323 on 2008-01-04
I have an MT3422 as well, i havn't really gotten around to any actual wireless fixes but Sound is working great, go here and follow this guys tutorial, you will have to run these scripts every time kernel is updated. [http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)

---

