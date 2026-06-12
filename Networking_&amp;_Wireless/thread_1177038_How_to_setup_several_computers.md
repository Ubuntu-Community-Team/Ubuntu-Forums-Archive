---
title: "How to setup several computers"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by superpink99 on 2009-06-03
Ok so im putting up a small internet cafe, now i have 10 computers considered as slaves and one server, now i decided to install ubuntu on my server but xp on the other ten computers, now here are some problems i want to ask:
1. How do i get control of all the 10 client computers? (ex. shutting down the client computer using my server, etc) is there a software i need to install?
2. Whats the best way to monitor the 10 computers on my ubuntu server? (monitoring time, or any activities going on)

Thanks in advance.......

---

### Post by UBSec on 2009-06-03
Hi ,

From your Ubuntu Server, if you installed a desktop environnement (X, KDE, Gnome) you can use remote desktop ( sudo apt-get install rdesktop). And then rdesktop your_xp_host.

You may setup some authorizations on your XP hosts ( [http://www.microsoft.com/windowsXp/using/mobility/getstarted/Remoteintro.mspx](http://www.microsoft.com/windowsXp/using/mobility/getstarted/Remoteintro.mspx)) . You need to create a local account on your hosts.

UBSec

---

### Post by Sooner Al on 2009-06-03
> **UBSec said:**
> Hi ,

From your Ubuntu Server, if you installed a desktop environnement (X, KDE, Gnome) you can use remote desktop ( sudo apt-get install rdesktop). And then rdesktop your_xp_host.

You may setup some authorizations on your XP hosts ( [http://www.microsoft.com/windowsXp/using/mobility/getstarted/Remoteintro.mspx](http://www.microsoft.com/windowsXp/using/mobility/getstarted/Remoteintro.mspx)) . You need to create a local account on your hosts.

UBSec

Remember the XP boxes would need to be running XP Pro or MCE edition in order to remotely access/control them using Remote Desktop [RDC]. If they are not then VNC would work well in that situation. The OP would need to install the TightVNC or UltraVNC server on each XP box.

---

### Post by Sooner Al on 2009-06-03
> **superpink99 said:**
> Ok so im putting up a small internet cafe, now i have 10 computers considered as slaves and one server, now i decided to install ubuntu on my server but xp on the other ten computers, now here are some problems i want to ask:
1. How do i get control of all the 10 client computers? (ex. shutting down the client computer using my server, etc) is there a software i need to install?
2. Whats the best way to monitor the 10 computers on my ubuntu server? (monitoring time, or any activities going on)

Thanks in advance.......

You might consider a product like this for your internet cafe.

[http://www.zyxel.com/web/product_family_detail.php?PC1indexflag=20040520161313&CategoryGroupNo=4E14C850-478D-4204-8C85-2994C9552426](http://www.zyxel.com/web/product_family_detail.php?PC1indexflag=20040520161313&CategoryGroupNo=4E14C850-478D-4204-8C85-2994C9552426)

...or if your running a supported router use DD-WRT which has a hot spot function.

[http://www.dd-wrt.com/wiki/index.php/Chillispot](http://www.dd-wrt.com/wiki/index.php/Chillispot)

---

