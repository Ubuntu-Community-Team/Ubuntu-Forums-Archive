---
title: "xruns no matter what"
date: 2006-09-13
forum: Multimedia &amp; Video
---

### Post by mikezackles on 2006-09-13
I'm trying to transition to ubuntu from a digi001/xp combo on a 2.66GHz Pentium 4 with integrated Realtek AC'97 audio.  I want to get the integrated audio working before I buy any new hardware, but I'm having no luck getting jackd/qjackctl to behave.  I've followed the wiki instructions for dapper and compiled the real-time kernel, but I get xruns using every buffer size on both kernels.  I have an agp nvidia card, but I'm using the nv driver, and there is absolutely nothing in the pci bus.  I've had very little luck looking for a way to trace xruns, so any help is welcome!
P.S. I've also tried using 3 periods/buffer as suggested in another thread.
Thanks!

---

### Post by floogy on 2006-09-13
I got an asus A8N-SLI Deluxe, with onboard sound ck804
```
lspci -v |grep -A5 audio
0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        I/O ports at dc00 [size=256]
        I/O ports at 1000 [size=256]
        Memory at d2003000 (32-bit, non-prefetchable) [size=4K]

```

I can avoid these xruns by setting jackd this way ;-) :
```
/usr/bin/jackd -R -t1000 -dalsa -dhw:0 -r44100 -p128 -n2 -P -S -o2 -I170
```

That's no option! I'll go for an ESI Juli@ or some M-Audio stuff (audiophile), or for a Tascam us-122 usb soundcard.

---

### Post by mikezackles on 2006-09-13
Your jackd options do allow jack to run on my system, but only in playback mode, correct?  I'm looking to see if there are issues with running this card full duplex.  Thanks for the help!

---

