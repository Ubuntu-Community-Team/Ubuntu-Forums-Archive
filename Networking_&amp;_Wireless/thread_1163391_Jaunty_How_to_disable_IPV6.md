---
title: "Jaunty: How to disable IPV6?"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by milasch on 2009-05-18
OK, someone may say I'm the 1000th person to ask this but i haven't found the answer anywhere. Actually I've found the same solution in different places but it doesn't work at all here.

I tried setting /proc/sys/net/ipv6/conf/all/disable_ipv6 to 1, then booting. But as soon as I login, it's back to 0 and "ip a" shows inet6 there.

I also tried adding ipv6.disable=1 to my kernel boot line in /boot/menu/grub.lst, but I get "unknown option ipv6.disable ignoring".

The only way I succeeded was recompiling the kernel with no ipv6 support, but then I can't manage to install broadcom sta drivers, so I gave up on that.

I'm having serious package drops with ipv6 enabled. When I tried opensuse 11.1, I disabled ipv6 and got virtually no package drop. And I tested it thoroughly, so I'm almost certain it's something to do with IPV6 before someone asks.

This url addresses the problem:
[http://patchwork.ozlabs.org/patch/24127/]("http://patchwork.ozlabs.org/patch/24127/")

But I have no idea of how to apply this patch... And if it results in recompiling the kernel, no thanks.

I tried to recompile the kernel removing the option ipv6 and was successful. But then I couldn't compile my Broadcom sta drivers.

Can anyone point me to the right direction?

---

### Post by Brandon Williams on 2009-05-18
I don't know whether changing that kernel parameter actually makes a difference, because I don't have any IPv6 problems, so I can't test for improvement when this parameter is changed.

However, if you want it to be set on boot, then add this line to /etc/sysctl.conf:
```
net.ipv6.conf.all.disable_ipv6=1
```

---

### Post by binbash on 2009-05-19
I totally re-write my ipv6 blog post today and it disables ipv6 now : 

[http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html)

---

### Post by brendanpiater on 2009-06-09
"net.ipv6.conf.all.disable_ipv6=1"

This did not work for me, IPv6 was still enabled on reboot.

# CORRECTION
This DID work. Running "cat /proc/sys/net/ipv6/conf/all/disable_ipv6" give = 1 which apparently means DISABLED.

---

### Post by Brandon Williams on 2009-06-09
As I noted in my previous post, this shows that the sysctl setting was successfully changed, but it doesn't show that IPv6 was disabled. You will have to test whatever it was that made you decide that you had to disable IPv6 in order to determine whether that behavior has gone away.

---

