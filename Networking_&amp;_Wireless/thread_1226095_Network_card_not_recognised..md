---
title: "Network card not recognised."
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by noidtluom on 2009-07-29
I have a brand new Acer Aspire 4535. I am trying to get online via a wired connection. I plug in my ethernet cable but I am unable to get online.

I am using Kubuntu Jaunty.

lspci lists it as Ethernet Controller [0200]: Attansic Technology Corp. Device [1969:1063] (rev c0)

In ifconfig I only see lo, wlan0 and wmaster0 (note I am NOT trying to get wireless working). There is no eth0.

I have tried modprobing atl1 and atl2 as well as atl1e. It seems as though this NIC requires atl1c, which is only available in kernel versions 2.6.29 and above. uname -r currently lists mine as 2.6.28-11-generic. Is there a way to get this working?

Also I have found out on other distros (such as Sidux - which has released a LiveCD with 2.6.30 on it) even though it detects my network card and shows eth0 in ifconfig, I am still unable to go online for some reason. It is not a modem/router/cable problem. It is not a hardware issue (works on Win 7 beta). Replacing the NIC is not an option as it is a laptop.

I would really appreciate any and all help. I have been searching for quite some time now and nothing has worked. If possible I would also like detailed answers as I am new to Kubuntu though I have used other Linux distros before (I am unfamiliar with Debian-based distros).

---

### Post by hughh on 2009-07-29
I have a new Acer Aspire 5810TZ with a similar problem: no eth0 interface.  In addition to lo, wlan0 and wmaster0, I also have a pan0 interface.  Wireless works fine.

---

### Post by Onsanit on 2009-09-16
I have same problem  (ACER 4535) All network not work.

---

