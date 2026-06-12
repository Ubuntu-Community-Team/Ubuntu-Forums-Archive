---
title: "No network, no internet, no evolution working !"
date: 2012-07-14
forum: Networking &amp; Wireless
---

### Post by chitragurung on 2012-07-14
Hi,

I have been using dell mini inspiron with ubuntu 10.04 

when try to use blue tooth applet it does not work so I uninstall it via software manager but unfortunately it disabled all my internet connection, network, evolution.

How can I revert back it with out deleting all my data ?

Can you help me.

---

### Post by Akhilpm135 on 2012-07-14
goto system->administration->Additional drivers and check if the driver is activated.If not activate it from there.

---

### Post by chitragurung on 2012-07-14
when i try to activate it says need to download. But have no internet how can install without download.

---

### Post by Kirk Schnable on 2012-07-15
> **chitragurung said:**
> when i try to activate it says need to download. But have no internet how can install without download.

I would find out what deb package it needs, go download it from the Ubuntu repository on another computer, and bring it over on a flash drive. 

Kirk

---

### Post by Akhilpm135 on 2012-07-15
In ubuntu you need to use proprietary driver for wireless.It will not be available in the live disk.So you need to download it..:!!

But i think ubuntu 12.04 comes with all the drivers for wireless..

---

### Post by Kirk Schnable on 2012-07-15
> **Akhilpm135 said:**
> In ubuntu you need to use proprietary driver for wireless.It will not be available in the live disk.So you need to download it..:!!

But i think ubuntu 12.04 comes with all the drivers for wireless..

Yes, but if you can find out which package you need, you can go to [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) on another computer in a web browser, navigate the folders yourself, and find the package.  Then you can download it, put it on a flash drive, and bring it to the other computer.  Then you can install it using "dpkg -i packagename.deb".

Kirk

---

### Post by chitragurung on 2012-07-16
Which package should I download.

1. My network adaptor is broadcom 4312

2. Now what happened that my computer just check error up to 70% than it stock. Because it happened when I try to override the with live cd ubuntu 10.04 again. How to solve this problem.

---

