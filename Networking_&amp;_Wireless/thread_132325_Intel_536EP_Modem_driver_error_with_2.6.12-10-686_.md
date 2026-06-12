---
title: "Intel 536EP Modem driver error with 2.6.12-10-686 kernel"
date: 2006-02-18
forum: Networking &amp; Wireless
---

### Post by BrianFitzgerald on 2006-02-18
I have tried to install the modem driver Intel-536EP-4.71.tgz using the instructions in the Modem HOWTO, but with the appropriate changes for the -686 kernel that I am using.

However I get the following fatal error:-

root@advent:~# modprobe Intel536
FATAL: Error inserting Intel536 (/lib/modules/2.6.12-10-686/kernel/drivers/char/Intel536.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@advent:~# dmesg
.
.
.
.
[4295247.762000] Intel536: module license 'Proprietary' taints kernel.
[4295247.763000] Intel536: Unknown symbol pm_access
root@advent:~#

I had previously used Synaptic to install the linux-headers-2.6.12-10-686
and gcc-4.0.

What other package do I need to define this symbol?


P.S.
Fortunately, I also have a broadband router for my downloads and want this modem only for a voice / fax answering machine.

---

