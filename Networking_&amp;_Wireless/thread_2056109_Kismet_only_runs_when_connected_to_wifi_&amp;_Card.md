---
title: "Kismet only runs when connected to wifi &amp; Card can't channel hop"
date: 2012-09-10
forum: Networking &amp; Wireless
---

### Post by nothreat33 on 2012-09-10
Hello, 

I'm having two issues I can't figure out. First, I can only successfully start kismet when I am already connected to a wireless network. If I am not connected to a wireless network and try to run kismet I get this error:

FATAL: channel get ioctl failed 22:Invalid argument.

It happens whether or not I run ifconfig wlan0 up/down.

The other issue I'm having is my card is not able to change channels. I have the iwl4965AGN Chipset. I downloaded compat-drivers to find my chipset is not listed but iwl3945, and iwlagn are. Would either of those be the drivers I need to enable my card to channel hop and allow me to manually change it's channel (via airmon-ng)

---

