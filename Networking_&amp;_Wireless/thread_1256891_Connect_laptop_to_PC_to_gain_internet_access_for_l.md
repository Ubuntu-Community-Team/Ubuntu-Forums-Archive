---
title: "Connect laptop to PC to gain internet access for laptop"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by darkworld on 2009-09-03
I have a laptop running Dapper and a PC running Jaunty, I have connected the two with a cross over cable between their Ethernet ports. 

The PC has internet connection via a USB Mobile modem. Im want to gain access to the internet for my dapper laptop so that I can get the dapper laptop software updates. Plus, if possible, obtain the software that jaunty uses to run the USB modem on my dapper laptop.

Can this be done. 

I have never tried joining two machines like this before. Many thanks, help much appreciated.

---

### Post by stefangr1 on 2009-09-03
This is possible, but I don't think there's an easy way.

One way to achieve this is to set up a dhcp server and dns server on the notebook, and offer services on your NIC while using the wifi connection as default gateway.

---

