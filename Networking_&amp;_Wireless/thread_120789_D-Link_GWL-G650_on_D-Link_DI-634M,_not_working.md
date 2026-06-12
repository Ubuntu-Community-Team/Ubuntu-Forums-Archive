---
title: "D-Link GWL-G650 on D-Link DI-634M, not working"
date: 2006-01-23
forum: Networking &amp; Wireless
---

### Post by Lambert on 2006-01-23
Also post the output of iwconfig here.

What kind of key are you using? hexadecimal or passphrase?

Do you know if there are multiple key settings and if so what key is being used?

Add a line
wireless-mode managed

also try adding - in the key every 4 characters

xxxx-xxxx-xx

Have you tried configuring from command line


sudo iwconfig ath0 mode managed key restricted xxxxxxx essid xxxxxx

---

### Post by blitz666 on 2006-01-23
Using a Hex key.

Added the line, no difference noticed.

The command has no effect it seems.

sudo iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11  ESSID:"XX XXXXXX XXXXXXX"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:0614-1982-03   Security mode:restricted
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

---

### Post by blitz666 on 2006-01-23
I noticed it said signal strength 0... I moved closer so it said somewhere in the range of 50...

it actually connected for a short time, yet, I could not access network, nor internet (despite it telling me I was connected).

---

### Post by blitz666 on 2006-01-23
I have been trying to get my laptop to see my router for the past 8 hours now... still to no avail.  I have tried several of the HowTo's offered here, none seem to work.

Can someone help me please?  I am new to Linux still, so try to take it slow.

sudo iwlist ath0 scan```
ath0      Scan completed :
          Cell 01 - Address: 00:13:46:D0:65:65
                    ESSID:"XX XXXXXX XXXXXXX"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/94  Signal level=-77 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
```
sudo lshw -C network```
  *-network
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:11
  *-network
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 00
       serial: 00:0d:9d:83:45:41
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10b t-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=natsemi driververs ion=1.07+LK1.0.17 duplex=full ip=192.168.0.110 link=yes multicast=yes port=twist ed pair speed=100MB/s
       resources: ioport:8c00-8cff iomemory:d0004000-d0004fff irq:11
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@02:00.0
       logical name: ath0
       version: 01
       serial: 00:0d:88:a5:09:71
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERI MENTAL) multicast=yes wireless=IEEE 802.11g
       resources: iomemory:38000000-3800ffff irq:11
```
lspci -v | grep Eth```
0000:00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (Ma cPhyter) Ethernet Controller
0000:02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```
sudo gedit /etc/network/interfaces```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0
	map ath0

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The wireless network interface
iface ath0 inet dhcp
pre-up iwpriv ath0 authmode 2
post-up route add default gw 192.168.0.1
wireless-essid "XX XXXXXX XXXXXXX"
wireless-key restricted "XXXXXXXXXX"
auto ath0
```
sudo route```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```
ifconfig```
ath0      Link encap:Ethernet  HWaddr 00:0D:88:A5:09:71
          inet6 addr: fe80::20d:88ff:fea5:971/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:3196 dropped:0 overruns:0 frame:3196
          TX packets:0 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:f8bc0000-f8bd0000

eth0      Link encap:Ethernet  HWaddr 00:0D:9D:83:45:41
          inet addr:192.168.0.110  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:9dff:fe83:4541/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:483 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:580084 (566.4 KiB)  TX bytes:66095 (64.5 KiB)
          Interrupt:11 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2924 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2924 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:266228 (259.9 KiB)  TX bytes:266228 (259.9 KiB)
```
sudo iwpriv ath0 get_authmode```
ath0      get_authmode:2
```

I think that is everything you might need to help me... let me know if you need anything else.  I had tried ndiswrapper-utils with the newest drivers from D-link (excluding the beta, thus, version 2.54, Hardware version B) and it didn't seem to help anything, so I removed it.  I had also tried WiFi-Radar, to a similar effect.

Oh, I know the router works, works on both of my PCs on Winboot mode.  The router also works from Linux in wired mode, just not wireless.

WEP must be enabled (network-admin's orders) as does Shared access mode, so disabling either of those aren't really options.

---

