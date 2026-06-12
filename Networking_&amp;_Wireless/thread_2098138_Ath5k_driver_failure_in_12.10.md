---
title: "Ath5k driver failure in 12.10"
date: 2012-12-25
forum: Networking &amp; Wireless
---

### Post by klugja on 2012-12-25
This appears to be a kernel bug.  Connections seem to hang. I am not sure which levels of Ubuntu this affects, but it happens to me in 12.10.  It is impossible to update the system, because it never finishes downloading the package lists.

From dmesg:

```
[   73.084718] ath5k: ath5k_hw_get_isr: ISR: 0x00000400 IMR: 0x00000000
[  802.024954] ath5k: ath5k_hw_get_isr: ISR: 0x00000080 IMR: 0x00000000
[ 1281.874667] ath5k: ath5k_hw_get_isr: ISR: 0x00000080 IMR: 0x00000000

```

I am going to try 12.04 next.  I had been using 12.04 on an older system with the same WIFI board, but I got a new system, and thought I would put in 12.10.

The Windows driver for this board works just fine, so hopefully 12.04 will work too.

I found this bug report, but I do not lose my wifi connection:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/983025]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/983025")


After installing Ubuntu 12.04, I get no driver messages in the kernel, but internet is very slow with ubuntu, even when bringing up my DSL modem's built-in web page.

---

### Post by klugja on 2012-12-26
I installed a Tenda W311Ma, and it works just great as Ralink RT5370 in Ubuntu 12.04. So the workaround was a new device.  Not sure if this qualifies as solved.

---

