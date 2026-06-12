---
title: "Wireless problems"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by KajaK on 2009-04-03
Hey...

I recently installed ubuntu on my pc, and now i have problems using wireless internet; it connects to the internet, but it only stays connected for 1 minute at a time. I installed a driver for my for "Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
RaLink Device 0781" using the following guide:

-------------------------------------------------------------------
[https://bugs.launchpad.net/linux/+bug/210725/comments/152](https://bugs.launchpad.net/linux/+bug/210725/comments/152)


Please include RaLink RT2860 driver
 Alex Krastelev wrote on 2009-01-19: (permalink)

Unfortunately RT2860 isn't yet supported out of box by Jaunty Jackalope 9.04 alpha 3, but the latest driver from debian source tree works on my eee 901. The installation procedure:

- Download rt2860-source_1.8.0.0-3_all.deb from [http://packages.debian.org/sid/all/rt2860-source/download](http://packages.debian.org/sid/all/rt2860-source/download)
$ wget [http://http.us.debian.org/debian/pool/non-free/r/rt2860-source/rt2860-source_1.8.0.0-3_all.deb](http://http.us.debian.org/debian/pool/non-free/r/rt2860-source/rt2860-source_1.8.0.0-3_all.deb)

- install source .deb:
$ sudo dpkg -i rt2860-source_1.8.0.0-3_all.deb

- compile
$ sudo aptitude install debhelper module-assistant
$ sudo module-assistant auto-install rt2860

- install the module
$ sudo modprobe rt2860sta
this should activate the new wireless interface without reboot

- to load the module automatically on each reboot, add rt2860sta to /etc/modules

Installation procedure originally for 8.10 from [http://k.dieplz.net/evolution/2008/11/22/wlan-in-ubuntu-8-10-on-new-msi-wind-u100/](http://k.dieplz.net/evolution/2008/11/22/wlan-in-ubuntu-8-10-on-new-msi-wind-u100/)










Terminal:

sudo gedit /etc/network/interfaces

Add:

auto 
iface wlan0 inet dhcp
wireless_mode managed
wireless-essid network
wireless_rate 54M auto
wireless-key s:wireless-key <--- wireless-key = din nøgle
wireless-channel 3









Automatic startup:
Terminal:

sudo gedit /etc/modules

Add:

rt2860sta

-------------------------------------------------------------------


When run the hardware test, it gives me an error when testing the internet connection:


-------------------------------------------------------------------

ERROR:root:Could not find def gateway info in /proc
Traceback (most recent call last):
File "/usr/share/hwtest/scripts/internet_test", line 132, in <module>
sys.exit(main(sys.argv[1:]))
File "/usr/share/hwtest/scripts/internet_test", line 118, in main
host = route.get_default_gateway()
File "/usr/share/hwtest/scripts/internet_test", line 81, in get_default_gateway
t1 = self._get_default_gateway_from_bin_route()
File "/usr/share/hwtest/scripts/internet_test", line 69, in _get_default_gateway_from_bin_route
if def_gateway:
UnboundLocalError: local variable 'def_gateway' referenced before assignment

-------------------------------------------------------------------

Therefore my question is... now what do I do??

---

### Post by x22 on 2009-04-03
welcome to the forum

here are some things to try:

1. does this show your wireless card? "lspci"

2. does this reveal "wlan0"? "ifconfig wlan0 up"

3. does this show the correct module? "lsmod |grep <module.name>"

please post the results

---

### Post by CyberMando on 2009-04-03
The error seems to indicat that your driver is installed, your network is configured, and the only problem is that a default route is not defined. You should run 
ifconfig
and it will probably show you something like this
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16516 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2883428 (2.8 MB)  TX bytes:2883428 (2.8 MB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:25:a3:6b
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fe25:a36b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:113452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33072 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:66018895 (66.0 MB)  TX bytes:4989455 (4.9 MB)

Look at the wlan0( or maybe ra0) entry to see if it has an ipaddress like inet addr:192.168.0.4.

Then run route.
It will show something like
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0

and will actually be missing this line
default         home            0.0.0.0         UG    0      0        0 wlan0

To add that line run 
sudo route add default gw 192.168.0.4
use you ip address where I put 192.168.0.4. That should make it work, but it should do that when you rnetworking comes up on boot.

---

### Post by CyberMando on 2009-04-04
I made a mistake in the route command. the ip address you should use is the ip address of your router, which acts a a gateway to the rest of the internet. That means 192.168.0.4 should be replaced by the number for your router, maybe 192.168.0.1?

---

### Post by KajaK on 2009-04-05
-----------------------------------------------------------------------
kajak@LG-E300:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 7930 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS7932 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc Device 7934
00:06.0 PCI bridge: ATI Technologies Inc RS7936 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc Device 7937
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Xpress 1250
01:05.2 Audio device: ATI Technologies Inc RS600 audio device [Radeon Xpress 12xx Series]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
08:00.0 Network controller: RaLink Device 0781
kajak@LG-E300:~$ ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
-----------------------------------------------------------------------

not sure about the last one.






...and where do i type in ipconfig? Didn't know that command in ubuntu.

---

