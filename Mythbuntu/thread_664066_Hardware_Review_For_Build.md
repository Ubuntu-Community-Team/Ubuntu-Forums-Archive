---
title: "Hardware Review For Build"
date: 2008-01-10
forum: Mythbuntu
---

### Post by Peterg707 on 2008-01-10
I'm getting ready to build a Mythbuntu box (I'm psyched!).
I just got the case, but have no other hardware.  I wanted to get some input/feedback from the community before buying anything else.  The case is a low-profile case, so the cards must be low profile.  I will need to purchase adaptor brackets for the cards listed, but they will fit.

If anyone sees any possible compatibility problems with this lineup, or any suggestions please reply and let me know!

Cheers,
Peter

**Case: ** Ahanix MCE 301
**Remote:** Mock-ro-soft Windows MCE (came with ahanix case)
**MOBO:  ** ASUS P5K-VM LGA 775 Intel G33 Micro ATX Intel Motherboard 
**CPU:  ** Intel Core 2 Duo E6550 Conroe 2.33GHz 
**Video Card:  **   MSI NX8500GT-MTD256EH GeForce 8500GT 256MB 128-bit GDDR2 PCI Express x16 HDCP Ready Silent Heatsink Video Card 
**Tuner Card: **  pcHDTV HD-5500
**Power Supply: **  CORSAIR CMPSU-550VX ATX12V V2.2 550W Power Supply 
**Memory:**   Kingston 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 667 (PC2 5300) 
**HD 1: **  Western Digital Caviar SE16 WD2500KS 250GB 7200 RPM SATA 3.0Gb/s Hard Drive - 
**HD 2: **  Western Digital Caviar SE16 WD7500AAKS 750GB 7200 RPM SATA 3.0Gb/s Hard Drive 
**Optical Drive: **  SAMSUNG 20X DVD±R DVD Burner with LightScribe Black SATA Model SH-S203N - 
**CPU Cooler: **  Scythe SCMNJ-1000 80mm Sleeve "NINJA MINI" CPU Cooler

---

### Post by e00 on 2008-01-11
I can tell you that the 2Gb RAM is way more than you'll need but memory is cheap so why not (its what I did!).

I've discovered that some so-called 'MCE' remotes will actually be recognised by the system as a keyboard and work as one (e.g. my 'Sunwave' MCE remote). That means that LIRC won't be used and in fact nothing will need to be done to have it 'do things'. That doesn't mean that it will all work with Mythbuntu as the system will only see Windows MCE compatible keystrokes being sent by the remote. If your remote is one of these (I don't know how you can tell ahead of time) then you'll probably need to change Myth's (and Mplayer & VLC etc.) key bindings to work. Not that I've actually done such a thing yet, it's only a theory :)

I think I've seen mention that pcHDTV tuners are supported, don't know for sure.

The rest is standard PC and should be fine... anyway, finding out is half the fun, right? :wink:

Good luck!

---

### Post by newlinux on 2008-01-11
It would help to better evaluate your choices if you went into more detail into what you want to use it for -- what type of display, resolution, what types of files (e.g. h.264 HD). Will this be a dedicated linux box? Will you be doing lots of transcoding? 

I'm not sure what reason there is the get the 8500 in Linux system unless you are looking forward to when Linux drivers support the hardware acceleration or audio over HDMI they have... Otherwise they really have no benefit over a 6 or 7 series. 

You proably know, the pcHDTV tuner is supported in Linux. I personally prefer the dvicos fusion 5s if you are looking for a low profile card, but it really won't make much of a difference. However, is one tuner enough for you? That's a lot of hard drive space for just one tuner, but maybe you have a lot of multimedia you want to use already.

I assume that case comes with an IR receiver as well?

You could probably build a system that does everything you want for less, but I don't know if price is your concern...

---

### Post by Peterg707 on 2008-01-11
This is helpful.  I didn't realize the nvidia 8 wouldn't make a difference over the 7 series.  I'm looking to do a fair amount of DVR (both ntsc and hd), so a two tuner solution might be better.  One of the main reasons for the large amount of disk space is that I have hundreds of gigs of mp3 files (and ogg and flac).  This will be dedicated to media only.  I also want to be able to rip dvd's to mpgs for convenience.  For instance, I have some guitar instruction dvd's that I want to store so I don't have to fumble around with discs. - things like that. I like to have seperate hard drives for media - a system drive and a data drive.

I know the box could take vista mce - but I don't like vista and I LOVE ubuntu.  If it weren't for MS Office apps I would only use Linux. (I find Wine a pain in the butt)

One of my main goals is to make the box as silent as possible.  I've chosen the PSU, CPU cooler and graphics card for those reasons. If there are better choices I'm up for hearing them. 

I just checked out the Divco tuner and it looks great. I may very well go wiith that one.

---

### Post by williammanda on 2008-01-11
You can view this link that has typical hardware for mythtv:

[http://ubuntuforums.org/showthread.php?t=566529](http://ubuntuforums.org/showthread.php?t=566529)

I too use the Dvico FusionHDTV5 Gold and the pcHDTV 5500. Very satified with both.

Also have you tried the open office suite?

---

### Post by Peterg707 on 2008-01-11
Thanks for the review and the suggestion.  My one challenge is eliminating noise and fanless vid cards often encroach on another slot, so using two tuner cards might be a challenge since I have to use a micro ATX for the box (which looks great and has the IR reciever built in.

This system will be replacing everything in my stereo system/media system except for the receiver (onkyo 601).

Yes, I've used open office and I really like it. It's a lot easier to navigate than MS Office.  THe one challenge I've had is that when I save docs as a .doc file, sometimes tables, bullets and headers are all screwed up when they are opened in Word.  So...I don't risk it and keep a windows machine around.

---

