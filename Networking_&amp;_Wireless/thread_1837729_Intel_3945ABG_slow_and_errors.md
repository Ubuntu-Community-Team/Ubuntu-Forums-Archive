---
title: "Intel 3945ABG slow and errors"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by chili555 on 2011-09-02
My Intel 3945ABG wireless card, using the module iwl3945, has been slow, difficult to get connected and has thrown many errors in /var/log/syslog:> Sep  1 20:12:06 LAPTOP60 kernel: [   12.630221] iwl3945 0000:03:00.0: Error setting Tx power (-5).
Sep  1 20:12:09 LAPTOP60 kernel: [   27.593167] iwl3945 0000:03:00.0: Error setting Tx power (-5).
Sep  1 20:12:09 LAPTOP60 kernel: [   27.707736] iwl3945 0000:03:00.0: Error setting Tx power (-5).
Sep  1 20:13:23 LAPTOP60 kernel: [  102.195550] iwl3945 0000:03:00.0: Error setting Tx power (-5).
Sep  1 20:13:23 LAPTOP60 kernel: [  102.295669] iwl3945 0000:03:00.0: Error setting Tx power (-5).
Sep  1 20:13:37 LAPTOP60 kernel: [  116.167503] iwl3945 0000:03:00.0: Error setting Tx power (-5).After some Googling, I decided to install the compat-wireless package in backports. I opened Synaptic Package Manager and installed *linux-backports-modules-cw-2.6.39-natty-generic*. After a reboot, the errors are gone and connectivity is much improved.

If you decide to install this package, be sure it matches your version. In my case, I needed Natty.

---

### Post by kiprit on 2011-09-09
Thanks for sharing this information...

I was suffering from very low connection speed due to weak reception of signal and wireless kept getting disconnected even 10 meters away from the modem. When i googled the outcome of "dmesg | grep iwl", i.e.  "Error setting Tx power (-5)" i found your post. All my problems are solved after applying your solution. So thanks again for sharing it, and sharing without having someone asking for help.

---

### Post by chili555 on 2011-09-16
> **kiprit said:**
> Thanks for sharing this information...

I was suffering from very low connection speed due to weak reception of signal and wireless kept getting disconnected even 10 meters away from the modem. When i googled the outcome of "dmesg | grep iwl", i.e.  "Error setting Tx power (-5)" i found your post. All my problems are solved after applying your solution. So thanks again for sharing it, and sharing without having someone asking for help.That's exactly the purpose. I hope others with similar issues will find and implement the fix with the help of Google or the search function on this forum.

Glad it's working!

---

### Post by rainboww on 2011-10-26
Thanks a lot for your tip :P

---

### Post by andylinux on 2011-11-24
Most likely caused by this bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265)

You can read the bug report for more details.  Many people report upgrading to the latest 3.0 kernel (Ubuntu 11.10) along with creating this file,
/etc/modprobe.d/iwl3945.conf
and put this into it.
options iwl3945 disable_hw_scan=0

Rather then upgrading to the latest version of Ubuntu I did the following and that also worked,
On my Ubunt 11.04 machine, I installed
linux-backports-modules-cw-3.0.0-natty-generic

which gave me the new wireless modules without having to update to the latest Linux 3.0 kernel.

I also had to setup the "disable_hw_scan=0" as described in #370.
creaate this file,

/etc/modprobe.d/iwl3945.conf

and put this into it.
options iwl3945 disable_hw_scan=0

To compare your hardware to the ones listed in the bug report you can use the following commands,

Here are my system details,
lspci -vnn |grep -A3 Wireless
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
 Subsystem: Intel Corporation Device [8086:1020]
 Flags: bus master, fast devsel, latency 0, IRQ 47
 Memory at f6cff000 (32-bit, non-prefetchable) [size=4K]

uname -a
Linux d630 2.6.38-12-generic #51-Ubuntu SMP Wed Sep 28 14:25:20 UTC 2011 i686 i686 i386 GNU/Linux

lsb_release -rd
Description: Ubuntu 11.04
Release: 11.04

---

### Post by juky on 2011-12-30
> **andylinux said:**
> Most likely caused by this bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265)

You can read the bug report for more details.  Many people report upgrading to the latest 3.0 kernel (Ubuntu 11.10) along with creating this file,
/etc/modprobe.d/iwl3945.conf
and put this into it.
options iwl3945 disable_hw_scan=0

Rather then upgrading to the latest version of Ubuntu I did the following and that also worked,
On my Ubunt 11.04 machine, I installed
linux-backports-modules-cw-3.0.0-natty-generic

which gave me the new wireless modules without having to update to the latest Linux 3.0 kernel.

I also had to setup the "disable_hw_scan=0" as described in #370.
creaate this file,

/etc/modprobe.d/iwl3945.conf

and put this into it.
options iwl3945 disable_hw_scan=0

To compare your hardware to the ones listed in the bug report you can use the following commands,

Here are my system details,
lspci -vnn |grep -A3 Wireless
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
 Subsystem: Intel Corporation Device [8086:1020]
 Flags: bus master, fast devsel, latency 0, IRQ 47
 Memory at f6cff000 (32-bit, non-prefetchable) [size=4K]

uname -a
Linux d630 2.6.38-12-generic #51-Ubuntu SMP Wed Sep 28 14:25:20 UTC 2011 i686 i686 i386 GNU/Linux

lsb_release -rd
Description: Ubuntu 11.04
Release: 11.04

```
/etc/modprobe.d/iwl3945.conf
```
and put this into it.
```
options iwl3945 disable_hw_scan=0
```

This helped me. After saving the file,  also do **as root**:

```
modprobe -r iwl3945
modprobe iwl3945
```

Cheers!

---

### Post by CurJam on 2012-03-29
This solves the problem. Many thanks!

---

### Post by ickefes on 2012-05-10
Thank you for this as it solves my speed issues. But how come this does not get fixed? It is the same thing in Precise. Regards.

---

### Post by timmson on 2012-06-01
Big thx! Its work for me!

---

