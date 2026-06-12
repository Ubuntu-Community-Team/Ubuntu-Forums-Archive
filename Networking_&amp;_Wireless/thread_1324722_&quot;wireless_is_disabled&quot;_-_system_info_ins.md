---
title: "&quot;wireless is disabled&quot; - system info inside"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by astembridge on 2009-11-12
Laptop: Dell Studio 1735
uname: 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

A few months ago I upgraded from 8.04 to 8.10 - after the update my wireless stopped working.  A few weeks ago I upgraded from 8.10 to 9.04, and then to 9.10.    Neither upgrade resolved the wireless problem.

When I click on the network link on my toolbar, my wireless device (Broadcom BCM 4312) is grayed out with "wireless is disabled".  

So, rather than mess with ndiswrapper I bought a Zonet ZEW2500p usb wireless adapter.   Installed tonight, and Ubuntu immediately recognized the device.    Unfortunately - it too says "wireless is disabled"

~$ iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

~$ sudo lsmod|grep wl
```
wl                   1272936  0 
lib80211                6432  2 lib80211_crypt_tkip,wl
```

~$ sudo modprobe -l|grep wl
```
kernel/drivers/gpio/twl4030-gpio.ko
kernel/drivers/net/wireless/wl3501_cs.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/mwl8k.ko
kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
kernel/drivers/net/wireless/wl12xx/wl12xx.ko
kernel/drivers/usb/otg/twl4030-usb.ko
kernel/drivers/input/misc/twl4030-pwrbutton.ko
kernel/drivers/rtc/rtc-twl4030.ko
kernel/drivers/watchdog/twl4030_wdt.ko
kernel/drivers/staging/wlan-ng/prism2_usb.ko
kernel/drivers/uwb/wlp/wlp.ko
kernel/drivers/uwb/i1480/i1480u-wlp/i1480u-wlp.ko
kernel/sound/soc/codecs/snd-soc-twl4030.ko
kernel/net/netfilter/ipvs/ip_vs_wlc.ko
updates/dkms/wl.ko

```

I added 'wl' to /etc/modules and rebooted - still no luck.

Can anyone help?

---

