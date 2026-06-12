---
title: "No wireless networks / scan - and everything OK - I'm loosing my mind, pls any ideas?"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by magozoom on 2009-12-29
I've spent most of my day learning about wireless networking with linux/ubuntu. I have uninstalled, re-installed, checked logfiles and trying to track down why 
- network-manager reports wireless networks - disconnected
- iwlist reports eth1 - Interface doesn't support scanning.
everything else seems OK, driver loaded and what not...

Pls, any ideas to what obvious things have I overlooked?
Below all information I could gather from my system.

Wireless is on eth1, wired (working) on eth0

Some odd things that caught my eye:
eth1 reports driver=wl0 for Broadcom BCM4315 , kernel module is "wl", there is no wl0 module. OK?
network-manager deactivates the eth1 device with "reason :2", why?

Grateful for any ideas on how to get out of this SNAFU.

/magnus


-----------------------------------
Ubuntu 9.10
2.6.31-16-generic i686

-------------- lspci ------------------
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

-------------- lsusb -----------------
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

-------------- ifconfig -------------------
eth0      Link encap:Ethernet  HWaddr 00:1f:16:1f:8b:80  
          inet addr:192.168.0.151  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe1f:8b80/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:511 errors:0 dropped:0 overruns:0 frame:0
          TX packets:482 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:420278 (420.2 KB)  TX bytes:63928 (63.9 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:24:2b:f6:3a:a1  
          inet6 addr: fe80::224:2bff:fef6:3aa1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

-------------- iwconfig -----------
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.

-------------- sudo lshw -C network ------------

  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:1f:8b:80
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v3.04 ip=192.168.0.151 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:f6000000-f600ffff
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:24:2b:f6:3a:a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f8000000-f8003fff

--------- lsmod | grep "wl" ----------------------------

wl                   1272936  0 
lib80211                6432  2 lib80211_crypt_tkip,wl

---------- iwlist scan -------------

lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
eth1      Interface doesn't support scanning.
pan0      Interface doesn't support scanning.

-------------- sudo /etc/init.d/networking restart ---------------------

 * Reconfiguring network interfaces...                                          
Ignoring unknown interface eth0=eth0. [ OK ]

------------------- log file messages-------------------
Dec 29 12:56:20 magnus-ubuntu kernel: [   18.572816] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
Dec 29 13:43:44 magnus-ubuntu kernel: [   17.843927] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
Dec 29 13:54:05 magnus-ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1, iface: eth1)
Dec 29 13:54:05 magnus-ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Dec 29 14:00:22 magnus-ubuntu NetworkManager:    SCPluginIfupdown: guessed connection type (eth1) = 802-3-ethernet
Dec 29 14:00:22 magnus-ubuntu NetworkManager:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth1, type:802-3-ethernet, id:Ifupdown (eth1), uuid: 7b635ed6-2640-7ad8-675d-744db12dd9fa
Dec 29 14:00:22 magnus-ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1, iface: eth1)
Dec 29 14:13:55 magnus-ubuntu kernel: [   18.012707] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
Dec 29 14:16:15 magnus-ubuntu kernel: [   18.465861] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
Dec 29 14:18:34 magnus-ubuntu kernel: [   23.437279] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
Dec 29 14:21:37 magnus-ubuntu kernel: [   10.513566] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
Dec 29 18:54:41 magnus-ubuntu kernel: [16394.711184] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
Dec 29 18:55:46 magnus-ubuntu kernel: [   17.897591] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9

------------------- syslog -----------------------
Dec 29 18:54:41 magnus-ubuntu avahi-daemon[846]: Withdrawing address record for fe80::224:2bff:fef6:3aa1 on eth1.
Dec 29 18:54:41 magnus-ubuntu NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1, iface: eth1)
Dec 29 18:54:41 magnus-ubuntu NetworkManager: <info>  (eth1): now unmanaged
Dec 29 18:54:41 magnus-ubuntu NetworkManager: <info>  (eth1): device state change: 3 -> 1 (reason 36)
Dec 29 18:54:41 magnus-ubuntu NetworkManager: <info>  (eth1): cleaning up...
Dec 29 18:54:41 magnus-ubuntu kernel: [16394.711184] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
Dec 29 18:54:42 magnus-ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1, iface: eth1)
Dec 29 18:54:42 magnus-ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Dec 29 18:54:42 magnus-ubuntu NetworkManager: <info>  (eth1): driver supports SSID scans (scan_capa 0x01).
Dec 29 18:54:42 magnus-ubuntu NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'wl')
Dec 29 18:54:42 magnus-ubuntu NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/2
Dec 29 18:54:42 magnus-ubuntu NetworkManager: <info>  (eth1): now managed
Dec 29 18:54:42 magnus-ubuntu NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Dec 29 18:54:42 magnus-ubuntu NetworkManager: <info>  (eth1): preparing device.
Dec 29 18:54:42 magnus-ubuntu NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Dec 29 18:54:42 magnus-ubuntu NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready
Dec 29 18:54:42 magnus-ubuntu NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 42)
Dec 29 18:54:43 magnus-ubuntu avahi-daemon[846]: Registering new address record for fe80::224:2bff:fef6:3aa1 on eth1.*.
Dec 29 18:54:52 magnus-ubuntu kernel: [16405.476063] eth1: no IPv6 routers present
Dec 29 18:55:45 magnus-ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1, iface: eth1)
Dec 29 18:55:45 magnus-ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Dec 29 18:55:46 magnus-ubuntu kernel: [   17.897591] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
Dec 29 18:55:46 magnus-ubuntu NetworkManager: <info>  (eth1): driver supports SSID scans (scan_capa 0x01).
Dec 29 18:55:46 magnus-ubuntu NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'wl')
Dec 29 18:55:46 magnus-ubuntu NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Dec 29 18:55:46 magnus-ubuntu NetworkManager: <info>  (eth1): now managed
Dec 29 18:55:46 magnus-ubuntu NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Dec 29 18:55:46 magnus-ubuntu NetworkManager: <info>  (eth1): preparing device.
Dec 29 18:55:46 magnus-ubuntu NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Dec 29 18:55:46 magnus-ubuntu NetworkManager: <info>  (eth1): supplicant manager state:  down -> idle
Dec 29 18:55:46 magnus-ubuntu NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 0)
Dec 29 18:55:46 magnus-ubuntu NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready
Dec 29 18:55:47 magnus-ubuntu avahi-daemon[863]: Registering new address record for fe80::224:2bff:fef6:3aa1 on eth1.*.
Dec 29 21:50:55 magnus-ubuntu kernel: [   41.556073] eth1: no IPv6 routers present
----------------------------------------

---

### Post by bkratz on 2009-12-29
Have you been here?

[http://ubuntuforums.org/showthread.php?t=1347483&highlight=BCM+4312](http://ubuntuforums.org/showthread.php?t=1347483&highlight=BCM+4312)

---

### Post by magozoom on 2009-12-29
> **bkratz said:**
> Have you been here?

[http://ubuntuforums.org/showthread.php?t=1347483&highlight=BCM+4312](http://ubuntuforums.org/showthread.php?t=1347483&highlight=BCM+4312)

Yes, I've tried both the STA driver, checking all blacklists and loaded modules, and running the B43 fwcutter driver as described in [http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

Same results - everything OK with ifconfig/iwconfig/lshw

With B43 driver interface is on wlan1 and i get "wlan1: No scan results"

And the kill-switch is on.... 
With the B43 driver i get 
Dec 29 22:56:20 magnus-ubuntu kernel: [   44.426031] ADDRCONF(NETDEV_UP): wlan1: link is not ready
when network-manager takes down the wlan1 interface.

I'm at the "Maybe if I move the computer facing east it will work" stage :)

---

### Post by bkratz on 2009-12-29
It looks like you have the low powered version which says on this page

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

that it is in process.  I thought I saw something about this device specifically so i will look and see if i can find it again.

---

### Post by magozoom on 2009-12-29
OK. It's working now. 

I **powered down** this Lenovo S12 notebook, instead of rebooting. That did it. Almost as fun as when I tried to get a wired network up, and the LAN-plug wasn't fully inserted into the socket. But just almost.

---

### Post by magozoom on 2009-12-29
> **bkratz said:**
>  I thought I saw something about this device specifically so i will look and see if i can find it again.

Thanks for helping. 
I need a beer. 
Next time i will power this netbook down aerial style through a window or something.

---

### Post by bkratz on 2009-12-29
> **magozoom said:**
> OK. It's working now. 

I **powered down** this Lenovo S12 notebook, instead of rebooting. That did it. Almost as fun as when I tried to get a wired network up, and the LAN-plug wasn't fully inserted into the socket. But just almost.




Sorry I wasn't able to help, but I did find this

[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

Glad you got it working though!!!

Please go to the thread tools and mark as solved, so other may benefit.

---

### Post by magozoom on 2009-12-29
For the record: This is a Lenovo S12 Atom/ION netbook which works great with Ubuntu 9.10

I used the instructions on 
[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)
to get the wireless running - after installing the driver I had to go to Systems - Administration - Hardware Drivers menu
and activate the B43 driver and then **power down** the computer

My PCI-ID is 14e4:4315 - BCM4312 802.11b/g - low power

/m

---

### Post by magozoom on 2009-12-29
**Correction:** yes the B43 drivers do get the Wirless networking up and runnning, and they also freeze my system at random intervals with a DMA error. Frustrating. As bkratz pointed out this Lenovo Ideapad uses a "low power" chip version from Broadcom which is not yet OK with the B43 drivers, your system may work with the B43 drivers...

So... 
I  reinstalled Ubuntu, and is now up and runnning with the STA Drivers.

---

### Post by bkratz on 2009-12-29
I believe the STA driver is actually the correct one for the card.

---

