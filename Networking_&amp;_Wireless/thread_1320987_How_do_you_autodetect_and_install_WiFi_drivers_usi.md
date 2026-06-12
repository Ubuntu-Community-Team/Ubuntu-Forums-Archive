---
title: "How do you autodetect and install WiFi drivers using modprobe?"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by Amurko on 2009-11-09
Let's say you have an unknown WiFi adapter or one that you have no idea what the appropriate driver is that you need.  How do you autodetect it and install it under modprobe (assuming a mod for the adapter is already included with your version of Ubuntu.)

What I've done in the past is:

1) Install the XP drivers using Ndiswrapper.  Ndiswrapper will report the name of the mod already available as an alternative.
2) Uninstall the XP drivers in Ndiswrapper.
3) Install the correct mod using Modprobe.

Is there any way to not use steps 1) and 2) to find the correct mod to use for your WiFi card?  Specifically, is there any program that'll detect the correct mod to use so you can then follow up with:

sudo modprobe xxxxx

where xxxxx is the correct module for your WiFi card.  And if no module exists, then you can proceed with Ndiswrapper as an alternative.

---

### Post by sisco311 on 2009-11-09
```
lspci
```should list the wifi device.

---

