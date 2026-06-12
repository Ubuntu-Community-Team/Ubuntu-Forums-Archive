---
title: "Enabling Wireless on Gateway laptop"
date: 2013-04-23
forum: Networking &amp; Wireless
---

### Post by icec0ld on 2013-04-23
Hello all,

I'm trying to get Ubuntu working wirelessly on my Gateway laptop.  It's a Model w350a t-1630 I believe.  I am running Ubuntu 12.04 LTS at the moment.  It has a realtek wireless adapter and after trying various fixes on here I'm still at a loss.  After reading more through the posts and running a iwconfig I received the following output:

icecold:~$ iwconfig
lo        no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Frequency=2.422 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

I have tried the function key to check that the wireless adapter is on.  I see from this output that it isn't.  Any terminal commands to enable this?  I would imagine I need a wireless extension to even check, for running a scan returns the following:icecold:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.

Also, in case it helps I will include the wireless info.  

lspci -v results:

icecold:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS690 Host Bridge
    Subsystem: Advanced Micro Devices [AMD] nee ATI Device 1234
    Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: cfd00000-cfefffff
    Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: c0100000-c02fffff
    Prefetchable memory behind bridge: 00000000c0300000-00000000c04fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 2) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=0d, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: f0200000-f02fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:07.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 3) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0e, subordinate=13, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: f0300000-f03fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000c00fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:12.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
    Subsystem: Gateway 2000 Device 0565
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at 8440 [size=8]
    I/O ports at 8434 [size=4]
    I/O ports at 8438 [size=8]
    I/O ports at 8430 [size=4]
    I/O ports at 8400 [size=16]
    Memory at f0409000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0) (prog-if 10 [OHCI])
    Subsystem: Gateway 2000 Device 0565
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at f0404000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1) (prog-if 10 [OHCI])
    Subsystem: Gateway 2000 Device 0565
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f0405000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2) (prog-if 10 [OHCI])
    Subsystem: Gateway 2000 Device 0565
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f0406000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.3 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3) (prog-if 10 [OHCI])
    Subsystem: Gateway 2000 Device 0565
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f0407000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.4 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4) (prog-if 10 [OHCI])
    Subsystem: Gateway 2000 Device 0565
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f0408000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
    Subsystem: Gateway 2000 Device 0565
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at f0409400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 14)
    Subsystem: Gateway 2000 Device 0565
    Flags: 66MHz, medium devsel
    I/O ports at 8410 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4

00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE (prog-if 8a [Master SecP PriP])
    Subsystem: Gateway 2000 Device 0565
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 8420 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
    Subsystem: Gateway 2000 Device 0565
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
    Subsystem: Gateway 2000 Device 0565
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=14, subordinate=19, sec-latency=64

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon X1200 Series] (prog-if 00 [VGA controller])
    Subsystem: Gateway 2000 Device 0565
    Flags: bus master, fast devsel, latency 64, IRQ 44
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at cfdf0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at 9000 [size=256]
    Memory at cfe00000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

01:05.2 Audio device: Advanced Micro Devices [AMD] nee ATI Radeon X1200 Series Audio Controller
    Subsystem: Advanced Micro Devices [AMD] nee ATI Radeon X1200 Series Audio Controller
    Flags: bus master, fast devsel, latency 64, IRQ 19
    Memory at cfdec000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

08:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller
    Flags: bus master, fast devsel, latency 0, IRQ 18
    I/O ports at a000 [size=256]
    Memory at f0200000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8180
    Kernel modules: r8187se

0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
    Subsystem: Gateway 2000 Device 0565
    Flags: bus master, fast devsel, latency 0, IRQ 43
    I/O ports at b000 [size=256]
    Memory at f0300000 (64-bit, non-prefetchable) [size=4K]
    [virtual] Expansion ROM at c0000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169


Thank you so much in advance and I really appreciate any suggestions!

---

### Post by chili555 on 2013-04-23
Please open a terminal and let us have a look at:```
rfkill list all
lsmod | grep r81
sudo iwlist wlan0 scan
nm-tool
```Thanks.

---

### Post by icec0ld on 2013-05-07
Thank you for your help, sorry for the long time in replying.  The output is as follows:

icecold:~$ rfkill list all
doug@icecold:~$ lsmod | grep r81
r8187se               177422  0 
eeprom_93cx6           12767  1 r8187se
r8169                  62154  0 
doug@icecold:~$ sudo iwlist wlan0 scan
[sudo] password for doug: 
wlan0     No scan results

doug@icecold:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:03:25:5B:79:32

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.110
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8180
  State:             disconnected
  Default:           no
  HW Address:        00:16:44:D5:69:B8

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

What puzzles me about this is that it worked fine on an older version of Ubuntu, believe it was 11 something.  Thanks again for your time, I'm really looking forward to getting this up and running.  

Doug

---

### Post by chili555 on 2013-05-08
Something a little deeper is wrong here. Let's check the message logs:```
dmesg | grep -e r81 -e 08:00
lspci -nn | grep 0280
```> after trying various fixes on here I'm still at a loss.What fixes?

---

### Post by icec0ld on 2013-05-08
I initally went through the batch of fixes posted here in the forums for a while.  After being unable to do get any of those to work, I did a vanilla reload of 12.04 LTS.  

Here's the output:

doug@icecold:~$ dmesg | grep -e r81 -e 08:00
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88010fc00000 s83136 r8192 d23360 u1048576
[    0.000000] pcpu-alloc: s83136 r8192 d23360 u1048576 alloc=1*2097152
[    0.202688] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.202693] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d1fff] (ignored)
[    0.202696] pci_root PNP0A08:00: host bridge window [mem 0x000d2000-0x000d3fff] (ignored)
[    0.202699] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d5fff] (ignored)
[    0.202703] pci_root PNP0A08:00: host bridge window [mem 0x000d6000-0x000d7fff] (ignored)
[    0.202706] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000d9fff] (ignored)
[    0.202709] pci_root PNP0A08:00: host bridge window [mem 0x000da000-0x000dbfff] (ignored)
[    0.202712] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000ddfff] (ignored)
[    0.202716] pci_root PNP0A08:00: host bridge window [mem 0x000de000-0x000dffff] (ignored)
[    0.202719] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e1fff] (ignored)
[    0.202722] pci_root PNP0A08:00: host bridge window [mem 0x000e2000-0x000e3fff] (ignored)
[    0.202726] pci_root PNP0A08:00: host bridge window [mem 0xb0000000-0xdfffffff] (ignored)
[    0.202729] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xffffffff] (ignored)
[    0.202733] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.202736] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.204644] pci 0000:08:00.0: [10ec:8199] type 0 class 0x000280
[    0.204659] pci 0000:08:00.0: reg 10: [io  0xa000-0xa0ff]
[    0.204670] pci 0000:08:00.0: reg 14: [mem 0xf0200000-0xf0203fff]
[    0.204752] pci 0000:08:00.0: supports D1 D2
[    0.204754] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot
[    0.204759] pci 0000:08:00.0: PME# disabled
[    0.306293] pci 0000:08:00.0: Signaling PME through PCIe PME interrupt
[    1.434318] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.434345] r8169 0000:0e:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.434383] r8169 0000:0e:00.0: setting latency timer to 64
[    1.434453] r8169 0000:0e:00.0: irq 43 for MSI/MSI-X
[    1.434995] r8169 0000:0e:00.0: eth0: RTL8101e at 0xffffc90000610000, 00:03:25:5b:79:32, XID 94200000 IRQ 43
[    9.200548] r8187se: module is from the staging directory, the quality is unknown, you have been warned.
[    9.201959] r8180: Initializing module
[    9.201960] r8180: Wireless extensions version 22
[    9.201963] r8180: Initializing proc filesystem
[    9.202135] r8180: Configuring chip resources
[    9.202157] r8180 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.202168] r8180 0000:08:00.0: setting latency timer to 64
[    9.204520] r8180: Channel plan is 1
[    9.204528] r8180: MAC controller is a RTL8187SE b/g
[    9.206623] r8180: usValue is 0x100
[    9.248605] r8180: EEPROM version 104
[    9.252801] r8180: WW:**PLEASE** REPORT SUCCESSFUL/UNSUCCESSFUL TO Realtek!
[    9.253421] r8180: IRQ 18
[    9.254228] r8180: Driver probe completed
[    9.406860] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1a/LNXVIDEO:00/input/input5
[   18.409171] r8180: Bringing up iface
[   18.607665] r8180: Card successfully reset
[   19.342863] r8180: WIRELESS_MODE_G
[   19.363408] r8169 0000:0e:00.0: eth0: link down
[  437.428853] r8169 0000:0e:00.0: eth0: link up
doug@icecold:~$ lspci -nn | grep 0280
08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)

---

### Post by chili555 on 2013-05-08
> [COLOR="#FF0000"]r8187se[/COLOR]: module is from the staging directory, the quality is unknown, you have been warned.>  [COLOR="#FF0000"]r8180[/COLOR]: Initializing moduleDo you have two competing modules trying to load? May we see:```
modinfo r8187se | grep 8199
modinfo r8180 | grep 8199
lsmod
```If any command produces an error, please post it as it may be informative.

Usually, I try to find out these details myself, but I don't currently have a 12.04 installation.

---

### Post by icec0ld on 2013-05-14
Running the modinfo r8180 command produced the following error:
ERROR: modinfo: could not find module r8180

If you need, I can post the lsmod output too, but that was the only glaring error, so for brevity I will leave it out for now.  Thanks again for all your help!

---

### Post by chili555 on 2013-05-14
I am suspicious that this is not actually a driver error, but a hardware issue; here's my clue:> I have tried the function key to check that the wireless adapter is on. Can you please confirm that the wireless switch is set to enable the wireless radio? Please see attached. Next, does the wireless LED turn on or off? Does it change when you press the FN+F2 key combination?

---

### Post by icec0ld on 2013-05-21
That seems to have done it.  Seems it had been jostled just enough to turn it off.  No red was showing, but a couple of tries with it and the function key and the wireless LED is on and I am now able to search for networks.  Thanks for your patience with my completely moronic mistake.  

Looking forward to really getting into this now!

---

### Post by chili555 on 2013-05-21
Glad it's working!

No worries. I've made the same mistake myself a few times.

---

