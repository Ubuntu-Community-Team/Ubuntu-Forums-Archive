---
title: "Troubleshooting wireless network connectivity"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by taserian on 2011-01-01
I'm currently running Ubuntu 10.10, and I'm running  into trouble keeping my wireless  connection alive. After rebooting, I  get about 5-10 minutes of a good speed connection; afterwards, the  connection just zeroes out. I've gotten around to stirring up a shell  script that gives me another 10 minutes or so of connectivity. Script  contents below:```

  #! /bin/bash
sudo ifconfig wlan0 up
echo "Enabling wireless device . . ."
sleep 5
sudo iwconfig wlan0 essid MyNetworkName
echo "Connecting to network. . ."
sleep 10
sudo dhclient wlan0
echo "Getting IP address. . ."
sleep 5
echo "Done. Closing window. . ."
sleep 5
```Shortly after running the line "sudo iwconfig wlan0 essid  MyNetworkName" from the script, I notice the speed pick up. Other  computers in my home running Windows XP are not affected by this  problem, so all indications point to my Ubuntu machine.
  Does anyone have any pointers as to how to resolve this?

---

### Post by PatchesTheCaveman on 2011-01-01
Hi taserian.  Happy New Year!

Please run these commands and copy/paste the output into a reply to this thread:
```
lspci -v
sudo iwconfig
ifconfig -a
```

Make sure you are connected to the wireless when you run the last two.

---

### Post by perspectoff on 2011-01-01
Ditch network-manager and install wicd.

---

### Post by taserian on 2011-01-01
lspci -v:
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00008000-00008fff
    Memory behind bridge: f2200000-f23fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00007000-00007fff
    Memory behind bridge: f2100000-f21fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: f2500000-f25fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=09, sec-latency=0
    I/O behind bridge: 00002000-00005fff
    Memory behind bridge: f1100000-f20fffff
    Prefetchable memory behind bridge: 00000000f0100000-00000000f10fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 44
    I/O ports at 9038 [size=8]
    I/O ports at 904c [size=4]
    I/O ports at 9030 [size=8]
    I/O ports at 9048 [size=4]
    I/O ports at 9010 [size=16]
    Memory at f2408000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at f2407000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10 [OHCI])
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at f2406000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f2408500 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f2405000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10 [OHCI])
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f2404000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at f2408400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: 66MHz, medium devsel
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f2400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=64
    Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
    Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200] (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device ff1f
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 8000 [size=256]
    Memory at f2300000 (32-bit, non-prefetchable) [size=64K]
    Memory at f2200000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8181
    Flags: bus master, fast devsel, latency 0, IRQ 16
    I/O ports at 7000 [size=256]
    Memory at f2100000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: rtl819xSE
    Kernel modules: r8192se_pci

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, fast devsel, latency 0, IRQ 43
    I/O ports at 6000 [size=256]
    Memory at f0010000 (64-bit, prefetchable) [size=4K]
    Memory at f0000000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at f0020000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

```sudo ipconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  ESSID:"fbivan42"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.452 GHz  Access Point: E0:91:F5:5E:A4:EE   
          Bit Rate=21.5 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=100/100  Signal level=-45 dBm  Noise level=-120 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```ifconfig -a:
```

eth0      Link encap:Ethernet  HWaddr 00:26:6c:4b:91:7c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3469285 (3.4 MB)  TX bytes:3469285 (3.4 MB)

wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:0e:c6:c0  
          inet addr:192.168.1.124  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::72f1:a1ff:fe0e:c6c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:362634 errors:0 dropped:0 overruns:0 frame:0
          TX packets:476220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:181211378 (181.2 MB)  TX bytes:432102342 (432.1 MB)
          Interrupt:16 Memory:ffffc90002770000-ffffc90002770100 

```

---

### Post by PatchesTheCaveman on 2011-01-02
Try running these commands on the terminal:
```
sudo modprobe -r rtl819xSE
sudo modprobe  r8192se_pci
```

Then see if your wireless works okay now.

---

