---
title: "Help with sound for Laptop Acer Aspire 1640Z"
date: 2006-08-20
forum: Multimedia &amp; Video
---

### Post by kele on 2006-08-20
Hi, 
   Please I a new to Linux. I have a laptop Acer Aspire 1640Z but I can not get sound. The sound chip is Realtek High Definition Audio.  I got this information by checking my hardware through control panel in windows xp. 
   I must hasten to say that I am using Ubunto 6.06 Livecd. Also I must say that I have used it on other systems and it worked. Infact my inability to get sound working while using other linux destros like Puppy, DSL, Austrami, and WOMP Linux is what made me move over to Ubunto.
   I would be must grateful for any form of assistance.

---

### Post by kele on 2006-08-22
Please somebody say something

---

### Post by lodp on 2006-08-22
i've got an Acer 1650Z with a Realtek ALC883 sound chip, and i've wasted WEEKS on this, as documented here: [http://ubuntuforums.org/showthread.php?t=202555](http://ubuntuforums.org/showthread.php?t=202555)

problem is, as of yet, the audio chip isn't properly supported by the ALSA audio drivers, which are part of ubuntu (and many other distros). i'll just have to wait.

if you've go the same chip (ALC883,882,880), i wouldn't waste my time on it (for the time being) if i were you. get yourself some cheap USB audio dongle (like i just did) and deal with it.

find out what chip you've got by typing

> 
cat /proc/asound/card0/codec#0

(assuming that your on-board soundcard is card#0, find out by typing "aplay -l" to list your sounddevices).

if you've got some other chip, there are chances you'll get it to work by compiling the latest version of ALSA.

[SIZE="4"]**EDIT**[/SIZE]: OK, turns out the ALSA issue with my sound chip was resolved litterally while i was typing the above. i've got sound now. if you've got the ALC883 chip as well, as i suspect, you may find a solution for your problem at the end of this thread: [http://ubuntuforums.org/showthread.php?t=202555&page=5](http://ubuntuforums.org/showthread.php?t=202555&page=5)

and use this stickie to get there (chiefly for information on how to get and compile alsa-driver): [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

if you're not sure about the whole patching thing, you can wait for the next alsa-driver release, and compile that.

---

### Post by rattlerviper on 2006-08-22
> **lodp said:**
> i've got an Acer 1650Z with a Realtek ALC883 sound chip, and i've wasted WEEKS on this, as documented here: [http://ubuntuforums.org/showthread.php?t=202555](http://ubuntuforums.org/showthread.php?t=202555)

problem is, as of yet, the audio chip isn't properly supported by the ALSA audio drivers, which are part of ubuntu (and many other distros). i'll just have to wait.

if you've go the same chip (ALC883,882,880), i wouldn't waste my time on it (for the time being) if i were you. get yourself some cheap USB audio dongle (like i just did) and deal with it.

find out what chip you've got by typing



(assuming that your on-board soundcard is card#0, find out by typing "aplay -l" to list your sounddevices).

if you've got some other chip, there are chances you'll get it to work by compiling the latest version of ALSA.

[SIZE="4"]**EDIT**[/SIZE]: OK, turns out the ALSA issue with my sound chip was resolved litterally while i was typing the above. i've got sound now. if you've got the ALC883 chip as well, as i suspect, you may find a solution for your problem at the end of this thread: [http://ubuntuforums.org/showthread.php?t=202555&page=5](http://ubuntuforums.org/showthread.php?t=202555&page=5)

and use this stickie to get there (chiefly for information on how to get and compile alsa-driver): [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

if you're not sure about the whole patching thing, you can wait for the next alsa-driver release, and compile that.


Good, I'm glad you were able to get it working, hopefully Kele will also.=D>

---

### Post by kele on 2006-08-25
Thanks I have just seen these heart warming replies. I would give it a try and then give a feed back.

---

