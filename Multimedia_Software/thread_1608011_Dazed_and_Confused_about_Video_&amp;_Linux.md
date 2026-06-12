---
title: "Dazed and Confused about Video &amp; Linux"
date: 2010-10-28
forum: Multimedia Software
---

### Post by Mark_in_Hollywood on 2010-10-28
I apologize for the lack of specificity in the Title of this post. But I am truly confused. I have searched the Multimedia & Video forum for some help about my TV stuff. I've found nothing I can apply to my system. I want to watch American ATSC tv, record on my hard drive and if possible schedule recording for another time. But I would take watching and recording alone.

Recently, I asked, in another Ubuntu forum, if the drivers for what I think are necessary for my TV-card (AVermedia A188 'Duet' Duet for dual tuenrs on 1 card) are now in-built into the kernel. The reply was:

[LGDT3305 and SAA7160]("http://ubuntuforums.org/showthread.php?t=1606520")

With the LG
[SIZE="3"]/lib/modules/2.6.35-22-generic-pae/kernel/drivers/media/dvb/frontends/lgdt3305.ko[/SIZE]

[SIZE="3"]/lib/modules/2.6.35-22-generic-pae/kernel/drivers/media/dvb/frontends/lgdt330x.ko[/SIZE]

With the Philips this was closest:
[SIZE="3"]/lib/modules/2.6.35-22-generic-pae/kernel/drivers/media/video/saa7164/saa7164.ko[/SIZE]

so, my AVermedia Duet should work?

I tried Me-TV and it said I had no DVB devices available.

I tried TV Time and the "screen" flashes on screen and vanishes off-screen.

I tried lspci | -vnn (or something I found in another post and they got some terminal output) and the terminal returned nothing for me.

I tried to look at DMESG, and saw some stuff about the recently installed TV Time, but I cannot understand enough of it and won't post that long string of lines unless asked.

I looked at the Video4Linux hardware section and I think that this AVermedia card, a pci-express device is working, although they don't specifically mention it. Only that SAA716x is working.

Reading some of the posts at Multimedia and Video, on a search for AVermedia, I see some people installing dvb-utils or some similarly named applet. That applet scans for digital tv signals and creates a list, which when added to some other existing file, allows some TV application to find the channels. I tried to install that and aptitude returned -no such program-.

I'm at a complete loss. 

Is this AVermedia card useable in Linux?
Are the SAA7160 and LGDT3304 the same as the above in-built drivers?

---

### Post by NT4usB on 2010-10-29
> **Mark_in_Hollywood said:**
> I apologize for the lack of specificity in the Title of this post. But I am truly confused. I have searched the Multimedia & Video forum for some help about my TV stuff. I've found nothing I can apply to my system. I want to watch American ATSC tv, record on my hard drive and if possible schedule recording for another time. But I would take watching and recording alone...

MythTV will do all the above.
It's in the repos.

---

### Post by Mark_in_Hollywood on 2010-10-30
> **NT4usB said:**
> MythTV will do all the above.
It's in the repos.

Do you mean you have the same card, an AVermedia Duet (model #188)? My question isn't whether Ubuntu or Linux has TV. It's whether my card has drivers and is supported. Please tell me that.

---

### Post by NT4usB on 2010-10-30
no, and no.

---

