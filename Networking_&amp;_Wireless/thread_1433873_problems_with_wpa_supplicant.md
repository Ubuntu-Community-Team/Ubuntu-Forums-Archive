---
title: "problems with wpa_supplicant"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by zythar on 2010-03-19
though method of editing /etc/network/interfaces worked for [me]("http://ubuntuforums.org/showthread.php?t=1431345") i have decided to get gui work.

i have installed wicd, i set wep key for connecting to my network. when i'm scanning wicd find my network. but i get error "couldn't obtain ip address". when i dived into logs i found that there is some problem with wpa_supplicant. here is piece of log:
```

2010/03/19 21:45:58 :: Connecting to wireless network MY_ESSID
2010/03/19 21:45:59 :: /sbin/dhclient -r eth0
2010/03/19 21:45:59 :: ifconfig eth0 0.0.0.0 
2010/03/19 21:45:59 :: /sbin/ip route flush dev eth0
2010/03/19 21:45:59 :: ifconfig eth0 down
2010/03/19 21:45:59 :: ifconfig eth0 up
2010/03/19 21:45:59 :: Putting interface down
2010/03/19 21:45:59 :: ifconfig eth1 down
2010/03/19 21:45:59 :: Releasing DHCP leases...
2010/03/19 21:45:59 :: /sbin/dhclient -r eth1
2010/03/19 21:45:59 :: iwconfig eth1
2010/03/19 21:45:59 :: Setting false IP...
2010/03/19 21:45:59 :: ifconfig eth1 0.0.0.0 
2010/03/19 21:45:59 :: Stopping wpa_supplicant
2010/03/19 21:45:59 :: wpa_cli -i eth1 terminate
2010/03/19 21:45:59 :: Flushing the routing table...
2010/03/19 21:45:59 :: /sbin/ip route flush dev eth1
2010/03/19 21:45:59 :: iwconfig eth1 mode managed
2010/03/19 21:45:59 :: Putting interface up...
2010/03/19 21:45:59 :: ifconfig eth1 up
2010/03/19 21:45:59 :: enctype is wep-hex
2010/03/19 21:45:59 :: Attempting to authenticate...
2010/03/19 21:45:59 :: ['wpa_supplicant', '-B', '-i', 'eth1', '-c', '/var/lib/wicd/configurations/001b2f0c95a2', '-D', 'wext']
2010/03/19 21:45:59 :: ['iwconfig', 'eth1', 'essid', 'MY_ESSID']
2010/03/19 21:45:59 :: iwconfig eth1 channel 11
2010/03/19 21:45:59 :: iwconfig eth1 ap 00:1B:2F:0C:95:A2
2010/03/19 21:45:59 :: WPA_CLI RESULT IS DISCONNECTED
2010/03/19 21:46:00 :: WPA_CLI RESULT IS ASSOCIATING
2010/03/19 21:46:01 :: iwconfig eth1
2010/03/19 21:46:01 :: WPA_CLI RESULT IS ASSOCIATING
2010/03/19 21:46:02 :: WPA_CLI RESULT IS ASSOCIATING
2010/03/19 21:46:03 :: iwconfig eth1
2010/03/19 21:46:03 :: WPA_CLI RESULT IS ASSOCIATING
2010/03/19 21:46:04 :: WPA_CLI RESULT IS DISCONNECTED
2010/03/19 21:46:05 :: WPA_CLI RESULT IS SCANNING
2010/03/19 21:46:05 :: iwconfig eth1
2010/03/19 21:46:06 :: WPA_CLI RESULT IS SCANNING
2010/03/19 21:46:07 :: WPA_CLI RESULT IS SCANNING
2010/03/19 21:46:08 :: iwconfig eth1
2010/03/19 21:46:08 :: WPA_CLI RESULT IS SCANNING
2010/03/19 21:46:09 :: WPA_CLI RESULT IS ASSOCIATING
2010/03/19 21:46:10 :: WPA_CLI RESULT IS ASSOCIATING
2010/03/19 21:46:10 :: iwconfig eth1
2010/03/19 21:46:11 :: WPA_CLI RESULT IS ASSOCIATING
2010/03/19 21:46:12 :: WPA_CLI RESULT IS ASSOCIATING
2010/03/19 21:46:13 :: iwconfig eth1
2010/03/19 21:46:13 :: WPA_CLI RESULT IS ASSOCIATING
2010/03/19 21:46:14 :: WPA_CLI RESULT IS SCANNING
2010/03/19 21:46:15 :: iwconfig eth1
2010/03/19 21:46:15 :: WPA_CLI RESULT IS SCANNING
2010/03/19 21:46:16 :: WPA_CLI RESULT IS SCANNING
2010/03/19 21:46:17 :: WPA_CLI RESULT IS SCANNING
2010/03/19 21:46:17 :: iwconfig eth1
2010/03/19 21:46:18 :: WPA_CLI RESULT IS SCANNING
2010/03/19 21:46:19 :: WPA_CLI RESULT IS ASSOCIATING
2010/03/19 21:46:20 :: iwconfig eth1
2010/03/19 21:46:20 :: WPA_CLI RESULT IS ASSOCIATING
2010/03/19 21:46:21 :: WPA_CLI RESULT IS ASSOCIATING
2010/03/19 21:46:22 :: WPA_CLI RESULT IS ASSOCIATING
2010/03/19 21:46:22 :: iwconfig eth1
2010/03/19 21:46:23 :: WPA_CLI RESULT IS ASSOCIATING
2010/03/19 21:46:24 :: WPA_CLI RESULT IS SCANNING
2010/03/19 21:46:24 :: iwconfig eth1
2010/03/19 21:46:25 :: WPA_CLI RESULT IS SCANNING
2010/03/19 21:46:26 :: WPA_CLI RESULT IS SCANNING
2010/03/19 21:46:27 :: iwconfig eth1
2010/03/19 21:46:27 :: WPA_CLI RESULT IS SCANNING
2010/03/19 21:46:28 :: WPA_CLI RESULT IS SCANNING
2010/03/19 21:46:29 :: iwconfig eth1
2010/03/19 21:46:29 :: WPA_CLI RESULT IS ASSOCIATING
2010/03/19 21:46:30 :: WPA_CLI RESULT IS ASSOCIATING
2010/03/19 21:46:31 :: iwconfig eth1
2010/03/19 21:46:31 :: WPA_CLI RESULT IS ASSOCIATING
2010/03/19 21:46:32 :: WPA_CLI RESULT IS ASSOCIATING
2010/03/19 21:46:33 :: WPA_CLI RESULT IS ASSOCIATING
2010/03/19 21:46:34 :: iwconfig eth1
2010/03/19 21:46:34 :: wpa_supplicant authentication may have failed.
2010/03/19 21:46:34 :: Running DHCP
2010/03/19 21:46:34 :: /sbin/dhclient eth1
2010/03/19 21:46:34 :: Internet Systems Consortium DHCP Client V3.1.2
2010/03/19 21:46:34 :: Copyright 2004-2008 Internet Systems Consortium.
2010/03/19 21:46:34 :: All rights reserved.
2010/03/19 21:46:34 :: For info, please visit http://www.isc.org/sw/dhcp/
2010/03/19 21:46:34 :: 
2010/03/19 21:46:36 :: Listening on LPF/eth1/00:02:2d:36:57:84
2010/03/19 21:46:36 :: Sending on   LPF/eth1/00:02:2d:36:57:84
2010/03/19 21:46:36 :: Sending on   Socket/fallback
2010/03/19 21:46:36 :: iwconfig eth1
2010/03/19 21:46:38 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
2010/03/19 21:46:38 :: iwconfig eth1
2010/03/19 21:46:41 :: iwconfig eth1
2010/03/19 21:46:42 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
2010/03/19 21:46:43 :: iwconfig eth1
2010/03/19 21:46:45 :: iwconfig eth1
2010/03/19 21:46:47 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
2010/03/19 21:46:48 :: iwconfig eth1
2010/03/19 21:46:50 :: iwconfig eth1
2010/03/19 21:46:53 :: iwconfig eth1
2010/03/19 21:46:55 :: iwconfig eth1
2010/03/19 21:46:57 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
2010/03/19 21:46:57 :: iwconfig eth1
2010/03/19 21:47:00 :: iwconfig eth1
2010/03/19 21:47:02 :: iwconfig eth1
2010/03/19 21:47:05 :: iwconfig eth1
2010/03/19 21:47:07 :: iwconfig eth1
2010/03/19 21:47:09 :: iwconfig eth1
2010/03/19 21:47:11 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
2010/03/19 21:47:12 :: iwconfig eth1
2010/03/19 21:47:14 :: iwconfig eth1
2010/03/19 21:47:17 :: iwconfig eth1
2010/03/19 21:47:19 :: iwconfig eth1
2010/03/19 21:47:21 :: iwconfig eth1
2010/03/19 21:47:24 :: iwconfig eth1
2010/03/19 21:47:26 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
2010/03/19 21:47:26 :: iwconfig eth1
2010/03/19 21:47:29 :: iwconfig eth1
2010/03/19 21:47:31 :: iwconfig eth1
2010/03/19 21:47:33 :: iwconfig eth1
2010/03/19 21:47:36 :: iwconfig eth1
2010/03/19 21:47:37 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
2010/03/19 21:47:38 :: iwconfig eth1
2010/03/19 21:47:39 :: No DHCPOFFERS received.
2010/03/19 21:47:39 :: No working leases in persistent database - sleeping.
2010/03/19 21:47:41 :: iwconfig eth1
2010/03/19 21:47:43 :: iwconfig eth1
2010/03/19 21:47:45 :: iwconfig eth1
2010/03/19 21:47:48 :: iwconfig eth1
2010/03/19 21:47:48 :: DHCP connection failed
2010/03/19 21:47:48 :: exiting connection thread
2010/03/19 21:47:48 :: Sending connection attempt result dhcp_failed

```here is my configuration for that network:
```

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant
network={
       ssid="MY_ESSID"
       scan_ssid=0
       key_mgmt=NONE
       wep_key0=1a2345b6c7
       wep_tx_keyidx=0
       priority=5
}

```where is the problem?

ps second question:
assume that in /etc/network/interfaces i have this configuration:
```

iface eth1 inet dhcp
wireless-essid MY_ESSID
wireless-key    1234abcd12

```
what is doing ifup eth1? i mean what sequence of commands?

pps i have no "hermes" driver support in wpa_supplicant. maybe there is the problem?

---

### Post by 2hot6ft2 on 2010-03-19
Might take a look at this thread it helped me.
[HowTo: WPA with wpa_supplicant]("http://ubuntuforums.org/showthread.php?t=263136")

---

### Post by 2hot6ft2 on 2010-03-19
I tried the suggestion by chili555 to get WPA working in the thread here
[HowTo: WPA with wpa_supplicant]("http://ubuntuforums.org/showthread.php?t=263136")

Which made it possible to connect by WiFi without using network manager which I disabled in System > Preferences > Startup Applications

I now have WPA working and can connect without network manager.

Here's what I did.

Made the key using
```
wpa_passphrase your_ssid your_psk
```
Added it to /etc/wpa_supplicant.conf
following the instructions and changing TKIP to AES so I had this
```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
	ssid="myapidhere"
        scan_ssid=1
        proto=WPA RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP AES
        group=CCMP AES 
	psk=reallylongstringoflettersandnumbershere
}

```
This works for wlan and I could connect without network manager with WPA2 AES
Here's /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto wlan3
iface wlan3 inet dhcp
wireless-essid myapidhere
pre-up wpa_supplicant -Bw -Dwext -iwlan3 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

When I tried running this from the [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)
```
sudo wpa_supplicant -iwlan3 -c/etc/wpa_supplicant.conf -Dwext -w
```
It gave me
wpa_supplicant: invalid option -- 'w'
so I removed the -w option and got
> $ sudo wpa_supplicant -iwlan3 -c/etc/wpa_supplicant.conf -Dwext
Line 9: invalid cipher 'AES'.
Line 9: failed to parse pairwise 'CCMP AES'.
Line 10: invalid cipher 'AES'.
Line 10: failed to parse group 'CCMP AES'.
Line 12: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
So I removed the lines
>         pairwise=CCMP AES
        group=CCMP AES
from /etc/wpa_supplicant.conf
and now running
```
sudo wpa_supplicant -iwlan3 -c/etc/wpa_supplicant.conf -Dwext
```
It tries to associate with my AP which since I'm already connected to it it fails but it tells me it's working.

And to summarize, it still works with WPA 2 Personal AES using:
In /etc/wpa_supplicant.conf
```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
	ssid="myapidhere"
        scan_ssid=1
        proto=WPA RSN
        key_mgmt=WPA-PSK
	psk=reallylongstringoflettersandnumbershere
}

```
This works for wlan
Here's /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto wlan3
iface wlan3 inet dhcp
wireless-essid myapidhere
pre-up wpa_supplicant -Bw -Dwext -iwlan3 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

Wherever I have wlan3 you would change it to your wifi connection as reported by
```
ifconfig
```

---

### Post by 2hot6ft2 on 2010-03-19
When I look at your post I see "i set **wep key** for connecting to my network".
"problem with **wpa_supplicant**"
```
       **key_mgmt=NONE**
       **wep_key**0=1a2345b6c7

```
and
what is doing ifup eth1? Means "**I**nter**F**ace **UP** eth1", starts the interface eth1.

I'm not surprised it's confused. So am I. You have to choose is it WEP or WPA. It can't be both.:confused::-k

---

### Post by zythar on 2010-03-19
thanks for answers.
yeah, i had it that way but not working (*.
also, when i was asking about ifup eth1, i meaned something else.
> ps second question:
assume that in /etc/network/interfaces i have this configuration:
```

iface eth1 inet dhcp
wireless-essid MY_ESSID
wireless-key    1234abcd12 

```what is doing ifup eth1? i mean what sequence of commands?


you can read it this way: when i write "ifup eth1" (assuming all that stuff above is in /etc/network/interfaces) what commands are called?

---

### Post by 2hot6ft2 on 2010-03-19
> **zythar said:**
> thanks for answers.
yeah, i had it that way but not working (*.
also, when i was asking about ifup eth1, i meaned something else.


you can read it this way: when i write "ifup eth1" (assuming all that stuff above is in /etc/network/interfaces) what commands are called?
The ifup will bring the interface up if it's down, and as far as I know that is all. I think what you want is
```
sudo /etc/init.d/networking restart
```
so it restarts the interface and reads the interfaces file to configure it/them.

---

### Post by zythar on 2010-03-20
and again it was an answer not on my question (*
i just think that i cant build my question correctly. ok, let's forget about that.

now, i have
```

iface eth1 inet dhcp
    wireless-essid MY_ESSID
    wireless-key   1A2345B6C7 #WEP key (64 bit)

```

when i am doing "ifup eth" it's alright, and i have got working wireless connection.
when i'm using wpa_supplicant (and also wicd, which is the same, i think. i mean algorithm of connection to the access point), i cant connect to my ap.

config files are given above. log file of  wicd also.

---

### Post by zythar on 2010-03-21
bump

---

### Post by zythar on 2010-03-21
bump

---

