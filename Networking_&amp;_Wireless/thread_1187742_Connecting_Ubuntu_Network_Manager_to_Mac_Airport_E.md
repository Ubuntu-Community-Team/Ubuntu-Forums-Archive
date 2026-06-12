---
title: "Connecting Ubuntu Network Manager to Mac Airport Extreme Base Station"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by rhiester on 2009-06-15
Anyone done this before?  I am not very computer savvy, if there is a walk through that someone knows of I would be very appreciative.  Anyone have experience with this?  Am I asking the right questions?  Bueller?  Bueller?

Thanks.

---

### Post by t0mppa on 2009-06-15
Long as the router (your Station) is providing a wired or wireless network according to the IEEE 802 standards (which the Airport is), it doesn't matter under what operating system you try to connect into it.

Thus, if you're having problems, the more appropriate question is how to set up Ubuntu to detect and associate proper drivers for your wired or wireless networking card in the computer you're using to connect the router with.

For this question to be answered, you need to provide info about what sort of a card you have by running **lspci** from the terminal - or **lsusb** if it's a USB dongle - and posting the output regarding your NIC (network interface card - usually shown as Ethernet controller or Network controller in lspci). Can also provide the output of **lshw -C network** to give even more info about the case and get better help.

Also, for questions related to Apple hardware and Macs, a good way to get in touch with people that have first hand experience is posting to the Apple users subforum.

---

### Post by DGortze380 on 2009-06-15
> **rhiester said:**
> Anyone done this before?  I am not very computer savvy, if there is a walk through that someone knows of I would be very appreciative.  Anyone have experience with this?  Am I asking the right questions?  Bueller?  Bueller?

Thanks.

AirPort Extreme is simply an 802.11g router.
You can connect to it just like any other router, regardless of OS.
Depending you how you set it up, you may need to provide a WEP or WPA Key in order to connect.

---

### Post by rhiester on 2009-06-15
> **t0mppa said:**
> 



For this question to be answered, you need to provide info about what sort of a card you have by running **lspci** from the terminal - or **lsusb** if it's a USB dongle - and posting the output regarding your NIC (network interface card - usually shown as Ethernet controller or Network controller in lspci). Can also provide the output of **lshw -C network** to give even more info about the case and get better help.




It is a USB wireless card.  A IOGEAR Wireless-N USB Adapter.

---

### Post by rhiester on 2009-06-15
When I run lsusb it looks like this is what it has to say about it:

BUS 001 Device 003: ID 0cf3:9170 Atheros Communications, Inc.

Does that help?  How do I set up my Netowork Manager?

Thanks.

---

### Post by t0mppa on 2009-06-17
Well, I've never set up a USB adapter on Ubuntu, so cannot be of that much help here. But a quick search with your device ID showed found others having had issues with the same chip.

Check [this thread]("http://ubuntuforums.org/showthread.php?t=1052619") for instance. The adapter name might be a bit odd there, but since lsusb gives the same ID, they should both have the same Atheros chip doing all the work and thus share the configuration necessary for the OS to handle them.

---

