---
title: "Beacon - Modification in Madwifi"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by hcwd on 2009-08-04
Hi guys

I need help with Madwifi in connection to Ubuntu...

Actually, I modified my Madwifi driver. After make, make install, modprobe I hoped, that my modification would be applied by ubuntu, but nothing happend. It looks like the original madwifi driver version without my modification...

So my thought is I maybe install my new driver in a wrong way.
Here my little script:
> 
modprobe -r ath_pci
rmmod wlan_scan_sta
rmmod ath_rate_sample
rmmod wlan
rmmod ath_hal

rm -r /lib/modules/2.6.28-14-generic/net

make clean
make
make reinstall
modprobe ath_pci

wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode adhoc

ifconfig ath0 down
iwconfig ath0 channel 10 essid Test
ifconfig ath0 up
Is this combination of commands correctly arranged to reinstall and reload the modified driver?

Greetz

---

