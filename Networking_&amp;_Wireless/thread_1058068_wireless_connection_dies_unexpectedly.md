---
title: "wireless connection dies unexpectedly"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by teethlikelions on 2009-02-02
I struggled for a couple of hours to get my Belkin Wireless G lus MIMO USB Network Adapter to work properly with my fresh install of Ubuntu 8.10 64-bit. with the help of this thread: [http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834"), I finally got connected. The problem, though, is that the connection dies after only a few minutes of connectivity.
When the connection dies, I am forced to restart using ```
sudo /etc/init.d/networking restart
```. The loss of connection does not seem to be a response to any particular type of activity on my part. It happens when copying a movie, running bittorrent (or not), running/using skype (or not), browsing on firefox (or not), and downloading (or not). I have experienced this with high network traffic loads and with nearly flatline traffic. I have this problem with DHCP as well as static IP resolution.
I am using a Buffalo WHR-G125 wireless router, though my iPod Touch is still connected, so I feel that the router is probably not the culprit.
Hopefully the error is in my config files, so here are some outputs:

/etc/network/interfaces:
```
auto lo
iface lo inet loopback

# auto eth0
#iface eth0 inet dhcp

auto wlan1
iface wlan1 inet static
address 192.168.11.100
gateway 192.168.11.1
#dns-nameservers 192.168.11.1
netmask 255.255.255.0
wpa-driver wext
wpa-ssid HwyW
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <omitted>

```

ifconfig:
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55129 (55.1 KB)  TX bytes:55129 (55.1 KB)

wlan1     Link encap:Ethernet  HWaddr 00:17:3f:18:24:5b  
          inet addr:192.168.11.100  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fe18:245b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:271227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:300382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:72031632 (72.0 MB)  TX bytes:88427420 (88.4 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-18-24-5B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"HwyW"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:16:01:9A:1F:B5   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=69/100  Signal level:-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```


These results are identical when the connection is alive or dead.
If there is any file content or output I could include to help, let me know.
(Let me just restart networking so I can post this!) #-o

---

### Post by teethlikelions on 2009-02-03
No replies... Not encouraging.
I resolved the problem though.
I thought that it might possibly be my router, so I installed DD-WRT on it... No positive results, issue persisted. I switched to WPA2, issue persisted.
I made some coffee and dug deep into google.
I found an explanation of how to install the rt2x00 drivers and blacklist the default ones. In the end, I got the drivers located at [rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page") to work and the problem has vanished.
I guess the default Ubuntu Ralink drivers just don't get along with the F5D9050.

---

