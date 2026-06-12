---
title: "How do I get and install wireless driver?"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by trakker01 on 2009-03-12
New to linux. Installed Ubuntu 8,10 on my gateway laptop and it would not divide my disk and allow dual boot.  It wiped out everything on my disk.  I can live with that, but it also did away with my wireless driver.  So where and how do I get and install a new wireless driver?

Also I would appreciate knowing of any other downloads that I should install.

Thank you,
[email]trakker01@msn.com[/email]

---

### Post by Ayuthia on 2009-03-12
You will need to first identify your wireless card.  Please go into the Terminal and post the results of the following:
```
lspci -nn
```
This will list the pci cards for your computer.  You will be looking for something called Network Controller or Ethernet Controller.  That will be your wireless card.  If you post the information, we can try to help you find what you need.  Otherwise, you will need to search for that card and you should be able to find the results that will help you get it installed.

---

### Post by trakker01 on 2009-03-12
Thanks for replying; here are the results:

02:00.0 Ethernet controller [0200] Marvell Techology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (Rev 10)

03:05.0 CardBus Bridge [0607]:  ENE Technology Inc CB1410 CardBus Controller [1524:1410] (Rev 01)

03:07.0 Network Controller Broadcom Corporation BCM4318 [AirForce one 54g] 802.11g Wireless LAN Controller {14e4:4318] (Rev 02)

The wireless is the actual one I am trying to get going, but didn't know whether you needed the others also.  

Thanks again.

---

### Post by Ayuthia on 2009-03-12
If you have a working wired connection in Ubuntu, you can first try to see if you can get the wireless working by going to System->Administration->Hardware Drivers.  There should be an option for Broadcom in there.  It will download a firmware file and a firmware cutter application and install the firmware portions for you.

If you don't have a working connection, you can try this [post]("http://ubuntuforums.org/showpost.php?p=6077792&postcount=72").

Hope that helps.

By the way, if you did not know already, you have the Broadcom 4318 rev 02 wireless card.

---

### Post by trakker01 on 2009-03-13
Another great big Big THANK YOU!!  I followed your System->Adm... instructions and after a lot of down loading and installing and a restart, it worked!!  I realize that I have an awfully lot to learn on this system.

Thank you again,
trakker01

---

