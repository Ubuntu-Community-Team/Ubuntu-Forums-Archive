---
title: "Programatically determine MAC address of local machine"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by BillRebey on 2009-02-12
I've scoured the Web in search of a way to determine my MAC address from a C program, but with no success.

I do this on BSD (Mac OS/X) by creating a connectionless socket to the target system, which can then be used to obtain my IP address (this allows for multi-homed networks with multiple network interfaces, in which case the hosts IP changes with a connection's context), then using getifadddrs(...)', traversing the returned list to find the entry that applies to my IP address and is an IF_LINK. Casting that element's sockaddr to a sockaddr_dl structure easily provides me with the MAC address.

Linux appears to support getifaddrs(...), but not the sockaddr_dl structure that provides the MAC address. Certainly it's s trivial matter to hand-create a sockaddr_dl structure, but its absence tells me that not only is the data structure missing, but so is the functionality to populate it.

Does anyone know how to programmatically obtain the MAC address of my host PC?

[I'm using gcc on "Ubuntu 2.6.20-generic" (according to 'uname -a'), or "7.04, feisty" (according to 'lsb_release -a'), with gcc 4.1.1]

---

### Post by jpeddicord on 2009-02-12
Moved to Networking & Wireless.

---

