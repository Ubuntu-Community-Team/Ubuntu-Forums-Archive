---
title: "Connected but no connection"
date: 2011-02-19
forum: Networking &amp; Wireless
---

### Post by lvqinghouer on 2011-02-19
hey guys, weird problems. I can get connected to the Internet when I reboot the system, but the connection usually fails after within 10 mins. However, even then the network manager says it's connected. Never reconnect, manually or automatically. I don't know what's going on and please help me out here. Thanks a lot. 

Information you might want. Please let me know if you need more. :)

uname -a
Linux JX-new 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux

lspci | grep net
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

Thanks.

---

### Post by Iowan on 2011-02-19
On bootup,  check (from a terminal) **ifconfig -a**, and **route -n**. Recheck when connection fails - see if interface IP address or routing changes.

---

### Post by lvqinghouer on 2011-02-19
> **Iowan said:**
> On bootup,  check (from a terminal) **ifconfig -a**, and **route -n**. Recheck when connection fails - see if interface IP address or routing changes.

Hi lowan, thanks for this fast reply.

I've done that many times, they're the same as long as you don't try to re-connect. They're valid addresses too, but just cannot ping through.

---

