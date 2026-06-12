---
title: "No ethernet on Dell Inspiron 6400"
date: 2013-01-17
forum: Networking &amp; Wireless
---

### Post by Cyril4133 on 2013-01-17
Hi,

I cannot make my ethernet work though wireless works perfectly.

```
ifconfig -v
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:105357 (105.3 KB)  TX bytes:105357 (105.3 KB)

wlan1     Link encap:Ethernet  HWaddr 00:19:d2:3c:a4:68  
          inet addr:128.179.145.49  Bcast:128.179.151.255  Mask:255.255.248.0
          inet6 addr: fe80::219:d2ff:fe3c:a468/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:91927 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49037 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:126577157 (126.5 MB)  TX bytes:4865322 (4.8 MB)

```

```
lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Dell Device 01bd
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: efd00000-efefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
	Subsystem: Dell Device 01bd
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: efc00000-efcfffff
	Prefetchable memory behind bridge: 0000000040000000-00000000401fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: efa00000-efbfffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000e01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at bf80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at bf60 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at bf40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at bf20 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Dell Device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at ffa80000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
	Subsystem: Dell Device 01bd
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: lpc_ich
	Kernel modules: leds-ss4200, lpc_ich, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 01) (prog-if 80 [Master])
	Subsystem: Dell Device 01bd
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
	Subsystem: Dell Device 01bd
	Flags: medium devsel, IRQ 5
	I/O ports at 10c0 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI M52 [Mobility Radeon X1300] (prog-if 00 [VGA controller])
	Subsystem: Dell Device 2003
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at ee00 [size=256]
	Memory at efdf0000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at efd00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon

0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1021
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at efcff000 (32-bit, non-prefetchable) [size=4K]
	**Capabilities: <access denied>**
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945


```

```
 cat /proc/version
Linux version 3.5.0-21-generic (buildd@roseapple) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #32-Ubuntu SMP Tue Dec 11 18:52:46 UTC 2012

```

Thank for any help,

Cyril

---

### Post by cogier on 2013-01-17
You need to be more explicit. Ethernet is wired. Wireless is not.

If you can provide a little more detail of the problem I am sure you will get some help.

---

### Post by Cyril4133 on 2013-01-24
Wifi work but there is no interfaces associated with a wired connection: the only interface of ifconfig is wlan1. So that nothing happen when I plug the rj45.

---

### Post by prodigy_ on 2013-01-24
Can you post the output of ```
cat /proc/net/dev
``` and ```
lshw -C network
```?

So far it seems that your wired adapter is not being recognized at all (it's not in the **lspci** output). Are you sure it's turned on in BIOS?

---

### Post by Cyril4133 on 2013-01-24
```
cat /proc/net/dev
Inter-|   Receive                                                |  Transmit
 face |bytes    packets errs drop fifo frame compressed multicast|bytes    packets errs drop fifo colls carrier compressed
    lo:  324344    3187    0    0    0     0          0         0   324344    3187    0    0    0     0       0          0
 wlan1: 106330343  143992    0    0    0     0          0         0  8896750   72600    0    0    0     0       0          0

```

```
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan1
       version: 02
       serial: 00:19:d2:3c:a4:68
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.5.0-21-generic firmware=15.32.2.9 ip=128.179.147.174 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:efcff000-efcfffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

---

### Post by prodigy_ on 2013-01-24
Looks like a driver or hardware issue. Try: ```
dmesg | grep -i eth0
```

---

### Post by mudguts on 2013-01-24
I have the exact SAME issue on a Dell e6400 and Dell e4300.
It just started happening in November but was working perfectly in Oct..
bizzare.

my lshow -class network returned:
 mike@mike-Latitude-E4300:~$ sudo lshw -class network
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:f9:69:aa
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=1.7-7 ip=192.168.1.114 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:f6ae0000-f6afffff memory:f6adb000-f6adbfff ioport:efe0(size=32)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       physical id: 2
       bus info: usb@2:4
       logical name: eth1
       serial: 52:ea:d6:11:1f:e2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth link=no multicast=yes

---

### Post by mudguts on 2013-01-24
how do you reply back with the boxes of your output?

on cat /proc/net/dev
I get:

[SIZE="1"]mike@mike-Latitude-E4300:~$ cat /proc/net/dev
Inter-|   Receive                                                |  Transmit
 face |bytes    packets errs drop fifo frame compressed multicast|bytes    packets errs drop fifo colls carrier compressed
  eth0: 20380723   31122    0    0    0     0          0      1190  1894742   16131    0    0    0     0       0          0
  eth1:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0
    lo:  169667    1221    0    0    0     0          0         0   169667    1221    0    0    0     0       0          0[/SIZE]

---

### Post by prodigy_ on 2013-01-24
**mudguts**, I can clearly see **eth0** and **eth1** in the output. So what do you mean by saying "exact same issue"?

---

### Post by mudguts on 2013-01-24
> **prodigy_ said:**
> **mudguts**, I can clearly see **eth0** and **eth1** in the output. So what do you mean by saying "exact same issue"?

well.. I have the same hardware and my wireless options are all greyed out.
the wifi 'works' but no connection.

I have dual boot with Win7, in win7, I can connect to my network.. in Ubuntu 12.10, it's just not showing any wireless..

---

### Post by prodigy_ on 2013-01-24
> **mudguts said:**
> I have dual boot with Win7, in win7, I can connect to my network.. in Ubuntu 12.10, it's just not showing any wireless..
Try: ```
dmesg | grep -i 'wl'
``` Any output?

---

### Post by mudguts on 2013-01-24
> **prodigy_ said:**
> Try: ```
dmesg | grep -i 'wl'
``` Any output?

this make sense to you?

[    6.564750] b43-phy0: Broadcom 4312 WLAN found (core revision 15)

---

### Post by prodigy_ on 2013-01-25
Did you install Broadcom Wi-Fi driver?
[http://ubuntuforums.org/showthread.php?t=2090138](http://ubuntuforums.org/showthread.php?t=2090138)
[http://ubuntuforums.org/showthread.php?t=2100005](http://ubuntuforums.org/showthread.php?t=2100005)

You Wi-Fi card seems to be OK but no driver is being loaded for it. That's why it's missing from network interfaces lists.

---

### Post by Cyril4133 on 2013-01-25
First, my ethernet card wasn't activated in BIOS.

Second I put in comment b44 in /etc/modprobe.d/broadcom-sta-common.conf which become

```
# wl module from Broadcom conflicts with ssb
# We must blacklist the following modules:
#blacklist b44
blacklist b43legacy
blacklist b43
blacklist brcm80211
blacklist brcmsmac
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS
```

Thanks for your help

---

### Post by mudguts on 2013-01-27
> **prodigy_ said:**
> Did you install Broadcom Wi-Fi driver?
[http://ubuntuforums.org/showthread.php?t=2090138](http://ubuntuforums.org/showthread.php?t=2090138)
[http://ubuntuforums.org/showthread.php?t=2100005](http://ubuntuforums.org/showthread.php?t=2100005)

You Wi-Fi card seems to be OK but no driver is being loaded for it. That's why it's missing from network interfaces lists.

That makes sense.  Thanks for your help.  I'll try that now.  I wonder why it wasn't loading?  It did load for a month or so (.10 release) but then quit in Nov.. bizarro.

---

