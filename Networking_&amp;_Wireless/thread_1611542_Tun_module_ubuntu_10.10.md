---
title: "Tun module ubuntu 10.10"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by spitfirekdv on 2010-11-02
Hello all,

How is it possible to enable tun module in Ubuntu 10.10?

# lsmod | grep tun
# modprobe tun
# lsmod | grep tun
#
And nothing happens.

# dmesg | grep tun
[    0.290009] tun: Universal TUN/TAP device driver, 1.6
[    0.290013] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[   26.319589] tun0: Disabled Privacy Extensions

Should I recompile kernel for this?

---

### Post by calarndt on 2011-03-25
bump!

---

### Post by ShyLion on 2011-04-06
Same problem.

---

### Post by ShyLion on 2011-04-06
modprobe ipip
modprobe ip_gre

now someone, please, tell me how to make it running over reboot?

---

### Post by treii28 on 2011-12-06
as I understand it, tun is in the kernel

---

