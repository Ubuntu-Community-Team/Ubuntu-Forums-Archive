---
title: "bt878, emu10k1 &amp; tvtime"
date: 2006-07-19
forum: Multimedia &amp; Video
---

### Post by DomH on 2006-07-19
Hello,

Question : 
[LIST]
Howto tell tvtime (or kdetv) that input sound should be come from emu10k1 and not from bt878 ?
[/LIST]

I found a lot of info to redirect output, but nothing I could understand for input. and unfortunatly I did not kept a image of my breezy config

This, because sound on my bt878 do not work anymore. I did not had this problem with breezy, it appears when I upgrade to dapper.

Some info on config:

**sound cards :**

> 0 [Audigy2        ]: Audigy2 - Audigy 2 [Unknown]
                     Audigy 2 [Unknown] (rev.4, serial:0x10031102) at 0xccc0, irq 169
1 [Bt878          ]: Bt87x - Brooktree Bt878
                     Brooktree Bt878 at 0xd8000000, irq 50


> 0000:04:00.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
	Subsystem: Creative Labs: Unknown device 1003
	Flags: bus master, medium devsel, latency 64, IRQ 169
	I/O ports at ccc0 [size=64]
	Capabilities: [dc] Power Management version 2

0000:04:00.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) (prog-if 10 [OHCI])
	Subsystem: Creative Labs SB Audigy FireWire Port
	Flags: bus master, medium devsel, latency 64, IRQ 177
	Memory at dfafb800 (32-bit, non-prefetchable) [size=2K]
	Memory at dfafc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2

0000:04:02.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
	Subsystem: Hauppauge computer works Inc. WinTV Series
	Flags: bus master, medium devsel, latency 64, IRQ 50
	Memory at d8001000 (32-bit, prefetchable) [size=4K]
	Capabilities: [44] Vital Product Data
	Capabilities: [4c] Power Management version 2

0000:04:02.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
	Subsystem: Hauppauge computer works Inc. WinTV Series
	Flags: bus master, medium devsel, latency 64, IRQ 50
	Memory at d8000000 (32-bit, prefetchable) [size=4K]
	Capabilities: [44] Vital Product Data
	Capabilities: [4c] Power Management version 2


Thanks in advance for your kind help.

DomH

---

### Post by Joeb on 2006-07-19
Are you sure you just don't have the right volume control turned up?  I use tvtime with a similar setup as yours and if I recall, after upgrading, the volume control for the input channel on the sound card was either muted or turned way down.  After adjusting it, sound worked fine. (I'm not at that computer right now, so I can't tell you which volume control it is).

---

### Post by DomH on 2006-07-20
Thanks for the suggestion. 

Unfortunatly it seems not to be the problem. The sound work fine with all the other tools like VLS, Totem and other sounds or video app. even when running together.

Have a nice day

---

### Post by Joeb on 2006-07-20
> **DomH said:**
> Thanks for the suggestion. 

Unfortunatly it seems not to be the problem. The sound work fine with all the other tools like VLS, Totem and other sounds or video app. even when running together.

Have a nice day

However, those would all be output volumes.  If I'm not mistaken, there should be a sound cable from your tvcard audio out jack to the input jack on your sound card.  If you don't turn up the line in jack (I believe that is the one), you don't get sound.

---

### Post by DomH on 2006-07-20
> **Joeb said:**
> However, those would all be output volumes.  If I'm not mistaken, there should be a sound cable from your tvcard audio out jack to the input jack on your sound card.  If you don't turn up the line in jack (I believe that is the one), you don't get sound.

Thanks for your response.

Nomore because the tvaudio out is out and sound from tv receptor goes directly to sound card line in (it is what I was trying to explain in my firt post). It is like mixing won't work even if I got the impression that it is correctly installed being able to ear all other sounds except the one coming through line in when I use one of the TV application and I am sure the volume of the line in is on max position.

So trying to reformulate is how to tell TV application to capture sound from sound card and not from TV card.

Thanks again for helping.

---

### Post by DomH on 2006-07-20
Solved by completly reinstalling mixer tools.

Thanks for your help.

Thread closed.:)

---

