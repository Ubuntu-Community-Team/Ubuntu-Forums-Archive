---
title: "Echo Mona issue on 8.04"
date: 2009-01-27
forum: Multimedia Software
---

### Post by JamesMcCanna on 2009-01-27
Hi,

First time post here by a lifetime Windows User trying to escape!  I have successfully loaded 8.04 on my PC, and downloaded the necessary drivers for my Echo Mona soundcard.  I am using Audacity to record music.

I can see the Mona with the aplay -l command, Audacity sees it and lets me select it for I/O but when I go to record I get an error that says it cannot open the device and that I need to check the inputs and sample rates.  These are set at standard 44k and 16-bit.

Also, I can play CDs through the Mona.

I can also see the echo mixer and the VU meters show that my microphone is provided input (it goes up and down when I make noise).

I am very new and feel pretty good about getting this far without having to ask but I am now stumped.

James
Washington state, USA

---

### Post by JamesMcCanna on 2009-01-31
BUMP!

I have upgraded to UbuntuStudio 8.04.  8.10 seemed to have some trouble.

When I run aplay -l I do not see the card but if I run lspci I do see it listed.

Also, the alsa files have the mona driver installed.

I am getting no sound at all.

A couple of days ago I was able to get it to at least play cd's and be seen by Audacity.

So now, I am a bit further back.

I know the motherboard and Ubuntu sees the card but I cannot get it to work.

It is probably really simple but my eyes are wearing out going through the forums/support.  Anyone have an idea of what to do?

Thanks so much.

James

---

