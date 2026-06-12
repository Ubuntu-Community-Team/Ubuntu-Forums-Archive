---
title: "Lost connections in eeepc netbook"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by vilunki on 2011-01-02
Hi,

posted this as a reply to another thread, now again as a new thread:

Lost wired&wireless conections in eeepc 1001px with 10.10 netbook edition, which used to work.

Wireless keeps asking password
Wired is disconnected and doesn't connect

PatchesTheCaveman asked some information, it's attached as a .txt-file, because I don't know how to copy and paste in this Mac I'm using now.

Thanks

---

### Post by PatchesTheCaveman on 2011-01-02
Alright, lets start with your wired adapter, cause that's probably going to be easier.  Make sure its plugged in, and run this command:
```
sudo dhclient eth0
```

If it still doesn't work after that, copy/paste or attach a text file with the output.

Does the wireless connect and then ask for the password later, then reconnect and work again for a little while, or does it just keep asking for the password and never works?

---

### Post by vilunki on 2011-01-03
Hi,

this is what I get after sudo dhclient eth0

> Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/20:cf:30:5e:7f:fc
Sending on   LPF/eth0/20:cf:30:5e:7f:fc
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.102 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.102 from 192.168.0.1
bound to 192.168.0.102 -- renewal in 246225 seconds.

Wireless shows all available networks and contacts automatically the one I'm trying (and have tried) to use, asks password and after typing that tries to establish a connection. Then after a while (about one minute) instead of establishing connection the box inquiring password appears again. Connection never works.

Thanks

---

### Post by PatchesTheCaveman on 2011-01-03
That means your wired network connection should be working.  NetworkManager (the network icon) might not be reporting as such for some reason. 

Try pinging your router:
```
ping 192.168.0.1
```

If that works, try pinging out to the Internet:
```
ping google.com
```

If you've rebooted, you might need to rerun that dhclient command to get back on.  If those commands work, you can try replacing NetworkManger with wicd, another program that drives a network icon but works better for some people.  To install that, run these commands:
```
sudo apt-get update
sudo apt-get remove network-manager
sudo apt-get install wicd
```

As for your wireless, I'll need you to copy/paste the result of these commands to see what's going on:
```
lspci -v
lshw -C network
sudo iwconfig
ifconfig -a
```

---

### Post by vilunki on 2011-01-04
Hi PatchesTheCaveman,

now got this wired connection working, but need to run dhclient in terminal in order to do so.

Removed network manager, but some failure in getting wicd running, see here:

```
inkeri@inkeri-1001PX:~$ sudo apt-get install wicd 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
The following packages were automatically installed and are no longer required: 
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic 
Use 'apt-get autoremove' to remove them. 
The following extra packages will be installed: 
  python-iniparse python-wicd wicd-daemon wicd-gtk 
The following NEW packages will be installed: 
  python-iniparse python-wicd wicd wicd-daemon wicd-gtk 
0 upgraded, 5 newly installed, 0 to remove and 7 not upgraded. 
Need to get 562kB of archives. 
After this operation, 3,121kB of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Get:1 http://fi.archive.ubuntu.com/ubuntu/ maverick/universe python-wicd all 1.7.0+ds1-5 [76.8kB] 
Get:2 http://fi.archive.ubuntu.com/ubuntu/ maverick/main python-iniparse all 0.3.2-1 [19.8kB] 
Get:3 http://fi.archive.ubuntu.com/ubuntu/ maverick/universe wicd-daemon all 1.7.0+ds1-5 [277kB] 
Get:4 http://fi.archive.ubuntu.com/ubuntu/ maverick/universe wicd-gtk all 1.7.0+ds1-5 [147kB] 
Get:5 http://fi.archive.ubuntu.com/ubuntu/ maverick/universe wicd all 1.7.0+ds1-5 [41.0kB] 
Fetched 562kB in 2s (210kB/s) 
Preconfiguring packages ... 
Selecting previously deselected package python-wicd. 
(Reading database ... 167859 files and directories currently installed.) 
Unpacking python-wicd (from .../python-wicd_1.7.0+ds1-5_all.deb) ... 
Selecting previously deselected package python-iniparse. 
Unpacking python-iniparse (from .../python-iniparse_0.3.2-1_all.deb) ... 
Selecting previously deselected package wicd-daemon. 
Unpacking wicd-daemon (from .../wicd-daemon_1.7.0+ds1-5_all.deb) ... 
Selecting previously deselected package wicd-gtk. 
Unpacking wicd-gtk (from .../wicd-gtk_1.7.0+ds1-5_all.deb) ... 
Selecting previously deselected package wicd. 
Unpacking wicd (from .../wicd_1.7.0+ds1-5_all.deb) ... 
Processing triggers for ureadahead ... 
Processing triggers for man-db ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for python-support ... 
Setting up python-wicd (1.7.0+ds1-5) ... 
Setting up python-iniparse (0.3.2-1) ... 
Setting up wicd-daemon (1.7.0+ds1-5) ... 
 * Starting Network connection manager wicd                                                                    [fail]  
Setting up wicd-gtk (1.7.0+ds1-5) ... 
Setting up wicd (1.7.0+ds1-5) ... 
Processing triggers for python-support ... 
inkeri@inkeri-1001PX:~$ wicd 
Root privileges are required for the daemon to run properly.  Exiting. 
inkeri@inkeri-1001PX:~$  
```And here's the output for the code you asked for:
```

inkeri@inkeri-1001PX:~$ lspci -v 
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge 
    Subsystem: ASUSTeK Computer Inc. Device 83ac 
    Flags: bus master, fast devsel, latency 0 
    Capabilities: <access denied> 
    Kernel driver in use: agpgart-intel 
    Kernel modules: intel-agp 
 
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (prog-if 00 [VGA controller]) 
    Subsystem: ASUSTeK Computer Inc. Device 83ac 
    Flags: bus master, fast devsel, latency 0, IRQ 44 
    Memory at f7e00000 (32-bit, non-prefetchable) [size=512K] 
    I/O ports at dc00 [size=8] 
    Memory at d0000000 (32-bit, prefetchable) [size=256M] 
    Memory at f7d00000 (32-bit, non-prefetchable) [size=1M] 
    Expansion ROM at <unassigned> [disabled] 
    Capabilities: <access denied> 
    Kernel driver in use: i915 
    Kernel modules: i915 
 
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller 
    Subsystem: ASUSTeK Computer Inc. Device 83ac 
    Flags: bus master, fast devsel, latency 0 
    Memory at f7e80000 (32-bit, non-prefetchable) [size=512K] 
    Capabilities: <access denied> 
 
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02) 
    Subsystem: ASUSTeK Computer Inc. Device 8437 
    Flags: bus master, fast devsel, latency 0, IRQ 46 
    Memory at f7cf8000 (64-bit, non-prefetchable) [size=16K] 
    Capabilities: <access denied> 
    Kernel driver in use: HDA Intel 
    Kernel modules: snd-hda-intel 
 
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode]) 
    Flags: bus master, fast devsel, latency 0 
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0 
    I/O behind bridge: 00001000-00001fff 
    Memory behind bridge: 3f700000-3f8fffff 
    Prefetchable memory behind bridge: 000000003f900000-000000003fafffff 
    Capabilities: <access denied> 
    Kernel driver in use: pcieport 
    Kernel modules: shpchp 
 
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode]) 
    Flags: bus master, fast devsel, latency 0 
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0 
    I/O behind bridge: 00002000-00002fff 
    Memory behind bridge: f8000000-fbffffff 
    Prefetchable memory behind bridge: 00000000f0000000-00000000f6ffffff 
    Capabilities: <access denied> 
    Kernel driver in use: pcieport 
    Kernel modules: shpchp 
 
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode]) 
    Flags: bus master, fast devsel, latency 0 
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0 
    I/O behind bridge: 0000e000-0000efff 
    Memory behind bridge: f7f00000-f7ffffff 
    Prefetchable memory behind bridge: 000000003fb00000-000000003fcfffff 
    Capabilities: <access denied> 
    Kernel driver in use: pcieport 
    Kernel modules: shpchp 
 
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI]) 
    Subsystem: ASUSTeK Computer Inc. Device 83ad 
    Flags: bus master, medium devsel, latency 0, IRQ 23 
    I/O ports at d400 [size=32] 
    Kernel driver in use: uhci_hcd 
 
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI]) 
    Subsystem: ASUSTeK Computer Inc. Device 83ad 
    Flags: bus master, medium devsel, latency 0, IRQ 19 
    I/O ports at d480 [size=32] 
    Kernel driver in use: uhci_hcd 
 
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI]) 
    Subsystem: ASUSTeK Computer Inc. Device 83ad 
    Flags: bus master, medium devsel, latency 0, IRQ 18 
    I/O ports at d800 [size=32] 
    Kernel driver in use: uhci_hcd 
 
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI]) 
    Subsystem: ASUSTeK Computer Inc. Device 83ad 
    Flags: bus master, medium devsel, latency 0, IRQ 16 
    I/O ports at d880 [size=32] 
    Kernel driver in use: uhci_hcd 
 
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI]) 
    Subsystem: ASUSTeK Computer Inc. Device 83ad 
    Flags: bus master, medium devsel, latency 0, IRQ 23 
    Memory at f7cf7c00 (32-bit, non-prefetchable) [size=1K] 
    Capabilities: <access denied> 
    Kernel driver in use: ehci_hcd 
 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode]) 
    Flags: bus master, fast devsel, latency 0 
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32 
    Capabilities: <access denied> 
 
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02) 
    Subsystem: ASUSTeK Computer Inc. Device 83ad 
    Flags: bus master, medium devsel, latency 0 
    Capabilities: <access denied> 
 
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0]) 
    Subsystem: ASUSTeK Computer Inc. Device 83ad 
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43 
    I/O ports at d080 [size=8] 
    I/O ports at d000 [size=4] 
    I/O ports at cc00 [size=8] 
    I/O ports at c880 [size=4] 
    I/O ports at c800 [size=32] 
    Memory at f7cf7800 (32-bit, non-prefetchable) [size=1K] 
    Capabilities: <access denied> 
    Kernel driver in use: ahci 
    Kernel modules: ahci 
 
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02) 
    Subsystem: ASUSTeK Computer Inc. Device 83ad 
    Flags: medium devsel, IRQ 11 
    I/O ports at 0400 [size=32] 
    Kernel modules: i2c-i801 
 
01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0) 
    Subsystem: ASUSTeK Computer Inc. Device 838a 
    Flags: bus master, fast devsel, latency 0, IRQ 45 
    Memory at f7fc0000 (64-bit, non-prefetchable) [size=256K] 
    I/O ports at ec00 [size=128] 
    Capabilities: <access denied> 
    Kernel driver in use: atl1c 
    Kernel modules: atl1c 
 
02:00.0 Network controller: Atheros Communications Inc. AR2427 Wireless Network Adapter (PCI-Express) (rev 01) 
    Subsystem: Device 1a3b:1112 
    Flags: bus master, fast devsel, latency 0, IRQ 17 
    Memory at fbff0000 (64-bit, non-prefetchable) [size=64K] 
    Capabilities: <access denied> 
    Kernel driver in use: ath9k 
    Kernel modules: ath9k 
 
inkeri@inkeri-1001PX:~$ lshw -C network 
WARNING: you should run this program as super-user. 
PCI (sysfs)   
 
  *-network DISABLED       
       description: Wireless interface 
       product: AR2427 Wireless Network Adapter (PCI-Express) 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: wlan0 
       version: 01 
       serial: 74:f0:6d:22:72:16 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-24-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bg 
       resources: irq:17 memory:fbff0000-fbffffff 
  *-network 
       description: Ethernet interface 
       product: AR8132 Fast Ethernet 
       vendor: Atheros Communications 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       logical name: eth0 
       version: c0 
       serial: 20:cf:30:5e:7f:fc 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A ip=192.168.0.102 latency=0 multicast=yes 
       resources: irq:45 memory:f7fc0000-f7ffffff ioport:ec00(size=128) 
 
inkeri@inkeri-1001PX:~$ sudo iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11bg  ESSID:off/any   
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated    
          Tx-Power=20 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Encryption key:off 
          Power Management:off 
           
inkeri@inkeri-1001PX:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 20:cf:30:5e:7f:fc   
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::22cf:30ff:fe5e:7ffc/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:1454 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1144 errors:0 dropped:0 overruns:0 carrier:1 
          collisions:0 txqueuelen:1000  
          RX bytes:1358755 (1.3 MB)  TX bytes:138342 (138.3 KB) 
          Interrupt:45  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B) 
 
wlan0     Link encap:Ethernet  HWaddr 74:f0:6d:22:72:16   
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:6215 (6.2 KB)  TX bytes:11513 (11.5 KB) 
```And btw, how do I stop pinging in terminal?

Thank you.

---

### Post by vilunki on 2011-01-04
Hello again,

now got wicd running and connects automatically when plugging in network cable. Wireless doesn't connect, but probably because of wrong password? Hard to say, because don't get any other password from the owner.

Thank you PatchesTheCaveman. I think this is it at the moment about this case.

---

