---
title: "Insanely slow wireless speeds"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by zozza on 2009-12-20
My wireless on XP is perfectly fine.  The signal strength says "low" but I can view streamed videos decently.

On Ubuntu it is another story.  The connection usually fails to connect the first time so I reboot.  Then on the second or third reboot it might connect but with a signal strength of 15%.  If I put the laptop right next to the router I get 60-70%.

I often cannot load webpages like Google for example.  

Can anyone explain how to sort this out.  At the moment with wifi on Ubuntu the Internet is useless (I am posting from XP now).  

I am using an Azure Wireless NIC which is not the problem, since, as mentioned, XP wifi is good.

Thanks.

---

### Post by zozza on 2009-12-20
Just to add that I have used an external USB NIC and it is better but I still have timing out problems.

And anyhow why should I need an external USB NIC.  I don't with XP.

---

### Post by zozza on 2009-12-22
BUMP!

Can someone suggest something - the whole point of Ubuntu is that it's superior to XP.

But I cannot use wireless internet on it but I can with XP!

HELP!

Thanks.

---

### Post by MooPi on 2009-12-22
Are you using Linux driver or ndiswrapper or other work around for your wireless. If you could type this command in your terminal and print results here.>  lspci

---

### Post by zozza on 2009-12-23
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)

---

### Post by bkratz on 2009-12-23
Have a look here for several different answers

[http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR928X](http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR928X)

---

### Post by gufran777 on 2009-12-26
To simplify, this (wireless data speed) works on the inverse square law idea where physical quantity or strength is inversely proportional to the square of the distance from the source of that physical quantity. 

Glassing over? Think of this way: An object twice as far away receives only 1/4 of the original intensity, which in this case means speed/signal strength. If you're right near the router, you'll get much better data transfer speed than if you were, say, 10 feet away.
_______________________________________________________
[Find Contractors](http://www.homeimprovementcorner.com/contractors_by_state.php)
[home painting colorado](http://www.homepaintingcolorado.com)

---

