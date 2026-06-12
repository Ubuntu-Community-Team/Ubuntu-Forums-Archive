---
title: "Can't get wireless to work"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by viniciuscarvalho on 2010-03-30
Hello there! I'm XBMC Live 9.10 which is built on top of ubuntu 9.10.

I have a desktop PC with an realtek wifi card. The card is working, as I tested it on windows.

I tried to follow this guide [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) but could not connect to my WIFI network.

Here's some info:

lspci:
```
01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```

ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:24:8c:c1:10:fb  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:8cff:fec1:10fb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40513 (40.5 KB)  TX bytes:20042 (20.0 KB)
          Interrupt:27 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:600 (600.0 B)  TX bytes:600 (600.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:06:4f:6a:b4:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-06-4F-6A-B4-20-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

iwconfig:
```

xbmc@XBMCLive:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"ROUTERM"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid   ROUTERM
wireless-key     ########
wireless-channel 8
wireless-mode    managed


```

Well, I can't find why my wifi is not working. it seems that my card is configured (from the iwconfig command) but it can not connect to my Router.

The router is using basic WEP key.

Any ideas?

I did not try switching of security of the router, but I really would not like to.

Regards

---

### Post by chili555 on 2010-03-30
Is Network Manager installed in XMBC? It wants to control your network and is difficult to overcome. How many characters are in your WEP key? Ten or 26?

---

### Post by viniciuscarvalho on 2010-03-30
My wep is 10 chars.

XBMC does not uses Gnome. It does not have networkmanager installed. I guess I could install it, but I'm just affraid to mess things up (since it is configured to run on other display manager)

Regards

---

### Post by chili555 on 2010-03-30
I wasn't suggesting that you install it; I was just trying to see if we had to fight and overcome it.

You computer will not be happy with two IP addresses, at least not without some serious fiddling under the hood. Please detach the ethernet cable and do:```
sudo ifdown eth0
sudo dhclient wlan0
```The 'auto' declaration in /etc/network/interfaces tells the system you want to start *both* interfaces automatically on boot. Once we troubleshoot the wireless, let's clean up interfaces.

Post the outcome and we'll see what happens.

---

### Post by viniciuscarvalho on 2010-04-10
Thanks for the help. Removing the WEP from the access point I was able to connect. I know filter the clients by MAC address. WEP is really break that I don't bother not having it on.

Regards

---

