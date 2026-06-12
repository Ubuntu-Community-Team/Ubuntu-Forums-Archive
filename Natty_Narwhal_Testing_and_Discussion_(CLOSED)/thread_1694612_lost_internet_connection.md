---
title: "lost internet connection"
date: 2011-02-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-02-24
after last safe updates lost my internet connection. have linux on a separate hard drive. can even open spm. everything fine on my windows7 hard drive.

---

### Post by Harry33 on 2011-02-24
> **rburkartjo said:**
> after last safe updates lost my internet connection. have linux on a separate hard drive. can even open spm. everything fine on my windows7 hard drive.

Yes I just opened a thread on this issue.
Here:
[http://ubuntuforums.org/showthread.php?t=1694601](http://ubuntuforums.org/showthread.php?t=1694601)

---

### Post by rebootme on 2011-02-24
Note the workaround I posted in the thread.

---

### Post by rburkartjo on 2011-02-24
kind of lost i also tried going back to the old natty kernels i had saved but still no internet

question ref this link
[https://launchpad.net/ubuntu/+source/isc-dhcp/4.1.1-P1-15ubuntu5/+buildjob/2285144](https://launchpad.net/ubuntu/+source/isc-dhcp/4.1.1-P1-15ubuntu5/+buildjob/2285144)

if i downloaded the all of the following to my flash drive then installed then when booted into my ubuntu hard drive would it fix my lost internet

Built files

Files resulting from this build:

    * dhcp3-client_4.1.1-P1-15ubuntu5_all.deb (5.4 KiB)
    * dhcp3-common_4.1.1-P1-15ubuntu5_all.deb (5.0 KiB)
    * dhcp3-dev_4.1.1-P1-15ubuntu5_all.deb (5.0 KiB)
    * dhcp3-relay_4.1.1-P1-15ubuntu5_all.deb (5.5 KiB)
    * dhcp3-server_4.1.1-P1-15ubuntu5_all.deb (5.8 KiB)
    * isc-dhcp-client-dbg_4.1.1-P1-15ubuntu5_i386.deb (639.3 KiB)
    * isc-dhcp-client-udeb_4.1.1-P1-15ubuntu5_i386.udeb (225.1 KiB)
    * isc-dhcp-client_4.1.1-P1-15ubuntu5_i386.deb (259.1 KiB)
    * isc-dhcp-common_4.1.1-P1-15ubuntu5_i386.deb (311.8 KiB)
    * isc-dhcp-dev_4.1.1-P1-15ubuntu5_i386.deb (678.3 KiB)
    * isc-dhcp-relay-dbg_4.1.1-P1-15ubuntu5_i386.deb (586.1 KiB)
    * isc-dhcp-relay_4.1.1-P1-15ubuntu5_i386.deb (203.6 KiB)
    * isc-dhcp-server-dbg_4.1.1-P1-15ubuntu5_i386.deb (853.6 KiB)
    * isc-dhcp-server-ldap_4.1.1-P1-15ubuntu5_i386.deb (350.2 KiB)
    * isc-dhcp-server_4.1.1-P1-15ubuntu5_i386.deb (392.2 KiB)

tks

---

### Post by tjeremiah on 2011-02-25
Same happened to me. I rebooted and ran recovery mode, fixed broken packages, rebooted again and my Internet is back.

---

### Post by Harry33 on 2011-02-25
> **rburkartjo said:**
> kind of lost i also tried going back to the old natty kernels i had saved but still no internet

question ref this link
[https://launchpad.net/ubuntu/+source/isc-dhcp/4.1.1-P1-15ubuntu5/+buildjob/2285144](https://launchpad.net/ubuntu/+source/isc-dhcp/4.1.1-P1-15ubuntu5/+buildjob/2285144)

if i downloaded the all of the following to my flash drive then installed then when booted into my ubuntu hard drive would it fix my lost internet

Built files

Files resulting from this build:

    * dhcp3-client_4.1.1-P1-15ubuntu5_all.deb (5.4 KiB)
    * dhcp3-common_4.1.1-P1-15ubuntu5_all.deb (5.0 KiB)
    * dhcp3-dev_4.1.1-P1-15ubuntu5_all.deb (5.0 KiB)
    * dhcp3-relay_4.1.1-P1-15ubuntu5_all.deb (5.5 KiB)
    * dhcp3-server_4.1.1-P1-15ubuntu5_all.deb (5.8 KiB)
    * isc-dhcp-client-dbg_4.1.1-P1-15ubuntu5_i386.deb (639.3 KiB)
    * isc-dhcp-client-udeb_4.1.1-P1-15ubuntu5_i386.udeb (225.1 KiB)
    * isc-dhcp-client_4.1.1-P1-15ubuntu5_i386.deb (259.1 KiB)
    * isc-dhcp-common_4.1.1-P1-15ubuntu5_i386.deb (311.8 KiB)
    * isc-dhcp-dev_4.1.1-P1-15ubuntu5_i386.deb (678.3 KiB)
    * isc-dhcp-relay-dbg_4.1.1-P1-15ubuntu5_i386.deb (586.1 KiB)
    * isc-dhcp-relay_4.1.1-P1-15ubuntu5_i386.deb (203.6 KiB)
    * isc-dhcp-server-dbg_4.1.1-P1-15ubuntu5_i386.deb (853.6 KiB)
    * isc-dhcp-server-ldap_4.1.1-P1-15ubuntu5_i386.deb (350.2 KiB)
    * isc-dhcp-server_4.1.1-P1-15ubuntu5_i386.deb (392.2 KiB)

tks

Kernel change does not change this bug at all.

No do not install all of those packages, only these:
- isc-dhcp-client
- isc-dhcp-common

---

### Post by rburkartjo on 2011-02-25
harry and reboot tks got it fixed. will appreciate it

---

### Post by Harry33 on 2011-02-25
> **rburkartjo said:**
> harry and reboot tks got it fixed. will appreciate it

You are wellcome. :)

---

