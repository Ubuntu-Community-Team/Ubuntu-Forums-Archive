---
title: "How fast your LAN speed?"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by R.Bucky on 2011-02-14
My LAN is mostly Gigabit, but have a few bottlenecks with 100BASE. When I transfer files from server to server, I get around 8MB/s. How does this speed compare to other similar LAN's?

---

### Post by dmizer on 2011-02-14
What protocol are you using for your file shares and how are you mounting them?

---

### Post by R.Bucky on 2011-02-14
I use cifs with defaults 0 0

---

### Post by tgalati4 on 2011-02-14
That's about right.  I get 8 to 12 MB/sec.  Realize that 12.5 MB/sec is the maximum for a 100 Mbit/sec connection (100 Megabits/sec divided 8 bits/byte = 12.5 MB/sec).  A typical Gigabit connection (1,000 Mbits/sec) only sustains 1/10 of that bit rate with traffic.  So now you are looking at 100 Mbits/sec or 12.5 MB/sec.  With overhead and handshaking that could easily drop to 8 MB/sec.

The quality of your network cards, switches, and cabling (shorter is better) can affect your speeds.  If you have a real server with dual Gigabit cards, you can bond the cards (similar to RAID for disks) to double throughput.  Of course any 100BaseT switches that you are going through would limit your speeds to 100 Mbits/sec peak or 10 Mbits/sec sustained with traffic.

---

### Post by dmizer on 2011-02-14
> **R.Bucky said:**
> I use cifs with defaults 0 0

Can you please post your /etc/fstab mount line?

---

### Post by R.Bucky on 2011-02-14
/etc/fstab mount line

```
//10.1.10.29/FOLDER /FOLDER username=name,password=pw 0 0
```

I mis-spoke on the defaults reference.

---

