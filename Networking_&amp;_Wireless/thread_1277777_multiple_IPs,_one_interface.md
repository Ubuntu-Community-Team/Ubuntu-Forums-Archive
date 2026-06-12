---
title: "multiple IPs, one interface"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by v0idnull on 2009-09-28
I have 5 assigned IP addresses to one NIC. Is there anything special I have to do to setup Ubuntu to use those IP addresses (originally, two were being used for name servers, a third one was being used as the MX record, and the remaining two, haven't found a true use for them yet).

Thanks for your input!

---

### Post by falconindy on 2009-09-28
Just make a new config file for each... eth1:0, eth1:1, eth1:2, etc.

---

### Post by Iowan on 2009-09-29
AKA aliases, you will be using */etc/network/interfaces* to set them up. Hopefully, [this ]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking#Creating_Interface_Aliases") How-To will help.

---

