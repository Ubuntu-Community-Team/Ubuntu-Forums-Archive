---
title: "Alternatives to the realtime kernel?"
date: 2007-12-16
forum: Multimedia Production
---

### Post by holotone on 2007-12-16
So I've dabbled a bit with Ubuntu Studio this time around, though mostly for the realtime kernel support in audio production. Unfortunately, I've found the experience to be buggy, especially with regards to wireless networking (network-manager seems to just get stuck on in a disconnected state on a network, requiring reboot) and with getting Virtualization up and running (VirtualBox won't install due to kernel issues).

What are my alternatives to running the realtime kernel? I was able to enable realtime when running JACK / Ardour as root on a non-rt system, but that obviously creates its own concerns.

Thanks!

---

### Post by nalmeth on 2007-12-17
I don't think the lowlatency-kernel is around anymore, and it didn't improve latency for me at all anyway. The virtualbox problem has bitten me before, but I don't run any virtual machines while recording/working.

About Network Manager, have you tried just killing it and restarting it? Or restarting networking manually? /etc/init.d/networking restart

Short of compiling your own kernel, I think your choices are limited. Try to solve the problems you're having, or try another distro

---

