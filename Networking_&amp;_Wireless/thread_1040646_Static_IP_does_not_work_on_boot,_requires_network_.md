---
title: "Static IP does not work on boot, requires network interface restart."
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by tominglis on 2009-01-15
I have an Edimax EW-7128g (with RT2561ST chipset) on Mythbuntu 8.04.1.

I have a Belkin F5D-7632-4 (v.5000uk).

I run a wireless g network with WPA, MAC filtering, and DHCP (for IP's 2 - 100).

I have inputted a static IP address for my media PC (175), and every time I boot the computer, I need to do sudo ifdown -a / sudo ifup -a to get networking to work. Is there a bug in the driver or in the networking stack that is causing this? If so, is it possible to fix it? If not, is there some kind of startup script I could use to run these commands during bootup?

---

### Post by Iowan on 2009-01-15
Post contents of /etc/network/interfaces and results of **ifconfig -a**

---

### Post by tominglis on 2009-03-02
I now have a Cisco 877W router, and the same problem. I think that this is a limitation in the kernel driver for this wireless chipset?

**********

/etc/network/interfaces:

auto lo
iface lo inet loopback

iface wlan0 inet static
address 10.7.1.175
netmask 255.255.255.0
gateway 10.7.1.1
wpa-psk a9b029b3f67fae7049fda556dda17f84aa41b353b129b986535567ce293d5dbf
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid Ilium

auto wlan0

**********

tominglis@Odysseus:~$ sudo ifdown -a
[sudo] password for tominglis: 
tominglis@Odysseus:~$ sudo ifup -a
tominglis@Odysseus:~$  * Stopping NTP server ntpd
   ...done.
 * Starting NTP server ntpd
   ...done.
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:18:f3:f4:b5:04  
          inet6 addr: fe80::218:f3ff:fef4:b504/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:95 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15147 (14.7 KB)  TX bytes:20294 (19.8 KB)
          Interrupt:217 Base address:0x2000 

eth0:avahi Link encap:Ethernet  HWaddr 00:18:f3:f4:b5:04  
          inet addr:169.254.7.195  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:217 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34444 (33.6 KB)  TX bytes:34444 (33.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0e:2e:ea:2a:c8  
          inet addr:10.7.1.175  Bcast:10.7.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:feea:2ac8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:924 errors:0 dropped:0 overruns:0 frame:0
          TX packets:870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1097994 (1.0 MB)  TX bytes:153402 (149.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0E-2E-EA-2A-C8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tominglis@Odysseus:~$ ping -c 3 4.2.2.1
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_seq=1 ttl=248 time=45.6 ms
64 bytes from 4.2.2.1: icmp_seq=2 ttl=248 time=45.7 ms
64 bytes from 4.2.2.1: icmp_seq=3 ttl=248 time=45.5 ms

--- 4.2.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 45.570/45.644/45.756/0.080 ms

---

