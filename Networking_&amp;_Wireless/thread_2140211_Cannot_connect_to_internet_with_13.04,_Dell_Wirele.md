---
title: "Cannot connect to internet with 13.04, Dell Wireless 1504 802.11b/g/n"
date: 2013-04-29
forum: Networking &amp; Wireless
---

### Post by tom327 on 2013-04-29
When I first tested Ubuntu on a liveUSB, the wifi worked fine. Then, when I started the installation process, I lost connection and could not regain it. After installing, I tried to connect via an ethernet cord, but I still could not connect. Finally, I tried to connect to one of my neighbor's open networks, and I connected. I can connect to my network on Windows, but I still cannot connect on Ubuntu.

Here is the hardware I am using:

Dell Latitude E6530
Dell Wireless 1504 802.11b/g/n
Intel(R) 82579LM Gigabit Network Connection
Belkin N+ Wireless Router

My neigbor's wifi (that I can connect to) is a Linksys router.

Finally, I have attached the outputs of lspci, lsusb, ifconfig, and iwconfig.

---

### Post by tom327 on 2013-04-29
*

---

### Post by wolldee on 2013-04-29
The same has happened to me yesterday. I installed it and replace the W7. I had internet connection during the installation but after completing it It detected the wifi and could connect automatically, it was connected a BUT when I open firefox I couldn't even go on google. I have an HP pavillon g4 with i3. I did the install with a USB. One thing I foud  weird is that when I downloaded it the file name ended with amdx86 but when I was doing the USB I bootable I saw there was the option for intel processors. So I am wondering if this might cause any issue beside the fact that the install did not go like I expected. (I lost My windows partition) :) .

---

### Post by tom327 on 2013-04-29
Interesting, but I think we have different problems. You had internet during the install, and I did not. Also, I cannot connect at all to my network (but I can connect to open networks).

---

### Post by tom327 on 2013-04-29
Just updated original post with relevant info and better explanation of problem

---

### Post by dandroid13 on 2013-04-29
Another person with issues with Broadcom? Try```
sudo apt-get purge bcmwl-kernel-source
```and install the version from Quantal: [http://packages.ubuntu.com/quantal/bcmwl-kernel-source](http://packages.ubuntu.com/quantal/bcmwl-kernel-source)

---

### Post by tom327 on 2013-04-29
Installed that version, but I still can't connect.

---

### Post by tom327 on 2013-04-29
nevermind, I just rebooted and I connected perfectly. Thanks!

---

### Post by tom327 on 2013-04-30
actually, I do still have some problems. Wireless works perfectly, but I still cannot connect using ethernet.

---

