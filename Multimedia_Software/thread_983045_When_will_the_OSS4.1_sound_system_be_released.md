---
title: "When will the OSS4.1 sound system be released?"
date: 2008-11-15
forum: Multimedia Software
---

### Post by perixx on 2008-11-15
Hi there...

does anybody know, about when the new OSS4.1 will be released? 
I've been having trouble getting 2 soundcards to work with Alsa, 
since I started with Ubuntu and want to try OSS, which will have
implemented MIDI support with the next release...

perixx

---

### Post by perixx on 2009-01-21
Hi - for everyone interested, 

**here's some new information on OSS 4.1 and the upcoming 4.2**
(the wikipedia page is actually pretty useless)


It's out, the new Open Source version of OSS 4.1:
**[http://www.4front-tech.com/forum/viewtopic.php?p=11573#11573](http://www.4front-tech.com/forum/viewtopic.php?p=11573#11573)**

I'll give it another shot, after my first attempt to get it working failed - as soon as 4.2 is out, which will implement a new MIDI interface.
Still can't use my Maudio Audiophile 2496 along with my Onboard Chip - it kills my soundcard's output. 
Perhaps OSS does it better...

Since Also and OSS don't like each other, the respective modules may have to be disabled manually, should that fail:
**[http://www.4front-tech.com/forum/viewtopic.php?t=2983](http://www.4front-tech.com/forum/viewtopic.php?t=2983)**

Regarding the features of OSS, like simultaneous access of multiple apps to an audio device:
**[http://www.opensound.com/wiki/index.php/Main_Page](http://www.opensound.com/wiki/index.php/Main_Page)**

Maybe it will be adventurous to compile it myself, but I'll try that soon. Can't find any package in the Synaptic repositories, anyway - here's how to compile OSS4.x:

**[http://www.opensound.com/wiki/index.php/…Sv4_from_source](http://www.opensound.com/wiki/index.php/…Sv4_from_source)**

From what I can see, the development is steadily continuing and well - looking at the Mercurial repositories and regarding to the dev's, the new version 4.2 with an implemented MIDI interface will come soon: [http://4front-tech.com/hannublog/](http://4front-tech.com/hannublog/)


The Ubuntu community help page for OSS: 
**[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)**

**In case of trouble**, see the official opensound wiki page or Temüjin's post: [http://ubuntuforums.org/showpost.php?p=5539687&postcount=331](http://ubuntuforums.org/showpost.php?p=5539687&postcount=331)

Regards,


perixx

---

