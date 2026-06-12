---
title: "Trouble getting D-Link DWA-548 PCIe Wi-Fi card working!"
date: 2012-10-16
forum: Networking &amp; Wireless
---

### Post by LinuxFanBoi on 2012-10-16
I have a Custom Desktop PC with onboard lan (working) and a D-Link DWA-548 PCIe wi-Fi card  that doesn't work and has no proprietary driver shown in  the additional drivers tool.

I have attempted to use ndiswrapper using the supplied windows 7 driver disk.  It seems like ndiswrapper is accepting the driver, however I still have no wireless capabilities in Network-manager

ndiswrapper -l shows the following responce:

```
chris@Nebuchadnezzar:~$ ndiswrapper -l
dnetr28x : driver installed
	device (1814:5392) present
```

lshw -C network gives the following:

```
chris@Nebuchadnezzar:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 13
       serial: 00:50:8d:b2:e5:cb
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full firmware=N/A ip=192.168.0.193 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:fddfc000-fddfffff ioport:8e00(size=256) memory:fdc00000-fdc1ffff
  *-network UNCLAIMED
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fdbf0000-fdbfffff
```

nm-tool returns:

```
chris@Nebuchadnezzar:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:50:8D:B2:E5:CB

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.193
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

```


lspci returns:

```
chris@Nebuchadnezzar:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce GTS 250] (rev a2)
03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 13)
05:00.0 Network controller: Ralink corp. Device 5392

```

---

### Post by LinuxFanBoi on 2012-10-16
update.  it seems I've gotten the driver compiled and loaded, but I still dont have wireless available in network-manager.  I do have some more outputs to share if it helps. 

lshw -C network now returns:

```
chris@Nebuchadnezzar:/etc/modprobe.d$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 13
       serial: 00:50:8d:b2:e5:cb
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full firmware=N/A ip=192.168.0.193 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:fddfc000-fddfffff ioport:8e00(size=256) memory:fdc00000-fdc1ffff
  *-network
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=rt2860 latency=0
       resources: irq:19 memory:fdbf0000-fdbfffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 90:94:e4:02:23:b6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN multicast=yes wireless=Ralink STA

```

iwconfig though returns:

```
chris@Nebuchadnezzar:/etc/modprobe.d$ iwconfig
lo        no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```

ifconfig now return:

```
chris@Nebuchadnezzar:/etc/modprobe.d$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8d:b2:e5:cb  
          inet addr:192.168.0.193  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:feb2:e5cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2749 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2347792 (2.3 MB)  TX bytes:377219 (377.2 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:530 errors:0 dropped:0 overruns:0 frame:0
          TX packets:530 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:95816 (95.8 KB)  TX bytes:95816 (95.8 KB)

ra0       Link encap:Ethernet  HWaddr 90:94:e4:02:23:b6  
          inet6 addr: fe80::9294:e4ff:fe02:23b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6598 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1669809 (1.6 MB)  TX bytes:0 (0.0 B)
          Interrupt:19 


```

---

### Post by chili555 on 2012-10-16
ndiswrapper requires the Windows *XP* driver, not 7 or 3.1 or otherwise. That's why ndiswrapper isn't working for you. I suggest you delete everything:```
sudo rm -rf /etc/ndiswrapper/*
```There may be a declaration in /etc/modprobe.d to load ndiswrapper automatically. Check for it:```
ls /etc/modprobe.d
```If you see any ndiswrapper files, remove them:```
sudo rm /etc/modprobe.d/[COLOR="Red"]whateveryoufind[/COLOR]
```If in doubt, stop and ask.

I assume you have the downloaded file on your Desktop. Right-click it and select 'extract here.' It is handily a bz2.bz2 file, so you may have to 'extract here' a couple of times. Good work, Realtek! Now open a terminal and do:```
sudo apt-get install linux-headers-generic
```Open the file os/linux/config.mk with a text editor and change:```
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[COLOR="Red"]y[/COLOR]
```Proofread, save and close the text editor. Now back to the terminal:```
cd Desktop/2011
```Press Tab and the rest will fill in automagically. Press Enter.```
sudo su
make
make install
modprobe rt5390sta
echo rt5390sta >> /etc/modules
exit
```Your wireless should now be working.

---

### Post by LinuxFanBoi on 2012-10-16
Found a ndiswrapper.conf file in the folder you mention, removed it, followed your instructions and all is right in the world again.

Thank you so much!

---

### Post by chili555 on 2012-10-16
Awesome! Whenever Update Manager delivers a new kernel version, you'll need to recompile:```
cd Desktop/2011

```
Press Tab and the rest will fill in automagically. Press Enter.
```
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe rt5390sta
exit

```Please use thread tools at the top to mark Solved; the searchers will appreciate it.

---

### Post by LinuxFanBoi on 2012-10-17
Confirmed!  Got a new kernel version just now and recompile also worked flawlessly.  Thank you!

---

