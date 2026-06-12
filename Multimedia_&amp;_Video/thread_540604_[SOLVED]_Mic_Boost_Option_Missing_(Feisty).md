---
title: "[SOLVED] Mic Boost Option Missing (Feisty)"
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by Kristopher on 2007-09-01
I have a HP Pavilion DV6000 Ubuntu 7,04. I was playing with its internal mic and noticed it was very low in volume but when i go to the volume options i dont see a mic boost.

I have two tabs PLAYBACK and SWITCHES

Under playback i see : MASTER, PCM, EXT MIC, INT MIC all of these apart from master are at full

Under SWITCHES i see: 3 check boxes 

- Line in
- ICE 958
- Int Mic

I have checked under terminal alsamixer but i see the same options, tho i did notice it was using Conexant rather than what Ubuntu says HDA Intel Alsa.

When i type  amixer controls in terminal this is what i see:

numid=7,iface=MIXER,name='Master Playback Switch'
numid=6,iface=MIXER,name='Master Playback Volume'
numid=12,iface=MIXER,name='PCM Playback Volume'
numid=1,iface=MIXER,name='Capture Source'
numid=8,iface=MIXER,name='IEC958 Playback Con Mask'
numid=9,iface=MIXER,name='IEC958 Playback Pro Mask'
numid=10,iface=MIXER,name='IEC958 Playback Default'
numid=11,iface=MIXER,name='IEC958 Playback Switch'
numid=5,iface=MIXER,name='Ext Mic Switch'
numid=4,iface=MIXER,name='Ext Mic Volume'
numid=3,iface=MIXER,name='Int Mic Switch'
numid=2,iface=MIXER,name='Int Mic Volume'


Any ideas?

---

### Post by nilsvdburg on 2007-09-02
I've the same problem.

I've haven an Asus F3JC laptop with and HDA Intel Audio card with the Realtek ALC861 chip.

I've alsamixer version 1.0.13 

There is no mic boost option.

---

### Post by Ivan_p on 2007-09-03
I had the same problem in Kubuntu (Feisty) :

[http://kubuntuforums.net/forums/index.php?topic=3086138.0](http://kubuntuforums.net/forums/index.php?topic=3086138.0)

All I had to do was to add a new line to /etc/modprobe.d/alsa-base :
options snd-hda-intel model=6stack-dig
and reboot.
Now I see 'mic-boost option' in alsamixer. After boosting my mic it is working all right now.

---

### Post by nilsvdburg on 2007-09-03
Hi,

I tried that and no Mic Boost option appeared, there appeared a lot of other switches, but no Mic Boost. In any case, with that option i hadn't any sound at all.

I updated the ALSA driver (now i've v 1.0.15rc1) and when upgrading from 1.0.13 to 1.0.14 on the alsamixer where the chip name was (ALC861) there is now ALC660. IT seems that when updating the driver it recognized the chip as an other one...

But thank you anyway.

---

### Post by Ivan_p on 2007-09-03
Here is a good thread on this topic :


[http://www.linuxquestions.org/questions/showthread.php?t=555391]("http://www.linuxquestions.org/questions/showthread.php?t=555391")

Maybe something in there will work for you.

---

### Post by Kristopher on 2007-09-03
@ Ivan_p  - Nope didn't make a difference same options no new ones, but thanks for the tip.

Any other advice?

---

### Post by Ivan_p on 2007-09-03
One more (desperate) try - you run alsamixer from the terminal, right ? Hit 'tab' to switch from 'Playback devices' view to 'Capture' view. 'Mic boost' use to be there, but unless you hit 'tab' you will not see it.

I guess you probably already know this but nevertheless...

---

### Post by Kristopher on 2007-09-04
Nope sorry its not there just the same options as i see via the GUI

---

### Post by Ivan_p on 2007-09-06
Just FYI - before I solved my mic issue, I have posted it as bug under :

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3369](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3369)

According to tiwai :

----------------------------------------------------------------------
 tiwai - 09-06-07 01:00
----------------------------------------------------------------------
1.0.15rc1 should have mic boost even without model option.  Did you try it?


If it does not help, I would post it as bug on [http://www.alsa-project.org/](http://www.alsa-project.org/)

Please also note that posting it under [http://bugs.kde.org/](http://bugs.kde.org/) does not really help as they do not consider it as bug. See :

[http://bugs.kde.org/show_bug.cgi?id=149376](http://bugs.kde.org/show_bug.cgi?id=149376) 

So alsa project is the right place for reporting it.

Sorry that I could not help you more - I know how frustrating my Skype calls used to be before. As Kubuntu user I am registered on other forum and I have signed up for this one only to be able to answer you (I have bookmarked this thread when I was still searching for solution). But that is life...

Good luck !

---

### Post by gints on 2008-02-23
For me gnome-alsamixer and sliders "Capture", "Digital" did like boost option trick.

---

