---
title: "Network interface not detected"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by rbrugman on 2006-06-01
Hello,
After upgrading from Breezy to Dapper my wired network interface isn't listed in ifconfig anymore.  It's a 3Com server nic and worked fine under breezy.  It's set up with a static IP, but since the device is not detected, it doesn't work.

---

### Post by rbrugman on 2006-06-01
Just for shits I booted with Kernel 2.6.12 (K7) and networking worked fine.  It's just the latest kernel that doesn't work for me.

---

### Post by wobin on 2006-06-01
[QUOTE=rbrugman]Just for shits I booted with Kernel 2.6.12 (K7) and networking worked fine.  It's just the latest kernel that doesn't work for me.[/QUOTE]

Had the same with an Intel controller. Turns out the interface is on eth1 now instead of eth0. It's at eth0 first, and moves to eth1 immediately. Very weird.

[4294696.751000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[4294696.751000] e100: Copyright(c) 1999-2005 Intel Corporation
[4294696.751000] ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 20 (level, low) -> IRQ 201
[4294696.776000] e100: eth0: e100_probe: addr 0xed800000, irq 201, MAC addr 00:90:27:A7:28:95
[4294696.945000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 22 (level, low) -> IRQ 169
[4294697.499000] e100: eth1: e100_watchdog: link up, 100Mbps, full-duplex

---

### Post by rbrugman on 2006-06-02
Not the same problem as I'm having.  Mine works great under the previous kernel, but when booting with the latest it just doesn't show up at all in ifconfig.  Says no interface on eth0 or eth1.  It's a server though so I don't NEED the latest kernel.

---

### Post by ahhell2 on 2006-06-02
I'm wondering if I am experiencing the same thing.  Yesterday for no good reason, I decided to upgrade my router to dapper.  After numerous failed attempts (Dapper install barfed on my Nvida card), I decided to install from scratch.  Now, regardless of what I do I can not get DHCP3 to run (2 identical Intel NICs...eth0 and eth1).  It is always failing.
Is there an easy to roll back to an older kernel (as I am kind of a noob)?

---

### Post by TimJ on 2006-06-02
You may have a different problem but see this thread [http://www.ubuntuforums.org/showthread.php?t=184795](http://www.ubuntuforums.org/showthread.php?t=184795) If it sounds the same check post 23 which has a link to a solution for some of us.

---

