---
title: "[SOLVED] DHCP vs. static IP"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by akelsall on 2009-01-07
Got an odd problem I need some help with. I currently have my eth1 set up for DHCP, but want to configure a static IP to make network printer sharing easier.  

I set it up today and noticed that after configuring a manual IP on the interface, I can ping the interface and my router, but nothing beyond that. Why would changing from DHCP to static IP cause this problem? I did restart networking after making the change (when I change back to dhcp and restart networking, and can ping beyond the router again).

Thanks,

Andy

---

### Post by arsenic23 on 2009-01-07
Check your DNS servers listed in your connection.

Also for a more hassle free solution you might want to see if your router suports staticDHCP, so that you can leave your clients set to DHCP, but they will always receive the same IP address from your DHCP server.

---

### Post by Iowan on 2009-01-07
Somewhere around here is a thread with a post that suggests static addresses in a DHCP environment have problems with DNS.  You might be able to manually specify them - or (as suggested) set up your router to issue a static lease.

---

### Post by capscrew on 2009-01-07
> ...see if your router suports staticDHCP

The above is inaccurate and can lead to misunderstandings.  

Using DHCP one can have **permanently** assigned IP addresses, but *not* static IP's.  To set permanent DHCP addresses you would need to be able to reserve the IP address by mapping it to the MAC address in the configuration of the dhcpd (DHCP). 

Static IP addressing means all of the parameters are set by the config files.

---

### Post by Iowan on 2009-01-07
/etc/dhcp3/dhcpd.conf calls them a fixed address, my router's forum calls them a static lease (because they are issued to client by DHCP server). To me, "assigned", "issued", and "receive...from" mean pretty much the same thing - but thanks for clarifying. :D

---

### Post by akelsall on 2009-01-09
I went through the iptables "howto" (URL is below) and I think that's what fixed my problem. After making changes to iptables and configuring a static IP, everything now works. Must have been some FW rule that was messed up is all I can figure.

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Andy

---

### Post by arsenic23 on 2009-01-09
> **capscrew said:**
> The above is inaccurate and can lead to misunderstandings.  

Using DHCP one can have **permanently** assigned IP addresses, but *not* static IP's.  To set permanent DHCP addresses you would need to be able to reserve the IP address by mapping it to the MAC address in the configuration of the dhcpd (DHCP). 

Static IP addressing means all of the parameters are set by the config files.

Most consumer routers label what your talking about as 'staticDHCP'.  Where you input the MAC address and desired IP of a computer into the router and it makes sure that machine always gets that same IP.

---

