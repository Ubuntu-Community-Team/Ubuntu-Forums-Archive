---
title: "Broadcom 4321, 14e4:4329 not showing wireless networks"
date: 2012-12-13
forum: Networking &amp; Wireless
---

### Post by Dave6187 on 2012-12-13
Hey guys, I'm moderately new to ubuntu, I installed 10.10 when it came out as a dual boot on my desktop (64 bit, if it makes a difference) , and had no issues whatsoever, but for various reasons i ended up removing it and sticking with my other OS.

I decided to reinstall it, which i did with no problem, and again had no issues running it. Decided to upgrade it to 12.04, which the upgrades went with no problem, other than as of 11.04 my wireless stopped working. I ended up using my laptop as a network bridge to finish the updates before seeking out help.

I spent a good couple hours scouring the internet for possible solutions, but nothing worked that i could find yet.

I do know that my adapter is a netgear wn311b, which is using broadcom 4321, and is 14e4:4329

based on what i've read, I should be using the STA driver, I uninstalled all the drivers via synaptic, restarted, then reinstalled the sta-source and sta-common, restarted, and all i get is "wireless networks, disconnected" greyed out. 

I'm at a loss as to where to go from here, any help you guys can give would be greatly appreciated

lspci -v

```
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: fast devsel
    Capabilities: <access denied>

00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: f8000000-fb8fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
    Subsystem: Device 0043:0083
    Flags: fast devsel
    Capabilities: <access denied>

00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
    Subsystem: Device 0043:0083
    Flags: fast devsel
    Capabilities: <access denied>

00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
    Subsystem: Device 0043:0083
    Flags: fast devsel
    Capabilities: <access denied>

00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
    Flags: fast devsel

00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
    Flags: fast devsel

00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
    Flags: fast devsel

00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7ffe000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 83d0
    Flags: bus master, fast devsel, latency 0, IRQ 59
    Memory at f7ff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=0b, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fbb00000-fbdfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fba00000-fbafffff
    Prefetchable memory behind bridge: 00000000f6f00000-00000000f6ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fb900000-fb9fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: c0000000-c01fffff
    Prefetchable memory behind bridge: 00000000c0200000-00000000c03fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7ffd000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=32
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fbe00000-fbefffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
    I/O ports at 8c00 [size=8]
    I/O ports at 8880 [size=4]
    I/O ports at 8800 [size=8]
    I/O ports at 8480 [size=4]
    I/O ports at 8400 [size=16]
    I/O ports at 8080 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: medium devsel, IRQ 15
    Memory at f7ffc000 (64-bit, non-prefetchable) [size=256]
    I/O ports at ffe0 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
    I/O ports at 9c00 [size=8]
    I/O ports at 9880 [size=4]
    I/O ports at 9800 [size=8]
    I/O ports at 9480 [size=4]
    I/O ports at 9400 [size=16]
    I/O ports at 9080 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce GTS 250] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Device 196e:079e
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at ac00 [size=128]
    [virtual] Expansion ROM at fb8e0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb

03:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 824f
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fb9fe000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

03:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 824f
    Flags: bus master, fast devsel, latency 0, IRQ 19
    I/O ports at bc00 [size=8]
    I/O ports at b880 [size=4]
    I/O ports at b800 [size=8]
    I/O ports at b480 [size=4]
    I/O ports at b400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_jmicron
    Kernel modules: pata_jmicron

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 58
    I/O ports at c800 [size=256]
    Memory at f6fff000 (64-bit, prefetchable) [size=4K]
    Memory at f6ff8000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at fbaf0000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

06:00.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Memory at fbbe0000 (32-bit, non-prefetchable) [size=128K]
    Bus: primary=06, secondary=07, subordinate=0b, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fbc00000-fbdfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

07:01.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=07, secondary=08, subordinate=08, sec-latency=0
    Memory behind bridge: fbc00000-fbcfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

07:05.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=07, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fbd00000-fbdfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

07:07.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=07, secondary=0a, subordinate=0a, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

07:09.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=07, secondary=0b, subordinate=0b, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

08:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fbcfe000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

09:00.0 IDE interface: Marvell Technology Group Ltd. Device 914d (rev 10) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. Device 8400
    Flags: fast devsel, IRQ 17
    I/O ports at dc00 [size=8]
    I/O ports at d880 [size=4]
    I/O ports at d800 [size=8]
    I/O ports at d480 [size=4]
    I/O ports at d400 [size=16]
    Memory at fbdff800 (32-bit, non-prefetchable) [size=2K]
    Expansion ROM at fbde0000 [disabled] [size=64K]
    Capabilities: <access denied>

0c:02.0 Network controller: Broadcom Corporation BCM4321 802.11b/g/n (rev 01)
    Subsystem: Netgear WN311B RangeMax Next 270 Mbps Wireless PCI Adapter
    Flags: fast devsel, IRQ 17
    Memory at fbefc000 (32-bit, non-prefetchable) [size=16K]
    Kernel driver in use: wl
    Kernel modules: wl, ssb

0c:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. M4A series motherboard
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at fbefb800 (32-bit, non-prefetchable) [size=2K]
    I/O ports at ec00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0
    Kernel driver in use: i7core_edac
    Kernel modules: i7core_edac

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

```

rfkill list all
```
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

sudo iwconfig
```

lo        no wireless extensions.

eth1      IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0

eth0      no wireless extensions.


```

if you guys need any other information from me, let me know. I'm off from work today

---

### Post by chili555 on 2012-12-13
How about letting us see:```
sudo iwlist eth1 scan
rfkill list all
```Thanks.

---

### Post by Dave6187 on 2012-12-13
```
~$ sudo iwlist eth1 scan
eth1      No scan results

~$ rfkill list all
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

---

### Post by chili555 on 2012-12-13
Most interesting. Now how about:```
lsmod | grep -e b43 -e wl -e bcma
dmesg | grep -i -e wl -e 0c:02
```Thanks.

---

### Post by Dave6187 on 2012-12-13
yea, i'm honestly pretty confused about this as well, it seems like it sees the adapter, just can't use it. But it worked fine in 10.10

```
~$ lsmod | grep -e b43 -e wl -e bcma
wl                   2568249  0 
lib80211               14381  2 lib80211_crypt_tkip,wl

~$ dmesg | grep -i -e wl -e 0c:02
[    1.206406] pci 0000:0c:02.0: [14e4:4329] type 0 class 0x000280
[    1.206417] pci 0000:0c:02.0: reg 10: [mem 0xfbefc000-0xfbefffff]
[   12.235692] wl 0000:0c:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  210.092543] wl 0000:0c:02.0: PCI INT A disabled
[  210.092588] pci_legacy_suspend(): wl_suspend+0x0/0xa0 [wl] returns -5
[  210.092601] PM: Device 0000:0c:02.0 failed to suspend async: error -5


```

---

### Post by chili555 on 2012-12-13
> PM: Device 0000:0c:02.0 failed to suspend async: error -5Old Chili doesn't like that much. Please see here: [https://bbs.archlinux.org/viewtopic.php?id=119042](https://bbs.archlinux.org/viewtopic.php?id=119042)> Suspending was failing because device 5-2 made a wakeup request.
To disable wakeup requests make```
echo disabled > /sys/bus/usb/devices/5-2/power/wakeup
```You might try this:```
sudo su
echo disabled > /sys/bus/pci/devices/0000:0c:02.0/power/wakeup
exit
```If it says there is no such file, look around a bit to find the location:```
ls /sys/bus/pci/devices
```Then unload and reload the driver:```
sudo modprobe -r wl
sudo modprobe wl
sudo iwlist eth1 scan
```This is a new one on me, so we are in experimental ground a bit here.

---

### Post by Dave6187 on 2012-12-13
ok, it took some effort, but this is what i've been able to come up with, which isn't much, but it's something.
```
root@Dave:/sys/bus/pci/devices/0000:0c:02.0/power# ls
async                 control              runtime_active_time  runtime_status          runtime_usage
autosuspend_delay_ms  runtime_active_kids  runtime_enabled      runtime_suspended_time
```


not sure where to go from there

---

### Post by chili555 on 2012-12-13
Is there anything interesting here?```
cat /sys/bus/pci/devices/0000:0c:02.0/power/async
```

---

### Post by Dave6187 on 2012-12-13
not really

```
root@Dave:/# cat /sys/bus/pci/devices/0000:0c:02.0/power/async
enabled
root@Dave:/# cat /sys/bus/pci/devices/0000:0c:02.0/power/control
on
root@Dave:/# cat /sys/bus/pci/devices/0000:0c:02.0/power/runtime_status
active

```

---

### Post by Dave6187 on 2012-12-13
also, interestingly enough the card will broadcast as a hot spot.

and i did just confirm my computer will not suspend anymore, which was working fine yesterday before the upgrade to 12.04

---

### Post by chili555 on 2012-12-13
> and i did just confirm my computer will not suspend anymore, which was working fine yesterday before the upgrade to 12.04I strongly suspect the two are related. I suggest you track down and fix the suspend issue here. [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

If the wireless doesn't work after that, post back and we'll proceed.

You might try:```
sudo apt-get update
sudo apt-get -f install
```I'm not very experienced in suspend issues. That's about all I can suggest.

---

### Post by Dave6187 on 2012-12-13
I tried doing a fresh install of 12.04 to make sure it wasn't something i had changed while tinkering at some point, which made no difference. I posted on the other section, no replies yet, but i wanted to put this over here too in case something stands out to you:

more pieces to the puzzle...  

in my pm-suspend log i found this after a suspend attempt:
```
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.
```

also thought that it couldn't find wl0 was interesting:

```
sudo lshw -C network
[sudo] password for dave6187: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 03
       serial: 48:5b:39:36:1a:94
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on  broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full  firmware=rtl_nic/rtl8168d-2.fw ip=192.168.137.104 latency=0 link=yes  multicast=yes port=MII speed=100Mbit/s
       resources: irq:58 ioport:c800(size=256) memory:f6fff000-f6ffffff memory:f6ff8000-f6ffbfff memory:fbaf0000-fbafffff
  *-network
       description: Wireless interface
       product: BCM4321 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:0c:02.0
       logical name: eth2
       version: 01
       serial: e0:91:f5:67:34:d1
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=64 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbefc000-fbefffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 02:e5:f1:43:60:51
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device link=yes multicast=yes
dave6187@Ubuntu-Dave:~$ sudo modprobe -r wl0
FATAL: Module wl0 not found.

```

i  stopped network-manager before trying to suspend, both from the console  and the dropdown, neither of which worked, and resulted in the same  errors in the log file

---

### Post by Dave6187 on 2012-12-16
ok. suspend issue fixed, the WL driver for some reason was causing the hang up. I removed, and blacklisted the driver, downloaded and installed sta-source and sta-common via synaptic. now I have no suspend/shutdown/restart issues, but now it doesn't even list wireless in network manager. I know i'm forgetting a step in here somewhere, but not sure what it is.

the wireless card is showing up as "unclaimed" under sudo lshw -C network now too

---

### Post by chili555 on 2012-12-16
> I removed, and blacklisted the driver, Your device is not going to run, at least not properly, without the driver *wl*. If it's blacklisted, it has no available driver (UNCLAIMED). If you load *wl *and the system doesn't suspend, the you still *do* have a suspend issue:```
sudo modprobe wl
```If it suspends correctly, then un-blacklist the driver and you're all set.

---

### Post by Dave6187 on 2012-12-16
Well, the guy that was helping me on my other post was saying something about just using the generic b43 driver instead of wl /sta. What's your take on this?

---

### Post by chili555 on 2012-12-16
My take is that it probably won't work. Try it:```
sudo modprobe b43
```Are you connected? No??

---

### Post by Dave6187 on 2012-12-16
just running sudo modprobe b43 comes up as "device not ready, firmware missing" in network manager, i un-blacklisted wl, ran sudo modprobe wl and it comes up as module wl not found.

edit:

i installed the b43 firmware and after restarting and running sudo modprobe b43 again i now have my wireless networks listed, but when i try to connect, it asks for my WEP key, and then it just perpetually shows trying to connect

---

### Post by chili555 on 2012-12-17
> i now have my wireless networks listed, but when i try to connect, it asks for my WEP key, and then it just perpetually shows trying to connectSo now you have your answer to...> about just using the generic b43 driver instead of wl /sta. With a temporary wired ethernet connection, let's repair the wl driver:```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel source
sudo modprobe wl
```

---

### Post by Dave6187 on 2012-12-17
I was just noticing something, not sure if it's actually anything important, but thought i'd point it out. I reinstalled the wl driver like you suggested, and everythings back to the way it was. but under lshw -C network i noticed that 1, my wireless is coming up as eth2, and 2, it's showing it as 32bit, this is a 64bit system i'm on...

```
dave6187@Ubuntu-Dave:/$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 03
       serial: 48:5b:39:36:1a:94
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=192.168.137.7 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:58 ioport:c800(size=256) memory:f6fff000-f6ffffff memory:f6ff8000-f6ffbfff memory:fbaf0000-fbafffff
  *-network
       description: Wireless interface
       product: BCM4321 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:0c:02.0
       logical name: eth2
       version: 01
       serial: e0:91:f5:67:34:d1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=64 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbefc000-fbefffff

```

---

### Post by Dave6187 on 2012-12-18
ok, well I think i might as well just revert back to 10.10 because i had no issues there, and the only answers i've been able to get are "you need the wl driver, but it's the wl driver causing your computer to not suspend"

---

