---
title: "Not enough power?"
date: 2010-02-03
forum: Mythbuntu
---

### Post by Lossif on 2010-02-03
Lately I have been backing up my collection of Blu-rays onto my myth setup and have been running into some problems.  When I play the backups (.264 in a .mkv container) in VLC on my work computer they play fine.
[INDENT]ASUS P5Q Pro Turbo LGA 775 Intel P45 ATX Intel Motherboard
Intel Core2 Duo E7500 Wolfdale 2.93GHz LGA 775 65W Dual-Core
4 gigs 240-Pin DDR2 SDRAM DDR2 667
ASUS EN6200LE/TC256/TD/64 GeForce 6200LE 256MB(64MB on Board) 32-bit DDR PCI Express x16 Video Card[/INDENT]

But when I play them on Mythbuntu 9.10 in VLC they start to stutter and skip.
[INDENT]ASUS M3N78-VM AM2+/AM2 NVIDIA GeForce 8200 HDMI Micro ATX AMD Motherboard
AMD Athlon 64 X2 3800+ Windsor 2.0GHz Socket AM2 Dual-Core
3 gigs 240-Pin DDR2 SDRAM DDR2 800 (2 x 1 gig and 2 x 512 meg)[/INDENT]

My question is, should I upgrade the Ram to a full 4 gigs or the processor to something faster?

I understand that .264 compression can be pretty  intensive, I just don't know if my problem is the processor or the ram.

Thanks a lot for any help!

---

### Post by nickrout on 2010-02-03
This isn't really a mythbuntu question is it...

Have you tried using vdpau acceleration to play it? You can do this from within mythtv or by using mplayer.

---

### Post by Lossif on 2010-02-03
I understand that the questions was not directely about a Myth problem exactly, so maybe I can restate it:

I have some video that is running rather choppy on my Myth box (9.10) I thought the hardware was strong enough to handle it, however I am not sure anymore.  It runs on my Windows 7 machine just fine (with the above hardware) but not on my (admittedly less powerfull) Mythbox.  Being that they are 4 gig files, running Myth, is my computer powerfull enough? and if not what can I do to make it so?

In regards to "vdpau acceleration" I  have not even heard of it and will do some research.  When I tried to play these within Myth they would not play at all, does VLC support it?

---

### Post by nickrout on 2010-02-03
upgrading your ram will not help.

I don't know much about that processor, but the symptoms you describe (and you haven't provided any log files) would tend to suggest your system does not have enough grunt to play it via the cpu. However it can probably be played with hardware acceleration from the nVidia GPU if you are using vdpau. (Again you haven't given any details of the file other than the codec and container). 

I suggest you read this page:

[http://www.mythtv.org/wiki/Vdpau](http://www.mythtv.org/wiki/Vdpau)

You can also try mplayer which has support for vdpau. VLC does not (as far as I know).

Unless the file is extraordinarily difficult to decode, your nvidia graphics ship should play it just fine.

PS recent xbmc builds also have vdpau support, so that's another test you can use :)

---

### Post by movieman on 2010-02-04
I would agree that it's probably the processor: assuming that AMD's '3800+' meant it was supposed to be comparable to a 3.8GHz P4, then I can't really see it managing HD H264... my 3GHz P4 struggles even with 720P.

VDPAU would seem like the first thing to try, if the graphics card can handle the decoding then you won't need to upgrade anything.

---

### Post by nickrout on 2010-02-04
Looking at the wiki page, the 8200 will play it alright, even if it won't do the most advanced deinterlacing option, it will definitely play it unless it is encoded very stoopidlee.

---

### Post by ian dobson on 2010-02-04
Hi,

Get VDPAU working and give you poor old AMD a break. I use VDPAU on my frontend (C2D e5200 underclocked to 1.2GHz and a NVidia 9300 graphic card), when playing back HD h264 videos in a mkv container using mplayer I only see a CPU load of about 10-20%.

Regards
Ian Dobson

---

