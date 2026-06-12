---
title: "hostapd + nl80211 + RTL8188RU/RTL8192CU"
date: 2012-11-29
forum: Networking &amp; Wireless
---

### Post by mehta_4v on 2012-11-29
Hi all,

    I am having ALFA AWUS036NHR Wireless USB adapter which has RTL8188RU chipset. I am using the compat-wireless v3.4 driver rtl8192cu. It works fine and when I plug in my adapter I can see the interface in iwconfig. Now I run hostapd with the following conf file:

```
***********************************
             hostapd.conf
***********************************
interface=wlan15
driver=nl80211
ssid=rtwap
channel=6
wpa=1
wpa_passphrase=87654321
device_name=RTL8188RU
hw_mode=g
wpa_key_mgmt=WPA-PSK
wpa_pairwise=CCMP

```

But when I run the following command:

```
# ./hostapd hostapd.conf -B
```

I get the following output and the interface is up but doesn't get any SSID.
```

root@10.99.14.100:/bin/wifi# iwconfig
lo        no wirnet eth0: DaVinci EMAC: ioctl not supported
eless extensions.

eth0      no wireless extensions.

Warning: Driver for device wlan15 has been compiled with version 22
of Wireless Extension, while this program supports up to version 21.
Some things may be broken...

wlan15    IEEE 802.11bgn  Mode:Master  Frequency:2.437 GHz  Tx-Power=20 dBm
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on

mon.wlan15  IEEE 802.11bgn  Mode:Monitor  Frequency:2.437 GHz  Tx-Power=20 dBm
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
```

No SSID to the interface. Its not that it isn't being broadcasted but its not getting connected event as hidden network.


Additional outputs that may help figure out something:
```

root@10.99.14.100:/home/compat_wireless# iwconfig
lo        no wirnet eth0: DaVinci EMAC: ioctl not supported
eless extensions.

eth0      no wireless extensions.

Warning: Driver for device wlan15 has been compiled with version 22
of Wireless Extension, while this program supports up to version 21.
Some things may be broken...

wlan15    IEEE 802.11bgn  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:on
``` 

Also the output of the hostapd command with -dd is following:

```
root@10.99.14.100:/bin/wifi# ./hostapd_nl minimalistic.conf -B
Configuration file: minimalistic.conf
rfkill: Cannot open RFKILL control device
rtl8192cu: MAC auto ON okay!
rtl8192cu: Tx queue select: 0x05
Using interface wlan15 with hwaddr 00:c0:ca:6a:e4:2e and ssid 'rtwap'
random: Cannot read from /dev/random: Resource temporarily unavailable
random: Only 0/20 bytes of strong random data available from /dev/random
random: Not enough entropy pool available for secure operations
WPA: Not enough entropy in random pool for secure operations - update keys later when the first station connects

```

Also the 
```
uname -r
2.6.38
```

---

### Post by mehta_4v on 2012-11-29
Just moving the message up the stack..

---

