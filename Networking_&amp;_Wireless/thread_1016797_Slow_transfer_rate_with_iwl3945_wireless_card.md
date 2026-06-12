---
title: "Slow transfer rate with iwl3945 wireless card"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by speedsix on 2008-12-20
The wifi card in my Compaq 6720s laptop seems to give very poor performance with the afore mentioned driver. I've tried it on several wireless networks and transfer rate peaks at around 1.5MB/sec, Samba/SSH etc.

lspci lists

```

10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

I believe it's a 54Mbit/sec card.


Thanks

---

### Post by speedsix on 2008-12-27
Anyone?

I'm currently copying some files via SCP and getting ~700kb/s

---

### Post by speedsix on 2008-12-29
Is anyone aware of a command to determine the exact mode the card is operating in as my speeds are definitely around the 11mbps mark instead of nearer 54.


Thanks

---

### Post by alex wingnut on 2008-12-29
dmesg | grep iwl3945

I'm trying to solve the same issue at the moment and found this link, I hop it helps.

[http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html](http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html)

---

