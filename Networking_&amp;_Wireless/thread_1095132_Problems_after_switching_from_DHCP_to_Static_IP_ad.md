---
title: "Problems after switching from DHCP to Static IP address"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by derdud on 2009-03-13
Initially when I had set my server up, I was using DHCP. I had a reservation set up to assign it an IP of 10.56.232.150. I have this server doing a bit more now, so I want to move it into our DMZ. I tried to assign it an IP address of 172.16.1.5, but it doesn't seem to be working. I tried 172.16.1.8 as well, just in case I screwed up and .5 was in use by something already, but that didn't work either. 

To summarize what I did:

[LIST=1]
[*]Edited /etc/resolv.conf:
```
search my.domain.com domain.com
nameserver 172.16.1.2
nameserver 4.2.2.1
nameserver 64.102.255.4
```
[*]Edited /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 172.16.1.5
gateway 172.16.1.1
netmask 255.255.255.0
```
[*]Restarted the network services:
/etc/init.d/networking restart
[/LIST]

Once the networking restarts, if I try to ping anything else on 172.16.1.0 I get no response. The gateway is 172.16.1.1, and I have two other servers that should respond at 172.16.1.2 and 172.16.1.3. I get no response from them however. It just says:

PING 172.16.1.2 (172.16.1.2) 56(84) bytes of data.
From 172.16.1.5 icmp_seq=1 Destination Host Unreachable
From 172.16.1.5 icmp_seq=2 Destination Host Unreachable
From 172.16.1.5 icmp_seq=3 Destination Host Unreachable

I can ping its own IP address, however. If I ping 172.16.1.5 I get a response, so I guess that's a plus but it's still not doing me any good. I tried rebooting the server for the hell of it, just to see if that made a difference, but I get the same behavior once the server comes back up.

Now I don't know if this may be part of the problem (I doubt it), but I had a shared folder that I was mounting prior to me putting this server on our DMZ. Whenever I restart the networking services, I get a warning that looks like this:

"mount error: could not find target server. TCP name backupserver/backup-disk not found
No ip address specified and hostname not found."

I went back in and changed it to DHCP and everything works fine again with the 150 address.

Any ideas as to why I can't seem to get this server to work properly with a static IP?

---

### Post by derdud on 2009-03-16
bump

---

