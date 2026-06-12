---
title: "usb to ethernet device is not detected"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by rajthala on 2011-07-28
I'm using ubuntu 10.04 enterprise cloud server for my project. I use USB NIC to interface with other 2 servers. but the system doesnot detect USB NIC. please help me to detect & configure USB NIC in the network.

---

### Post by chili555 on 2011-07-29
First, let's find out what it is. Please open a terminal and run and post:```
lsusb
```

---

### Post by beadrifle on 2011-07-31
Hello, 

I have a similar issue here. The  device I have is a "Techno tech HY-QF9700" Ethernet to USB. Below, I am pasting the results of what  I feel are relevant, do let me know if anything more is needed.

dmesg:
[PHP][ 4492.720283] usb 5-2: new full speed USB device using uhci_hcd and address 3[/PHP]lsusb:
[PHP]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 0fe6:9700 Kontron (Industrial Computer Source / ICS Advent) 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 15d9:0a4c Trust International B.V. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b023 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/PHP]/var/log/messages:
[PHP]Jul 31 17:52:25 dingbat kernel: [   73.980276] usb 5-2: new full speed USB device using uhci_hcd and address 3
Jul 31 17:56:43 dingbat kernel: [  331.907439] r8169 0000:08:00.0: eth0: link down
Jul 31 18:00:50 dingbat kernel: [  578.411309] r8169 0000:08:00.0: eth0: link up
Jul 31 18:02:36 dingbat kernel: [  684.872988] r8169 0000:08:00.0: PCI INT A disabled
Jul 31 18:02:43 dingbat kernel: [  691.207475] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jul 31 18:02:43 dingbat kernel: [  691.207508] r8169 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 31 18:02:43 dingbat kernel: [  691.208892] r8169 0000:08:00.0: eth0: RTL8168b/8111b at 0xffffc90011118000, 00:1e:68:20:ba:20, XID 18000000 IRQ 44
Jul 31 18:02:43 dingbat kernel: [  691.217379] r8169 0000:08:00.0: eth0: link down
Jul 31 18:02:43 dingbat kernel: [  691.217391] r8169 0000:08:00.0: eth0: link down
Jul 31 18:02:43 dingbat kernel: [  691.218539] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 31 18:02:44 dingbat kernel: [  692.813608] r8169 0000:08:00.0: eth0: link up
Jul 31 18:02:44 dingbat kernel: [  692.814663] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jul 31 18:02:57 dingbat kernel: [  705.179772] r8169 0000:08:00.0: eth0: link down
Jul 31 18:03:14 dingbat kernel: [  722.460224] r8169 0000:08:00.0: PCI INT A disabled
Jul 31 18:03:18 dingbat kernel: [  726.277621] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jul 31 18:03:18 dingbat kernel: [  726.277652] r8169 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul 31 18:03:18 dingbat kernel: [  726.278441] r8169 0000:08:00.0: eth0: RTL8168b/8111b at 0xffffc900111b6000, 00:1e:68:20:ba:20, XID 18000000 IRQ 44
Jul 31 18:03:18 dingbat kernel: [  726.288923] r8169 0000:08:00.0: eth0: link down
Jul 31 18:03:18 dingbat kernel: [  726.289411] ADDRCONF(NETDEV_UP): eth0: link is not ready[/PHP]/var/log/daemon.log:
[PHP]Jul 31 18:04:00 dingbat dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 31 18:04:03 dingbat dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul 31 18:04:06 dingbat dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jul 31 18:04:14 dingbat dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Jul 31 18:04:34 dingbat dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jul 31 18:04:41 dingbat dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Jul 31 18:04:50 dingbat dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Jul 31 18:05:01 dingbat dhclient: No DHCPOFFERS received.
Jul 31 18:05:01 dingbat dhclient: No working leases in persistent database - sleeping.
Jul 31 18:05:01 dingbat avahi-autoipd(eth0)[2492]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 110).
Jul 31 18:05:01 dingbat avahi-autoipd(eth0)[2492]: Successfully called chroot().
Jul 31 18:05:01 dingbat avahi-autoipd(eth0)[2492]: Successfully dropped root privileges.
Jul 31 18:05:01 dingbat avahi-autoipd(eth0)[2492]: Starting with address 169.254.5.215
Jul 31 18:05:06 dingbat avahi-autoipd(eth0)[2492]: Callout BIND, address 169.254.5.215 on interface eth0
Jul 31 18:05:06 dingbat avahi-daemon[994]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.5.215.
Jul 31 18:05:06 dingbat avahi-daemon[994]: New relevant interface eth0.IPv4 for mDNS.
Jul 31 18:05:06 dingbat avahi-daemon[994]: Registering new address record for 169.254.5.215 on eth0.IPv4.
Jul 31 18:05:10 dingbat avahi-autoipd(eth0)[2492]: Successfully claimed IP address 169.254.5.215[/PHP]After some reading, I saw wireless users facing a similar avahi issue and the solution was to use wicd instead of network-manager. But I want to try and get it to work using the interfaces file first. 
I have tried disabling network-manager while bringing the interfaces up and also a rmmod and modprobe of r8169. 
Also, I have tried assigning a static ip to eth0 but that doesn't work. Lastly, I am unable to understand how this would function, I'm not able to trace anything such as a MAC ID for this device. Please help! Thank you.

---

### Post by chili555 on 2011-07-31
I'm confused. Your lsusb shows this:> Bus 005 Device 003: ID [COLOR="Red"]0fe6:9700[/COLOR] Kontron (Industrial Computer Source / ICS Advent) That device is driven by the module *dm9601*:> $ modinfo dm9601
filename:       /lib/modules/2.6.38-10-generic/kernel/drivers/net/usb/dm9601.ko
license:        GPL
description:    Davicom DM9601 USB 1.1 ethernet devices
author:         Peter Korsgaard <jacmet@sunsite.dk>
srcversion:     0398CE1DC79ECEAA250DA7F
alias:          usb:v0A46p9000d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Red"]0FE6[/COLOR]p[COLOR="Red"]9700[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0FE6p8101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0A47p9601d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0A46p8515d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0A46p0268d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0A46p6688d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0A46p9601d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp9601d*dc*dsc*dp*ic*isc*ip*
depends:        usbnet
vermagic:       2.6.38-10-generic SMP mod_unload modversions 686 
On the other hand, r8169 is the usual module for a built-in ethernet card. Did you get the USB-to-ethernet because the internal isn't working or what? It actually looks healthy, although it is not going to connect if the cable is attached to the USB.

---

### Post by beadrifle on 2011-07-31
Oh no, My internal eth0 is indeed healthy. This is for a friend of mine and he has the same ubuntu  I run so I was testing it out on mine before replicating it on his.

I have made some progress however. I managed to get the drivers to recognise the device by modprobing the dm9601 module. 

lsmod:

[PHP]dm9601                  7953  0 
mii                     5261  3 dm9601,usbnet,r8169[/PHP]

however, the device still won't turn up as an interface. The udev rules generator too does not pick up anything on a restart. 

Do let me know if you need anything more.

---

### Post by chili555 on 2011-07-31
What interesting messages are here?```
dmesg | grep dm9
sudo cat /var/log/syslog | grep -e dm9 -e usb | tail -n25
```

---

### Post by flurl on 2012-01-04
Though this thread is old I want to throw in, that it seems there are different USB ethernet adapters lurking around with the same USB id 0fe6:9700.
The davicom module doesn't drive mine but a driver called qf9700 does.
Have a look here [http://mquin.livejournal.com/178482.html](http://mquin.livejournal.com/178482.html) . That worked for me.

---

