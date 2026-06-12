---
title: "Wireless Gone?"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by Pawnda on 2009-02-23
Hi Guys.
I installed ubuntu on my msi wind last week.
Everything have been running fine until now.
While i was downloading a torrent i suddently got disconnected.
Now i can't connect to any wireless networks...
I got a rtl8187se mini-pci express wireless card.
If you need me to provide any information just ask me.

---

### Post by Pawnda on 2009-02-23
okay... i just reinstalled ubuntu... still no wireless..
both internal rtl8187se and my external awus036h...

---

### Post by puppywhacker on 2009-02-23
I installed the drivers for the rtl8187se from MSI. compiled them against my kernel and it works.

[http://global.msi.com.tw drivers]("http://global.msi.com.tw/index.php?func=downloaddetail&type=driver&maincat_no=135&prod_no=1474")

---

### Post by Pawnda on 2009-02-23
I formatted my pc and installed ubuntu again...
Both my internal and external wireless card is unable to connect.
But just figured out that i can still connect to unsecure networks...

From daemon log:
Feb 23 23:38:44 crimson-laptop NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-wifi.c.1512 (get_secrets_dialog_response_cb): canceled.

---

