---
title: "Looks like everything is finally working but no joy"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by wpsmithii on 2009-02-04
Ubuntu 8.04 LTS kernal 2.6.24-16, dual boot with XP Pro, wlan0 is recognized in network tools and can send and receive. Ndiswrapper installed an *.inf driver for my Trendnet TEW 423 PI (Realtek chipset RTL 8185) wireless card and it is now recognized by the system on the PCI bus. When I go into the configuation, there is no place to input the security key and none of the local (at my house) wireless networks are available to add. I got the driver off the CD for the card. Ndiswrapper would not install the *.sys drivers from the XP partition, said they were invalid. This has been no fun as I'm an absolute newby, by the way it works fine on the XP side. I've got my laptop beside the Linux box so I can respond quickly. Thanks in advance. Bill Smith

---

### Post by Iowan on 2009-02-04
In 8.04 you can probably edit the information into */etc/network/interfaces*.  I don't yet do wireless, so I don't know the format, but there are several threads with questions/answers about essid, etc.

---

