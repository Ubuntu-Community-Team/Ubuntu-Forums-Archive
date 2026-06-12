---
title: "Internet connectivity issues after being connected to a network after time."
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by earthmeLon on 2010-08-02
Currently running 10.4x64 and I am having connectivity issues after being connected to a network for some time.

I am not sure if this happens with eth0 connections, but it happens on multiple wireless networks if I stay on them for a little while.

I believe the issue has to deal with something wrong with DNS.  Sustained connections (AIM/IRC) remain active and connected while new requests (ie: from firefox, re-opening aim client) have problems.

Problems stop whenever I disconnect and then re-connect to the router, but I'm having to do this every 1-20 minutes (very annoying).

I have tried both default (router given) DNS and OpenDNS, both of which are failing me.

Any suggestions or requests for more information will be greatly appreciated.

Thanks :D


Edit:
$dmesg | tail
```

[ 2855.927884] wlan0: direct probe to AP 00:14:xx:xx:xx:ee (try 2)
[ 2855.932406] wlan0: direct probe responded
[ 2855.932413] wlan0: authenticate with AP 00:14:xx:xx:xx:ee (try 1)
[ 2855.934810] wlan0: authenticated
[ 2855.934847] wlan0: associate with AP 00:14:xx:xx:xx:ee (try 1)
[ 2855.938580] wlan0: RX AssocResp from 00:14:xx:xx:xx:ee (capab=0x421 status=0 aid=4)
[ 2855.938586] wlan0: associated
[ 3364.969082] CE: hpet increasing min_delta_ns to 22500 nsec
[ 3364.969223] CE: hpet increasing min_delta_ns to 33750 nsec
[ 3700.192987] CE: hpet increasing min_delta_ns to 50624 nsec

```

This is dmesg just after I noticed the problem happening again.


Edit2:
lscpi shows that I have Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (rev 01), which was giving issues to other users.
Following and updating recommendation from [this post]("http://ubuntuforums.org/showthread.php?t=1442051"), I ran:
```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

Will post results

---

### Post by earthmeLon on 2010-08-02
It seems that
```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

Has fixed my issue.  I hope that this helps people in the future with this chipset.

Laptop: Vaio VPCF126FM

---

### Post by Strayfolk on 2010-08-20
Inspired by this, I tried installing linux-backports-modules-wireless-lucid-preempt.  I'm running Ubuntu Studio 10.04 64 bit on a Sony Vaio F12.  This fixed a lot of disconnects. It even fixed issues with Logitech wireless headset interference with wireless network/wifi.   BTW. To be able to connect to wireless networks in the first place, I uninstalled gnome-network-manager and installed wicd network manager! The gnome one didn't work, and the wicd one simply worked for whatever reason.  Don't have any logs or proof, but you can take my word for it!

---

### Post by z987k on 2010-10-22
I'm having a problem with this chipset on 10.10.
AR9287 wireless network adapter on an acer 5742G-7200.

Wireless is cutting(disconnecting) out every so many minutes and if I download large files or keep the computer up for a long period of time, it gets really bad - as in every 1 min or less.

I installed linux-backports-modules-wireless-maveric-generic and now uname -r yields 2.6.35-22-generic-pae.

dmesg | tail right after to drop:

```
[ 2503.438472] wlan0: authenticate with 22:1d:60:d3:a0:c3 (try 1)
[ 2503.635642] wlan0: authenticate with 22:1d:60:d3:a0:c3 (try 2)
[ 2503.835509] wlan0: authenticate with 22:1d:60:d3:a0:c3 (try 3)
[ 2504.035889] wlan0: authentication with 22:1d:60:d3:a0:c3 timed out

```

---

