---
title: "HP printer on eth0 always busy"
date: 2005-12-31
forum: Networking &amp; Wireless
---

### Post by gdlx on 2005-12-31
Breezy 5.10 on AMD-64 laptop. Dual boot
Lan connection is Ethernet 10/100 full duplex. Access to internet goes thru XP desktop.
The HP business jet 1200 works from windows on both computers.
It is connected to the computers thru a Linksys ezxs55w switch. Cables are cat 5e. 
No problem with internet access on Ubuntu or XP. Printing on XP is great. All features work.
On Ubuntu, the closest it has come to printing is to give a busy message.

Printing: Network host '192.168.0.149' is busy; will retry in 30 seconds...

I have been lurking and working on this for over three weeks. I have been through the CUPS tutorial several times and other tutorials as well. In short, I have tried every suggestion I can find on the internet. What can I try next??

---

### Post by hajk on 2006-01-02
It might help if you provided a bit more information on your local network setup.
What is the output from "sudo route"? What does /etc/network/interfaces look like?

---

