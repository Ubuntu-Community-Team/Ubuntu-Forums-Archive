---
title: "Issues with Fusion HDTV7 PCI in Ubuntu 10.04"
date: 2010-05-21
forum: Multimedia Software
---

### Post by jbhtexas on 2010-05-21
Equipment:
Dell GX620 using onboard Intel Graphics, 3 GHz processor, 4GB RAM.
Fusion HDTV7 PCI
Turtle Beach Montego DDL soundcard (C-Media 8768+ chipset)

I dual boot this configuration between Windows XP and Ubuntu 10.04.  In XP, I can view all HTDV channels without problems.

In Ubuntu, it seems that I can view channels that are broadcasting 780p or lower without trouble, but when I try to view 1080i channels, I start to get significant sound drop out and occasional video stuttering.  

I'm using the Kaffeine player.  There is an SMPlayer also installed, but that one doesn't work at all. It recognizes that the card is present, and has a channel list, but I just get a blank screen.  I checked the performance monitor, and it indicates about 37% CPU usage when Kaffeine is running.

Also of interest, If I have my other HDTV on while watching the HTDV7 in XP, the programs on the two devices are in sync.  However, when watching the HDTV7 in Ubuntu 10.04 with Kaffeine, Ubuntu lags the other HTDV by several seconds, and that lag seems to increase the longer the program runs (must be some kind of buffering going on).

I'm just wondering if there are some tweaks that might fix this, or if this is a limitation due to the hardware.  

Is there a better player than Kaffeine?  I looked through all the Kaffeine menus, but I didn't find settings that helped this issue.  Does something need to be tweaked in the underlying libraries that Kaffeine uses?

I know that the onboard Intel graphics chipset is not stellar, but this setup does work fine in XP.

I'm quite new to multimedia in Ubuntu, so I apologize if these questions are basic.  Thanks for any help.

---

