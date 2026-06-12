---
title: "WiFi problem. Card detected but no surfing"
date: 2006-01-06
forum: Networking &amp; Wireless
---

### Post by rozojc on 2006-01-06
Hi every1

Here's the thing: I was using Ubuntu and I had my wireless card (Broadcom) working through ndiswrapper, and it worked. I switched to Kubuntu (I didn't reinstall, I basically uninstalled gnome and then installed the package 'kubuntu-desktop').

My card seems to be working through ndiswrapper like it was before (if I type ifconfig on the terminal I get some info about it), KWiFiManager picks it up, I can connect to networks (supposedly) but it's not really working!

In other words, according to KWiFiManager it's connected, but I can't browse the net. It's an open WiFi network without password or anything, and I used to be able to surf with gnome.... any ideas? HELP!!!!

---

### Post by gruepig on 2006-01-08
I need more information.  Post the output of 'iwconfig -a' and 'ifconfig -a'.

The relevant things you are trying to determine are whether you are associated with an access point (iwconfig shows this) and whether you have an IP address (ifconfig) shows this.

If you don't have an IP address, you need to either use DHCP or specify your IP configuration manually.

If you have an IP address, the next thing to check is whether you have a route: 'route -n' or 'netstat -rn'.

Try pinging your gateway address, another IP address not on your local subnet, and a computer by hostname.  If the former two work, but not the latter, it's a DNS issue.

All of these settings are loaded from the file /etc/network/interfaces (which may specify that IP configuration is obtained via DHCP) and /etc/resolv.conf (for DNS).

---

### Post by rozojc on 2006-01-08
Ok:
iwconfig -a gives me nothing (it says "no such device")
iwconfig gives me this:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"MartinezWireless "
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:0F:66:B0:2B:10
          Bit Rate:5.5 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-84 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

vmnet8    no wireless extensions.

-------------------------
ifconfig -a gives me this:
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:A3:23:E4
          inet addr:69.79.172.163  Bcast:255.255.255.255  Mask:255.255.240.0
          inet6 addr: fe80::2c0:9fff:fea3:23e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2657219 (2.5 MiB)  TX bytes:161315 (157.5 KiB)
          Interrupt:19 Base address:0x1800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6467 (6.3 KiB)  TX bytes:6467 (6.3 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.61.1  Bcast:192.168.61.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0E:9B:CD:5C:98
          inet6 addr: fe80::20e:9bff:fecd:5c98/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4109 (4.0 KiB)  TX bytes:378 (378.0 b)
          Memory:e2000000-e2001fff
---------------------------------------------------------------------------------
What I can tell is that the device supposedly works, it has the ESSID configured, it lists something as an access point, but I think I don't have an IP and I don't know how to get one...But I don't really know much about this anyway so I don't really know for sure what the problem is

---

### Post by rozojc on 2006-01-08
Oh I forgot, I tried this and this is the result (didn't work, did it?):

rozojc@Dorothy:~$ sudo dhclient wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0e:9b:cd:5c:98
Sending on   LPF/wlan0/00:0e:9b:cd:5c:98
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

