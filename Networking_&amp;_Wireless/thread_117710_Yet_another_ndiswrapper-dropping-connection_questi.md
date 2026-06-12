---
title: "Yet another ndiswrapper-dropping-connection question"
date: 2006-01-15
forum: Networking &amp; Wireless
---

### Post by tzimtzum on 2006-01-15
I apologize in advance if this question has been answered before, but I couldnt find any solution that worked for me.

Connection dies (not able to ping the gateway) after a few minutes browsing using a ndiswrapper-wificard.

I have a Netgear WG121 usb wifi device, that worked great in Ubuntu 5.04 via ndiswrapper 1.2 (connection died pretty fast with v1.1), using windows drivers netwg121v200, wep and static ip.

Now I tried the same device on another machine running Ubuntu  5.10. Using any browser in X, connection dies after a few minutes, but there is no problem downloading or updating from apt repositories or browsing with lynx. I tries ndiswrapper 1.1, 1.2, 1.6 and 1.7 with 2.6.12-9 and 2.6.12-10 kernel. Defining a specific channel didnt help. Power-management of the card is off. No messages in the logs. Reloading the module restores the connection. Another machine is online on the same wifi 24/7.

Im at a loss, please help me.

---

### Post by tzimtzum on 2006-01-18
UPDATE:

Im experiencing the same on Drapper (ndiswrapper 1.5). Connection works fine, as long as Im not browsing in X.

---

