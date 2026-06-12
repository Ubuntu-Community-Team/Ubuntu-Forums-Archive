---
title: "very low volume - Compaq laptop"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by marcw on 2006-08-13
On my new Compaq Presario v5209us laptop, I can't get the volume to an acceptable level.  Speakers and headphone both work, there's just not enough volume.  On the Windows side (original installation which I made dual boot) the volume is perhaps 3 times greater than what I get with Ubuntu.  The Windows side says that this is a Conexant HDA device.  Here's what Ubuntu says:

$ cat /proc/asound/cards
0 [Intel          ]: HDA-Intel - HDA Intel
                     HDA Intel at 0xd0340000 irq 66

$ cat /proc/asound/devices
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
 33:       : timer

$ lspci -v |grep -A 5 Audio
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Hewlett-Packard Company: Unknown device 30a5
        Flags: bus master, fast devsel, latency 0, IRQ 66
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

All (3) volume sliders are maxxed.

I have seen other, similar posts but haven't seen a solution.  I tried to install a newer alsa driver but didn't get very far; when I would try to uninstall the current alsa-utils and linux-sound-base, Ubuntu wanted to uninstall all sorts of Gnome goodies.  Being brave, I did it anyway only to have apt-get insist on reinstalling alsa-utils and linux-sound-base when I went to those Gnome goodies back.

Any suggestions?

---

### Post by roguenoir on 2006-08-13
I'm having a very simlar problem too, though only with applications that are run through "aoss".  Previously, I was getting no sound in RealPlayer and Macromedia Flash until I followed some instructions to enable "aoss" for both but now the sound is very low even though I have my speaker volume cranked all the way up as well as the master volume in Ubuntu as well as the volume controllers in Flash and Realplayer respectively.

Edit: Fixed according to instruction here -

[http://www.ubuntuforums.org/showthread.php?t=235245](http://www.ubuntuforums.org/showthread.php?t=235245)

---

### Post by marcw on 2006-08-13
Glad you got yours working.  But like I said, my sliders with both alsamixer and Volume Applet are at 100%.  And my volume problems are accross the board - system, dvd, cd, browser, audacity, everything.  Not just browser.

---

### Post by monteiro on 2006-08-27
i have the same problem, with intel sound card.
i'm using a hp pavilion dv5180ea laptop.
in windows i get a lot more sound than in ubuntu.

has anyone solve the problem?

---

### Post by ese5 on 2006-08-27
OK ...  I have the same exact problem with the same exact sound card (Intel High Definition Audio.)  I've verified that all levels are 100% in alsamixer but still have volume about a third of what it would be in windows.  

I wonder,  is this a bug with the HD audio driver itself?

My system is a HP dv5000t laptop.

---

### Post by suicidal666 on 2006-09-04
hi
I have a pavilion dv5*** and exactly the same problem...
i've tried most of the available solutions on the web to no avail


anything new for you guys?

---

### Post by Nick Wilson on 2006-11-09
Anyone find a fix yet? I have the same card, and it *just* went like this. Previously it was working fine :(

---

### Post by matt_risi on 2006-11-19
I tooled around a bit, and this is what worked for me in solving this problem.

Double click on your speaker beside the date/time.
Bring up the volume meter labelled "PCM"

..that's all.

Give it a shot, let me know if it works for you guys.

---

### Post by eviltang on 2006-12-13
> **matt_risi said:**
> I tooled around a bit, and this is what worked for me in solving this problem.

Double click on your speaker beside the date/time.
Bring up the volume meter labelled "PCM"

..that's all.

Give it a shot, let me know if it works for you guys.

Thank you very much.  This worked for me!

Compaq Presario C300 (Model C307NR).

Respect!

---

### Post by commonplace on 2006-12-27
I have my volume sliders all the way up, but the volume is still VERY low (in Windows, it was much, much louder). Any other fixes out there for this?

---

### Post by naaman on 2007-01-03
Hey guys,

The "solutions" offered by Matt_risi and roguenoir are no different from what the majority of posters to this thread have already tried.

After an exhaustive search, I believe I have greatly improved the volume and sound quality of my HP Pavillion dv5129TX by installing the latest alsa-drivers (alsa-driver-1.0.14rc1) along with alsa-lib and alsa-utils.

I have re-written [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) to guide n00bs and l33t h4x0r5 alike on how I got it to work under the "Update to the latest version of alsa" section.

The definitive sign that the snd-hda-intel module was properly identifying my card was the change of how ALSA identified my codec:

BEFORE:
head -1 /proc/asound/card0/codec*
Codec: Generic 14f1 ID 5047

AFTER:
head -1 /proc/asound/card0/codec*
Codec: Conexant CXT5047

Thanks to Sébastien Wains - [www.wains.be](www.wains.be) - for his blogging of his solution.


Naaman.

---

### Post by commonplace on 2007-01-03
Thanks **naaman**. I'll definitely give this a try and post back my results.

/Kevin

---

### Post by commonplace on 2007-01-03
Your directions worked perfectly on my wife's laptop (Compaq Presario C301NR). We're both thrilled!! The sound is SO much louder. Thank you! (This was in Ubuntu 6.10, btw).

/Kevin

---

### Post by bvmou on 2007-01-04
Thank you Naaman!  This had been on my nerves for weeks, your fix was straightforward and totally effective.  I have a Compaq Presario C304NR, Ubuntu 6.10, by way of enhancing searchability.

Thanks again!

---

### Post by kedarkarthik on 2007-05-09
even i had same problem .... type alsamixer on te terminal ... increase the volume of all bars ... my PCM-2 was very low .... now it works fine ,,,,,, sometimes feel better then windows ...:) though not true

---

