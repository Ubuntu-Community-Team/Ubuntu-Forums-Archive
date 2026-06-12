---
title: "WiFi can't connect to Internet"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by [::H@$$@N::] on 2009-06-11
I can connect to the WiFi in UBUNTU 9.04, but I cant use the Internet!, I can also see other PCs connected to the WiFi, so there is no error in connectivity!
Moreover, on the same machine using Windows Vista Home Premium, I can connect to the Internet via same WiFi card!

Please tell me how to solve the problem!

---

### Post by [::H@$$@N::] on 2009-06-16
Can someone solve my problem please???

---

### Post by Iowan on 2009-06-16
What's in */etc/resolv.conf* and what are results of **route -n**?

---

### Post by Purple Grant on 2009-06-24
I have the exact same problem.

In **etc/resolv.conf **
There is a folder "*update-libc.d*" containing a file "*avahi-daemon*"

The Results for **route -n** are...

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0

Can you help?

---

