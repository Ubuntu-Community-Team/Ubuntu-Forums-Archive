---
title: "Asus USB-N13 hostapd disconnect loop"
date: 2013-05-08
forum: Networking &amp; Wireless
---

### Post by 8Kuula on 2013-05-08
Im trying to make AP to my Ubuntu 12.04 64bit server box (3.2.0-41-generic) with Asus USB-N13.
Problem is that it apears that it connects OK, but then for some reason it disconnects. My tablet and phone doing same thing.
Authenticating... -> getting IP address... -> connected -> about 3sec it apears working -> disconnect -> Autheinticating... -> ...

So question is, what im doing wrong? :\

I have 'apt-get install linux-backports-modules-cw-3.8-precise-generic' package, but do not help, maybe not driver issue then?


```
# lsusb
Bus 001 Device 002: ID 0b05:17ab ASUSTek Computer, Inc. 
```
```
# cat hostapd.conf
interface=wlan0
driver=nl80211
uapsd_advertisement_enabled=1
wme_enabled=1
ieee80211n=1
ht_capab=[HT40+][SHORT-GI-40][DSSS_CCK-40]
hw_mode=g
channel=2
auth_algs=1
country_code=FI

ssid=WLAN
ignore_broadcast_ssid=0

wpa=2
wpa_passphrase=password
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
```
```
# iwconfig
wlan0     IEEE 802.11bgn  Mode:Master  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          
mon.wlan0  IEEE 802.11bgn  Mode:Monitor  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
```
```
# cat /etc/default/isc-dhcp-server
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/isc-dhcp-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1".
#INTERFACES=""
INTERFACES="eth0 wlan0"
```

Syslog output:
```
May  8 19:49:10 gatekeeper hostapd: wlan0: STA 08:60:6e:3c:f1:93 IEEE 802.11: authenticated
May  8 19:49:10 gatekeeper hostapd: wlan0: STA 08:60:6e:3c:f1:93 IEEE 802.11: associated (aid 1)
May  8 19:49:10 gatekeeper hostapd: wlan0: STA 08:60:6e:3c:f1:93 RADIUS: starting accounting session 518A815B-00000012
May  8 19:49:10 gatekeeper hostapd: wlan0: STA 08:60:6e:3c:f1:93 WPA: pairwise key handshake completed (RSN)
May  8 19:49:11 gatekeeper dhcpd: DHCPREQUEST for 192.168.1.102 from 08:60:6e:3c:f1:93 (android-5492696d7be78a6f) via wlan0
May  8 19:49:11 gatekeeper dhcpd: DHCPACK on 192.168.1.102 to 08:60:6e:3c:f1:93 (android-5492696d7be78a6f) via wlan0
May  8 19:49:11 gatekeeper dhcpd: DHCPREQUEST for 192.168.1.102 from 08:60:6e:3c:f1:93 (android-5492696d7be78a6f) via wlan0
May  8 19:49:11 gatekeeper dhcpd: DHCPACK on 192.168.1.102 to 08:60:6e:3c:f1:93 (android-5492696d7be78a6f) via wlan0
May  8 19:49:19 gatekeeper hostapd: wlan0: STA 08:60:6e:3c:f1:93 IEEE 802.11: authenticated
May  8 19:49:19 gatekeeper hostapd: wlan0: STA 08:60:6e:3c:f1:93 IEEE 802.11: associated (aid 1)
May  8 19:49:19 gatekeeper hostapd: wlan0: STA 08:60:6e:3c:f1:93 RADIUS: starting accounting session 518A815B-00000013
May  8 19:49:19 gatekeeper hostapd: wlan0: STA 08:60:6e:3c:f1:93 WPA: pairwise key handshake completed (RSN)
May  8 19:49:19 gatekeeper dhcpd: DHCPREQUEST for 192.168.1.102 from 08:60:6e:3c:f1:93 (android-5492696d7be78a6f) via wlan0
May  8 19:49:19 gatekeeper dhcpd: DHCPACK on 192.168.1.102 to 08:60:6e:3c:f1:93 (android-5492696d7be78a6f) via wlan0
May  8 19:49:19 gatekeeper dhcpd: DHCPREQUEST for 192.168.1.102 from 08:60:6e:3c:f1:93 (android-5492696d7be78a6f) via wlan0
May  8 19:49:19 gatekeeper dhcpd: DHCPACK on 192.168.1.102 to 08:60:6e:3c:f1:93 (android-5492696d7be78a6f) via wlan0

```

---

### Post by meldroc on 2013-05-10
The Asus USB-N13 drivers in the most recent kernel are broken. The only way I've been able to work around this is to downgrade to an older kernel.

---

### Post by flash63 on 2013-05-11
Hello,
switch off the power management first, before you start hostapd

```
wlan0     IEEE 802.11bgn  Mode:Master  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          [COLOR=#ff0000]Power Management:on[/COLOR]
```

---

### Post by 8Kuula on 2013-05-11
> **flash63 said:**
> Hello,
switch off the power management first, before you start hostapd

```
wlan0     IEEE 802.11bgn  Mode:Master  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          [COLOR=#ff0000]Power Management:on[/COLOR]
```

```
# iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
```
I do it wrong?

---

### Post by 8Kuula on 2013-05-11
> **meldroc said:**
> The Asus USB-N13 drivers in the most recent kernel are broken. The only way I've been able to work around this is to downgrade to an older kernel.
And I bet there won't be any kernel update that would fix it until next LTS (using LTS versions only), if even then...

---

### Post by 8Kuula on 2013-05-12
Tested with linux-image-generic-lts-raring package (Version: 3.8.0.19.18).
Same loop continues...

---

### Post by flash63 on 2013-05-12
> **8Kuula said:**
> ```
# iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
```
I do it wrong?


try alternative
```
sudo iw dev wlan0 set power_save off 
```

but take a look at [http://wireless.kernel.org/en/users/Drivers](http://wireless.kernel.org/en/users/Drivers) 

rtl8192cu basically may not work with hostapd

---

### Post by 8Kuula on 2013-05-12
> **flash63 said:**
> try alternative
```
sudo iw dev wlan0 set power_save off 
```

```
sudo iw dev wlan0 set power_save off
command failed: Operation not supported (-95)
```

Looks like hostapd or rtl8192cu actualy do not play ball with asus usb-n13.
[http://home.comcast.net/~tomhorsley/hardware/rtl8192cu/rtl8192cu.html](http://home.comcast.net/~tomhorsley/hardware/rtl8192cu/rtl8192cu.html) tl;dr: Solution there were to get new dogle that works.

---

