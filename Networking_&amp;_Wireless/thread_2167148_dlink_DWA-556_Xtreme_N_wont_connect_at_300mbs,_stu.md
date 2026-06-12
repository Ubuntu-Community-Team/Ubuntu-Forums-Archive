---
title: "dlink DWA-556 Xtreme N wont connect at 300mbs, stuck at 130mbs"
date: 2013-08-12
forum: Networking &amp; Wireless
---

### Post by ezra-hubbell on 2013-08-12
I have a dlink DWA-556 Xtreme N wireless card and it wont at 300mbs, tops out at 130mbs.
I have the ath9k driver installed
[http://wireless.kernel.org/en/users/Drivers/ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k)

I am extremely new to linux and am loving it so far.  I'm just trying to work out some of the kinks and this is one of them.  
Thanks for the help.

---

### Post by flash63 on 2013-08-12
Hello,
the adapter supports only the 2.4 GHz band. &#8594; [http://www.dlink.com/us/en/home-solutions/connect/adapters/dwa-556-xtreme-n-pci-express-desktop-adapter](http://www.dlink.com/us/en/home-solutions/connect/adapters/dwa-556-xtreme-n-pci-express-desktop-adapter) - *Specifications*

---

### Post by ezra-hubbell on 2013-08-13
I still am unable to connect at the full 300mbs the card can do.  It caps out at 130mbs.  Wont go any higher.
I've done tons of searching and can't find anyone with a similar problem.

---

### Post by flash63 on 2013-08-13
300Mbps denotes the gross transfer rate, 150Mbps net is a good realistic value. 180 Mbps with three transport-streams (3x mimo/Antennas) is the theoretical maximum.

---

### Post by ezra-hubbell on 2013-08-13
hmm so even though its showing me 130mbs its multiplied and not telling me?
Is there a command to do a speed test or anything like that?

---

### Post by flash63 on 2013-08-14
> **ezra-hubbell said:**
> 
Is there a command to do a speed test or anything like that?

with iperf &#8594; [https://code.google.com/p/iperf/](https://code.google.com/p/iperf/)
```
sudo apt-get install iperf
```
Note, iperf is a client-server application! &#8594; [http://openmaniak.com/iperf.php](http://openmaniak.com/iperf.php)

---

### Post by ezra-hubbell on 2013-08-14
I just installed 13.10 and i am seeing the full 300mbs so i guess problem soleved. :)

---

