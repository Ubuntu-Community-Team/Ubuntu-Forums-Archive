---
title: "How to get Ubuntu to connect with my wireless network"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by trunkmonkeytoo on 2010-02-23
I posted a topic like this before, but I didn't get anything that was able to work on my computer, so I uninstalled Ubuntu, and just today reinstalled it inside of Windows 7. I have been trying to connect, getting help from this [https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html) guide. But nothing seems to work. I have a cradlepoint wireless router, and a Sprint Air card. My computer is a Toshiba Satellite L505 laptop. How can I make Ubuntu recognize my wireless card, so that I can go onto the internet with it? 

So I could try to be specific as possible, I looked up in my computer what Wireless card it has. I'm not sure if I came up with the right thing, but under Network Adapters, I got Microsoft Virtual Wifi Miniport Adapter, Realtek PCIe FE Family Controller, and Realtek RTL8191SE Wireless LAN 802.11n PCI-E NIC. 

I would really appreciate it if anyone could help me figure out how to get my computer online. Thank you in advance.

---

### Post by coskierken on 2010-02-24
Please post the output of these commands:

lshw -C network

lsusb

---

### Post by trunkmonkeytoo on 2010-02-24
[SIZE=5][SIZE=2]I had to scan this in, because I can only use the internet with Windows 7 on my computer. [/SIZE]
[IMG]http://i678.photobucket.com/albums/vv148/trunkmonkeytoo/UbuntuOutput1.jpg[/IMG][/SIZE]

---

### Post by coskierken on 2010-03-02
Sorry for the delay, but been out of the loop.  I don't see your 802.11N at all.  Is it built in?  Is it a cardslot or USB?

---

