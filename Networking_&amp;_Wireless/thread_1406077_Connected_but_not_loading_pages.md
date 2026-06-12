---
title: "Connected but not loading pages"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by sacher on 2010-02-13
Hi,
 
I just installed Ubuntu 9.10 in a dual boot Vista system (DELL INSPIRON 530). Everything was ok except the wireless network configuration. Afrer checking on the Internet I realized There was an issue with my network card (Broadcom BCM431. I first tried to install the drivers using Ndiswrapper with not succes. Finally, I was able to use the b43 driver by installing b43-fwcutter. Now the driver is shown and active in the Hardware Drivers Utilily. I am even connected to my Wireless Network. However, I can´t load any website.
I have checked the parameters in the network set up. I have even tried different options, like static or dinamic IP. But I can´t load any website.
 
Any idea?

---

### Post by Iowan on 2010-02-13
Check */etc/resolv.conf* to verify a valid nameserver. 
Also check results of **route -n** - the last line should list your default gateway (probably your router).

---

### Post by sacher on 2010-02-13
Thanks Iowan,
I don know what happened but I just restarted my system to boot Linux and it automatically connected to the internet using an automatic DHCD and it is working.

---

