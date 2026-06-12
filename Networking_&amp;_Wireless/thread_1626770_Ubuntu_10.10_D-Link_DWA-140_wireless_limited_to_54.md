---
title: "Ubuntu 10.10 D-Link DWA-140 wireless limited to 54 mbps (rt2870sta)"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by havarha on 2010-11-20
Hi!

I have an ASRock 330 with a D-Link DWA-140 usb adapter connected to a D-Link DIR-655 set to use G and N, and I can't get more than 54 MBit. iwconfig says the connection speed is 54 MBit, and it never changes.

I've tried to search a bit for a solution, and what I've found is that the card should work ootb in 10.10 (it does, but with a limit). Those who solved their problems (with pre 10.10 releases) did so by downloading the rt2870sta driver, but that won't help me much, since that's the one I'm using.

When I tried setting the router to use N only, the usb adapter couldn't connect at all, so it seems to be locked to G in some way.

The router works fine with other devices running N.

Any clues?

---

### Post by uncaspi on 2010-11-20
Try iwlist
See man iwlist for options

---

### Post by havarha on 2010-11-21
This is what I get when I ran iwlist wlan0 rate:

```

wlan0     unknown bit-rate information.
          Current Bit Rate:54 Mb/s

```

Tried "iwconfig wlan0 rate" with 100M, 300M and auto. None of them changed anything.

---

### Post by kylewhittington on 2011-08-05
I'm having the exact same issue. Did you ever manage to resolve it?

---

### Post by kylewhittington on 2011-09-14
Bump. This is still happening to me. I'm running 11.04 and am an advanced user.

---

### Post by gewone on 2011-09-25
I can confirm this issue. Running 10.10/Maverick.
My USB adapter [D-Link DWA-140]("http://www.dlink.com/products/?pid=652") seems to be stuck to 802.11g.

Any ideas?

---

