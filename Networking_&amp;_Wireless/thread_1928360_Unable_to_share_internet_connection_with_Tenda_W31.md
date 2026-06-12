---
title: "Unable to share internet connection with Tenda W311M"
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by skywriter on 2012-02-20
I have read my W311M dongle supports WAP by using hostapd:
[https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M](https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M)

I have loaded module rt2800usb by applying this script:
```
#!/bin/sh
modprobe rt2800usb
echo 148F 5370 > /sys/bus/usb/drivers/rt2800usb/new_id
```After that I get wlan0 interface:
$ iwconfig 
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  Mode:Master  Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```Then I have compiled (0.7.3) it and tried to run according to this manual:
[http://linuxwireless.org/en/users/Documentation/hostapd](http://linuxwireless.org/en/users/Documentation/hostapd)

I stuck into this error:

```
$ sudo ./hostapd ~/hostapd-minimal.conf 
Configuration file: /home/user/hostapd-minimal.conf
Could not set interface mon.wlan0 flags: No such file or directory
nl80211: Failed to set interface wlan0 into AP mode
nl80211 driver initialization failed.
ELOOP: remaining socket: sock=4 eloop_data=0xb670d0 user_data=0xb67790
handler=0x42b750
ELOOP: remaining socket: sock=6 eloop_data=0xb69cb0 user_data=(nil)
handler=0x434460
```The content of hostapd-minimal.conf is:
```
#change wlan0 to your wireless device
interface=wlan0
driver=nl80211
ssid=test
channel=1
```Ubuntu 10.04 kernel 3.0.0-15-generic #26~lucid1-Ubuntu SMP Wed Jan 25 15:37:10 UTC 2012 x86_64 GNU/Linux
With kernels 2.6.x I was unable to setup driver rt2800usb: it doesn't create network interface wlan0.

---

### Post by skywriter on 2012-02-22
It looks like magic but I got some progress after google-translating some [chinesse discussion]("http://forum.ubuntu.org.cn/viewtopic.php?t=338643").
I have downloaded ['rt2870.bin']("http://www.ralinktech.com/en/04_support/license.php?sn=5030") and put it in '/lib/firmware'.

Now I got some progress... hostapd starts now!

---

### Post by skywriter on 2012-02-22
Stuck again... According to [manual]("http://linuxwireless.org/en/users/Documentation/hostapd") I have applied the following config for hostapd:

```
interface=wlan0
driver=nl80211
bridge=br0
ssid=localbridge
hw_mode=g
channel=1
#macaddr_acl=0
#auth_algs=1
#ignore_broadcast_ssid=0
wpa=3
wpa_passphrase=1024x768
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
```

But my Galaxy doesn't connect. Attached the log of hostapd.

---

