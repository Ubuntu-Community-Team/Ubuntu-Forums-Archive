---
title: "Wifi on Acer Aspire One very limited after 11.10 upgrade"
date: 2011-12-19
forum: Networking &amp; Wireless
---

### Post by Viman on 2011-12-19
Hello all,

I've installed Natty on an Acer Aspire One with an Intel Wireless card for a while now with no major problems. It's my parents' computer, so I'm not around very often to fix/tweak it.

Trouble came, however, as I updated to Oneiric and the Wifi started to stutter. The system is able to detect the card, no ndiswrapper or proprietary drivers necessary, and some connection can indeed be established (load a few websites VERY slowly). The procedure is usually the following:

-Boot;
-Connect Automatically to my wifi router;
-Open Firefox, 1st tab loads at fair speed;
-Anything else beyond this cannot be loaded anymore.

I've seen "fixes" or workarounds for similar problems to this (regarding Acer machines or) in which the power management for wlan0 was disabled through this command:

```
sudo iwconfig wlan0 power off
```

Which turned out to be fruitless. Any thoughts on what could fix this?

Additional info:

lsmod | grep wla
```
iwlagn                273944  0 
mac80211              272785  1 iwlagn
cfg80211              172392  2 iwlagn,mac80211

```

lspci | grep -i net
```
01:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000

```

dmesg | grep -i wlan
```
[   54.778068] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  147.325002] wlan0: authenticate with 1c:af:f7:56:db:84 (try 1)
[  147.327336] wlan0: authenticated
[  147.341490] wlan0: associate with 1c:af:f7:56:db:84 (try 1)
[  147.346413] wlan0: RX AssocResp from 1c:af:f7:56:db:84 (capab=0x431 status=0 aid=1)
[  147.346426] wlan0: associated
[  147.361300] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  158.336110] wlan0: no IPv6 routers present
[ 1857.329795] wlan0: deauthenticated from 1c:af:f7:56:db:84 (Reason: 3)
[ 1857.936111] wlan0: authenticate with 1c:af:f7:56:db:84 (try 1)
[ 1857.938502] wlan0: authenticated
[ 1857.939400] wlan0: associate with 1c:af:f7:56:db:84 (try 1)
[ 1857.943065] wlan0: RX ReassocResp from 1c:af:f7:56:db:84 (capab=0x431 status=0 aid=1)
[ 1857.943078] wlan0: associated

```

Thanks in advance

---

### Post by praseodym on 2011-12-19
Hi,

there is a bug with the N-mode of the driver iwlagn. It needs to be deactivated in kernel 3:

```
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
```
You may need to change the channel if using the 5 GHz region

---

### Post by Viman on 2011-12-20
Hey thanks, praseodym. The patch worked.
I have one more question, though. Will it remain in the next boot or should I create a script to autostart it?
Also, I ran `lsmod | grep wla` and it prints the same message still (iwlagn                273944  0)
Does it mean that the module is still broken?
Thanks!

---

### Post by praseodym on 2011-12-20
No, the 1st command created a permanent config file:

> cat /etc/modprobe.d/iwlagn.conf

---

### Post by Viman on 2011-12-20
Thank you so much man!

---

