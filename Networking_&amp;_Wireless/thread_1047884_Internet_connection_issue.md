---
title: "Internet connection issue"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by bribri124 on 2009-01-22
I am just curious to see if anyone else has had this issue before.  Every once in a while, I will lose my ISP connection briefly, but it will come back 1-2 minutes later.  Ever since I upgraded to Intrepid, whenever this happens my system will not gain Internet connection again.  I have not gone into depth of this issue, but I do believe this may be a DNS issue.  I'm running DHCP and have been able to connect internally and externally to/from this system via SSH whenever this issue occurs.  I will post whatever might help.

Any thoughts?

---

### Post by superprash2003 on 2009-01-23
when your internet connection is down.. go to the terminal and type ping 72.14.205.100 .. if it pings successfully.. then its mostly a dns issue!!

---

### Post by bribri124 on 2009-01-24
I wasn't questioning the whole DNS issue, but I do appreciate your help.  I discovered Network Manager only listed my router as a Nameserver, so I just added my DNS servers, and the issue is fixed.

---

