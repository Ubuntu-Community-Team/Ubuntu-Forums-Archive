---
title: "Compro M1F TV tuner ubuntu 10.10 no sound."
date: 2010-11-06
forum: Multimedia Software
---

### Post by glore2002 on 2010-11-06
Hello!

I have a Compro Videomate M1F TV tuner card (internal PCI). After installing ubuntu 10.10 I noticed my card was not recognized and tvtime showed no image no sound.

After a Google search, I found differente threads and I tried the following:

I've created saa1734.conf in directory /etc/modprobe.d (with administrative rights) with these lines:

> alias char-major-81 videodev
alias char-major-81-0 saa7134
options i2c-algo-bit bit_test=1
options saa7134 card=99 tuner=59 secam=dk
options tuner secam=d

After that, I rebooted the computer and after starting tvtime, I can see all the tv channels (great) but I have No SOUND :-( and I don't know how to deal with that and couldn't find a solution.

I know there is a problem with OSS not being supported anymore or something like that and I am a bit confused.

I only want to have sound!!! :-)

**lspci** shows...

> 
:
03:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
:


**Kernel Version: 2.6.35-22-generic**

Any help will be very welcome. Thanks in advance,
Glore2002.-

---

### Post by lgvh on 2010-11-18
I had the same problem, but I found in a Russian forum that if I load the **gnome-alsamixer** and un-mute the "line" (or "CD" depending where your tv card is attached) channel I could control the sound with it.

It worked for me, but the functionality in tvtime is not working because they were made using OSS that it looks like Ubuntu 10.10 is not supporting any more.

I read that the developers of Gentoo are working in a patch for tvtime so alow it to work with ALSA 


I hope it works for you.

---

