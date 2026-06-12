---
title: "cs4235 identifed incorrectly"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by -error on 2007-12-17
hi
i have an old p3 based PC (it was a server years ago, but now it is my workstation :) ). it has onboard cs4236 sound card which has being incorrectly identified (by what?) as cs4232. if i stop all processes, remove this module and `modprobe snd_cs4236' - things became ok.
i'v put a `cs_4236' line in /etc/modules but it doesn't help.
any input is greatly appreciated.

---

### Post by tgalati4 on 2007-12-17
I have the same problem.  I had to add a bunch of switches to the snd_cs4236 module to get it to work.  I haven't tried blacklisting the cs4232 module yet.  Have you tried that?

I think what happens is the hardware detection algorithm finds the first driver in the cs42XX family and loads it.  Once loaded, it moves on with the rest of the boot.  

I don't have the switches handy, but a forum search will provide several suggestions.

Edit:  These worked for me:

Add to /etc/modules

snd-cs4236 isapnp=0 port=0x530 cport=0xf00 irq=5 dma1=1 dma2=0

Reboot.

---

### Post by -error on 2007-12-17
> **tgalati4 said:**
> I haven't tried blacklisting the cs4232 module yet.  Have you tried that?
blacklisting? didn't even knew about this thing. ok, thanks for the suggestion. i'll try it at next reboot.
as for other options - i don't need 'em since my soundcard working well with default ones. it just detected incorrectly.

---

