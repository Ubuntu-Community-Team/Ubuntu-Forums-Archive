---
title: "Two Ubuntu machines can't ping each other by hostname?"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-04-11
I have two Ubuntu desktops. Each with a DHCP IP address and each I manually put in the hostname of each computer.

I cannot ping each computer by its hostname, but I can ping by the IP.

I kind of expected that Ubuntu would at least recognize other Ubuntu computers on the network via hostname, but I'm finding this isn't the case. 

Is this normal?

---

### Post by Iowan on 2009-04-12
Ubuntu probably wouldn't recognize itself by hostname without that information being stored somewhere.  **/etc/hosts** is one place the machine links hostnames with IP addresses.  Sometimes the DHCP server will keep track of address/hostname if /etc/dhcp3/dhclient.conf is modified to use the line ```
send host-name "<hostname>";
``` 
Sometimes **Winbind** and adjustment in */etc/nsswitch.conf* will make it work (check [this]("http://www.sigmundvoid.com/2007/08/netbios-names-and-ubuntu/") link), sometimes it requires a more integrated DHS/DHCP server (like DNSMasq).

---

### Post by doas777 on 2009-04-12
ubuntu doesn't really have a mechanism to automatically detect host names. there are a couple ways you can do it.
1) configure your hosts file on each pc as the poster above indicated 
2) configure a samba box as your WINS server (this will work for samba shareing but not for ping)
3) configure a DNS (bind) server on your network

almost all of these will require that you statically address your hosts. if you want ot do it dynamically, the trick is to integrate DHCP with DNS, so that when a PC is assigned an IP via DHCP, it registers teh address in DNS.

good luck,
franklin

---

