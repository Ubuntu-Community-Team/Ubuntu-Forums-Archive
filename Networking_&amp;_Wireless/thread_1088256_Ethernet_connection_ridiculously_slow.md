---
title: "Ethernet connection ridiculously slow"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by dugguz on 2009-03-05
Hi,

My ethernet connection runs really slowly whenever I use ubuntu. I am able to ping google, so I guess it connects to the DNS, but the connection times out before loading the page in firefox. This doesn't happen when I run windows on the same box. Any ideas as to what is happening? Thanks.

---

### Post by phillroberts on 2009-03-05
Does the ping take a long time to respond -say more than about 5 seconds or so?  

Do you use any vpn clients or anything that would change your resolv.conf?  If so, I'd check and make sure the correct values are in there before going further.  I use kvpnc and for some reason it didn't remove the search parameter from my resolv.conf and my internet connection got really slooooow.  DNS lookups it seemed took 10-15 seconds.


If that doesn't work, you can try disabling ipv6.  See [this thread]("http://ubuntuforums.org/showthread.php?t=87798").  Some say it works for them, but it didn't work for me. YMMV.

---

### Post by dugguz on 2009-03-05
Pings take ~150ms, and resolv.conf looks fine. Thanks for the link, I'll try disabling ipv6.

---

### Post by dugguz on 2009-03-05
Wow, disabling ipv6 worked perfectly. Thanks heaps.

---

