---
title: "Intel 3945ABG on Mini 9 Hardy"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by kakotako on 2009-12-23
This [post]("http://www.ubuntumini.com/2009/09/replacing-wireless-card.html") suggested that Intel 3945ABG would work with Dell Mini 9 in Ubuntu. I installed on my Mini 9 (Hardy) it and it's having a slight problem.

sudo ifconfig does not show the wireless interface. lspci sees the card:

```
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

I read at one or two places that I may need to install linux-backports-modules-hardy-generic but for the life of me I can't seem to add the correct repository. I combined the default repository with the Dell modded repository and I am getting "not found" errors when I run apt-get update.

```
deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted

# 
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
```

---

### Post by chili555 on 2009-12-23
Let's see if the appropriate module, *iwl3945*, is loading at all. Please post:```
lsmod | grep iwl
dmesg | grep iwl
```Thanks.

---

### Post by kakotako on 2009-12-23
I put the Broadcom card that came with Mini 9 back in so I can have the wireless again. Just in case that doesn't matter, lsmod and dmesg don't return anything on "iwl." Is that the Intel driver?

Should I install the Intel card and try lsmod and dmesg again?

---

### Post by chili555 on 2009-12-23
> lsmod and dmesg don't return anything on "iwl." Is that the Intel driver?Yes.> Should I install the Intel card and try lsmod and dmesg again? If you want to try the Intel card and driver, sure. dmesg will tell us messages thrown up (no pun intended!) by the kernel and we are especially interested in what is happening ...or not... with the iwl3945 module.

---

### Post by kakotako on 2009-12-24
Thank you for your guidance. I am new to Linux, still going through Windoze detox and trying to grasp new concepts. 

I got the card to work. The module didn't load automatically as I thought it would. I had to put an iwl3945 line in /etc/modules.

For some reason I could not blacklist the Dell Mini 9 wl driver:
```

lsmod | grep wl
wl                   1487188  0 
```

and I wonder if it could be responsible for the dismal radio performance of this card but I will start another thread on this subject.

---

