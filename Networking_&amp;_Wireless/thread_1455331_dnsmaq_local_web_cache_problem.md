---
title: "dnsmaq local web cache problem"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by dre12b on 2010-04-15
I'm using a USB modem 3g broadband connection (ppp0).  I want to improve speed and conserve bandwidth so I set up a local web cache that I believe is resolving addresses for my ubuntu machine and the three other machines it is routing a connection too.  I followed the instructions [here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") to convert my ubuntu machine into a router with a dhcp and dns server and then used followed this [tutorial]("http://embraceubuntu.com/2006/08/02/local-dns-cache-for-faster-browsing/") for dnsmasq to set up the local dns cache.  The unpleasant surprise is that every time my connection resets, resolv.conf loses the first line (nameserver=127.0.0.1) and the local dns cache goes down.

This is confusing because I edited my dnsmasq.conf to prepend this address, as per the instructions here.

This is the edited section of /etc/dhcp3/dhclient.conf:

```
prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers;
```
 
Anyone have any helpful suggestions?

---

### Post by GeorgeVita on 2010-04-17
Hi **dre12b**, just some ideas:

How are you connecting via 3g?
Each method tries to 'update' file /etc/resolv.conf changing its contents.

For example using wvdial to connect you have to edit 2 files:
1. remove 'usepeerdns' from file etc/ppp/peers/wvdial
2. add 'check DNS = no' and 'auto DNS = no' to file /etc/wvdial.conf
(above taken from: [http://ubuntuforums.org/showthread.php?t=1420718](http://ubuntuforums.org/showthread.php?t=1420718))

Other methods possibly need 'trimming' to their configuration files.

Regards,
George

---

### Post by dre12b on 2010-04-17
Yes, I am using wvdial to connect a USB 3g modem.  Thanks a lot George!  I'm going to try your recommendations and I'll report back.

*Edit.  Looking at these suggestions it seems like they'll prevent wvdial from updating the DNS when it connects, which was not my intent.  What I was hoping to do was just prepend 127.0.0.1 in front of the DNS nameservers that are updated on connection.  

On the other hand, another option is to ditch my ISP's DNS and statically configure to use openDNS and 127.0.0.1.  That way, preventing wvdial from updating the dns on connection will be fine.  Ahh, sometimes it's so hard to remember that there's more than one way to skin a cat.

---

### Post by GeorgeVita on 2010-04-17
> **dre12b said:**
> ...
On the other hand, another option is to ditch my ISP's DNS and statically configure to use openDNS and 127.0.0.1.  That way, preventing wvdial from updating the dns on connection will be fine.  Ahh, sometimes it's so hard to remember that there's more than one way to skin a cat.

I think this 'trick' will make it!

Good Luck,
George

---

