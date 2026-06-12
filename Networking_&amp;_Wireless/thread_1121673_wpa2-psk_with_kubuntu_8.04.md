---
title: "wpa2-psk with kubuntu 8.04"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by michiedo on 2009-04-10
kubuntu 8.04
wireless usb stick (ralink something), managed by madwifi
works like a charme since many months ... with an unprotected network.

Today I tried to protect my net with WPA2-PSK
The hardware it's ok: it works with windows.

With kubuntu (i installed wpasupplicant) i'm not able to reach the network:
ping 192.168.0.1 gives me:
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.73 icmp_seq=2 Destination Host Unreachable
From 192.168.0.73 icmp_seq=3 Destination Host Unreachable

What's really strange is that i can see my linux box connected to the router (it's a netgear something, it has a fram that "shows connected devices" where i see the linux ip (192.168.0.73) and the MAC of the usb stick !!

Another thing is strange: dhcp don't works (it works if the network is unprotected), but i don't care about it.
I'we tried configuring the router with both options: broadcast/don't broadcast ESSID, but nothing changes.

I feel like i'm just a small (very small) step away from success (ifconfig/iwconfig/router' display ... all it's ok) ...but i can't find out what i'm missing :-(

I thank a lot any who would mind to help me !!
:-))


here is the wpa.conf:
network={
        ssid="myessid"
        psk=4341801f5535344ef3d25369471491f8327f156bed10756e580bb0cd57277288
	scan_ssid=1  <- i've also tried scan_ssid=0, no luck
	key_mgmt=WPA-PSK
}

here's the /etc/netw/interfaces:
-------------------------------------------/etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
#auto eth0

auto wlan0
iface wlan0 inet static
address 192.168.0.73
netmask 255.255.255.0
gateway 192.168.0.1
     wpa-driver wext any
     wpa-conf /etc/wpa_supplicant.conf
-------------------------------------------/etc/network/interfaces
output of ifconfig command:
cb@ubuntu:~/wpa_supplicant-0.6.9/wpa_supplicant$ ifconfig
lo        Link encap:Loopback locale
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:310 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0
          Byte RX:34050 (33.2 KB)  Byte TX:34050 (33.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:80:5a:50:eb:f5
          inet addr:192.168.0.73  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::280:5aff:fe50:ebf5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3858 errors:0 dropped:0 overruns:0 frame:0
          TX packets:488 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000
          Byte RX:174532 (170.4 KB)  Byte TX:46527 (45.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-80-5A-50-EB-F5-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)
-------------------------------------------
and the output of the "route" command:
-------------------------------------------
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    100    0        0 wlan0
-------------------------------------------
output of the iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"myessid"
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:1B:2F:43:24:5A
          Bit Rate=11 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality=72/100  Signal level=-48 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by michiedo on 2009-04-10
8-()

after posting the message in the forum, i've installed the knetworkmanager applet (that i removed during my tests) and rebooted (that i've already done many times (too many) today) and now ...
magically (!!) my wireless WORKS !
even the DHCP it works !

sorry, really sorry, for the disturb.

---

