---
title: "IVP6 can't be disabled in Jaunty?"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by Wtwine on 2009-06-26
HI

I have recently installed Jaunty on my machine and find Firefox really slow.  Firefox typically downloads at 5Kbps or less (!), although bandwidth speed test shows that I can easily download at speeds ten times that. 

I have optimized Firefox in about:config as recommended in some threads. I have also tried disabling ivp6 every way possible (disabling alias, blacklist alias, disable ivp6 in Firefox=TRUE etc etc), but it seems ivp6 cannot be disabled in Jaunty because it is in the kernel.

Has anybody found a way around this??

Thanks

---

### Post by wirelessmonkey on 2009-06-26
IPv6 is compiled into the kernel in Jaunty, unfortunately it is not a modulized. The only way to remove it is to compile a custom kernel.

---

### Post by External on 2009-06-26
This is a Jaunty bug that has been reported already on launchpad. ([https://launchpad.net/bugs/313218](https://launchpad.net/bugs/313218))

However building a custom kernel just because of this would be unnecessary. If you use Firefox, you can easily disable ipv6 by following a few simple steps. Here's how:

Enter this in the FFox address line:
**about:config**

Then find the line "**network.dns.disableipv6**"

Set the value to **"true"**

Restart Firefox.

---

### Post by Brandon Williams on 2009-06-26
IPv6 should only have an impact on hostname lookup time and connection initialization time. Once a connection is established via IPv4, the presence of IPv6 support in the kernel should have no impact on the throughput of the connection. If this realy is a throughput issue (not just a connection initialization problem), then I doubt that disabling IPv6 will improve the situation. You're better off trying to figure out why the TCP send/receive windows aren't growing.

---

### Post by vaikz on 2009-06-26
hi, why dont you try adding ¨ipv6.disable=1¨ on the grub menu.lst and add it at the end of the kernel. I&#7743; no export on linux but it works for me. I was able to read it on one of the forums but I forgot the link.

---

### Post by superprash2003 on 2009-06-27
[http://ubuntuforums.org/showthread.php?t=1191972](http://ubuntuforums.org/showthread.php?t=1191972)

---

### Post by mnoyes on 2009-07-18
Had the same problem in Firefox on Jaunty on my Dell Mini 9, switched to Open DNS and to Wicd, but the problem did not go away. Now trying the "network.dns.disableipv6 = true" solution. Will report back.

Update: my son was on pbskids.org for several hours, the connection didn't drop out. Looks like it worked. This is the kind of problem that should not exist, though, isn't it? I'm willing to go through the steps to figure out the problem and try several solutions, but most regular users would not be...

---

### Post by Crafty Kisses on 2009-07-18
> **wirelessmonkey said:**
> IPv6 is compiled into the kernel in Jaunty, unfortunately it is not a modulized. The only way to remove it is to compile a custom kernel.

I actually compiled a custom kernel. It's fairly easy.

---

