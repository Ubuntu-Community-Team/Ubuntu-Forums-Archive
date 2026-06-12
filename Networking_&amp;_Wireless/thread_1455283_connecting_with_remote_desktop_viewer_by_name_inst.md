---
title: "connecting with remote desktop viewer by name instead of IP address"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by cedardoc on 2010-04-15
The computers on my network change IP address from day to day, so connecting through trial and error is becoming a pain.  When I used to use UltraVNC in windows you could just enter the computer name and it would just find it.  Is there a way to do this with Remote Desktop Viewer 2.28.1 (on Ubuntu 9.1)

I've tried "smb://computername/", and just "computername"

there doesn't seem to be a lot of documentation for this application (or at least I haven't been able to find it - other than the Vinage Manual which didn't help)

I am pretty much samba-illiterate... I wonder if it has to do with that.

anyone have any ideas?

Thanks,
Dave

---

### Post by n2stc on 2010-04-17
I am looking for an answer to this also.:confused:

---

### Post by howefield on 2010-04-17
> **cedardoc said:**
> The computers on my network change IP address from day to day, so connecting through trial and error is becoming a pain.

Can't you assign specific IPs to your computers via your router settings ?

---

### Post by Iowan on 2010-04-17
I use DNSMasq for DHCP/DNS on my network. It allows me to ping/ssh/etc via hostname rather than IP address - even to DHCP clients. However, the clients must provide their hostname. I needed to edit */etc/dhcp3/dhclient.conf* and change the line:```
send host-name "<hostname>";

``` to the machine's actual name.

---

