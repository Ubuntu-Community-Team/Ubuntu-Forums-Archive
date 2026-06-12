---
title: "Installation problems"
date: 2007-12-29
forum: Mythbuntu
---

### Post by burtil on 2007-12-29
Hi,

I'm trying to install mythbuntu 7.10 on my new HTPC and are having problems with the display. 

Chassi: Antec Fusion V2 Black
Motherboard: Gigabyte GA-MA69GM-S2H
Processor: AMD Athlon 64 X2 4800+ 2.5GHz
Memory: Kingston ValueR. DDR2 PC6400 2048MB 
HD: Western Digital Caviar SE16 500GB SATA2 16MB 
DVD: Samsung DVD-burner SH-S203N SATA 
TV-Card: Technotrend C-1500 
TV: Panasonic Plasma TV TH-42PZ70E

When I tried and used an old VGA monitor the installation stopped (for at least 10 minutes). The last printout was showing that rc.local was executed.

After connecting the HTPC to the TV instead using HDMI the installation started. But know I can't see the lower part of the screen so I have to guess which button is which and use TAB to select the guessed button.
And it don't seem to be possible to change the size of the installation window so I can see the buttons.
But I managed to make a basic installation this way and was able to test a DVD that was shown on the TV. So some things seems to work. 

When I should install the TV-Card which entry should I select for the Technotrend card ? I can't find it in the list.

How to get use of the full HDTV resolution (1920x1080) ? First installation I selected vesa driver and got something on the TV but with very low resolution. After a new installation choosing the AMD driver I don't get anything on the TV. The xorg.0.log contains an error about a missing symbol in the fbglx driver (__driCreateNewScreen). Do I need a newer version than the one included in the mythbuntu distribution ?

---

### Post by burtil on 2007-12-30
I have now managed to get high resolution on my TV. It needed an Option line in the xorg.conf file switching off the AIGLX.
Option "AIGLX" "off"

The problem now is that the picture is larger than the screen. Have tried using DisplaySize but it didn't help.

I still haven't been able to find out how to configure the Technotrend TV-card.

---

### Post by burtil on 2007-12-30
OK, I now have a full resolution picture on my Panasonic TH-42PZ70E TV. It also required that I set the number of vertical lines to 1079 instead of 1080 in the modeline in xorg.conf. So now it's only the TV-card, remote and VFD left. Lucky I have a week off from work :-)

---

### Post by alancw on 2008-01-03
Can you post your modelines? I couldn't find any to work and I've got the same motherboard and tv as you.

Using Envy, I was able to install the proprietary ATI drivers and run at 1920x1080, but lack of xv support meant it was sometimes unusable.

Alan

---

