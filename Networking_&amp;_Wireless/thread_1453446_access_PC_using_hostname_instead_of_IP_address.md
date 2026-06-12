---
title: "access PC using hostname instead of IP address"
date: 2010-04-13
forum: Networking &amp; Wireless
---

### Post by G.D.C. on 2010-04-13
Right now my setup is as follows: I have an Asus Eeepc 900 running Netbook Remix named eeepc, and a media centre running 64-bit Ubuntu named media.
 
When I try to ping or ssh into one machine from the other, for example
```
$ ping media
```
I get an "unknown host name" error. However, pinging the device's IP address works. How do I get the computers to recognize each other's host names? Did I miss something in the setup?

---

### Post by estamand on 2010-04-13
Edit the /etc/hosts file on each machine.

on the eeepc add the entry for media and it's IP.  To the same for the media pc.

---

### Post by Iowan on 2010-04-13
I use DNSMasq as my network's DHCP/DNS server for that very reason, but even then, the client (Ubuntu) machines must have */etc/dhcp3/dhclient.conf* modified to ```
send host-name "mycomputer";
```
*/etc/hosts* file works fine if you only have a few machines and short-term (otherwise, dynamic IP's means starting over).

---

