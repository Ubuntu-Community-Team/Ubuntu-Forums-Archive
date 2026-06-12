---
title: "New network card - no internet connection"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by kerius on 2006-07-02
I've just started using Ubuntu.  I've been experiencing slow internet connection speed so installed a new network card to see if that would help speed things up.  In doing so, I've lost my internet connection.  

Any ideas as to where to start troubleshooting?  Is there configuration that needs to happen and where would I find this. 

Any help much appreciated,

Kerry

---

### Post by mips on 2006-07-02
Put the old card back and start looking at your DNS configuration.

---

### Post by kerius on 2006-07-02
Re-installed old card and now I'm connected.  Still slow but not broken anymore. 

Thanks,

Kerry

---

### Post by mips on 2006-07-02
Kerry,

Have a look at your DNS settings as well as IPv6. I suspect your issues might be dns related because you say things are slow.

---

### Post by fragos on 2006-07-02
Using IPV6 now will insure that when and if it is actually used your system will transparently work.  The penalty comes from attempting to communicate with IPV6 the system must wait for timeouts to know to try IPV4.  The delay is for some reason most noticable when accessing dns to resolve domains into IP addresses.

---

### Post by mips on 2006-07-05
[QUOTE=fragos]Using IPV6 now will insure that when and if it is actually used your system will transparently work.  The penalty comes from attempting to communicate with IPV6 the system must wait for timeouts to know to try IPV4.  The delay is for some reason most noticable when accessing dns to resolve domains into IP addresses.[/QUOTE]

The majority of home networking devices do not support IPv6 and you will have to upgrade your adsl router or whatever when the time comes for IPv6 deployment from ISPs. For years they bitched & moaned about a lack of addresses until NAT came along, now they could care less about IPv6 as far as it looks.

---

