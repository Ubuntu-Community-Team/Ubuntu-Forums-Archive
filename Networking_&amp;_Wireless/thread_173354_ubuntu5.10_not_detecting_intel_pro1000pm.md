---
title: "ubuntu5.10 not detecting intel pro/1000pm?"
date: 2006-05-10
forum: Networking &amp; Wireless
---

### Post by pan8609 on 2006-05-10
Hi there, I'm new to linux so excuse me if the problem seemed stupid..:confused: 

I've just installed ubuntu5.10 on a Acer TM8204 with Intel Pro/1000 PM NIC.
The card was not detected during installation so now I can only use firewire for network access

I downloaded the e1000-7.0.38 (from sourceforge), then 
make install.

and I got this message:
"cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode"
but I do have a new file "e1000.ko" created at /lib/modules/kernel-version/drivers/net/e1000/

then I tried "modprobe e1000" and saw it loaded in "lsmod"
but I cannot see any new interface using "ifconfig -a"

I also tried adding e1000 in /etc/modules then restart, but I still cannot get my card working  :neutral:

---

