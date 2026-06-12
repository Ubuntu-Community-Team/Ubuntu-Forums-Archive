---
title: "Trying to get wireless to work in Ubunto 8.0.4"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by Howinlinux on 2008-12-12
I can not get my wireless card to work no matter what I try.  I am going to post my drivers, device, and network information below in hope that someone can help me out.  This is Ubuntu 8.0.4 using a D Link-G132 Usb Wireless Adapter
The following commands will be shown:
ifconfig
iwconfig
lsusb
ndiswrapper -l

======================ifconfig=============================
$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0b:db:c0:98:65  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:615 errors:0 dropped:0 overruns:0 frame:0
          TX packets:615 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30788 (30.0 KB)  TX bytes:30788 (30.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:95:bb:78:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1338 (1.3 KB)  TX bytes:1646 (1.6 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:11:95:bb:78:48  
          inet addr:169.254.6.181  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

****I never had this avahi before now, also, I notice it is very similar to getting a "Private IP Address" when you have network issues in Windows..Basically not handshaking with host***
========================iwconfig======================
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  Mode:Managed  Frequency:2.437 GHz  
          Access Point: Not-Associated   Bit Rate:108 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

======================lsusb======================
$ lsusb
Bus 004 Device 004: ID 2001:3a02 D-Link Corp. [hex] 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
==================ndiswrapper -l==========================
ndiswrapper -l
athfmwdl : driver installed
neta5agu : driver installed
	device (2001:3A02) present

---

### Post by Kobalt on 2008-12-12
Everything seems ok, what happens when you click on the Network Manager icon? Do you get a list of available networks?

---

### Post by Howinlinux on 2008-12-12
Thanks for resonding,

Yes I get a list of networks and I see mine, but it will not connect.  I use WPA-Personal and I enter my key.  It like connects for 1 second, never issues the IP and then the signal bars go to 0.  I have tried selecting TKIP also but that didn't seem to matter.

---

### Post by Howinlinux on 2008-12-12
I didn't modprobe this time.  I can not remember the command.  Also, I think I edited the wpa_supplicant last time but I am not sure...Any ideas..

---

### Post by Kobalt on 2008-12-12
You edited wpa_supplicant? Why? Ubuntu 8.04 comes with support for WPA and WPA2 encryption, if your wireless card and its driver supports it. Maybe the problem comes from the modifications you made...

---

### Post by Howinlinux on 2008-12-12
No, I edited them previously in the Gutsy Gibbon install.  It worked after that.  It was when I upgraded that they stopped working.  Remember, I had this device working 5 hours ago under a different Distro

---

