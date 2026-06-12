---
title: "any USB wireless card can work as AP under ubuntu?"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by say2sky on 2010-01-23
I know some wireless card can work in Master Mode but it seems use madwifi driver.

I know madwifi doesn't support usb dongles

I hope to find a usb wireless card which can work as AP under Ubuntu.

any one have suggestion?

Thanks a lot for help.

I have check this list 
[http://atheros.rapla.net/](http://atheros.rapla.net/)

I am not sure if ar9170usb.ko and its device support Master MOde.

---

### Post by darkod on 2010-01-24
I wasn't able to find a way for AP for my adapter but you could always try ad-hoc too. Just click on Network Manager icon and select Create Wireless network. It allows to set WPA2 password (at least on mine) and the connection is OK for short ranges (as you would expect from ad-hoc).
I know it's not the same as AP but sometimes it helps if nothing else works.

---

### Post by say2sky on 2010-01-24
thanks a lot for your input.

I am googling a lot and found some useful background info.

[https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode)
combine with 
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

Now I focus on usb wifi card with chipset
1. rt2x00 2. rt2870 3. ZD1211

if anybody have already tried these device, hope can heard the result.

---

### Post by say2sky on 2010-01-26
I have gotten my usb wireless card with ar9170usb chip
everything works OK.

```

$ lsusb
Bus 003 Device 002: ID 0cf3:1002 Atheros Communications, Inc. 

```

```

# ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:27:19:xx:xx:xx  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::227:19ff:feaa:dc0a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60529208 (60.5 MB)  TX bytes:3865826 (3.8 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-27-19-xx-xx-xx-61-61-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```



```

# netstat -i
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
lo        16436 0        12      0      0 0            12      0      0      0 LRU
wlan0      1500 0     44274      0      0 0         40852      0      0      0 BMRU
wmaster0      0 0         0      0      0 0             0      0      0      0 RU

```

I hope to know if this usb wifi card can be used as AP.

---

### Post by say2sky on 2010-01-26
I got this info when do setting.

```
# iwconfig wlan0 mode ad-hoc
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.

```

```
# iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

```

```
# /sbin/iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

br0       no wireless extensions.

nas0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0D:88:xx:xx:xx   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Who on 2010-01-26
> **say2sky said:**
> thanks a lot for your input.

I am googling a lot and found some useful background info.

[https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode)
combine with 
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

Now I focus on usb wifi card with chipset
1. rt2x00 2. rt2870 3. ZD1211

if anybody have already tried these device, hope can heard the result.


I tried one with rt2870(usb, of course) a couple of days ago and it definitely did not work 'trivially' - ie I set it to master mode but set failed. My understanding is the drivers don't support master mode yet.

---

### Post by say2sky on 2010-01-27
> **Who said:**
> I tried one with rt2870(usb, of course) a couple of days ago and it definitely did not work 'trivially' - ie I set it to master mode but set failed. My understanding is the drivers don't support master mode yet.

thanks a lot for your input.


so neither rt2870 nor  ar9170usb can work as AP.

it means no 802.11n usb lan adapter can at current time.

---

