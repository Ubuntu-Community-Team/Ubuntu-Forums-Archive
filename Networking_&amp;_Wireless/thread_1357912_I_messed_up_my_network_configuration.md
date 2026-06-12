---
title: "I messed up my network configuration"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by kalaka on 2009-12-17
Fellow Ubunters,

Honestly, I have no idea what I did or how I did it but I must've changed something (maybe the hosts file or something), its totally my own fault.

I have Ubuntu Intrepid and I can't go online. The funny thing is, I get an IP address and I can even go into my router's config page (192.168.1.1). I can't ping [www.google.com](www.google.com) but I get a response from my router's IP.

When I pop in an Ubuntu LiveCD or when I boot into Windows everything works fine, I can go online with no problems.

Something must be wrong with my Intrepid's network setup.

I don't want to reinstall Ubuntu. Please help.

thanks in advance

---

### Post by Iowan on 2009-12-17
Can you ping internet by IP address? Try ```
ping -c4 209.85.225.106
```If that works, check */etc/resolv.conf* to see if you have valid nameservers listed.

---

### Post by kalaka on 2009-12-17
Hi, thanks for your help,

I can ping it!
my resolv.conf says > nameserver 192.168.1.1

---

### Post by Iowan on 2009-12-17
Check what LiveCD and Windows use for DNS servers. Intrepid is using the router for DNS server - presumably, the router gets DNS from elsewhere... but maybe Intrepid should have  a different nameserver listed...

---

