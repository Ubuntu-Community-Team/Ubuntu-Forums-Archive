---
title: "Strange problem with wireshark and TL-WN422G"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by anon55672 on 2010-10-31
Hello everyone! I've recently bought TP-Link WN422G wireless adapter with atheros chipset.   I've followed [this guide]("http://marko-m-markovic.blogspot.com/2010/08/tp-link-tl-wn422g-v2-ar9271-usb-stick.html") successfuly and now I can see the adaptor with iw/ifconfig.    However, when i tried connecting with wicd to ANY wireless network (no encryption and pretty good signal) I got error 'unable to get IP'.   I've ran wireshark to see what is happening when I try to connect and - voila! It immediatally got connected!    I've tested at least 30 times connecting to the AP with and without wireshark running, and I can connect with no problems while it is running and not at all while it isn't.    So, I'm just asking what does wireshark have to do with connecting to router at all?

---

### Post by anon55672 on 2010-10-31
The problem is solved. Apparently the problem was that I spoofed MAC address of the wireless adapter and running wireshark had put it into promiscuous mode.  But still, I've worked with many wireless cards and every one of them worked fine when I spoofed it's MAC.

---

