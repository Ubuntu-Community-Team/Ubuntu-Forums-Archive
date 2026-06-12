---
title: "dhcp send hostname"
date: 2013-08-01
forum: Networking &amp; Wireless
---

### Post by spip on 2013-08-01
Hello,

Configured an Ubuntu 12.04 machine in a predominantly windows shop, so that machine is the exception (use it for network simulation on games). No problem using qdiscs, ip masquerading, etc. All good.

However, I would like the dhcp client to register its hostname to the DNS server. Searching around it seems that everything is configured correctly for this to happen. The main issue people usually encounter is the missing line from/etc/dhcp/dhclient.conf:

   send host-name "<hostname>";

But I have it, yet it is not working, I am not able to resolve that machine's hostname from another machine (on the same subnet).

Knowing this machine lives on a windows network mostly, are there known compatibility issues between dhclient and whatever DNS server software typical windows shops use? :)

Thank you,
spip

---

### Post by AvitarX on 2013-08-01
Is it possible that the Windows machines are all using WINS to look up IP addresses, and not dynamic DNS from the DHCP server?

---

### Post by spip on 2013-08-02
I will find out. However my linux machine is able to resolve hostnames on the network and I would assume it isn't using WINS to do so. I will find out though.

Thanks,
spip

---

### Post by ozseptember on 2013-08-07
G'Day,

Usually I run my Ubuntu machines in a pure linux environment and have DDNS working just fine. Currently trying to do the same under a Windows environment and having a similar issue with getting my machines to update properly with the Windows DNS server.

Have you found a solution yet? Mine might be a bit different, I have a number of PCs (Ubuntu 11.04), that I've attempted to image, all of them have the hostname set correctly in /etc/hostname, yet in DHCP and DNS they keep the original hostname and haven't been under to locate where it's coming from.

Anyway would like to hear back on how you went, I think my next step will be to manually set the "send host-name" to the actual hostname rather then letting <hostname> decide.

---

### Post by spip on 2013-08-09
Hi there,

In my case the IT department told me that the DNS update message has been rejected because it was unsecure (I think we do session authentication using kerberos). You're right, your issue is different.

spip

---

