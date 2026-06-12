---
title: "problem detecting wireless networks"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by ayvah on 2010-03-17
I'm using the latest version of Linux Mint, based on Karmic Koala.

In System -> Administration -> Hardware Drivers I installed the Broadcom driver for my wireless network card. This made it so that I have wireless options in my networking stuff. However, the networking doesn't seem to actually work. 

The laptop is sitting about 3 metres away from a wireless access point using wireless-N and WPA encryption. I'm not sure what the problem is. I can't detect any wireless networks at all, and I can't seem to connect to it as a "hidden" network either. Is this something wrong with the driver? Where should I try to tackle the problem?

```
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bgn  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:44 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
I did this, but I'm not sure what it means. I'm sure there must be a troubleshooting guide for this somewhere, but I'm not sure what I'm looking for. The [community docs here](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) don't seem to deal with this issue precisely.

---

### Post by chili555 on 2010-03-17
> Tx-Power:off  This is a little bothersome. Please do:```
sudo ifconfig eth1 up
sudo iwconfig eth1 txpower 5
```If it does not error out, repeat the command with higher numbers until you get an error. Then check for networks and, hopefully, connect. Post back if not.

---

### Post by ayvah on 2010-04-01
Well, as much as this problem has bothered me, I've been putting it off because dealing with it has become something of a headache. 

Anyway, before I could try out your suggestion, the nature of the problem had changed.

I believe, that when I had asked the original question, I had installed the drivers, *and then* installed updates on Ubuntu. However, I had not reset my system since then.

When I *did* reset, the laptop started to reject the drivers. It seemed that the updates had broken compatibility. In low-graphics mode, I activated the video driver again, so it re-installed and it was fixed.

However, ever since then the option for wireless has disappeared from the menus, and the wireless driver has displayed "The driver is activated but not currently in use". I couldn't fix this simply by de-activating and re-activating the driver. 

I've found the thread [Broadcom "Activated but not in use"]("http://ubuntuforums.org/showthread.php?t=1059819")and the title made it sound perfect, but -- well, I can't even try Phis's solution because I'm not aware of any way to turn off my wireless card. (It seems like an odd solution too. o_O )

---

### Post by chili555 on 2010-04-01
Let's see what the kernel has to say about all this. Please do:```
dmesg |  grep -e b43 -e wl
```We will get to the bottom of this!

---

### Post by ayvah on 2010-04-05
Okay, this is the output

> ~ $ dmesg | grep -e b43 -e wl
[   12.886451] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   12.886455] wl: Unknown symbol lib80211_get_crypto_ops

---

### Post by chili555 on 2010-04-05
Let's try to re-install a couple of things. Open a terminal and do:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo apt-get install --reinstall lib80211
```Reboot and see if your wireless is working.

---

### Post by ayvah on 2010-04-05
The first reinstall worked fine. However, the second spat this out.

> ~ $ sudo apt-get install --reinstall lib80211
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lib80211

---

### Post by chili555 on 2010-04-05
> E: Couldn't find package lib80211 Please try:```
sudo apt-get install --reinstall linux-image-`uname -r`
```Those tickmarks are on the upper left of my US keyboard on the same key with ~.

Then reboot and let's see if we have any improvements.

---

### Post by ayvah on 2010-04-06
Okay, I did that. It all seemed to go fine. Except now that I've rebooted, I can't seem to access wired networks either.

:(

---

### Post by chili555 on 2010-04-06
May I please see:```
sudo lshw -C network
```Thanks.

---

### Post by ayvah on 2010-04-06
Weird. I booted up the computer again, and the wired network is working. Maybe it was just some weird quirk? o.o

I'm not sure if you still want this, but here it is anyway.

```
~ $ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:da100000-da103fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 00:26:9e:ef:dc:3b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.3 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:35 ioport:4000(size=256) memory:d4104000-d4104fff(prefetchable) memory:d4100000-d4103fff(prefetchable) memory:d4110000-d411ffff(prefetchable)
```


I thought I'd also try this again...
```
~ $ sudo apt-get install --reinstall lib80211
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lib80211
```
No change.

---

### Post by chili555 on 2010-04-06
lib80211, I learned, is included in linux-image, which we reinstalled. I'd like to know more about your Broadcom. Please post:```
lspci -nn | grep Network
```Also, since we reinstalled the kernel, let's try an earlier test:```
dmesg | grep -e b43 -e wl
```Thanks.

---

### Post by ayvah on 2010-04-06
```
~ $ lspci -nn | grep Network
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4357] (rev 01)
```
```
~ $ dmesg | grep -e b43 -e wl
[   12.223585] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   12.223589] wl: Unknown symbol lib80211_get_crypto_ops

```
I take it this is not a good sign? XD


PS I wonder if I should be able to find lib80211 in synaptic? I can't find anything beginning with lib8, but I'm not sure if that means anything.

---

### Post by ayvah on 2010-04-14
Are you unsure about what I should do now?

---

### Post by chili555 on 2010-04-14
Let's try:```
sudo apt-get remove linux-backports-modules-*
```Reboot and then run:```
sudo modprobe wl
dmesg | grep wl
```Let us know your progress. Thanks.

---

### Post by ayvah on 2010-04-14
Done, and...
```
~ $ sudo modprobe wl
~ $ dmesg | grep wl
[   11.307150] wl: module license 'MIXED/Proprietary' taints kernel.
[   11.308627] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.308636] wl 0000:02:00.0: setting latency timer to 64
```

I'm not sure what all this means, but it seems some progress has been made. I haven't actually checked this for a while, but now in Hardware Drivers, the broadcom driver is described as activated AND in use. Also, the Wireless Networks group appears in the dropdown from the network tray icon.

Of course, it still seems to be incapable of finding anything.

---

### Post by chili555 on 2010-04-14
It means it no longer has any complaints about lib80211. All those lines look like a healthy interface. Is your interface still eth1? What does this say?```
iwconfig
sudo iwlist eth1 scan
```> Wireless Networks group appears in the dropdown from the network tray icon.Are there any networks at all in there? Yours, mine, anybody??

---

### Post by ayvah on 2010-04-14
```
~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated 

~ $ sudo iwlist eth1 scan
eth1      Interface doesn't support scanning.

~ $ sudo iwlist eth2 scan
eth2      Failed to read scan data : Invalid argument

```
So it looks like it's managed to become eth2?

> Are there any networks at all in there? Yours, mine, anybody??
Nothing at all. That doesn't mean too much though. As far as I'm aware, my wireless network is the only one in range.

---

### Post by chili555 on 2010-04-14
Let's have a look at:```
rfkill list
sudo cat /var/log/syslog | grep eth
sudo iwpriv eth2
```Is your router set for 'N' speeds only or for mixed B, G and N?

---

### Post by ayvah on 2010-04-14
Okay, I've done that. Only, the output for the second command is so long it won't even fit in Terminal. Is there something from that you wanted to read? This is all I could grab...

```
Apr  6 17:54:30 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr  6 17:54:30 Chertograd NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Apr  6 17:54:30 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr  6 17:54:30 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr  6 17:54:30 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr  6 17:54:30 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr  6 17:54:30 Chertograd NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Apr  6 17:54:30 Chertograd NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Apr  6 17:54:30 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Apr  6 17:54:30 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr  6 17:54:30 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Apr  6 17:54:30 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Apr  6 17:54:30 Chertograd NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Apr  6 17:54:30 Chertograd dhclient: Listening on LPF/eth0/00:26:9e:ef:dc:3b
Apr  6 17:54:30 Chertograd dhclient: Sending on   LPF/eth0/00:26:9e:ef:dc:3b
Apr  6 17:54:33 Chertograd dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr  6 17:54:38 Chertograd dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  6 17:54:44 Chertograd dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  6 17:54:50 Chertograd dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  6 17:54:58 Chertograd dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  6 17:55:09 Chertograd dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr  6 17:55:16 Chertograd NetworkManager: <info>  (eth0): DHCP transaction took too long, stopping it.
Apr  6 17:55:16 Chertograd NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 2107
Apr  6 17:55:16 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Apr  6 17:55:16 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Apr  6 17:55:16 Chertograd NetworkManager: <info>  (eth0): device state change: 7 -> 9 (reason 5)
Apr  6 17:55:16 Chertograd NetworkManager: <info>  Marking connection 'Auto eth0' invalid.
Apr  6 17:55:16 Chertograd NetworkManager: <info>  Activation (eth0) failed.
Apr  6 17:55:16 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Apr  6 17:55:16 Chertograd NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
Apr  6 17:55:16 Chertograd NetworkManager: <info>  (eth0): deactivating device (reason: 0).
Apr  6 18:03:04 Chertograd NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Apr  6 18:03:04 Chertograd NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Apr  6 18:03:04 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr  6 18:03:04 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr  6 18:03:04 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr  6 18:03:04 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr  6 18:03:04 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr  6 18:03:04 Chertograd NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Apr  6 18:03:04 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr  6 18:03:04 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr  6 18:03:04 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr  6 18:03:04 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr  6 18:03:04 Chertograd NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Apr  6 18:03:04 Chertograd NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Apr  6 18:03:04 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Apr  6 18:03:04 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr  6 18:03:04 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Apr  6 18:03:04 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Apr  6 18:03:04 Chertograd NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Apr  6 18:03:04 Chertograd dhclient: Listening on LPF/eth0/00:26:9e:ef:dc:3b
Apr  6 18:03:04 Chertograd dhclient: Sending on   LPF/eth0/00:26:9e:ef:dc:3b
Apr  6 18:03:06 Chertograd dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  6 18:03:12 Chertograd dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  6 18:03:23 Chertograd dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  6 18:03:31 Chertograd dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  6 18:03:41 Chertograd dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Apr  6 18:03:49 Chertograd NetworkManager: <info>  (eth0): DHCP transaction took too long, stopping it.
Apr  6 18:03:50 Chertograd NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 2110
Apr  6 18:03:50 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Apr  6 18:03:50 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Apr  6 18:03:50 Chertograd NetworkManager: <info>  (eth0): device state change: 7 -> 9 (reason 5)
Apr  6 18:03:50 Chertograd NetworkManager: <info>  Marking connection 'Auto eth0' invalid.
Apr  6 18:03:50 Chertograd NetworkManager: <info>  Activation (eth0) failed.
Apr  6 18:03:50 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Apr  6 18:03:50 Chertograd NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
Apr  6 18:03:50 Chertograd NetworkManager: <info>  (eth0): deactivating device (reason: 0).
Apr  6 22:51:49 Chertograd kernel: [    0.565953] ACPI Error (psparse-0537): Method parse/execution failed [\CPUT] (Node f701ee10), AE_NOT_FOUND
Apr  6 22:51:49 Chertograd kernel: [    0.565987] ACPI Error (psparse-0537): Method parse/execution failed [\PSSC] (Node f701ee28), AE_NOT_FOUND
Apr  6 22:51:49 Chertograd kernel: [    0.566021] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._REG] (Node f7011ed0), AE_NOT_FOUND
Apr  6 22:51:49 Chertograd kernel: [    0.806757] ACPI Error (psparse-0537): Method parse/execution failed [\CPUT] (Node f701ee10), AE_NOT_FOUND
Apr  6 22:51:49 Chertograd kernel: [    0.806800] ACPI Error (psparse-0537): Method parse/execution failed [\_TZ_.TZ01.OTHD] (Node f701ecf0), AE_NOT_FOUND
Apr  6 22:51:49 Chertograd kernel: [    0.806845] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._Q80] (Node f7011f78), AE_NOT_FOUND
Apr  6 22:51:49 Chertograd NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0)
Apr  6 22:51:49 Chertograd NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr  6 22:51:49 Chertograd kernel: [    2.497289] eth0: RTL8168d/8111d at 0xf813a000, 00:26:9e:ef:dc:3b, XID 283000c0 IRQ 35
Apr  6 22:51:49 Chertograd NetworkManager: <info>  (eth0): carrier is OFF
Apr  6 22:51:49 Chertograd NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Apr  6 22:51:49 Chertograd NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr  6 22:51:49 Chertograd NetworkManager: <info>  (eth0): now managed
Apr  6 22:51:49 Chertograd NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Apr  6 22:51:49 Chertograd NetworkManager: <info>  (eth0): bringing up device.
Apr  6 22:51:49 Chertograd NetworkManager: <info>  (eth0): preparing device.
Apr  6 22:51:49 Chertograd NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Apr  6 22:51:49 Chertograd kernel: [   12.212208] r8169: eth0: link up
Apr  6 22:51:49 Chertograd kernel: [   12.212229] r8169: eth0: link up
Apr  6 22:51:49 Chertograd NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0
Apr  6 22:51:49 Chertograd NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Apr  6 22:51:49 Chertograd NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Apr  6 22:51:49 Chertograd NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Apr  6 22:51:49 Chertograd NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Apr  6 22:51:49 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr  6 22:51:49 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr  6 22:51:49 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr  6 22:51:49 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr  6 22:51:49 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr  6 22:51:49 Chertograd NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Apr  6 22:51:49 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr  6 22:51:49 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr  6 22:51:49 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr  6 22:51:49 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr  6 22:51:49 Chertograd NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Apr  6 22:51:49 Chertograd NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Apr  6 22:51:49 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Apr  6 22:51:49 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr  6 22:51:49 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Apr  6 22:51:49 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Apr  6 22:51:49 Chertograd NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Apr  6 22:51:49 Chertograd dhclient: Listening on LPF/eth0/00:26:9e:ef:dc:3b
Apr  6 22:51:49 Chertograd dhclient: Sending on   LPF/eth0/00:26:9e:ef:dc:3b
Apr  6 22:51:49 Chertograd avahi-daemon[979]: Registering new address record for fe80::226:9eff:feef:dc3b on eth0.*.
Apr  6 22:51:50 Chertograd dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  6 22:51:50 Chertograd dhclient: DHCPREQUEST of 192.168.0.3 on eth0 to 255.255.255.255 port 67
Apr  6 22:51:50 Chertograd NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Apr  6 22:51:50 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr  6 22:51:50 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Apr  6 22:51:50 Chertograd NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr  6 22:51:50 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr  6 22:51:50 Chertograd NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr  6 22:51:50 Chertograd avahi-daemon[979]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.3.
Apr  6 22:51:50 Chertograd avahi-daemon[979]: New relevant interface eth0.IPv4 for mDNS.
Apr  6 22:51:50 Chertograd avahi-daemon[979]: Registering new address record for 192.168.0.3 on eth0.IPv4.
Apr  6 22:51:51 Chertograd NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Apr  6 22:51:51 Chertograd NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Apr  6 22:51:51 Chertograd NetworkManager: <info>  Activation (eth0) successful, device activated.
Apr  6 22:51:51 Chertograd NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr  6 22:51:59 Chertograd kernel: [   22.273686] eth0: no IPv6 routers present
Apr  7 09:53:28 Chertograd kernel: [    0.563043] ACPI Error (psparse-0537): Method parse/execution failed [\CPUT] (Node f701ee10), AE_NOT_FOUND
Apr  7 09:53:28 Chertograd kernel: [    0.563078] ACPI Error (psparse-0537): Method parse/execution failed [\PSSC] (Node f701ee28), AE_NOT_FOUND
Apr  7 09:53:28 Chertograd kernel: [    0.563111] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._REG] (Node f7011ed0), AE_NOT_FOUND
Apr  7 09:53:28 Chertograd NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0)
Apr  7 09:53:28 Chertograd NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr  7 09:53:28 Chertograd kernel: [    0.846798] ACPI Error (psparse-0537): Method parse/execution failed [\CPUT] (Node f701ee10), AE_NOT_FOUND
Apr  7 09:53:28 Chertograd kernel: [    0.846839] ACPI Error (psparse-0537): Method parse/execution failed [\_TZ_.TZ01.OTHD] (Node f701ecf0), AE_NOT_FOUND
Apr  7 09:53:28 Chertograd kernel: [    0.846882] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._Q80] (Node f7011f78), AE_NOT_FOUND
Apr  7 09:53:28 Chertograd kernel: [    2.530297] eth0: RTL8168d/8111d at 0xf8174000, 00:26:9e:ef:dc:3b, XID 283000c0 IRQ 35
Apr  7 09:53:28 Chertograd NetworkManager: <info>  (eth0): carrier is OFF
Apr  7 09:53:28 Chertograd kernel: [   12.489342] r8169: eth0: link up
Apr  7 09:53:28 Chertograd kernel: [   12.489357] r8169: eth0: link up
Apr  7 09:53:28 Chertograd NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Apr  7 09:53:28 Chertograd NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr  7 09:53:28 Chertograd NetworkManager: <info>  (eth0): now managed
Apr  7 09:53:28 Chertograd NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Apr  7 09:53:28 Chertograd NetworkManager: <info>  (eth0): bringing up device.
Apr  7 09:53:28 Chertograd NetworkManager: <info>  (eth0): preparing device.
Apr  7 09:53:28 Chertograd NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Apr  7 09:53:28 Chertograd NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0
Apr  7 09:53:28 Chertograd NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Apr  7 09:53:28 Chertograd NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Apr  7 09:53:28 Chertograd NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr  7 09:53:28 Chertograd NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr  7 09:53:28 Chertograd NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Apr  7 09:53:28 Chertograd NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Apr  7 09:53:28 Chertograd dhclient: Listening on LPF/eth0/00:26:9e:ef:dc:3b
Apr  7 09:53:28 Chertograd dhclient: Sending on   LPF/eth0/00:26:9e:ef:dc:3b
Apr  7 09:53:28 Chertograd dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  7 09:53:28 Chertograd dhclient: DHCPREQUEST of 192.168.0.3 on eth0 to 255.255.255.255 port 67
Apr  7 09:53:28 Chertograd NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr  7 09:53:28 Chertograd NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr  7 09:53:29 Chertograd avahi-daemon[913]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.3.
Apr  7 09:53:29 Chertograd avahi-daemon[913]: New relevant interface eth0.IPv4 for mDNS.
Apr  7 09:53:29 Chertograd avahi-daemon[913]: Registering new address record for fe80::226:9eff:feef:dc3b on eth0.*.
Apr  7 09:53:29 Chertograd avahi-daemon[913]: Registering new address record for 192.168.0.3 on eth0.IPv4.
Apr  7 09:53:29 Chertograd NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Apr  7 09:53:29 Chertograd NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Apr  7 09:53:29 Chertograd NetworkManager: <info>  Activation (eth0) successful, device activated.
Apr  7 09:53:29 Chertograd NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr  7 09:53:39 Chertograd kernel: [   22.894670] eth0: no IPv6 routers present
Apr 15 00:06:14 Chertograd kernel: [    0.564086] ACPI Error (psparse-0537): Method parse/execution failed [\CPUT] (Node f701ee10), AE_NOT_FOUND
Apr 15 00:06:14 Chertograd kernel: [    0.564120] ACPI Error (psparse-0537): Method parse/execution failed [\PSSC] (Node f701ee28), AE_NOT_FOUND
Apr 15 00:06:14 Chertograd kernel: [    0.564154] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._REG] (Node f7011ed0), AE_NOT_FOUND
Apr 15 00:06:14 Chertograd NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0)
Apr 15 00:06:14 Chertograd NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr 15 00:06:14 Chertograd kernel: [    2.531082] eth0: RTL8168d/8111d at 0xf81a8000, 00:26:9e:ef:dc:3b, XID 283000c0 IRQ 35
Apr 15 00:06:14 Chertograd kernel: [   12.547419] r8169: eth0: link up
Apr 15 00:06:14 Chertograd kernel: [   12.547440] r8169: eth0: link up
Apr 15 00:06:14 Chertograd NetworkManager: <info>  (eth0): carrier is OFF
Apr 15 00:06:14 Chertograd NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Apr 15 00:06:14 Chertograd NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 15 00:06:14 Chertograd NetworkManager: <info>  (eth0): now managed
Apr 15 00:06:14 Chertograd NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Apr 15 00:06:14 Chertograd NetworkManager: <info>  (eth0): bringing up device.
Apr 15 00:06:14 Chertograd NetworkManager: <info>  (eth0): preparing device.
Apr 15 00:06:14 Chertograd NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Apr 15 00:06:14 Chertograd NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0
Apr 15 00:06:14 Chertograd NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Apr 15 00:06:14 Chertograd NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Apr 15 00:06:14 Chertograd NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Apr 15 00:06:14 Chertograd NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Apr 15 00:06:14 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 15 00:06:14 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 15 00:06:14 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 15 00:06:14 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 15 00:06:14 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 15 00:06:14 Chertograd NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Apr 15 00:06:14 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 15 00:06:14 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 15 00:06:14 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 15 00:06:14 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 15 00:06:14 Chertograd NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Apr 15 00:06:14 Chertograd NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Apr 15 00:06:14 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Apr 15 00:06:14 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 15 00:06:14 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Apr 15 00:06:14 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Apr 15 00:06:14 Chertograd NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Apr 15 00:06:14 Chertograd dhclient: Listening on LPF/eth0/00:26:9e:ef:dc:3b
Apr 15 00:06:14 Chertograd dhclient: Sending on   LPF/eth0/00:26:9e:ef:dc:3b
Apr 15 00:06:14 Chertograd dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr 15 00:06:16 Chertograd avahi-daemon[923]: Registering new address record for fe80::226:9eff:feef:dc3b on eth0.*.
Apr 15 00:06:16 Chertograd dhclient: DHCPREQUEST of 192.168.0.8 on eth0 to 255.255.255.255 port 67
Apr 15 00:06:16 Chertograd NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Apr 15 00:06:16 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 15 00:06:16 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Apr 15 00:06:16 Chertograd NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 15 00:06:16 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr 15 00:06:16 Chertograd NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr 15 00:06:16 Chertograd avahi-daemon[923]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.8.
Apr 15 00:06:16 Chertograd avahi-daemon[923]: New relevant interface eth0.IPv4 for mDNS.
Apr 15 00:06:16 Chertograd avahi-daemon[923]: Registering new address record for 192.168.0.8 on eth0.IPv4.
Apr 15 00:06:17 Chertograd NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Apr 15 00:06:17 Chertograd NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Apr 15 00:06:17 Chertograd NetworkManager: <info>  Activation (eth0) successful, device activated.
Apr 15 00:06:17 Chertograd NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 15 00:06:25 Chertograd kernel: [   23.263050] eth0: no IPv6 routers present
Apr 15 00:11:23 Chertograd NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth2, iface: eth2)
Apr 15 00:11:23 Chertograd kernel: [    0.534239] ACPI Error (psparse-0537): Method parse/execution failed [\CPUT] (Node f701ee10), AE_NOT_FOUND
Apr 15 00:11:23 Chertograd kernel: [    0.534274] ACPI Error (psparse-0537): Method parse/execution failed [\PSSC] (Node f701ee28), AE_NOT_FOUND
Apr 15 00:11:23 Chertograd kernel: [    0.534308] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._REG] (Node f7011ed0), AE_NOT_FOUND
Apr 15 00:11:23 Chertograd NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth2, iface: eth2): no ifupdown configuration found.
Apr 15 00:11:23 Chertograd NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0)
Apr 15 00:11:23 Chertograd kernel: [    2.519358] eth0: RTL8168d/8111d at 0xf816a000, 00:26:9e:ef:dc:3b, XID 283000c0 IRQ 35
Apr 15 00:11:23 Chertograd kernel: [   11.907346] eth1: Broadcom BCM4357 802.11 Wireless Controller 5.10.91.9
Apr 15 00:11:23 Chertograd kernel: [   11.911592] udev: renamed network interface eth1 to eth2
Apr 15 00:11:23 Chertograd NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth2): driver supports SSID scans (scan_capa 0x01).
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth2): new 802.11 WiFi device (driver: 'wl')
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth2): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth2): now managed
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth2): device state change: 1 -> 2 (reason 2)
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth2): preparing device.
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth2): deactivating device (reason: 2).
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth0): carrier is OFF
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth0): now managed
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth0): bringing up device.
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth0): preparing device.
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Apr 15 00:11:23 Chertograd NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0
Apr 15 00:11:23 Chertograd kernel: [   12.538896] r8169: eth0: link up
Apr 15 00:11:23 Chertograd kernel: [   12.538917] r8169: eth0: link up
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Apr 15 00:11:23 Chertograd NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Apr 15 00:11:23 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 15 00:11:23 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 15 00:11:23 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 15 00:11:23 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 15 00:11:23 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Apr 15 00:11:23 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 15 00:11:23 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 15 00:11:23 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 15 00:11:23 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Apr 15 00:11:23 Chertograd NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Apr 15 00:11:23 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Apr 15 00:11:23 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 15 00:11:23 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Apr 15 00:11:23 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Apr 15 00:11:23 Chertograd NetworkManager: <info>  (eth2): supplicant manager state:  down -> idle
Apr 15 00:11:23 Chertograd dhclient: Listening on LPF/eth0/00:26:9e:ef:dc:3b
Apr 15 00:11:23 Chertograd dhclient: Sending on   LPF/eth0/00:26:9e:ef:dc:3b
Apr 15 00:11:23 Chertograd dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 15 00:11:23 Chertograd dhclient: DHCPREQUEST of 192.168.0.8 on eth0 to 255.255.255.255 port 67
Apr 15 00:11:24 Chertograd NetworkManager: <info>  (eth2): device state change: 2 -> 3 (reason 0)
Apr 15 00:11:24 Chertograd NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Apr 15 00:11:24 Chertograd NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Apr 15 00:11:24 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 15 00:11:24 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Apr 15 00:11:24 Chertograd NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 15 00:11:24 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr 15 00:11:24 Chertograd NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr 15 00:11:24 Chertograd avahi-daemon[873]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.8.
Apr 15 00:11:24 Chertograd avahi-daemon[873]: New relevant interface eth0.IPv4 for mDNS.
Apr 15 00:11:24 Chertograd avahi-daemon[873]: Registering new address record for fe80::c617:feff:fe34:c269 on eth2.*.
Apr 15 00:11:24 Chertograd avahi-daemon[873]: Registering new address record for fe80::226:9eff:feef:dc3b on eth0.*.
Apr 15 00:11:24 Chertograd avahi-daemon[873]: Registering new address record for 192.168.0.8 on eth0.IPv4.
Apr 15 00:11:25 Chertograd NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Apr 15 00:11:25 Chertograd NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Apr 15 00:11:25 Chertograd NetworkManager: <info>  Activation (eth0) successful, device activated.
Apr 15 00:11:25 Chertograd NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 15 00:11:25 Chertograd NetworkManager: <info>  (eth2): supplicant interface state:  starting -> ready
Apr 15 00:11:33 Chertograd kernel: [   22.667242] eth2: no IPv6 routers present
Apr 15 00:11:34 Chertograd kernel: [   23.014701] eth0: no IPv6 routers present
Apr 15 10:27:36 Chertograd kernel: [    0.536646] ACPI Error (psparse-0537): Method parse/execution failed [\CPUT] (Node f701ee10), AE_NOT_FOUND
Apr 15 10:27:36 Chertograd kernel: [    0.536681] ACPI Error (psparse-0537): Method parse/execution failed [\PSSC] (Node f701ee28), AE_NOT_FOUND
Apr 15 10:27:36 Chertograd kernel: [    0.536714] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._REG] (Node f7011ed0), AE_NOT_FOUND
Apr 15 10:27:36 Chertograd NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth2, iface: eth2)
Apr 15 10:27:36 Chertograd NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth2, iface: eth2): no ifupdown configuration found.
Apr 15 10:27:36 Chertograd NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0)
Apr 15 10:27:36 Chertograd NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr 15 10:27:36 Chertograd kernel: [    2.547483] eth0: RTL8168d/8111d at 0xf81b6000, 00:26:9e:ef:dc:3b, XID 283000c0 IRQ 35
Apr 15 10:27:36 Chertograd kernel: [   12.541390] eth1: Broadcom BCM4357 802.11 Wireless Controller 5.10.91.9
Apr 15 10:27:36 Chertograd kernel: [   12.545049] udev: renamed network interface eth1 to eth2
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth2): driver supports SSID scans (scan_capa 0x01).
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth2): new 802.11 WiFi device (driver: 'wl')
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth2): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth2): now managed
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth2): device state change: 1 -> 2 (reason 2)
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth2): preparing device.
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth2): deactivating device (reason: 2).
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth0): carrier is OFF
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth0): now managed
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth0): bringing up device.
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth0): preparing device.
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Apr 15 10:27:37 Chertograd NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0
Apr 15 10:27:37 Chertograd kernel: [   12.818081] r8169: eth0: link up
Apr 15 10:27:37 Chertograd kernel: [   12.818101] r8169: eth0: link up
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Apr 15 10:27:37 Chertograd NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Apr 15 10:27:37 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 15 10:27:37 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 15 10:27:37 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 15 10:27:37 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 15 10:27:37 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Apr 15 10:27:37 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 15 10:27:37 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 15 10:27:37 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 15 10:27:37 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Apr 15 10:27:37 Chertograd NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Apr 15 10:27:37 Chertograd avahi-daemon[931]: Registering new address record for fe80::c617:feff:fe34:c269 on eth2.*.
Apr 15 10:27:37 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Apr 15 10:27:37 Chertograd avahi-daemon[931]: Registering new address record for fe80::226:9eff:feef:dc3b on eth0.*.
Apr 15 10:27:37 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 15 10:27:37 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Apr 15 10:27:37 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth2): supplicant manager state:  down -> idle
Apr 15 10:27:37 Chertograd dhclient: Listening on LPF/eth0/00:26:9e:ef:dc:3b
Apr 15 10:27:37 Chertograd dhclient: Sending on   LPF/eth0/00:26:9e:ef:dc:3b
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth2): device state change: 2 -> 3 (reason 0)
Apr 15 10:27:37 Chertograd NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Apr 15 10:27:37 Chertograd NetworkManager: <info>  (eth2): supplicant interface state:  starting -> ready
Apr 15 10:27:39 Chertograd dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr 15 10:27:39 Chertograd dhclient: DHCPREQUEST of 192.168.0.8 on eth0 to 255.255.255.255 port 67
Apr 15 10:27:39 Chertograd NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Apr 15 10:27:39 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 15 10:27:39 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Apr 15 10:27:39 Chertograd NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 15 10:27:39 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr 15 10:27:39 Chertograd NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr 15 10:27:39 Chertograd avahi-daemon[931]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.8.
Apr 15 10:27:39 Chertograd avahi-daemon[931]: New relevant interface eth0.IPv4 for mDNS.
Apr 15 10:27:39 Chertograd avahi-daemon[931]: Registering new address record for 192.168.0.8 on eth0.IPv4.
Apr 15 10:27:40 Chertograd NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Apr 15 10:27:40 Chertograd NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Apr 15 10:27:40 Chertograd NetworkManager: <info>  Activation (eth0) successful, device activated.
Apr 15 10:27:40 Chertograd NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 15 10:27:47 Chertograd kernel: [   22.868388] eth0: no IPv6 routers present
Apr 15 10:27:47 Chertograd kernel: [   23.003462] eth2: no IPv6 routers present
Apr 15 13:23:01 Chertograd NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth2, iface: eth2)
Apr 15 13:23:01 Chertograd kernel: [    0.562565] ACPI Error (psparse-0537): Method parse/execution failed [\CPUT] (Node f701ee10), AE_NOT_FOUND
Apr 15 13:23:01 Chertograd kernel: [    0.562600] ACPI Error (psparse-0537): Method parse/execution failed [\PSSC] (Node f701ee28), AE_NOT_FOUND
Apr 15 13:23:01 Chertograd kernel: [    0.562633] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._REG] (Node f7011ed0), AE_NOT_FOUND
Apr 15 13:23:01 Chertograd NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth2, iface: eth2): no ifupdown configuration found.
Apr 15 13:23:02 Chertograd NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0)
Apr 15 13:23:02 Chertograd NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr 15 13:23:02 Chertograd kernel: [    2.516317] eth0: RTL8168d/8111d at 0xf81a2000, 00:26:9e:ef:dc:3b, XID 283000c0 IRQ 35
Apr 15 13:23:02 Chertograd kernel: [   11.962380] eth1: Broadcom BCM4357 802.11 Wireless Controller 5.10.91.9
Apr 15 13:23:02 Chertograd kernel: [   11.966334] udev: renamed network interface eth1 to eth2
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth2): driver supports SSID scans (scan_capa 0x01).
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth2): new 802.11 WiFi device (driver: 'wl')
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth2): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth2): now managed
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth2): device state change: 1 -> 2 (reason 2)
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth2): preparing device.
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth2): deactivating device (reason: 2).
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth0): carrier is OFF
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth0): now managed
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth0): bringing up device.
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth0): preparing device.
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Apr 15 13:23:02 Chertograd NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0
Apr 15 13:23:02 Chertograd kernel: [   12.883907] r8169: eth0: link up
Apr 15 13:23:02 Chertograd kernel: [   12.883923] r8169: eth0: link up
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Apr 15 13:23:02 Chertograd NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Apr 15 13:23:02 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 15 13:23:02 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 15 13:23:02 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 15 13:23:02 Chertograd NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 15 13:23:02 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Apr 15 13:23:02 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 15 13:23:02 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 15 13:23:02 Chertograd NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 15 13:23:02 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Apr 15 13:23:02 Chertograd NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Apr 15 13:23:02 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Apr 15 13:23:02 Chertograd NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 15 13:23:02 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Apr 15 13:23:02 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Apr 15 13:23:02 Chertograd NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth2): supplicant manager state:  down -> idle
Apr 15 13:23:02 Chertograd dhclient: Listening on LPF/eth0/00:26:9e:ef:dc:3b
Apr 15 13:23:02 Chertograd dhclient: Sending on   LPF/eth0/00:26:9e:ef:dc:3b
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth2): device state change: 2 -> 3 (reason 0)
Apr 15 13:23:02 Chertograd avahi-daemon[998]: Registering new address record for fe80::c617:feff:fe34:c269 on eth2.*.
Apr 15 13:23:02 Chertograd avahi-daemon[998]: Registering new address record for fe80::226:9eff:feef:dc3b on eth0.*.
Apr 15 13:23:02 Chertograd NetworkManager: <info>  (eth2): supplicant interface state:  starting -> ready
Apr 15 13:23:06 Chertograd dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 15 13:23:06 Chertograd dhclient: DHCPREQUEST of 192.168.0.8 on eth0 to 255.255.255.255 port 67
Apr 15 13:23:06 Chertograd NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Apr 15 13:23:06 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 15 13:23:06 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Apr 15 13:23:06 Chertograd NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 15 13:23:06 Chertograd NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr 15 13:23:06 Chertograd NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr 15 13:23:06 Chertograd avahi-daemon[998]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.8.
Apr 15 13:23:06 Chertograd avahi-daemon[998]: New relevant interface eth0.IPv4 for mDNS.
Apr 15 13:23:06 Chertograd avahi-daemon[998]: Registering new address record for 192.168.0.8 on eth0.IPv4.
Apr 15 13:23:07 Chertograd NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Apr 15 13:23:07 Chertograd NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Apr 15 13:23:07 Chertograd NetworkManager: <info>  Activation (eth0) successful, device activated.
Apr 15 13:23:07 Chertograd NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr 15 13:23:12 Chertograd kernel: [   23.085031] eth0: no IPv6 routers present
Apr 15 13:23:12 Chertograd kernel: [   23.364380] eth2: no IPv6 routers present

```

```
~ $ sudo iwpriv eth2
eth2      Available private ioctls :
          set_leddc        (8BE0) : set   1 int   & get   0      
          set_vlanmode     (8BE1) : set   1 int   & get   0      
          set_pm           (8BE2) : set   1 int   & get   0    
```

The hub supports multiple speeds. We've had a wireless-G laptop on the network before.

---

### Post by chili555 on 2010-04-15
Does scanning work with the ethernet cable detached? What kind of computer is it? May I see:```
lsmod
```Thanks.

---

### Post by ayvah on 2010-04-15
Whether or not I have the lan cable plugged in, it doesn't make any difference.

```
~ $ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
dm_crypt               12928  0 
snd_hda_codec_idt      59876  1 
lib80211_crypt_tkip     8636  0 
snd_hda_intel          26920  1 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
wl                   1272936  0 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
nvidia               9586440  40 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
lib80211                6432  2 lib80211_crypt_tkip,wl
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3100  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
jmb38x_ms               9600  0 
uvcvideo               59080  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
joydev                 10240  0 
snd                    59204  14 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               36736  1 uvcvideo
v4l1_compat            14336  2 uvcvideo,videodev
memstick               10072  1 jmb38x_ms
sdhci_pci               7100  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lirc_ene0100            8096  0 
lirc_dev               10804  1 lirc_ene0100
hp_accel               11228  0 
lis3lv02d               7452  1 hp_accel
input_polldev           3716  1 lis3lv02d
psmouse                56500  0 
sdhci                  17504  1 sdhci_pci
lp                      8964  0 
serio_raw               5280  0 
parport                35340  2 ppdev,lp
led_class               4096  2 hp_accel,sdhci
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
video                  19380  0 
output                  2780  1 video
r8169                  32064  0 
mii                     5212  1 r8169
intel_agp              27676  0 
agpgart                34988  2 nvidia,intel_agp
```

---

