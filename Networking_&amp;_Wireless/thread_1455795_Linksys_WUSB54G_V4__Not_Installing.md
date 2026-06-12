---
title: "Linksys WUSB54G V4  Not Installing"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by Rhodess on 2010-04-16
:confused:
I really need help with this folks. I have gone through all the posts, need ndis wrapper, don't need it use rt2500 driver, use rt2570 drive, make sure build- essentials installed, make sure gcc installed etc. NOTHING WORKS!

This seems to be a recurring theme based on the number of different posts about the same issue, unfortunately they all gloss over something and make lots of presuppositions.
Can someone please walk me through this?
 I based my efforts on this thread

[http://ubuntuforums.org/showthread.php?t=106846&highlight=rt2570](http://ubuntuforums.org/showthread.php?t=106846&highlight=rt2570)
plus several other external ones.

Here is my system:
Ubuntu Karmic Koala V9.1
Build-essentials: linux-headers-2.6.31-20-generic
GCC v4.4.1
ndiswrapper-1.56

using wpa-psk
non broadcast ESSID:Rhodess

Linksys WUSB54G v4 USB wifi card
lsusb:
Bus 001 Device 004: ID 13b1:000d Linksys WUSB54G Wireless Adapter
iwconfig:
wlan0     IEEE 802.11g  ESSID:off/any 
          Mode:Auto  Frequency:2.437 GHz  Access Point: Not-Associated  
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm 
          RTS thr=2347 B   Fragment thr=2346 B  
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:14:bf:7a:67:2e 
          inet6 addr: fe80::214:bfff:fe7a:672e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:672 (672.0 B)  TX bytes:1855 (1.8 KB)
/etc/network/interfaces:
auto lo
iface lo inet loopback
#auto eth0
#iface eth0 inet dhcp
auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid Rhodess
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK=xxxxxx

lsmod shows no driver!

Ralink driver rt2570-cvs-daily
also Linksys windows driver

Here is what I have tried so far:
1. Clean install of Ubuntu 9.1 with usb wifi connected and  ethernet disconnected.
Wireless connection shows up but cannot connect to Internet

2 Downloaded rt2570-cvs-daily.tar.gz driver
3. Unpacked driver and tried to install.
Failed with the following msg:
rhodess@rhodess-desktop:~/Desktop/rt2570-cvs-2009041204/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
rt2570.ko failed to build!
make: *** [module] Error 1 (why is this? - nobody has to date explained why this fails)

4. Downloaded and installed latest ndiswrapper 1.56
5. Blacklisted rt2500 in modprobe
6. Tried to install windows driver
rhodess@rhodess-desktop:~$ ndiswrapper -l
rt2500usb : driver installed
    device (13B1:000D) present (alternate driver: rt2500usb)
After rebooting the driver is not installed and I still cannot connect.

Please help............

---

