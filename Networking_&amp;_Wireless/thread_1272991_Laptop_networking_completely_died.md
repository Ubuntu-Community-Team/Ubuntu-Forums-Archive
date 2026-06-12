---
title: "Laptop networking completely died"
date: 2009-09-22
forum: Networking &amp; Wireless
---

### Post by HyperHacker on 2009-09-22
I have a Gateway MX7515 laptop, running Xubuntu 9.04. Was working a while ago, now it refuses to connect to any network. It acts as if wireless is enabled when in fact it refuses to turn on (so there's an empty wireless network list). Nothing happens when I plug in an ethernet cable - before it would immediately pop up a "disconnected" message. ifconfig only shows the lo interface.
At one point it worked for a while, then froze up at random and hasn't worked again since.
In dmesg it tells me to download some firmware from linuxwireless.org, which I did a while ago; it had been working before. IIRC wired connections worked even without the drivers. I also can go into the Hardware Drivers program and see the driver listed there, but disabled. When I try to enable it it wants to download some files which of course fails (with a completely blank error message).

I started up the 8.10 live CD and it gives the same report in dmesg and doesn't react at all to the cable being plugged in. Of course I can't try to install a driver on a live CD so I can't tell if it works or not.

---

