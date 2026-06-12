---
title: "WG111v2 Ubuntu 5.1"
date: 2006-02-27
forum: Networking &amp; Wireless
---

### Post by Eyebolt on 2006-02-27
So I used ndisgtk and install the xp drivers of my cd. Works fine.
Use the network settings to configure my network on my wlan0.

Then all that happens is the little blue light on the adapter blinks a few seconds...is off a few seconds and blinks again over and over. I got this USB dongle because I thought it was prism54 and easy...I'm not finding so. Any help would be great.

---

### Post by Lambert on 2006-02-27
Open a terminal and post the output of these commands here:

sudo lshw -C network
iwconfig
ifconfig

What happens if you run these commands?

sudo ifconfig wlan0 down && sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid ______
sudo dhclient wlan0

What kind of network configuration are you runnign? encrypted or not? if encrypted basic settings?

---

### Post by Eyebolt on 2006-02-28
I'll try out those commmand when I get home during lunch, thanks for your help. My network is set up with 128 bit WEP.

---

### Post by Eyebolt on 2006-02-28
So I ran those first 3 commands...the first time I ran them was with the 128 bit WEP enabled on my router, and the second was after I changed the connection settings in the network settings and turned off WEP. It works with WEP turned off, but not with it on.

ike@mythbox:~$ sudo lshw -C network
  *-network DISABLED
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 78
       serial: 00:15:f2:71:5d:16
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=full link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:b000-b0ff iomemory:fac00000-fac000ff irq:23
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0f:b5:d4:56:98
       capabilities: ethernet physical wireless
       configuration: broadcast=yes link=no multicast=yes wireless=IEEE 802.11g
ike@mythbox:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2346 B   Fragment thr:2400 B
          Power Management:off
          Link Quality:100/100  Signal level:-50 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ike@mythbox:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:294801 (287.8 KiB)  TX bytes:294801 (287.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:D4:56:98
          inet6 addr: fe80::20f:b5ff:fed4:5698/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

WITH WEP DISABLED ON ROUTER:

ike@mythbox:~$ sudo lshw -C network
  *-network DISABLED
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 78
       serial: 00:15:f2:71:5d:16
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=full link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:b000-b0ff iomemory:fac00000-fac000ff irq:23
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0f:b5:d4:56:98
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11g
ike@mythbox:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"MyESSID"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:10:34:2F:9F
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2346 B   Fragment thr:2400 B
          Power Management:off
          Link Quality:100/100  Signal level:-49 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ike@mythbox:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5050 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5050 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:393439 (384.2 KiB)  TX bytes:393439 (384.2 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:D4:56:98
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fed4:5698/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:12981 (12.6 KiB)  TX bytes:5922 (5.7 KiB)

---

