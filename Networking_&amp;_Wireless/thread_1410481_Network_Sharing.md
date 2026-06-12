---
title: "Network Sharing"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by joncleve on 2010-02-18
I have 4 desktop machines and two laptops connected to my home network. One desktop  and one laptop are running Ubuntu 9.10.
When I browse the network from my Ubuntu laptop, I can see all the  other pc's except the Ubuntu desktop. I have printer sharing enabled on it but it just won't show up. Is there something I'm missing?

---

### Post by johnson.d on 2010-02-19
Can you specify the method of printer sharing, samba or through printer configuration?

If you have shared the printer through printer configuration, You can connect to the printer from the laptop using the following steps:

Goto printer configuration-> Server-> Connect
At "Cups Server" enter the ip-address of the Ubuntu desktop machine
Now it will display the printers connected to the system

---

