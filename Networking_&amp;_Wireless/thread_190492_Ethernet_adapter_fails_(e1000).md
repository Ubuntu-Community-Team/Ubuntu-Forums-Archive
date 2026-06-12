---
title: "Ethernet adapter fails (e1000)"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by jdrugo on 2006-06-06
Hi, I've got an odd problem:

After having had my laptop motherboard replaced (Thinkpad R50p), the e1000 module doesn't seem to work anymore. The ethernet adapter (Intel 82540ep, PRO/1000 family) still works in windows, so it doesn't seem to be a hardware fault.

I'm getting the following error:
```
# ifconfig eth0 up 192.168.0.123
eth0: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
```

The hardware is recognised:
```
#lspci
[...]
0000:02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
[...]
```

The e1000 module is loaded:
```
# dmesg |grep eth
[4294688.968000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
# lsmod |grep e1000
e1000               118840    0
```

I'm using the standard ubuntu kernel:
```
#uname -srv
Linux 2.6.15-22-386 #1 PREEMPT Sun May 7 15:49:09 UTC 2006
```
I know that it's not the latest version, but it is a bit hard to update it without a network connection.

Any ideas what could be the problem?
Any help is much appreciated!

---

### Post by jdrugo on 2006-06-06
Hmm, after having posted the message I've found this thread: [http://ubuntuforums.org/showthread.php?t=189842](http://ubuntuforums.org/showthread.php?t=189842)

Seems like that they've also replaced the ethernet adapter as I have a different MAC address than before (and was then called eth1 rather than eth0). Updating /etc/iftab fixed the problem.

It strange that I couldn't find above thread when using the forum search function. Sorry for the noise.

---

