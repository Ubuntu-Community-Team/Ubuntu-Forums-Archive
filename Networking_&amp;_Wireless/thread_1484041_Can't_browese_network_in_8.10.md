---
title: "Can't browese network in 8.10"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by Coder68 on 2010-05-15
Sometimes I can see my Windows PC's names in my network, and even connect... but most of the time I can't. It is very rare that I can see them.  I can't even see my freenas in Ubuntu 99% of the time. 

I have tried adding wins to my nsswitch.conf, moved the order around... and I have tried changing the resolver order? (cant find that post again to remember what it was but I changed it back after it did not work)... but nothing changes. I even tried shutting down the firewall.   I can mount Windows shares by IP via the connect to  server, but not my freenas. I now have everything I changed  back to "stock".  The only installs I have done to Ubuntu 8.10 was Wireshark, Nmap, a codec/player package and Flash. (Flash does not play worth a dman  in full screen!)

I have tried all the fixes I can find here in the forum and out in Googleland.  I just want to be able to reliably see and connect to Windows shares. 

One thing I did notice in Wireshark and terminal... when I try to ping my freenas or any other PC name on my network... it gets resolved to an 8.x.x.x IP... I am not sure why it is going to DNS over local... But that explains why it can't mount the network. Windows PC's have zero issues with each other or the freenas. 

Any help would be greatly aprecieated. 

Coder68


Current nsswitch.conf:
> # /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

---

### Post by Coder68 on 2010-05-15
Bump.
Bump.

Anyone?

---

### Post by Coder68 on 2010-05-15
Anyone?

---

### Post by Iowan on 2010-05-16
Once/day should be plenty for bumping...
[This]("http://ubuntuforums.org/showthread.php?t=1169149") How-To should have some information for setting **winbind** and **nsswitch.conf**.

---

