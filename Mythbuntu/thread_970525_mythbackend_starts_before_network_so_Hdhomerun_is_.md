---
title: "mythbackend starts before network so Hdhomerun is not initialized"
date: 2008-11-04
forum: Mythbuntu
---

### Post by the Goat on 2008-11-04
Every time I reboot my backend machine mythbackend can not initialize one of my HDhomerun units because the network is not available when it tries to contact it.  The second HDhomerun initializes fine because it gets initialized just a bit later.

After the reboot is complete I run:
```
sudo /etc/init.d/mythbackend restart
```
And both my HDhomruns get initialized correctly.  But I would prefer not having to manually do this everytime I reboot.

Any solution?

---

### Post by SiHa on 2008-11-04
If it's just a timing issue, rather than the specific order the bits are initialized, which it looks like, as your second card is OK. Could you just put a sleep command in the mythbackend init script? ```
 sleep 10 
```
...or something similar at the beginning.

---

### Post by 7bigjohn on 2008-11-04
This has happened to me before too.  This seemed to fix the problem.  I haven't tried it on 8.10 though

[http://ubuntuforums.org/showthread.php?t=593181&highlight=roaming+mode]("http://ubuntuforums.org/showthread.php?t=593181&highlight=roaming+mode")

---

### Post by the Goat on 2008-11-04
> **7bigjohn said:**
> This has happened to me before too.  This seemed to fix the problem.  I haven't tried it on 8.10 though

[http://ubuntuforums.org/showthread.php?t=593181&highlight=roaming+mode]("http://ubuntuforums.org/showthread.php?t=593181&highlight=roaming+mode")

Yes that was the old solution to the problem (you can see I was the one who started that old thread).  But in ubuntu 8.10 I can not find a "roaming mode" setting to turn off.

---

### Post by luigidk on 2009-11-09
Was this ever solved?

I'm on 9.04 and having the same issue.

---

### Post by ian dobson on 2009-11-09
Hi,

"Roaming mode" is a nice name for a Network connection where the IP address is obtained by DHCP. This is configured by the X-Window app. Network-Manager (yuck). The best solution would be to go over to a hardwired IP address by editing /etc/network/interface and adding a fixed IP address for your main network card.

Regards
Ian Dobson

---

