---
title: "Lost Sound - 8.10"
date: 2009-03-13
forum: Multimedia Software
---

### Post by Dusenberg on 2009-03-13
Help please!  I've lost sound on my 8.10 laptop.  It was working fine then one day it was just a crackle. I hadn't been fiddling at all. I have sound if I boot into Vista so the hardware's ok.

I have removed and re-installed the sound modules with coding below, rebooted but no change:
> 
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils


Any ideas??

---

### Post by ExtrazE on 2009-03-14
Dusenbueg
This is one of my fist posts. Hope if follows the rules. I had a similar problem on my hp pavilion dv1000 notebook.
My hardware: Obtained by typing in a terminal $lspci -l
Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

I installed ubuntu 8.10 and everything was great. About a week ago sound stopped working in everything. Volume controls worked, but not sound was coming from the speakers. I accidentally found out that system beeps worked in the terminal still. No MP3, videos, youtube, etc, sound worked though. I googled the heck out of it with little success. I tried the alsa slider stuff in the terminal found in many other posts. I reinstalled all the "driver" stuff from following various guides and other posts. No help.

I booted ubuntu 8.10 from the live cd and sound was fine so I knew it was a software setting on my PC.

What fixed it for me was an accident. I double (left)clicked the speaker icon found on the top panel (bar across the top of desktop). It brings up a window with several settings in it. The "Master" volume slider was all the way up. The "PCM" slider was all the way down, and there was a little red x on the speaker below the slider. I click the x, turned the slider up and bam, my music started playing through the speakers. I have no idea what this setting is or how it got muted. I am pretty new to ubuntu and linux so I can't provide any other insight. I do know that my volume control keys and mute button only effect the "Master" volume not the "PCM"

It may be a shot in the dark but I hope this works for you too. Good luck

---

### Post by Dusenberg on 2009-03-14
Thanks ExtraZe - tried that but everything is on and at full volume and still only a crackle from the speakers or headphone....

As no-one else seems able to help it looks like I'll have to do a re-install of Ubuntu :mad:

---

### Post by superkret on 2009-03-14
Here's yet another [[COLOR="Blue"]Step by step instruction[/COLOR]](http://ubuntuforums.org/showthread.php?t=26567).

What you could try:

-type sudo alsamixer
-see if sound is muted in there.
-after changing sth here, you'll have to save the settings with:
sudo alsactl store 0

-follow the [[COLOR="Blue"]Comprehensive Sound Problem Solutions Guide[/COLOR]](http://ubuntuforums.org/showthread.php?t=205449). Basically you'll probably have to download and compile your sound drivers manually. It tells you how to do that step by step.

---

### Post by dtsatwicz on 2009-03-15
i cannot make my sound work either. did you re-install? did that help?

---

