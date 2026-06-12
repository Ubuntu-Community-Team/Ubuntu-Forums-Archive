---
title: "internet dies after some time"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by MOB_Figga on 2010-09-24
hello,

I don't want to 'spam', (I had started a first thread about this some time ago), but I'm (still) experiencing problems with my internet:

I can use the internet (I am connected through a simple switch) for some time, that is: surf the internet (in firefox) and download using vuze (azureus) but after some time, the internet connection 'dies' (downloadspeeds jump to 0b/s and I am not able to surf to any site in firefox). When that happens, the only 'solution' to this is restarting my pc.

I first experienced this when using ubuntu 10.04, so I thought that it was a 10.04 issue. I knew that when I had ubuntu 9.10 (karmic koala) installed, this didn't happen. So today, I installed karmic koala, but much to my surprise I am experiencing the same problem.

I used 'lspci' to find out what NIC is in my pc and I found out I have the following NIC:

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78 )

I'm suspecting the NIC to be the problem. Is this probable? If so, I want to buy a add-in network card (simple one, not a gigabit card): does anyone have any suggestions?

---

### Post by MOB_Figga on 2010-09-29
anyone?

---

### Post by lukeiamyourfather on 2010-09-29
Yes, a faulty NIC could be causing the issues you are having. Also faulty networking equipment could cause this too (switches, routers, etc.). Pretty much any NIC with a Realtek or Intel chipset will work out of the box in Linux, there are many others that are supported but you'd have to check on those to be sure.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833156139](http://www.newegg.com/Product/Product.aspx?Item=N82E16833156139)

I have one of those because an integrated Marvell NIC on my motherboard failed. Works great in Windows 7 and Ubuntu 10.04 (both are 64-bit).

---

### Post by mathia on 2010-09-29
[SIZE=1]Hi lukeiamyourfather,

[/SIZE]For your Marvell device you can download the vendor driver from link below and give it a try to solve your LAN problems by ubuntu:

[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "88E8057 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices	Linux 2.6 - Fedora v10.85.9.3

 $ tar xvfj install_v10.85.9.3.tar.bz2
$ cd DriverInstall
$ sudo bash ./install.sh

and let me know if it works.

Have a lot of fun ...:razz:

---

### Post by lukeiamyourfather on 2010-09-29
> **mathia said:**
> [SIZE=1]For your Marvell device you can download the vendor driver from link below and give it a try to solve your LAN problems by ubuntu

The problem with my NIC wasn't the drivers. It failed completely in all operating systems. Prior to the failure it worked out of the box in Ubuntu. Also, I'm not the one seeking assistance, the original poster is. :)

---

### Post by mathia on 2010-09-30
Hi Luke,

sorry for that, I know it. The reason was that I saw the following in your post:
> I have one of those because an integrated Marvell NIC on my motherboard failed.

---

### Post by MOB_Figga on 2010-10-01
@lukimyourfather: thank you for the reply:

 I ordered a conceptronic gigabit lan adapter (pci-card) which has a realtek chip on it. I know gigabit might be over the top (I don't have a gigabit switch), but it wasn't that expensive i.m.o and they had it in stock at the online store where I ordered it (they didn't have the 100mbit one in stock).

---

