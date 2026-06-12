---
title: "Installing and configuring D-LINK DIR-601 Wireless N 150 Home Router"
date: 2012-05-26
forum: Networking &amp; Wireless
---

### Post by vi1985 on 2012-05-26
Hi!
I've spent hours online trying to find a decent how-to for how to get this router to work in my Ubuntu 10.04, but so far without success. I tried looking for drivers on the installation CD - but couldn't find them. I downloaded the firmware, and followed this guide: [http://www.downloadatoz.com/howto/how-to-use-windows-drivers-in-ubuntu,29074.html](http://www.downloadatoz.com/howto/how-to-use-windows-drivers-in-ubuntu,29074.html), but the firmware had a ".bin" file, and ndiswrapper only accepts ".inf" driver files. After spending some time looking in this forum and various Ubuntu how-to pages, I still couldn't find anything. I would really appreciate help!

Thanks,
vic.

---

### Post by chili555 on 2012-05-27
I don't think you need the driver CD and the Windows files at all. I suggest you plug an ethernet cable into any of the four LAN ports and connect it to your computer. If the computer is running Network Manager, it ought to connect automagically. Open Firefox web browser and type in 192.168.0.1. The web-based administration pages of the router will open and you can proceed as outlined on pages 13 and following in the manual.

Be sure to use secure encryption for wireless, ideally WPA-AES and a strong password that isn't guessable by that pesky kid next door.

If you get stuck, please post back.

[http://www.dlink.com/products/default.aspx?pid=DIR-601&tab=3](http://www.dlink.com/products/default.aspx?pid=DIR-601&tab=3)

---

### Post by qmqmqm on 2012-06-08
Make sure to use the "pre-shared key" and not the password that you use to log into webpage at 192.168.0.1.

You can also call your ISP, and they should be able to give you a phone number for DLink Tech Support that you can call. Those guys should be able to walk you through the steps of setting up the network.

---

