---
title: "ip_masq_ftp"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by dmbfck on 2010-01-26
Hey,

FTP is not working through a gateway and I think I found that I need to modprobe ip_masq_ftp.  However, when I do try to load ip_masq_ftp I get the error: FATAL: Module ip_masq_ftp.o not found.

My question is: how do I get ip_masq_ftp?  

More questions:  Do I have to build a new kernel?  If I do need to build a new kernel do I just include the ip_masq_ftp module or are there other modules that I need?

Thanks,
G

---

### Post by dmbfck on 2010-01-26
> modprobe nf_nat_ftp

^fixed me right up.  I got my gateway working the way I want it to now.

---

