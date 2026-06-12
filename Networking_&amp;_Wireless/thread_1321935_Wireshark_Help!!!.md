---
title: "Wireshark Help!!!"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by zyhlo on 2009-11-10
Hi, i tried wireshark in monitor mode on ubuntu 9.04 on my desktop. I got my laptop on, connected to my wireless router & used the internet. Wireshark did not capture any stmp, pop3, tcp web browsing, nothing. There are other hotspots around & all wireshark capture was udp, beacons, etc..

Why did this happen ?

---

### Post by zyhlo on 2009-11-11
Bump Bump!

---

### Post by zyhlo on 2009-11-11
If you guys are wondering, here's how i went about it.

terminal:

sudo -s
ifconfig wlan0 down
iwconfig wlan0 mode monitor
ifconfig wlan0 up

Open wireshark as root, enter password.

Open devices, wlan0, save capture file, untick promiscuous mode & then start capturing.

I have an atheros wireless usb dongle.

Thing is i logged onto my wireless router afterwards from my apple laptop & started browsing, emailing, chatting, etc... wireshark did not capture any of these packets.

Any ideas why ?

---

