---
title: "Engenius eub9703 usb"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by phoenixpb on 2010-11-16
i have bought an engenius eub-9703 wireless usb adaptater
it does not want to work in ubuntu
internet pages don't load
it works very well in virtualbox indeed (windows xp)
so i suppose it is recognised by system (view as a ralink)

it seems that is a dhcp problem i think

any idea ??

p.s. ubuntu 10.04 LTS

---

### Post by uncaspi on 2010-11-16
Open a terminal and please post the content of sudo lsusb
sudo ifconfig   and sudo iwconfig

Thanks.

---

### Post by phoenixpb on 2010-11-17
made :)

phoenix@phoenix-desktop:~$ sudo lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 003: ID 046d:c525 Logitech, Inc. 
Bus 003 Device 002: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 05ac:1209 Apple, Inc. iPod Video
Bus 001 Device 005: ID 1740:9703 Senao 
Bus 001 Device 003: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

eth0      Link encap:Ethernet  HWaddr 00:11:d8:73:9d:92  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fe73:9d92/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11506 (11.5 KB)  TX bytes:25494 (25.4 KB)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:02:6f:8a:ae:13  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:6fff:fe8a:ae13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:906 (906.0 B)  TX bytes:5076 (5.0 KB)

phoenix@phoenix-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"motel rose"  
          Mode:Managed  Frequency:2.412 GHz  Access Point:
00:0F:3D:AB:F2:27   
          Bit Rate=48 Mb/s   Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:1234-5678-91
          Power Management:on
          Link Quality=70/70  Signal level=30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by uncaspi on 2010-11-17
It's not a dhcp problem cause wlan0 got an valid ip from the router. If it's a laptop try sudo rfkill unblock wifi or rfkill unblock

and please post the output of sudo rfkill list 

If it's a laptop you may also have a switch on the keyboard to turn your wifi on.

---

### Post by phoenixpb on 2010-11-17
it's not a laptop
i have entered manually the ip adress (copied from windows) because dhcp don't work

thanks

---

### Post by phoenixpb on 2010-11-17
phoenix@phoenix-desktop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=127 time=3.31 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=127 time=2.98 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=127 time=3.44 ms
^C
--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 2.987/3.247/3.445/0.197 ms
phoenix@phoenix-desktop:~$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (72.14.204.147) 56(84) bytes of data.
64 bytes from iad04s01-in-f147.1e100.net (72.14.204.147): icmp_seq=1 ttl=55 time=28.7 ms
64 bytes from iad04s01-in-f147.1e100.net (72.14.204.147): icmp_seq=2 ttl=55 time=28.9 ms
64 bytes from iad04s01-in-f147.1e100.net (72.14.204.147): icmp_seq=3 ttl=55 time=29.1 ms
^C64 bytes from iad04s01-in-f147.1e100.net (72.14.204.147): icmp_seq=4 ttl=55 time=27.8 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 12140ms
rtt min/avg/max/mdev = 27.835/28.680/29.159/0.533 ms

strange i can ping the router i can ping www external sites
but pages don't load neither in firefox neither in chrome

thanks :)

---

### Post by chili555 on 2010-11-17
Why do you have two different IP addresses from two different gateways?> eth0 Link encap:Ethernet HWaddr 00:11:d8:73:9d:92
inet addr:[COLOR="Red"]192.168.1.2[/COLOR] Bcast:192.168.1.255 Mask:255.255.255.0


wlan0 Link encap:Ethernet HWaddr 00:02:6f:8a:ae:13
inet addr:[COLOR="Red"]192.168.0.101[/COLOR] Bcast:192.168.0.255 Mask:255.255.255.0

---

### Post by phoenixpb on 2010-11-17
one is from adsl eth0
the other is from wireless adaptater wlan0

---

### Post by chili555 on 2010-11-17
No kidding?

Do you wonder why your computer might be confused about which interface to use; which is coming and going? Is this some kind of connection sharing or an accident?

Unless you do some serious manual fiddling in your /etc files to set up one interface for WAN and another for LAN, it's not supposed to work this way.

Which interface are the pings coming from? How do you know which interface is the trouble?

---

### Post by phoenixpb on 2010-11-17
i can turn off adsl modem anyway adsl don't work
so i know pings come from wireless
just to make sudo route add default gw 192.168.0.1 dev wlan0
anyway

in virtualbox all work perfectly i access the site in a windows xp running in oracle wm connected by wireless
there is no reason this not work in ubuntu

Thanks guys

---

### Post by chili555 on 2010-11-17
Please detach the ADSL cable and do:```
sudo ifconfig eth0 down
iwconfig wlan0 
ping -c3 www.google.com
```Thanks.

---

### Post by chili555 on 2010-11-17
Please also let us see:```
lsmod | grep rt2
```Thanks.

---

### Post by phoenixpb on 2010-11-17
phoenix@phoenix-desktop:~$ iwconfig wlan0 
wlan0     IEEE 802.11bgn  ESSID:"motel rose"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0F:3D:AB:F2:27   
          Bit Rate=6 Mb/s   Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

phoenix@phoenix-desktop:~$ ping -c3 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (72.14.204.103) 56(84) bytes of data.
64 bytes from iad04s01-in-f103.1e100.net (72.14.204.103): icmp_seq=1 ttl=55 time=30.7 ms
64 bytes from iad04s01-in-f103.1e100.net (72.14.204.103): icmp_seq=2 ttl=55 time=37.6 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 6051ms
rtt min/avg/max/mdev = 30.773/34.207/37.641/3.434 ms

---

### Post by chili555 on 2010-11-17
Ouch! Let's see the lsmod, also, please.

---

### Post by phoenixpb on 2010-11-17
phoenix@phoenix-desktop:~$ lsmod | grep rt2
rt2870sta             461811  0 
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              205402  2 rt2x00usb,rt2x00lib
cfg80211              126528  2 rt2x00lib,mac80211
crc_ccitt               1339  2 rt2800usb,irda

thanks :)

---

### Post by chili555 on 2010-11-17
Man! That is a lot of modules fighting over your poor little Engenious! Let's kick a few out and see if we can improve:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four new lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800lib
```Proofread carefully, save and close gedit. Reboot and tell us about your wireless.

---

### Post by phoenixpb on 2010-11-17
yes it works thanks a lot man :)

---

### Post by Tekkboi on 2011-05-28
> **phoenixpb said:**
> yes it works thanks a lot man :)
 
This also works with the Engenius 9706  usb adapter as well!
Was having to boot narwhal with the old kernel to get wireless and tried everything till I saw this post.
 
Thanks chili555!

---

