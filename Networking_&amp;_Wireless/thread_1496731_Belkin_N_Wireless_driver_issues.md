---
title: "Belkin N Wireless driver issues"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by Keinlicht on 2010-05-29
So I have a second (older) computer that I've been trying to get ubuntu to run on. I downloaded the latest (10.04) version and did a fresh install the other day.

I'm using a wireless usb adapter, as I'm sure you've gathered, and through investigation managed to figure out that I needed ndisgtk, which i installed. 

After finding the appropriate driver in the adapter's install disk through ndisgtk, I installed and checked it by doing

```
ndiswrapper -l
```

Which returned with

```
WARNING: All config files need .conf: /ect/modprobe.d/ndiswrapper, 
it will be ignored in a future release.
rt870: driver installed
      device (050D:815C) present (alternate driver: rt2800 usb)
```

I'm not sure if the warning message is of any consequence, but I included it anyways.

The adapter no longer recognizes any networks (before this it would recognize the nearby networks and connect, but it couldn't actually transfer any information; that is, I couldn't go in the internet) and I have no idea how to go about fixing it.

Any ideas would be much appreciated, thanks for helping out a noob :P

---

