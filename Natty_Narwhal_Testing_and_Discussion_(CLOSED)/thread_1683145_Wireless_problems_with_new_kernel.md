---
title: "Wireless problems with new kernel"
date: 2011-02-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2011-02-07
Is anyone having wireless problems with the most recent kernel upgrade. I cannot get any connection since the latest upgrade on previously working machine.

---

### Post by teachop on 2011-02-07
Wireless isn't working on my Acer Aspire 3100 with Atheros.  What wireless hardware are you using?

---

### Post by TBABill on 2011-02-07
I'm not running it, but I did see a post from a user with a Broadcom card and with the latest updates had to switch from the Broadcom STA driver to the B43 because the STA would just not work at all after the update. I don't believe the issue was resolved and the b43 was the workaround.

---

### Post by Peter09 on 2011-02-07
This is happening with an Atheros card and a DLink Raxxx card.

Looking in the syslog for the machine it is telling me that the connection > has security but secrets are required 

Not sure where the problem lies at the moment. Both the internal and USB card are identified, but remain disconnected.

---

### Post by eddygorge on 2011-02-07
148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter

Same here using 2.6.38 kernel.  Wifi will only connect to an open networks not WPA or WPA2.
Works great if I boot up with previous 2.6.37 kernel.

I've plugged in my old Zydas chipset USB dongle for the time being to get round the problem :p

---

### Post by ronacc on 2011-02-27
I'm getting random disconnects with my rtl8185 since 2.6.38 sometimes it don't connect at boot sometimes it does but disconnect after a random time and when it does I have to disable wireless and then re-enable to get it to connect again filed bug # 726058 .

---

### Post by macroshaft on 2011-02-27
I was really impressed with Natty, usually I have to re-install pre-release versions of ubuntu several times because of show stopper bugs but I managed to keep Natty on the straight and narrow until this week when both wireless and wired cards were not recognised!

I suspect I'm getting random disconnects now but I'm just monitoring the situation at the moment.

---

### Post by jennybrew on 2011-02-27
> **Peter09 said:**
> Is anyone having wireless problems with the most recent kernel upgrade. I cannot get any connection since the latest upgrade on previously working machine.

Which kernel are you using?
I always keep myself with at least two options ..one which I know recognises my hardware and the other being the latest version.

---

