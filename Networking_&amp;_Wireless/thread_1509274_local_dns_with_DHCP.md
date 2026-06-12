---
title: "local dns with DHCP"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2010-06-14
I'm setting up my home server.
I have a server and 2 clients. (1 windows, 1 ubuntu)
I set the server to use DHCP and it working.


However I want to resolve the clients names by their dhcp.

The only way I know is to edit /etc/hosts  but that uses static ips.

Can i do it by mac address and where?


(side note would that be considered WINS since one is a PC?)

---

### Post by Peter09 on 2010-06-14
Well the only way I have ever been able to do this is to install winbind
 
```
sudo apt-get install winbind
```
 
and also edit the file /etc/nsswitch.conf
 
and change the line
 
> hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
to
> hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4
 
then restart winbind
 
```
sudo service winbind restart
```

---

### Post by wlraider70 on 2010-06-14
I don't quite see how that would help. could you explain it better.


After a little more thinking and i night sleep, I think what I was looking for is a netbios.

I want to do "ping lappy" and have my serverknow the ip address of the lappy.

My issues it that im using DHCP so the hosts file wont do.

---

### Post by Peter09 on 2010-06-14
Wellwinbind will resolve your host names on the fly for you.

---

### Post by Iowan on 2010-06-14
I have DNSMasq for DHCP/DNS server on my netowrk - it seems to do a good job linking DHCP with DNS - DHCP clients can ping other DHCP clients by name... IF the machines have sent their hostname to DNSMasq. This didn't happen by default - I needed to change the "send hostname" line in */etc/dhcp3/dhclient.conf*

---

