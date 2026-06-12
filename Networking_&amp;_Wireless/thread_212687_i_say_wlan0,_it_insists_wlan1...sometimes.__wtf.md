---
title: "i say wlan0, it insists wlan1...sometimes.  wtf?"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by kr0m3 on 2006-07-10
ok, first the details.
dell d600 with onboard broadcom 1400 wireless.
yes, it was a dud with the dapper broadcom driver so i removed it, installed ndiswrapper and configured appropriately...thanks 2 these forums for the tips!

ok, so now it works, but it cycles between being wlan0 and wlan1 after reboots.  for some reason, it often believes that wlan0 is still in use by...whatever.  this is no biggie by itself, but it is messing up my network applets and configs.

here is my interfaces:
---------------------
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp



and here is my iftab:
---------------------
> 
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0d:56:de:81:66 arp 1
wlan0 mac 00:90:4b:6b:f8:ab arp 1


here is my iwconfig:
--------------------
> 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:-2147483648 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


...and my ifconfig:
-------------------
> 
eth0      Link encap:Ethernet  HWaddr 00:0D:56:DE:81:66
          inet addr:10.22.136.22  Bcast:10.22.136.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fede:8166/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:967 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:847816 (827.9 KiB)  TX bytes:142746 (139.4 KiB)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:508 (508.0 b)  TX bytes:508 (508.0 b)

wlan1     Link encap:Ethernet  HWaddr 00:90:4B:6B:F8:AA
          inet6 addr: fe80::290:4bff:fe6b:f8aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Memory:fafee000-faff0000


...so, what the heck am i missing here?

thanx in advance!
~k

---

### Post by kr0m3 on 2006-07-10
ok... i got it figured... but i'll leave this up so others can get to it as well.
---
for some weird reason, iftab had sequentially bumped the mac of my wifi card (:ab instead of :aa)

so, i edited iftab to reflect the actual mac and rebooted...it's all good.


peace!
~k

---

