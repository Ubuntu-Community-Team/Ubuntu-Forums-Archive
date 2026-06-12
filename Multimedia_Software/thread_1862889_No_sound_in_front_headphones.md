---
title: "No sound in front headphones"
date: 2011-10-17
forum: Multimedia Software
---

### Post by shags_j on 2011-10-17
Hi All,

New to linux and just installed ubuntu 11.04. Runs great however I cannot get sound through my front headphone jack on my desktop. Main speakers coming from back work fine but nothing through the front headphones. 

I have dual boot windows for some games and sound is fine in it.
I've done a quick search but could find nothing exactly the same.

Please help.

Cheers,

Shags

---

### Post by cerda on 2011-10-17
I also have the same problem, in a hp-mini netbook. Sound coming from the Analog Speakers work fine, but when i plug the headphones (1 jack for mic and phone) the sound stops working.

I've already tried every combination of mute/sound in alsamixer and no success. It's like sound stops working when i plug the dam phones.

I've had some similar problem back in 11.04 but i could manage to get it working through gnome-alsamixer, but in 11.10 gnome-alsamixer is not working because some segmentation fault.

---

### Post by cerda on 2011-10-17
I've just got it working by rebooting and unplugging the source power cable from the netbook. Now it works properly, i'll do some more testing with source power cable in/out and see how it goes.

From some google searching you can see that a lot of people are having headphones audio problems, specially in laptops, maybe this kinda be similar.

---

### Post by Pr0t3us on 2011-10-17
I have like the opposite problem i get sound from both the speakers and headphones at the same time. I have 2 jacks one on the desktop and one on the monitor with built in speakers on the desktop sound comes out of both the speakers and headphones and on the monitor jack sound comes out of only the headphones when plugged in as it should except i get static noises.

Anyone else have this issue? or I the only one????

---

### Post by shags_j on 2011-10-18
I'd be happy to get sound from both.
 
In alsamixer the headphones slider is greyed out and unable to be adjusted. Leads me to believe that it's not reading that they are there (driver issue?)

---

### Post by JosephWheatley on 2011-10-18
This post may help

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

It appears to be an issue affecting many laptops. My **Packard Bell EasyNote MZ35-U-005** was saved by adding 

*options snd-hda-intel model=dallas* 

to **/etc/modprobe.d/alsa-base.conf**

---

### Post by shags_j on 2011-10-18
Looks like it would work but my card is not showing up.

Codec is showing as VIA VT1708S

---

### Post by shags_j on 2011-10-18
I just found the hd-audio-models.txt file (seems to be the updated version of cards etc that the link above refers to)

For my card it has the following entry

VIA VT17xx/VT18xx/VT20xx ========================   auto		BIOS setup (default)

Does that mean I should add the model=auto to the config file?

---

