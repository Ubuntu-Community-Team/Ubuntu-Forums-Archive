---
title: "Connecting to wireless network (Ubuntu Server 12)"
date: 2012-05-12
forum: Networking &amp; Wireless
---

### Post by camilstaps on 2012-05-12
Hi guys,

I'm a linux newbie, trying to set up a server with a wireless connection. I'm using Ubuntu Server 12.

I installed the driver for my DELL1450 wireless stuff with ndiswrapper and it works. Actually, I worked with the wireless yesterday and it worked. After that, I took my laptop to another place, and there it didn't work! I did a whole lot of things to try to get it working. In the end, I needed to change the /etc/network/interfaces file with the new essid and key. Now, at home again, I changed that file to the right values, but I just can't get the wireless working.

Using the same hardware on windows, I do get internet and a lot of found networks.
On Ubuntu Server, it just can't connect. The Wireless LED is flashing, but no idea what that means?

Some files & outputs:

/etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
    address 192.168.0.1
    netmask 255.255.255.0

auto eth0
iface eth0 inet dhcp
    wpa-ssid MY_SSID
    wpa-psk MY_KEY
```

lo is localhost, for the server. eth1 is the ethernet interface that I'll use later on to route the internet to another computer. eth0 is the wireless interface.
I believe this file is as I used it at home before. SSID and KEY are 100% sure OK.

ifconfig eth0:
```
Link encap: Ethernet  HWaddr 00:15:00:15:ab:1e
inet6 addr: fe80::215:ff:fe15:ab1e/64 Scope:Link
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B)  TX bytes:4752 (4.7 KB)
Interrupt:21 Base address:0x6000 Memory:d0000000-d0000fff
```

iwconfig eth0:
```
IEEE 802.11bg  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"
Mode:Managed  Channel:0  Acces Point: Not-Associated
Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
Retry limit:7   RTS thr:off   Fragment thr:offf
Encryption key: off
Power Management:off
Link Quality:0 Signa level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

iwlist eth0 scan:
```
No scan results
```
Please note that on windows I found several networks, with the same hardware.

dhclient eth0:
just takes ages, after 5min no feedback is given

route -n:
```

destination Gateway Genmask       Flags Metric Ref Use Iface
192.168.0.0 0.0.0.0 255.255.255.0 U     0      0   0   eth1
```

When booting, it takes a very long time to configure the network. After a few minutes, linux boots without the correct configuration.

If any more information is needed, please ask! What commands should I use to connect to the network?

Any help appreciated!

---

