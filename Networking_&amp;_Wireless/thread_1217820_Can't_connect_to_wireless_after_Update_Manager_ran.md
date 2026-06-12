---
title: "Can't connect to wireless after Update Manager ran"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by caitriana on 2009-07-20
Hi,
 
I'm an Ubuntu novice, installed Ubuntu 9.04 last week and things worked fine. A few days ago, wireless suddenly stopped connecting, after some updates were installed. After lots of googling, thought it was a conflict with acpi, and after turning off acpi I did get connectivity back for a couple of days. However, that's now gone too... have been searching this and other forums, trying different things with no success.
 
I'm using a Dell Vostro 1000, with Broadcom BCM4311 wireless card. It can see the network OK, (though that seems to come and go, even when another laptop sitting right next to it which sees it all the time), tries to connect, but just does not connect.
 
Nothing's changed on the router and my flatmate's laptop, which I'm using just now, has no problem, so the problem can't be there.
 
ifconfig:
```
eth1     Link encap:Ethernet  HWaddr 00:1f:3a:0e:1d
                      inet6 addr:  fe80::21f:3aff:fe0e:ec1d/64 Scope:Link
                      UP BROADCAST MULTICAST  MTU:1500  Metric:1
                      RX packets:0 errors:0 dropped:0 overruns:0 frame:906
                      TX packets:13 errors:6 overruns:0 carrier:0
                      collisions:0 txqueuelen:1000
                      RX bytes:0 (0.0 B)   TX bytes:4550 (4.5 KB)
                      Interrupt: 18
```
 
iwconfig when it is trying to connect and picking up the network, before it fails:
```
eth1     IEEE 802.11bg  ESSID:"force"  Nickname:""
                      Mode:Managed  Frequency:2.412 GHz  Access Point:00:15:F2:7D:5F:72
                      Bit Rate=54 Mb/s    Tx-Power:32 dBm
                      Retry min limit:7    RTS thr:off   Fragment thr:off
                      Power Managementmode:All packets received
                      Link Quality=4/5   Signal level=-63 dBm  Noise level=-96 dBm
                      Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
                      Tx excessive retries:1   Invalid misc:0   Missed beacon:0
```
 
iwconfig after it's failed to connect:
```
eth1     IEEE 802.11bg  ESSID:""  Nickname:""
                      Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
                      Bit Rate=54 Mb/s    Tx-Power:32 dBm
                      Retry min limit:7    RTS thr:off   Fragment thr:off
                      Power Managementmode:All packets received
                      Link Quality=5/5   Signal level=-57 dBm  Noise level=-92 dBm
                      Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
                      Tx excessive retries:17   Invalid misc:0   Missed beacon:0
```
 
lspci:
```
Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```
 
If anyone can help, please let me know what to do - I am really stuck!
 
Thanks!

---

### Post by caitriana on 2009-07-21
I have since discovered that:
 
/etc/network/interfaces only had
```
auto lo
iface lo inet loopback
```
 
so following some other suggestions on this forum I added 
```
auto eth1
iface eth1 inet dhcp
```
 
This changed my NetworkManager gui to have "Wireless Networks: device not managed" so I tried manually getting it connected:
 
```
sudo ifconfig eth1 up
sudo iwconfig eth1 mode managed
sudo iwconfig eth1 channel 11
sudo iwconfig eth1 essid "force"
sudo dhclient eth1
```
 
However, this didn't get any DHCP offers... so I thought still no further forward.
 
Then, after a while doing some other things, I looked at /etc/resolv.conf and the output of route, found
```
nameserver 192.168.1.1
```
 
which wasn't there before.. so I tried some pings and found it was connected! 
 
So now, the NetworkManager applet doesn't show any networks but using the terminal I can connect, apparently.
 
Can anyone explain to me what was happening and how I can get it to bring the connection up automatically when I login?
 
Thanks!

---

