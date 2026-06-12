---
title: "Asus wifi tv card problems on Ibex amd64"
date: 2009-02-05
forum: Multimedia Software
---

### Post by vallhaus71 on 2009-02-05
I have been trying to sort this out by myself reading through posts and guides but did not manage, I really appreciate any help you can give.
I have an Asus wifi tv card with Philips saa7131E chip. In xp it is shown as Asus Tiger Analog Tv card.  There are also these numbers on the chip; CE4403 and TN05211.  I have installed (from CD not upgrade) ubuntu 8.10 amd64, then installed mercurial. After that installed v4l drivers and placed firmware drivers in place.

my lspci shows this

01:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d0)

my lspci -vnn displays the following

01:01.0 Multimedia controller [0480]: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:818c]
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at e7edb800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [40] Power Management version 2
	Kernel driver in use: saa7134
	Kernel modules: saa7134
According to what I've read so far I should be getting a /dev/dvb folder if all is well, however I do not have this folder created. I can see audio0, radio0 and video0 but /dev/dvb is not there.

If anyone has any idea what I might be doing wrong I appreciate any help.

---

