---
title: "Trouble connecting wireless adapter"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by dd896 on 2009-09-06
I have just co-installed Ubuntu on my home PC with a previous installation of Windows XP Home. The computer has a Linksys Wireless-B USB network adapter, model WUSB11. The XP OS on this PC can connect to my home wireless network, as do a MAC and another Windows PC, but on Ubuntu the network adapter can see the wireless network, but fails to connect. I have set up my home network security so that it only accepts PC's with accepted MAC addresses, but since the Windows XP install in this machine connects, I assume the Ubunto OS should connect as well.

---

### Post by x22 on 2009-09-06
he MAC address is specific to the network
hardware--the linksys wusb11--so you should be OK
there.

> the network adapter can see the wireless network

meaning...what?  

> but fails to connect

have you assigned the correct ESSID, channel, mode &
encryption key if any?  We use "iwconfig" to do this
somewhat thus:

ifconfig wlan0 up
iwconfig wlan0 essid 2236a
iwconfig wlan0 channel 40
iwconfig wlan0 mode managed
iwconfig wlan0 key ..........
iwconfig wlan0 key open
dhclient wlan0 2>&1>/dev/null

change to suit local conditions.

---

