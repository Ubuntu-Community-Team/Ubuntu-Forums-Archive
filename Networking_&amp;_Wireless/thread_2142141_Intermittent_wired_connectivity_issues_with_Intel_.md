---
title: "Intermittent wired connectivity issues with Intel 82579V"
date: 2013-05-04
forum: Networking &amp; Wireless
---

### Post by 1beb on 2013-05-04
If I shutdown my computer, I'm plagued with interrmittent connectivity issues. A few restarts and it goes away for a while. I had 5 days of great connectivity, shutdown last night, now it seems to stall on every third of fourth page load. Full dmesg is attached. There are a few errors associated with attempting to mount a NAS device, but it usually just resolves itself (not sure if this is a chicken or egg problem). I think I've included everything relevant below - but if there's something else, let me know! 

Appreciate your support here. It's a particularly frustrating issue, given that wired connections have always been nothing but fantastic for me in the past. 


[LIST]
[*]If I load a live usb, internet works as expected 
[*]If enable and disable the connection, it works well for a short time. 
[/LIST]

$ uname -r 

```
3.8.0-19-generic
```

$ lspci | grep eth

```
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 06)
```

$ lspci

```
00:00.0 Host bridge: Intel Corporation Xeon E5/Core i7 DMI2 (rev 07)
00:01.0 PCI bridge: Intel Corporation Xeon E5/Core i7 IIO PCI Express Root Port 1a (rev 07)
00:02.0 PCI bridge: Intel Corporation Xeon E5/Core i7 IIO PCI Express Root Port 2a (rev 07)
00:03.0 PCI bridge: Intel Corporation Xeon E5/Core i7 IIO PCI Express Root Port 3a in PCI Express Mode (rev 07)
00:05.0 System peripheral: Intel Corporation Xeon E5/Core i7 Address Map, VTd_Misc, System Management (rev 07)
00:05.2 System peripheral: Intel Corporation Xeon E5/Core i7 Control Status and Global Errors (rev 07)
00:05.4 PIC: Intel Corporation Xeon E5/Core i7 I/O APIC (rev 07)
00:11.0 PCI bridge: Intel Corporation C600/X79 series chipset PCI Express Virtual Root Port (rev 06)
00:16.0 Communication controller: Intel Corporation C600/X79 series chipset MEI Controller #1 (rev 05)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 06)
00:1a.0 USB controller: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #2 (rev 06)
00:1b.0 Audio device: Intel Corporation C600/X79 series chipset High Definition Audio Controller (rev 06)
00:1c.0 PCI bridge: Intel Corporation C600/X79 series chipset PCI Express Root Port 1 (rev b6)
00:1c.1 PCI bridge: Intel Corporation C600/X79 series chipset PCI Express Root Port 2 (rev b6)
00:1c.3 PCI bridge: Intel Corporation C600/X79 series chipset PCI Express Root Port 4 (rev b6)
00:1c.4 PCI bridge: Intel Corporation C600/X79 series chipset PCI Express Root Port 5 (rev b6)
00:1c.5 PCI bridge: Intel Corporation C600/X79 series chipset PCI Express Root Port 6 (rev b6)
00:1d.0 USB controller: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #1 (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation C600/X79 series chipset LPC Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation C600/X79 series chipset 6-Port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation C600/X79 series chipset SMBus Host Controller (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GK106 [GeForce GTX 660] (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 0e0b (rev a1)
06:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
07:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
08:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)
09:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller (rev 01)
ff:08.0 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link 0 (rev 07)
ff:08.3 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 0 (rev 07)
ff:08.4 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 0 (rev 07)
ff:09.0 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link 1 (rev 07)
ff:09.3 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 1 (rev 07)
ff:09.4 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 1 (rev 07)
ff:0a.0 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 0 (rev 07)
ff:0a.1 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 1 (rev 07)
ff:0a.2 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 2 (rev 07)
ff:0a.3 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 3 (rev 07)
ff:0b.0 System peripheral: Intel Corporation Xeon E5/Core i7 Interrupt Control Registers (rev 07)
ff:0b.3 System peripheral: Intel Corporation Xeon E5/Core i7 Semaphore and Scratchpad Configuration Registers (rev 07)
ff:0c.0 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 07)
ff:0c.1 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 07)
ff:0c.2 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 07)
ff:0c.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 0 (rev 07)
ff:0c.7 System peripheral: Intel Corporation Xeon E5/Core i7 System Address Decoder (rev 07)
ff:0d.0 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 07)
ff:0d.1 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 07)
ff:0d.2 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 07)
ff:0d.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 1 (rev 07)
ff:0e.0 System peripheral: Intel Corporation Xeon E5/Core i7 Processor Home Agent (rev 07)
ff:0e.1 Performance counters: Intel Corporation Xeon E5/Core i7 Processor Home Agent Performance Monitoring (rev 07)
ff:0f.0 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Registers (rev 07)
ff:0f.1 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller RAS Registers (rev 07)
ff:0f.2 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 0 (rev 07)
ff:0f.3 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 1 (rev 07)
ff:0f.4 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 2 (rev 07)
ff:0f.5 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 3 (rev 07)
ff:0f.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 4 (rev 07)
ff:10.0 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 0 (rev 07)
ff:10.1 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 1 (rev 07)
ff:10.2 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 0 (rev 07)
ff:10.3 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 1 (rev 07)
ff:10.4 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 2 (rev 07)
ff:10.5 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 3 (rev 07)
ff:10.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 2 (rev 07)
ff:10.7 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 3 (rev 07)
ff:11.0 System peripheral: Intel Corporation Xeon E5/Core i7 DDRIO (rev 07)
ff:13.0 System peripheral: Intel Corporation Xeon E5/Core i7 R2PCIe (rev 07)
ff:13.1 Performance counters: Intel Corporation Xeon E5/Core i7 Ring to PCI Express Performance Monitor (rev 07)
ff:13.4 Performance counters: Intel Corporation Xeon E5/Core i7 QuickPath Interconnect Agent Ring Registers (rev 07)
ff:13.5 Performance counters: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 0 Performance Monitor (rev 07)
ff:13.6 System peripheral: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 1 Performance Monitor (rev 07)

```

$ ifconfig -a

```

eth0      Link encap:Ethernet  HWaddr 50:46:5d:71:64:48  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5246:5dff:fe71:6448/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30829 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57516540 (57.5 MB)  TX bytes:4154454 (4.1 MB)
          Interrupt:18 Memory:fb500000-fb520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4865 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4865 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:397927 (397.9 KB)  TX bytes:397927 (397.9 KB)

```

$ dmesg | grep eth

```

[    1.011863] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 50:46:5d:71:64:48
[    1.011865] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.011895] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    1.858760] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.392182] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.392428] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.122516] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[    5.122548] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3948.496281] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3951.358539] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 3951.358595] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

$ route -nn
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

```

$ dmesg (from first error)

```

    1.858760] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    1.859536] udevd[463]: starting version 175
[    1.881113] lp: driver loaded but no devices found
[    1.892249] usb 2-1.3: new low-speed USB device number 5 using ehci-pci
[    1.919380] wmi: Mapper loaded
[    1.933051] mei 0000:00:16.0: setting latency timer to 64
[    1.933102] mei 0000:00:16.0: irq 83 for MSI/MSI-X
[    1.936358] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.SBRG.GPBX 1 (20121018/utaddress-251)
[    1.936363] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    1.936364] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.SBRG.GPBX 1 (20121018/utaddress-251)
[    1.936366] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    1.936367] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    1.938172] type=1400 audit(1367697646.703:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=662 comm="apparmor_parser"
[    1.938449] type=1400 audit(1367697646.703:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=662 comm="apparmor_parser"
[    1.938604] type=1400 audit(1367697646.703:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=662 comm="apparmor_parser"
[    1.946813] EDAC MC: Ver: 3.0.0
[    1.948682] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    1.948798] EDAC sbridge: Seeking for: dev 0e.0 PCI ID 8086:3ca0
[    1.948806] EDAC sbridge: Seeking for: dev 0e.0 PCI ID 8086:3ca0
[    1.948811] EDAC sbridge: Seeking for: dev 0f.0 PCI ID 8086:3ca8
[    1.948815] EDAC sbridge: Seeking for: dev 0f.0 PCI ID 8086:3ca8
[    1.948817] EDAC sbridge: Seeking for: dev 0f.1 PCI ID 8086:3c71
[    1.948822] EDAC sbridge: Seeking for: dev 0f.1 PCI ID 8086:3c71
[    1.948824] EDAC sbridge: Seeking for: dev 0f.2 PCI ID 8086:3caa
[    1.948828] EDAC sbridge: Seeking for: dev 0f.2 PCI ID 8086:3caa
[    1.948831] EDAC sbridge: Seeking for: dev 0f.3 PCI ID 8086:3cab
[    1.948835] EDAC sbridge: Seeking for: dev 0f.3 PCI ID 8086:3cab
[    1.948837] EDAC sbridge: Seeking for: dev 0f.4 PCI ID 8086:3cac
[    1.948842] EDAC sbridge: Seeking for: dev 0f.4 PCI ID 8086:3cac
[    1.948844] EDAC sbridge: Seeking for: dev 0f.5 PCI ID 8086:3cad
[    1.948849] EDAC sbridge: Seeking for: dev 0f.5 PCI ID 8086:3cad
[    1.948851] EDAC sbridge: Seeking for: dev 11.0 PCI ID 8086:3cb8
[    1.948856] EDAC sbridge: Seeking for: dev 11.0 PCI ID 8086:3cb8
[    1.948858] EDAC sbridge: Seeking for: dev 0c.6 PCI ID 8086:3cf4
[    1.948862] EDAC sbridge: Seeking for: dev 0c.6 PCI ID 8086:3cf4
[    1.948864] EDAC sbridge: Seeking for: dev 0c.7 PCI ID 8086:3cf6
[    1.948868] EDAC sbridge: Seeking for: dev 0c.7 PCI ID 8086:3cf6
[    1.948870] EDAC sbridge: Seeking for: dev 0d.6 PCI ID 8086:3cf5
[    1.948874] EDAC sbridge: Seeking for: dev 0d.6 PCI ID 8086:3cf5
[    1.948877] EDAC sbridge: ECC is disabled. Aborting
[    1.948920] EDAC sbridge: Couldn't find mci handler
[    1.961429] snd_hda_intel 0000:00:1b.0: irq 84 for MSI/MSI-X
[    1.973037] microcode: CPU0 sig=0x206d7, pf=0x4, revision=0x705
[    1.982697] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[    1.982996] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[    1.983318] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[    1.983584] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    1.983677] input: HDA Intel PCH Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    1.984157] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    1.984260] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    1.984363] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    1.984621] hda_intel: Disabling MSI
[    1.984629] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    1.985844] FS-Cache: Loaded
[    1.990493] usb 2-1.3: New USB device found, idVendor=047d, idProduct=1020
[    1.990496] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.990499] usb 2-1.3: Product: Kensington Expert Mouse
[    1.990501] usb 2-1.3: Manufacturer: Kensington     
[    1.992863] input: Kensington      Kensington Expert Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input12
[    1.992985] hid-generic 0003:047D:1020.0004: input,hidraw3: USB HID v1.10 Mouse [Kensington      Kensington Expert Mouse] on usb-0000:00:1d.0-1.3/input0
[    1.993357] FS-Cache: Netfs 'cifs' registered for caching
[    1.993449] Key type cifs.spnego registered
[    1.993455] Key type cifs.idmap registered
[    1.999748] nvidia: module license 'NVIDIA' taints kernel.
[    2.000450] CIFS VFS: Error connecting to socket. Aborting operation
[    2.001206] CIFS VFS: cifs_mount failed w/return code = -101
[    2.001305] CIFS VFS: Error connecting to socket. Aborting operation
[    2.001405] CIFS VFS: cifs_mount failed w/return code = -101
[    2.009975] microcode: CPU1 sig=0x206d7, pf=0x4, revision=0x705
[    2.010885] microcode: CPU2 sig=0x206d7, pf=0x4, revision=0x705
[    2.011311] asus_wmi: ASUS WMI generic driver loaded
[    2.011325] asus_wmi: Initialization: 0x0
[    2.011349] asus_wmi: BIOS WMI version: 0.9
[    2.011580] asus_wmi: SFUN value: 0x0
[    2.011580] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input13
[    2.012063] microcode: CPU3 sig=0x206d7, pf=0x4, revision=0x705
[    2.012097] asus_wmi: Disabling ACPI video driver
[    2.013247] microcode: CPU4 sig=0x206d7, pf=0x4, revision=0x705
[    2.013583] usblp 2-1.1:1.0: usblp2: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0045
[    2.013600] usbcore: registered new interface driver usblp
[    2.014272] microcode: CPU5 sig=0x206d7, pf=0x4, revision=0x705
[    2.015174] microcode: CPU6 sig=0x206d7, pf=0x4, revision=0x705
[    2.016133] microcode: CPU7 sig=0x206d7, pf=0x4, revision=0x705
[    2.016924] microcode: CPU8 sig=0x206d7, pf=0x4, revision=0x705
[    2.017706] microcode: CPU9 sig=0x206d7, pf=0x4, revision=0x705
[    2.018523] microcode: CPU10 sig=0x206d7, pf=0x4, revision=0x705
[    2.019271] microcode: CPU11 sig=0x206d7, pf=0x4, revision=0x705
[    2.020131] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.032306] CIFS VFS: Error connecting to socket. Aborting operation
[    2.033089] CIFS VFS: Error connecting to socket. Aborting operation
[    2.035895] CIFS VFS: cifs_mount failed w/return code = -101
[    2.042869] CIFS VFS: Error connecting to socket. Aborting operation
[    2.042971] CIFS VFS: cifs_mount failed w/return code = -101
[    2.044111] CIFS VFS: cifs_mount failed w/return code = -101
[    2.056806] Bluetooth: Core ver 2.16
[    2.056818] NET: Registered protocol family 31
[    2.056819] Bluetooth: HCI device and connection manager initialized
[    2.056825] Bluetooth: HCI socket layer initialized
[    2.056827] Bluetooth: L2CAP socket layer initialized
[    2.056829] Bluetooth: SCO socket layer initialized
[    2.058805] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    2.058807] Bluetooth: BNEP filters: protocol multicast
[    2.058810] Bluetooth: BNEP socket layer initialized
[    2.061830] Bluetooth: RFCOMM TTY layer initialized
[    2.061838] Bluetooth: RFCOMM socket layer initialized
[    2.061839] Bluetooth: RFCOMM ver 1.11
[    2.085085] ppdev: user-space parallel port driver
[    2.090220] init: failsafe main process (1042) killed by TERM signal
[    2.104409] init: avahi-cups-reload main process (1072) terminated with status 1
[    2.109287] CIFS VFS: Error connecting to socket. Aborting operation
[    2.109392] CIFS VFS: cifs_mount failed w/return code = -101
[    2.109603] CIFS VFS: Error connecting to socket. Aborting operation
[    2.109706] CIFS VFS: cifs_mount failed w/return code = -101
[    2.110660] type=1400 audit(1367697646.875:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1107 comm="apparmor_parser"
[    2.110995] type=1400 audit(1367697646.875:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1107 comm="apparmor_parser"
[    2.125501] type=1400 audit(1367697646.891:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1150 comm="apparmor_parser"
[    2.125855] type=1400 audit(1367697646.891:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=1148 comm="apparmor_parser"
[    2.125889] type=1400 audit(1367697646.891:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1147 comm="apparmor_parser"
[    2.126072] type=1400 audit(1367697646.891:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1146 comm="apparmor_parser"
[    2.291711] e1000e 0000:00:19.0: irq 80 for MSI/MSI-X
[    2.392093] e1000e 0000:00:19.0: irq 80 for MSI/MSI-X
[    2.392182] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.392428] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.452108] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14
[    2.452212] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input15
[    2.452310] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input16
[    2.452410] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input17
[    2.452939] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    2.453155] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.88  Wed Mar 27 14:26:46 PDT 2013
[    2.473323] init: udev-fallback-graphics main process (1419) terminated with status 1
[    3.676167] CIFS VFS: Error connecting to socket. Aborting operation
[    3.676241] CIFS VFS: cifs_mount failed w/return code = -101
[    3.676408] CIFS VFS: Error connecting to socket. Aborting operation
[    3.676463] CIFS VFS: cifs_mount failed w/return code = -101
[    5.122516] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[    5.122548] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  464.966142] systemd-hostnamed[19281]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 3948.394167] e1000e 0000:00:19.0: irq 80 for MSI/MSI-X
[ 3948.496146] e1000e 0000:00:19.0: irq 80 for MSI/MSI-X
[ 3948.496281] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3951.358539] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 3951.358595] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

---

### Post by chili555 on 2013-05-04
Please try the suggestion at post #25 and following here: [http://ubuntuforums.org/showthread.php?t=2050514&page=3](http://ubuntuforums.org/showthread.php?t=2050514&page=3)

We may have a genuine bug in e1000e.

---

### Post by 1beb on 2013-05-05
I fixed this by disabling ipv6 entirely, adding the following to ```
/etc/sysctl.conf
```

```

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

```

---

