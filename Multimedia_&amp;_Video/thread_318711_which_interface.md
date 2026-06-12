---
title: "which interface?"
date: 2006-12-14
forum: Multimedia &amp; Video
---

### Post by theotrst on 2006-12-14
hi,
this is my first post here.
I know that this subject has been often discussed, but I would like to buy a new external sound interface (I have Mbox's digidesign but I would like to use it in linux, and I think mbox's driver will never developed for linux...), so...

my first idea is M-audio firewire 410 (but I should wait and hope that freebob solve the problems!!), I also found that Presonus devices have a good compatibility with ubuntu so...

which are your suggestions? (in the same area of price...:mrgreen: )

thanks

---

### Post by tristan_koen on 2006-12-18
The external (firewire) M-Audio devices work really well with FreeBob. I am running an M-Audio Firewire Solo and haven't had any problems other than the one described below.

Getting libfreebob compiled on Ubuntu is not easy. There is a conflict between the libc6 and libthreads packages (and you need them both). The best option right now is probably to install the Debian package. It works OK, but I did get some odd crashes. 

If you don't want to use Freebob, you will have to go for a PCI device. The M-Audio Delta series of cards are well-supported out-of-the-box. 

I chose to move (temporarily) onto Fedora Core 6 until Feisty is released (or they get the %#@^%#$ libc6/libthreads issue sorted out). On FC6, it has been rock solid.

**EDIT:** Don't get the FW410!!! From the Freebob FAQ:
**Q:** Will the M-Audio 410 / 1814 be supported?

**A:** Maybe. The problem is that the M-Audio 410 / 1814 does not support the AV/C commands for device discovering. Though for transporting the signals the IEC 618863-6 standard is used. So that means that streaming is no problem while controlling the device is.
The M-Audio 410 is BridgeCo's first product and differs heavily from the rest. FW410 tries to collect information about this device.
The state about the M-Audio 1814 is unknown.

---

### Post by theotrst on 2007-01-09
thanks for your answer! :D 
I unfortunately M-Audio Solo have just 1 XLR imput, and I plan to use more...
but ok!, thanx for your advice (in Freebob) for Firewire410, 1814...do you think they will never developed completely?

ciao

---

