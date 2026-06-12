---
title: "PVR-150 MRC problems"
date: 2007-10-30
forum: Mythbuntu
---

### Post by shadowxdragon on 2007-10-30
Hi all, I'm new to Linux and to Mythtv.  Here is my problem .... I have MythBuntu 7.10 installed on an AMD 64 motherboard with a Huuppage 150 MCE (26552 rev B628).  I can't get ivtv to see the card: here are the logs

[   36.762470] ivtv:  ==================== START INIT IVTV ====================
[   36.762476] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload ) loading
[   36.771328] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   37.461421] ivtv0: loaded v4l-cx2341x-enc.fw firmware (-139637549215920 bytes)
[   37.693417] ivtv0: Encoder mailbox not found
[   37.693423] ivtv0: Retry loading firmware
[   38.331438] ivtv0: loaded v4l-cx2341x-enc.fw firmware (-139637549215904 bytes)
[   38.564219] ivtv0: Encoder mailbox not found
[   38.564225] ivtv0: Error initializing firmware
[   38.564514] ivtv0: Error -19 on initialization
[   38.564557] ivtv:  ====================  END INIT IVTV  ====================
I have trided moving the card to diffrent PCI slots but nothing works.  I have a software TV card that works but is very choppy, so I know that the system and Mythtv are working, just not this card.  Thanks for any help

---

### Post by superm1 on 2007-10-30
Two things:

you SURE this isn't the newer hvr-1600?

Also, the PCI bracket, is it improperly grounded?

Is your case not allowing for a full contact of the PCI slot and card by chance?

Reference:
[http://g-ding.tv/?q=node/2227](http://g-ding.tv/?q=node/2227)

---

### Post by shadowxdragon on 2007-10-31
The card is seated well I tried twice to reset it.  This is the info off the chip: 

Conexaxt MPEG II A/V Encoder
CX23416-12

The part number is: P/N 5187-7619

I did remove the card and installed it into a Windows unit and it works fine.  I think I might need to reinstall the firmware, but can't figure out how to do that.

---

### Post by shadowxdragon on 2007-10-31
Ok it's just not my day.  I took the card and an older system I had and tried to install Myth with this card.... yep you guessed it no go??? I'm at a dead end... the web says that this card is supported but for some reason myth see it but can't use it.  Any more ideas or should I just buy a new card:(.... my third try.   Thanks again for any help.

---

### Post by shadowxdragon on 2007-11-01
Ok i just bought a Hauppauge WinTV-PVR-500 MC from Hauppauge and that way if it's bad I can at least get my money back unlike ebay.:) I'll report back on how this card works:)

---

