---
title: "Recommended tuner card and software for over-the-air recording?"
date: 2013-09-18
forum: Multimedia Software
---

### Post by zuren on 2013-09-18
I'm taking my first dive into building an open source HTPC and wanted to gather some information regarding TV cards that have a good reputation of working with Ubuntu.  My build is mostly from a system I picked up cheap with a few added pieces more suited to HTPC duty; the system components will be listed below.

I do not have cable TV or satellite so I'm only looking to record and playback a couple over-the-air TV shows during the week.  I was hoping to use XBMC (which I believe uses MythTV on the backend) but didn't know if it just easier to use MythTV directly (if I'm understanding correctly)?

Any suggestions or insight would be appreciated!  I think I'm leaning toward a Hauppauge 2250 but I'm open to other cards.  Like I said, this is my first venture into building a PC (period) and toying with a HTPC for streaming video and recording programs so any advise will be appreciated!

Thanks!  

System specs:
Case - Silverstone LC13 USB3.0 (ordered)
Mobo -[COLOR=#000000][FONT=arial] Gigabyte EP45-UD3P v. 1.1[/FONT][/COLOR]
Processor -[COLOR=#000000][FONT=arial] Core 2 Duo E8400 3.0GHz[/FONT][/COLOR]PSU - Corsair HX620W
GPU - HIS Radeon HD 5850 (for now and if it fits the case; considering going fanless)
SSD - Kingston HyperX SSD 128GB (run the OS and applications)
Optical drive - LG Blu-ray
RAM - [COLOR=#000000][FONT=arial]Cosair 4GB DDR2 1066
[/FONT][/COLOR]HDD - TBD (storage)
TV tuner - TBD

---

### Post by itlarson2 on 2013-09-28
I'm trying to determine the best dual tuner setup for OTA myself.  The Hauppauge 2250  is probably at the top of my list, although I have heard setup can be tricky- something about it needing firmware.

The hardware you chose is fine, although There are a few things I would do differently.    If this is only a mythtv box I would go with much lower specs, both to save money and keep power consumption down.  I have run a combined frontend/backend on a Zotac Ion board with a dual core Atom, and it worked fine.  I have always used Nvidia because vdpau can ofload playback to the GPU, and that board has Nvidia built in.

One of my main considerations is always noise- especialy for a box that's in the livingroom.  To keep it quiet you need a good aftermarket cpu cooler, large slow-turning fans (never smaller than 120mm), and a quiet video card.  Keeping power consumption down helps.  Using an Atom may be overkill, but there are i3 chips that draw as little as 35w.  If you do need the faster CPU, the one you've chosen ins't bad at 65w though.  Asus makes great passively cooled cards, and even their high end ones are known for being quiet.   Corsair PSU's are great, by the way, although I've never gone over 430w.  For more info on keeping noise down see [silentpcreview.com]("http://www.silentpcreview.com/").

Of course the best hardware is the hardware you already own, though.

---

