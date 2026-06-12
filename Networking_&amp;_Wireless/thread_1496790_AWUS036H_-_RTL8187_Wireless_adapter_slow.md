---
title: "AWUS036H - RTL8187 Wireless adapter slow"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by Fireking300 on 2010-05-29
Hello, I love Ubuntu but only 1 problem so lets get started.

This is wireless adapter: [http://www.data-alliance.net/-strse-73/Alfa-AWUS036H-1000mW-USB/Detail.bok](http://www.data-alliance.net/-strse-73/Alfa-AWUS036H-1000mW-USB/Detail.bok)
I have 2 AWUS036H Wireless USB adapter that uses the RTL8187 Chipset connected to a USB 2.0 Port.
It is very slow when I try to go to websites or download anything using Ubuntu 10.04 Lucid Lynx.
The max speed I can get out of it is 135 Kilobytes per second when downloading anything.
But when I am on Windows I can max out 2.6 Megabytes per second.

I have been trying to find a solution but have found none.
When I look at the light on the wireless adapter and compare it to what it looks like on both Ubuntu and Windows. It seems that the wireless adapter light is dimmer on Ubuntu. So I was thinking it was txpower set very low. I changed it but no success on changing speed.
I am using WPA2-PSK which obviously uses AES. I have also tested it while it is in WEP and when it is Open with no change in speed.

Speed results Ubuntu 10.04:
[[IMG]http://www.speedtest.net/result/830289016.png[/IMG]](http://www.speedtest.net)
Speed results Windows 7:
[[IMG]http://www.speedtest.net/result/830290066.png[/IMG]](http://www.speedtest.net)

I changed the settings to Megabytes on those speed results.

iwconfig results:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"MYWIFI"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:23:9C:4A:0D:A3   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lspci
```

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567V-2 Gigabit Network Connection
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403

```
lsusb
```

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0461:4d64 Primax Electronics, Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 003: ID 0a48:4001 I/O Interconnect 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
lshw
```

fireking300@fireking300-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82567V-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 00
       serial: 00:25:11:5a:bd:ea
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.8-5 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:26 memory:feac0000-feadffff memory:feafb000-feafbfff ioport:d880(size=32)
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:c0:ca:3a:9e:7a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netrtuw driverversion=1.55+Realtek Semiconductor Corp. ip=192.168.0.13 link=yes multicast=yes wireless=IEEE 802.11g


```
So any help is appreciated. Thank You.

---

### Post by Fireking300 on 2010-05-31
bump

---

### Post by elclanrs on 2010-05-31
The module for this driver is screwed! I tried literally everything to make it work full speed but nothing. Ndsiwrapper driver doesn't work on 64bit, even tough there's a 64bit driver on windows, I didn't try 32bit...

I'm on Arch now and it's better, I can get full speed but it keeps dropping to like 5kb/s for some minutes then it goes up to full speed again, so really unstable.
The best distro I tried is PCLinuxOS, it works pretty well, it dropss too but less than on arch.

The worst distro of all for this chipstet is Ubuntu and Ubuntu based distros, it simply doesn't work full speed.

Just give up and buy another adapter, it's not worth it to spend time on trying to fix it because it won't work well, trust me, It's been 2 weeks trying to solve it and nothing...

I bought a Mini PCI to PCI adapter for 5$ on ebay so I can use my b43 Mini PCI card that I know it works great on linux. That's the solution I came up with.

---

### Post by htrex on 2010-06-13
I'm on lucid 64bit using an AWUS036H v2 (1000mW) and it worked out of the box!

By default the device tx power is limited to 20dB (100mW), but if you're on a country that allows more power you can just set it using

```

sudo iw reg set BO

```

"BO" is for Bolivia, and it allows up to 30dB (1000mW) for the V2 and 27dB (500mW) for V1 I guess.

Anyway, to have a stable connection is sometimes usefull to limit the max transmission rate:

```

sudo iwconfig wlan1 rate 11M auto

```

this means up to 11Mb, try with 1M or 2M for very low signals.

---

