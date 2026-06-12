---
title: "Wireless crashes during NFS transfer"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by di_dum_dum on 2010-10-15
Hello all,

During NFS transfers my laptop crashes my entire wireless network. Laptop is a Samsung R20, Ubuntu 32-bit 10.04 with atheros AR5001 wifi and ath5k driver.

What works:
->NFS is working. I have 3 other machines on wired connections that use NFS happily. And the NFS shares work fine if i plug the laptop into a wired connection.
->Wifi works. I can browse the internet and a large download (700MB) with bittorrent takes 8 mins and doesn't down the wireless.

What doesn't work:
->NFS and wireless together. Any NFS transfer over wireless eventually downs the wifi. Forl example streaming one 3mb mp3 in rhythmbox crashes wireless after playing for about 30 seconds. When the wireless fails it breaks for ALL computers and the only way to re=establish it is by restarting the router. Wired connections remain OK even when wireless is down (both from the same router).
->I have a 64-bit desktop with wifi that also suffers the same problem but that doesn't matter so much since it also has a wired connection.

I am lost for ideas. Does anyone have any ideas/suggestions as to what might be causing this?

Thanks

---

### Post by SeijiSensei on 2010-10-15
Try using "async" among the options on the server.

---

