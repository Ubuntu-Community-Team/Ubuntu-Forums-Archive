---
title: "I changed motherboard and networking no longer works [Marvel Yukon 8056]"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by plonka2000 on 2008-12-16
Hi all,

I have a problem that I cant find a solution to.
I have just upgraded the motherboard in my server running Ubuntu 8.04 x64 from a Gigabyte GA-945P-S3 rev3.3 to a GA-965P-DS3P rev2.0.

All seems fine apart from my network card in that the onboard Marvell 8056 does not work or is not enabled for some reason.

I'm stuck on how to enable it.

Could someone please assist me with enabling it?

I'm pretty sure it should have drivers for it already.

Thanks all.

---

### Post by plonka2000 on 2008-12-16
Anyone?

---

### Post by plonka2000 on 2008-12-17
Bump

---

### Post by Catsworth on 2008-12-17
I had a similar problem with a Marvell Yukon ethernet adaptor, managed to get it working for a while using the drivers from here:

[http://www.marvell.com/drivers/driverDisplay.do?driverId=204](http://www.marvell.com/drivers/driverDisplay.do?driverId=204)

Problem is that I got it to connect to one LAN (my home one), but now it won't accept either manual or DHCP'd addresses from any other LAN (most annoying).

Give it a whirl, your mileage may vary (and by the sounds of it you have little to use ;) ).

Let me know how you get on, I'd be interested to know - thanks.

---

### Post by xmagixx on 2008-12-17
you could try see if ubuntu havent allrdy found it but it's turned off
try
sudo ifconfig
look on what devices that are up. probely your old one is up
then try
sudo ifconfig -a
this will show all network cards that your machine has found 
and if you found something new 
sudo ifconfig eth9 up
and away you go

---

### Post by plonka2000 on 2008-12-17
Thanks guys,

I will ty that and have get back here when I get home.

I appreciate your advice.

Cheers.

---

### Post by plonka2000 on 2008-12-17
> **xmagixx said:**
> you could try see if ubuntu havent allrdy found it but it's turned off
try
sudo ifconfig
look on what devices that are up. probely your old one is up
then try
sudo ifconfig -a
this will show all network cards that your machine has found 
and if you found something new 
sudo ifconfig eth9 up
and away you go

Further to this, can I ask how or where do I specify to always bring this interface up at boot?

Thanks again.

---

### Post by plonka2000 on 2008-12-17
> **Catsworth said:**
> I had a similar problem with a Marvell Yukon ethernet adaptor, managed to get it working for a while using the drivers from here:

[http://www.marvell.com/drivers/driverDisplay.do?driverId=204](http://www.marvell.com/drivers/driverDisplay.do?driverId=204)

Problem is that I got it to connect to one LAN (my home one), but now it won't accept either manual or DHCP'd addresses from any other LAN (most annoying).

Give it a whirl, your mileage may vary (and by the sounds of it you have little to use ;) ).

Let me know how you get on, I'd be interested to know - thanks.

I downloaded the Marvell driver from the Marvell site yesterday, but I was unsure of the install process. Do I need to compile the code from source or is there an included script for installing into ubuntu x64 server?

Did you get any issues installing?

Thanks.

---

### Post by plonka2000 on 2008-12-17
> **Catsworth said:**
> I had a similar problem with a Marvell Yukon ethernet adaptor, managed to get it working for a while using the drivers from here:

[http://www.marvell.com/drivers/driverDisplay.do?driverId=204](http://www.marvell.com/drivers/driverDisplay.do?driverId=204)

Problem is that I got it to connect to one LAN (my home one), but now it won't accept either manual or DHCP'd addresses from any other LAN (most annoying).

Give it a whirl, your mileage may vary (and by the sounds of it you have little to use ;) ).

Let me know how you get on, I'd be interested to know - thanks.

I downloaded the Marvell driver from the Marvell site yesterday, but I was unsure of the install process. Do I need to compile the code from source or is there an included script for installing into ubuntu x64 server?

Did you get any issues installing?

Thanks.

---

### Post by plonka2000 on 2008-12-18
> **xmagixx said:**
> you could try see if ubuntu havent allrdy found it but it's turned off
try
sudo ifconfig
look on what devices that are up. probely your old one is up
then try
sudo ifconfig -a
this will show all network cards that your machine has found 
and if you found something new 
sudo ifconfig eth9 up
and away you go

Thanks mate, this worked a charm.
My new card showed up as eth1 and I was able to enable it and configure it to come up at boot.

Thanks guys for your advice.

:)

---

### Post by plonka2000 on 2008-12-20
Hi all,

I'm having a strange problem with my networking on my server which I seem unable to solve.
Thanks for helping me getting my networking going again, but the only problem is now I seem unable to run apt-get or ping anything outside my network.

I noticed the problem when I tried to run 'apt-get update' and got this output:
```
root@soundwave:~# apt-get update
Err http://gb.archive.ubuntu.com hardy Release.gpg
  Could not resolve âgb.archive.ubuntu.comâ
Err http://gb.archive.ubuntu.com hardy/main Translation-en_GB
  Could not resolve âgb.archive.ubuntu.comâ
Err http://gb.archive.ubuntu.com hardy/restricted Translation-en_GB
  Could not resolve âgb.archive.ubuntu.comâ
Err http://gb.archive.ubuntu.com hardy/universe Translation-en_GB
  Could not resolve âgb.archive.ubuntu.comâ
Err http://gb.archive.ubuntu.com hardy/multiverse Translation-en_GB
  Could not resolve âgb.archive.ubuntu.comâ
Err http://gb.archive.ubuntu.com hardy-updates Release.gpg
  Could not resolve âgb.archive.ubuntu.comâ
Err http://gb.archive.ubuntu.com hardy-updates/main Translation-en_GB
  Could not resolve âgb.archive.ubuntu.comâ
Err http://gb.archive.ubuntu.com hardy-updates/restricted Translation-en_GB
  Could not resolve âgb.archive.ubuntu.comâ
Err http://gb.archive.ubuntu.com hardy-updates/universe Translation-en_GB
  Could not resolve âgb.archive.ubuntu.comâ
Err http://gb.archive.ubuntu.com hardy-updates/multiverse Translation-en_GB
  Could not resolve âgb.archive.ubuntu.comâ
Err http://security.ubuntu.com hardy-security Release.gpg
  Could not resolve âsecurity.ubuntu.comâ
Err http://security.ubuntu.com hardy-security/main Translation-en_GB
  Could not resolve âsecurity.ubuntu.comâ
Err http://security.ubuntu.com hardy-security/restricted Translation-en_GB
  Could not resolve âsecurity.ubuntu.comâ
Err http://security.ubuntu.com hardy-security/universe Translation-en_GB
  Could not resolve âsecurity.ubuntu.comâ
Err http://security.ubuntu.com hardy-security/multiverse Translation-en_GB
  Could not resolve âsecurity.ubuntu.comâ
Err http://download.webmin.com sarge Release.gpg
  Could not resolve âdownload.webmin.comâ
Err http://download.webmin.com sarge/contrib Translation-en_GB
  Could not resolve âdownload.webmin.comâ
Reading package lists... Done
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not resolve âgb.archive.ubuntu.comâ

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_GB.bz2  Could not resolve âgb.archive.ubuntu.comâ

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_GB.bz2  Could not resolve âgb.archive.ubuntu.comâ

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_GB.bz2  Could not resolve âgb.archive.ubuntu.comâ

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_GB.bz2  Could not resolve âgb.archive.ubuntu.comâ

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Could not resolve âgb.archive.ubuntu.comâ

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_GB.bz2  Could not resolve âgb.archive.ubuntu.comâ

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_GB.bz2  Could not resolve âgb.archive.ubuntu.comâ

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_GB.bz2  Could not resolve âgb.archive.ubuntu.comâ

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_GB.bz2  Could not resolve âgb.archive.ubuntu.comâ

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not resolve âsecurity.ubuntu.comâ

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_GB.bz2  Could not resolve âsecurity.ubuntu.comâ

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_GB.bz2  Could not resolve âsecurity.ubuntu.comâ

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_GB.bz2  Could not resolve âsecurity.ubuntu.comâ

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_GB.bz2  Could not resolve âsecurity.ubuntu.comâ

W: Failed to fetch http://download.webmin.com/download/repository/dists/sarge/Release.gpg  Could not resolve âdownload.webmin.comâ

W: Failed to fetch http://download.webmin.com/download/repository/dists/sarge/contrib/i18n/Translation-en_GB.bz2  Could not resolve âdownload.webmin.comâ

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
```

Here are some of my outputs, can someone please assist me?

```
#
# deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release amd64 (20080423.2)]/ hardy main restricted

#deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release amd64 (20080423.2)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

# ADDED FOR WEBMIN UPDATES!!!
deb http://download.webmin.com/download/repository sarge contrib

```

My /et/resolv.conf
```
nameserver 87.194.0.66
nameserver 87.194.0.67
search localdomain workgroup
```

My /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth1
iface lo inet loopback

# The primary network interface

iface eth1 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0

```

```
root@soundwave:~# ping www.google.com
ping: unknown host www.google.com
```

```
root@soundwave:~# ping 72.14.205.100
connect: Network is unreachable
```

Help... anyone?

---

