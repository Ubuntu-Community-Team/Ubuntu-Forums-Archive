---
title: "Lucent WiFi"
date: 2005-12-26
forum: Networking &amp; Wireless
---

### Post by MakingT on 2005-12-26
Hello ...I need help with my network card..
Im running Ubuntu 5.10 Kernal 2.6.12-9-386
My Wireless Network Card is Orinoco Silver.
Posted my problem on the beginner forum and they recomended this guide 
([https://wiki.ubuntu.com/WirelessTroubleshootingGuide#ndisc](https://wiki.ubuntu.com/WirelessTroubleshootingGuide#ndisc)) and then posting for help if that nott working here hop you can help me.. here is the info I think would maybe some help.



Using the "sudo lshw -C network" command
It seems the kernal identifies the card a little

Password:
[COLOR="Yellow"]  *-network
       description: WaveLAN/IEEE
       product: Version 01.01
       vendor: Lucent Technologies
       physical id: 0
       slot: Socket 0
       resources: irq:3[/COLOR]
  *-network DISABLED
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 03
       serial: 00:02:3f:78:0e:6e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.8-k2-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s
       resources: iomemory:e8104000-e8104fff ioport:4000-403f irq:11
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:3b:25:8e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS




Then using the "lspci -v" command I cant find it.

0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, fast devsel, latency 0
        Memory at ec000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 96
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: e8000000-e80fffff
        Prefetchable memory behind bridge: f0000000-f7ffffff

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 05) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: e8100000-e81fffff

0000:00:1f.0 ISA bridge: Intel Corp. 82801BA ISA Bridge (LPC) (rev 05)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801BA IDE U100 (rev 05) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0
        I/O ports at 1800 [size=16]

0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 05) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 1820 [size=32]

0000:00:1f.3 SMBus: Intel Corp. 82801BA/BAM SMBus (rev 05)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: medium devsel, IRQ 11
        I/O ports at 1810 [size=16]

0000:00:1f.4 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #2) (rev 05) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 1840 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (rev 05)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1c00 [size=256]
        I/O ports at 1880 [size=64]

0000:00:1f.6 Modem: Intel Corp. Intel 537 [82801BA/BAM AC'97 Modem] (rev 05) (prog-if 00 [Generic])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: medium devsel, IRQ 11
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 5
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 3000 [size=256]
        Memory at e8000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>

0000:02:00.0 CardBus bridge: O2 Micro, Inc. OZ6933 Cardbus Controller (rev 01)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 5
        Memory at 10000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 10400000-107ff000 (prefetchable)
        Memory window 1: 10800000-10bff000
        I/O window 0: 00004400-000044ff
        I/O window 1: 00004800-000048ff
        16-bit legacy interface ports at 0001

0000:02:00.1 CardBus bridge: O2 Micro, Inc. OZ6933 Cardbus Controller (rev 01)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 11
        Memory at 10001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 10c00000-10fff000 (prefetchable)
        Memory window 1: 11000000-113ff000
        I/O window 0: 00004c00-00004cff
        I/O window 1: 00005000-000050ff
        16-bit legacy interface ports at 0001

0000:02:08.0 Ethernet controller: Intel Corp. 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
        Subsystem: Toshiba America Info Systems PRO/100 VE Network Connection
        Flags: bus master, medium devsel, latency 66, IRQ 11
        Memory at e8104000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 4000 [size=64]
        Capabilities: <available only to root>

0000:02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at e8105000 (32-bit, non-prefetchable) [size=2K]
        Memory at e8100000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

And in hope that this will help you helping me the "lspci -n" command.

0000:00:00.0 0600: 8086:1a30 (rev 04)
0000:00:01.0 0604: 8086:1a31 (rev 04)
0000:00:1e.0 0604: 8086:244e (rev 05)
0000:00:1f.0 0601: 8086:2440 (rev 05)
0000:00:1f.1 0101: 8086:244b (rev 05)
0000:00:1f.2 0c03: 8086:2442 (rev 05)
0000:00:1f.3 0c05: 8086:2443 (rev 05)
0000:00:1f.4 0c03: 8086:2444 (rev 05)
0000:00:1f.5 0401: 8086:2445 (rev 05)
0000:00:1f.6 0703: 8086:2446 (rev 05)
0000:01:00.0 0300: 1002:4c59
0000:02:00.0 0607: 1217:6933 (rev 01)
0000:02:00.1 0607: 1217:6933 (rev 01)
0000:02:08.0 0200: 8086:2449 (rev 03)
0000:02:0a.0 0c00: 104c:8023



"sudo iwconfig" command.
And my network connection info.

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"SpeedTouch"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 44:44:44:44:44:44
          Bit Rate:2 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Encryption key:9256-6C1C-E3   Security mode:open
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.



:) hope that you can help me some how :þ

---

### Post by Lambert on 2005-12-26
This might be tough and no guarantees. What I'm going to recommend I've not done before and this may not work. 
You have an older card that's not PnP it looks like. I can tell this by your output. It's not putting the device on the pci bus anywhere (by the way, looks like you used a yellow font. It's very hard to read.) it's not showing up in lspci output and this line in the lshw output.

[COLOR=black]        physical id: 0

So let's try this.

Open up the following file.

```
sudo gedit /etc/pcmcia/config.opts
``` 
At the bottom of the file add this to it

card "orinoco silver"
  manfid 0x11c1, 0xab20
  bind "wavelan_cs"

reboot the pc and run the commands again to see if there is anything different in them.

I tried looking up the manfid from the web and they may be incorrect. Any more information off the card might help if there is any.
[/COLOR]

---

### Post by MakingT on 2005-12-27
Many thanks for the tip...
and sorry about the yellow color was trying to higlight it but :þ.....

But it didnt change anything it seems...... :þ
I added it to the bottom of the file... but one good question is it supposed to be over or under the:

#------------------------------------------------------

... Ill try to find all info about the card that I can and post it here.... :)

---

### Post by MakingT on 2005-12-27
cant find any :þ 

any way to gett any info from the windows driver????

---

### Post by Lambert on 2005-12-27
with the card in try this command

```
sudo cardctl ident
```

Post the output here.

After that try this command and run your previous commands again to see if any difference

```
sudo cardctl config
```

---

### Post by MakingT on 2005-12-27
sudo cardct1 ident 
command not found.......

:/

---

### Post by Lambert on 2005-12-27
cardctl (this ends in the letter L not numer 1)

the enter command is letters in both commands, no numbers in there.

---

### Post by MakingT on 2006-01-02
Oki...

here is the output from the first commands

hans@MakingT:~$ sudo cardctl ident
Password:
Socket 0:
  product info: "Lucent Technologies", "WaveLAN/IEEE", "Version 01.01", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)
Socket 1:
  no product info available
hans@MakingT:~$ sudo cardctl config
Socket 0:
  Vcc 5.0V  Vpp1 0.0V  Vpp2 0.0V
  interface type is "memory and I/O"
  irq 3 [exclusive] [level]
  function 0:
    config base 0x03e0
      option 0x41
    io 0x0100-0x013f [16bit]
Socket 1:
  not configured

the first thing I noticed was the "manfid" was diffrent from what you sett in before so I opened config.opts and changed it..
after restart the yellow triangle with the exclamation mark is gone from the connection symbol in the topp right but i cant connect....

Ill post the the other commands after few minutes
:)

---

### Post by MakingT on 2006-01-02
And here are the commands and there results

hans@MakingT:~$ sudo lshw -C Network
  *-network
       description: WaveLAN/IEEE
       product: Version 01.01
       vendor: Lucent Technologies
       physical id: 0
       slot: Socket 0
       resources: irq:3
  *-network DISABLED
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 03
       serial: 00:02:3f:78:0e:6e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.8-k2-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s
       resources: iomemory:e8104000-e8104fff ioport:4000-403f irq:11
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=wavelan_cs multicast=yes wireless=WaveLAN



hans@MakingT:~$ lspci -v
0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, fast devsel, latency 0
        Memory at ec000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 96
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: e8000000-e80fffff
        Prefetchable memory behind bridge: f0000000-f7ffffff

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 05) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: e8100000-e81fffff

0000:00:1f.0 ISA bridge: Intel Corp. 82801BA ISA Bridge (LPC) (rev 05)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801BA IDE U100 (rev 05) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0
        I/O ports at 1800 [size=16]

0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 05) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 1820 [size=32]

0000:00:1f.3 SMBus: Intel Corp. 82801BA/BAM SMBus (rev 05)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: medium devsel, IRQ 11
        I/O ports at 1810 [size=16]

0000:00:1f.4 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #2) (rev 05) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 1840 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (rev 05)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1c00 [size=256]
        I/O ports at 1880 [size=64]

0000:00:1f.6 Modem: Intel Corp. Intel 537 [82801BA/BAM AC'97 Modem] (rev 05) (prog-if 00 [Generic])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: medium devsel, IRQ 11
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 5
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 3000 [size=256]
        Memory at e8000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>

0000:02:00.0 CardBus bridge: O2 Micro, Inc. OZ6933 Cardbus Controller (rev 01)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 5
        Memory at 10000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 10400000-107ff000 (prefetchable)
        Memory window 1: 10800000-10bff000
        I/O window 0: 00004400-000044ff
        I/O window 1: 00004800-000048ff
        16-bit legacy interface ports at 0001

0000:02:00.1 CardBus bridge: O2 Micro, Inc. OZ6933 Cardbus Controller (rev 01)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 11
        Memory at 10001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 10c00000-10fff000 (prefetchable)
        Memory window 1: 11000000-113ff000
        I/O window 0: 00004c00-00004cff
        I/O window 1: 00005000-000050ff
        16-bit legacy interface ports at 0001

0000:02:08.0 Ethernet controller: Intel Corp. 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
        Subsystem: Toshiba America Info Systems PRO/100 VE Network Connection
        Flags: bus master, medium devsel, latency 66, IRQ 11
        Memory at e8104000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 4000 [size=64]
        Capabilities: <available only to root>

0000:02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at e8105000 (32-bit, non-prefetchable) [size=2K]
        Memory at e8100000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>



hans@MakingT:~$ lspci -n
0000:00:00.0 0600: 8086:1a30 (rev 04)
0000:00:01.0 0604: 8086:1a31 (rev 04)
0000:00:1e.0 0604: 8086:244e (rev 05)
0000:00:1f.0 0601: 8086:2440 (rev 05)
0000:00:1f.1 0101: 8086:244b (rev 05)
0000:00:1f.2 0c03: 8086:2442 (rev 05)
0000:00:1f.3 0c05: 8086:2443 (rev 05)
0000:00:1f.4 0c03: 8086:2444 (rev 05)
0000:00:1f.5 0401: 8086:2445 (rev 05)
0000:00:1f.6 0703: 8086:2446 (rev 05)
0000:01:00.0 0300: 1002:4c59
0000:02:00.0 0607: 1217:6933 (rev 01)
0000:02:00.1 0607: 1217:6933 (rev 01)
0000:02:08.0 0200: 8086:2449 (rev 03)
0000:02:0a.0 0c00: 104c:8023



hans@MakingT:~$ sudo lsusb -v

Bus 002 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.12-9-386 uhci_hcd
  iProduct                2 Intel Corporation 82801BA/BAM USB (Hub #2)
  iSerial                 1 0000:00:1f.4
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x48
  PortPwrCtrlMask    0x80
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power

Bus 001 Device 001: ID 0000:0000
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0000
  idProduct          0x0000
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.12-9-386 uhci_hcd
  iProduct                2 Intel Corporation 82801BA/BAM USB (Hub #1)
  iSerial                 1 0000:00:1f.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0xc0
  PortPwrCtrlMask    0x80
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power


hans@MakingT:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      WaveLAN  NWID:FFFF  Mode:Ad-Hoc  Frequency:2.4 GHz
          Sensitivity=63/63
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.



hans@MakingT:~$ sudo ifconfig
eth1      Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          inet6 addr: fe80::200:ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:18504 (18.0 KiB)
          Base address:0x100 Memory:d0bb8000-d0bb9000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12601 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12601 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1141739 (1.0 MiB)  TX bytes:1141739 (1.0 MiB)


hans@MakingT:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:00:00:00:00:00
Sending on   LPF/eth1/00:00:00:00:00:00
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database – sleeping.

---

### Post by MakingT on 2006-01-02
can this maybe help?


hans@MakingT:~$ dmesg
8.431000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4296518.444000] eth1: wavelan_watchdog: abort failed, trying reset
[4296518.444000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4296518.444000] eth1: wv_hw_config(): Can't configure the modem
[4296846.126000] NETDEV WATCHDOG: eth1: transmit timed out
[4296846.126000] eth1: wavelan_watchdog: watchdog timer expired
[4296846.126000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4296846.139000] eth1: wavelan_watchdog: abort failed, trying reset
[4296846.139000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4296846.139000] eth1: wv_hw_config(): Can't configure the modem
[4296853.821000] NETDEV WATCHDOG: eth1: transmit timed out
[4296853.821000] eth1: wavelan_watchdog: watchdog timer expired
[4296853.821000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4296853.834000] eth1: wavelan_watchdog: abort failed, trying reset
[4296853.834000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4296853.834000] eth1: wv_hw_config(): Can't configure the modem
[4296866.636000] NETDEV WATCHDOG: eth1: transmit timed out
[4296866.636000] eth1: wavelan_watchdog: watchdog timer expired
[4296866.636000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4296866.649000] eth1: wavelan_watchdog: abort failed, trying reset
[4296866.649000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4296866.649000] eth1: wv_hw_config(): Can't configure the modem
[4296879.451000] NETDEV WATCHDOG: eth1: transmit timed out
[4296879.451000] eth1: wavelan_watchdog: watchdog timer expired
[4296879.451000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4296879.464000] eth1: wavelan_watchdog: abort failed, trying reset
[4296879.464000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4296879.464000] eth1: wv_hw_config(): Can't configure the modem
[4296887.146000] NETDEV WATCHDOG: eth1: transmit timed out
[4296887.146000] eth1: wavelan_watchdog: watchdog timer expired
[4296887.146000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4296887.159000] eth1: wavelan_watchdog: abort failed, trying reset
[4296887.159000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4296887.159000] eth1: wv_hw_config(): Can't configure the modem
[4296902.521000] NETDEV WATCHDOG: eth1: transmit timed out
[4296902.521000] eth1: wavelan_watchdog: watchdog timer expired
[4296902.521000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4296902.534000] eth1: wavelan_watchdog: abort failed, trying reset
[4296902.534000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4296902.534000] eth1: wv_hw_config(): Can't configure the modem
[4297294.216000] NETDEV WATCHDOG: eth1: transmit timed out
[4297294.216000] eth1: wavelan_watchdog: watchdog timer expired
[4297294.216000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297294.229000] eth1: wavelan_watchdog: abort failed, trying reset
[4297294.229000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297294.229000] eth1: wv_hw_config(): Can't configure the modem
[4297299.351000] NETDEV WATCHDOG: eth1: transmit timed out
[4297299.351000] eth1: wavelan_watchdog: watchdog timer expired
[4297299.351000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297299.364000] eth1: wavelan_watchdog: abort failed, trying reset
[4297299.364000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297299.364000] eth1: wv_hw_config(): Can't configure the modem
[4297304.486000] NETDEV WATCHDOG: eth1: transmit timed out
[4297304.486000] eth1: wavelan_watchdog: watchdog timer expired
[4297304.486000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297304.499000] eth1: wavelan_watchdog: abort failed, trying reset
[4297304.499000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297304.499000] eth1: wv_hw_config(): Can't configure the modem
[4297317.301000] NETDEV WATCHDOG: eth1: transmit timed out
[4297317.301000] eth1: wavelan_watchdog: watchdog timer expired
[4297317.301000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297317.314000] eth1: wavelan_watchdog: abort failed, trying reset
[4297317.314000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297317.314000] eth1: wv_hw_config(): Can't configure the modem
[4297330.116000] NETDEV WATCHDOG: eth1: transmit timed out
[4297330.116000] eth1: wavelan_watchdog: watchdog timer expired
[4297330.116000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297330.129000] eth1: wavelan_watchdog: abort failed, trying reset
[4297330.129000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297330.129000] eth1: wv_hw_config(): Can't configure the modem
[4297337.811000] NETDEV WATCHDOG: eth1: transmit timed out
[4297337.811000] eth1: wavelan_watchdog: watchdog timer expired
[4297337.811000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297337.824000] eth1: wavelan_watchdog: abort failed, trying reset
[4297337.824000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297337.824000] eth1: wv_hw_config(): Can't configure the modem
[4297511.906000] NETDEV WATCHDOG: eth1: transmit timed out
[4297511.906000] eth1: wavelan_watchdog: watchdog timer expired
[4297511.906000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297511.919000] eth1: wavelan_watchdog: abort failed, trying reset
[4297511.919000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297511.919000] eth1: wv_hw_config(): Can't configure the modem
[4297517.041000] NETDEV WATCHDOG: eth1: transmit timed out
[4297517.041000] eth1: wavelan_watchdog: watchdog timer expired
[4297517.041000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297517.054000] eth1: wavelan_watchdog: abort failed, trying reset
[4297517.054000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297517.054000] eth1: wv_hw_config(): Can't configure the modem
[4297524.736000] NETDEV WATCHDOG: eth1: transmit timed out
[4297524.736000] eth1: wavelan_watchdog: watchdog timer expired
[4297524.736000] wv_82593_cmd: wavelan_watchdog(): abort timeout (previous command), status 0x12
[4297524.749000] eth1: wavelan_watchdog: abort failed, trying reset
[4297524.749000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297524.749000] eth1: wv_hw_config(): Can't configure the modem
[4297534.991000] NETDEV WATCHDOG: eth1: transmit timed out
[4297534.991000] eth1: wavelan_watchdog: watchdog timer expired
[4297534.991000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297535.004000] eth1: wavelan_watchdog: abort failed, trying reset
[4297535.004000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297535.004000] eth1: wv_hw_config(): Can't configure the modem
[4297550.366000] NETDEV WATCHDOG: eth1: transmit timed out
[4297550.366000] eth1: wavelan_watchdog: watchdog timer expired
[4297550.366000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297550.379000] eth1: wavelan_watchdog: abort failed, trying reset
[4297550.379000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297550.379000] eth1: wv_hw_config(): Can't configure the modem
[4297550.381000] wv_82593_cmd: wv_packet_write(): transmit timeout (previous command), status 0xff
[4297555.501000] NETDEV WATCHDOG: eth1: transmit timed out
[4297555.501000] eth1: wavelan_watchdog: watchdog timer expired
[4297555.501000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x00
[4297555.514000] eth1: wavelan_watchdog: abort failed, trying reset
[4297555.514000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297555.514000] eth1: wv_hw_config(): Can't configure the modem
[4297555.516000] wv_82593_cmd: wv_packet_write(): transmit timeout (previous command), status 0xff
[4297560.636000] NETDEV WATCHDOG: eth1: transmit timed out
[4297560.636000] eth1: wavelan_watchdog: watchdog timer expired
[4297560.636000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x00
[4297560.649000] eth1: wavelan_watchdog: abort failed, trying reset
[4297560.649000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297560.649000] eth1: wv_hw_config(): Can't configure the modem
[4297560.651000] wv_82593_cmd: wv_packet_write(): transmit timeout (previous command), status 0xff
[4297565.771000] NETDEV WATCHDOG: eth1: transmit timed out
[4297565.771000] eth1: wavelan_watchdog: watchdog timer expired
[4297565.771000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x00
[4297565.784000] eth1: wavelan_watchdog: abort failed, trying reset
[4297565.784000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297565.784000] eth1: wv_hw_config(): Can't configure the modem
[4297565.786000] wv_82593_cmd: wv_packet_write(): transmit timeout (previous command), status 0xff
[4297570.906000] NETDEV WATCHDOG: eth1: transmit timed out
[4297570.906000] eth1: wavelan_watchdog: watchdog timer expired
[4297570.906000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x00
[4297570.919000] eth1: wavelan_watchdog: abort failed, trying reset
[4297570.919000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297570.919000] eth1: wv_hw_config(): Can't configure the modem
[4297570.921000] wv_82593_cmd: wv_packet_write(): transmit timeout (previous command), status 0xff
[4297576.041000] NETDEV WATCHDOG: eth1: transmit timed out
[4297576.041000] eth1: wavelan_watchdog: watchdog timer expired
[4297576.041000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x00
[4297576.054000] eth1: wavelan_watchdog: abort failed, trying reset
[4297576.054000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297576.054000] eth1: wv_hw_config(): Can't configure the modem
[4297581.176000] NETDEV WATCHDOG: eth1: transmit timed out
[4297581.176000] eth1: wavelan_watchdog: watchdog timer expired
[4297581.176000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297581.189000] eth1: wavelan_watchdog: abort failed, trying reset
[4297581.189000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297581.189000] eth1: wv_hw_config(): Can't configure the modem
[4297596.551000] NETDEV WATCHDOG: eth1: transmit timed out
[4297596.551000] eth1: wavelan_watchdog: watchdog timer expired
[4297596.551000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297596.564000] eth1: wavelan_watchdog: abort failed, trying reset
[4297596.564000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297596.564000] eth1: wv_hw_config(): Can't configure the modem
[4297857.686000] NETDEV WATCHDOG: eth1: transmit timed out
[4297857.686000] eth1: wavelan_watchdog: watchdog timer expired
[4297857.686000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297857.699000] eth1: wavelan_watchdog: abort failed, trying reset
[4297857.699000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297857.699000] eth1: wv_hw_config(): Can't configure the modem
[4297857.701000] wv_82593_cmd: wv_packet_write(): transmit timeout (previous command), status 0xff
[4297862.821000] NETDEV WATCHDOG: eth1: transmit timed out
[4297862.821000] eth1: wavelan_watchdog: watchdog timer expired
[4297862.821000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x00
[4297862.834000] eth1: wavelan_watchdog: abort failed, trying reset
[4297862.834000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297862.834000] eth1: wv_hw_config(): Can't configure the modem
[4297862.836000] wv_82593_cmd: wv_packet_write(): transmit timeout (previous command), status 0xff
[4297867.956000] NETDEV WATCHDOG: eth1: transmit timed out
[4297867.956000] eth1: wavelan_watchdog: watchdog timer expired
[4297867.956000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x00
[4297867.969000] eth1: wavelan_watchdog: abort failed, trying reset
[4297867.969000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297867.969000] eth1: wv_hw_config(): Can't configure the modem
[4297867.971000] wv_82593_cmd: wv_packet_write(): transmit timeout (previous command), status 0xff
[4297873.091000] NETDEV WATCHDOG: eth1: transmit timed out
[4297873.091000] eth1: wavelan_watchdog: watchdog timer expired
[4297873.091000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x00
[4297873.104000] eth1: wavelan_watchdog: abort failed, trying reset
[4297873.104000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297873.104000] eth1: wv_hw_config(): Can't configure the modem
[4297891.026000] NETDEV WATCHDOG: eth1: transmit timed out
[4297891.026000] eth1: wavelan_watchdog: watchdog timer expired
[4297891.026000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297891.039000] eth1: wavelan_watchdog: abort failed, trying reset
[4297891.039000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297891.039000] eth1: wv_hw_config(): Can't configure the modem
[4297908.961000] NETDEV WATCHDOG: eth1: transmit timed out
[4297908.961000] eth1: wavelan_watchdog: watchdog timer expired
[4297908.961000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297908.974000] eth1: wavelan_watchdog: abort failed, trying reset
[4297908.974000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297908.974000] eth1: wv_hw_config(): Can't configure the modem
[4297919.216000] NETDEV WATCHDOG: eth1: transmit timed out
[4297919.216000] eth1: wavelan_watchdog: watchdog timer expired
[4297919.216000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297919.229000] eth1: wavelan_watchdog: abort failed, trying reset
[4297919.229000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297919.229000] eth1: wv_hw_config(): Can't configure the modem
[4297926.911000] NETDEV WATCHDOG: eth1: transmit timed out
[4297926.911000] eth1: wavelan_watchdog: watchdog timer expired
[4297926.911000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297926.924000] eth1: wavelan_watchdog: abort failed, trying reset
[4297926.924000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297926.924000] eth1: wv_hw_config(): Can't configure the modem
[4297937.166000] NETDEV WATCHDOG: eth1: transmit timed out
[4297937.166000] eth1: wavelan_watchdog: watchdog timer expired
[4297937.166000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297937.179000] eth1: wavelan_watchdog: abort failed, trying reset
[4297937.179000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297937.179000] eth1: wv_hw_config(): Can't configure the modem
[4297952.541000] NETDEV WATCHDOG: eth1: transmit timed out
[4297952.541000] eth1: wavelan_watchdog: watchdog timer expired
[4297952.541000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297952.554000] eth1: wavelan_watchdog: abort failed, trying reset
[4297952.554000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297952.554000] eth1: wv_hw_config(): Can't configure the modem
[4297970.476000] NETDEV WATCHDOG: eth1: transmit timed out
[4297970.476000] eth1: wavelan_watchdog: watchdog timer expired
[4297970.476000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297970.489000] eth1: wavelan_watchdog: abort failed, trying reset
[4297970.489000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297970.489000] eth1: wv_hw_config(): Can't configure the modem
[4297978.171000] NETDEV WATCHDOG: eth1: transmit timed out
[4297978.171000] eth1: wavelan_watchdog: watchdog timer expired
[4297978.171000] wv_82593_cmd: wavelan_watchdog(): abort timeout, status 0x30
[4297978.184000] eth1: wavelan_watchdog: abort failed, trying reset
[4297978.184000] eth1: wv_mmc_init(): Invalid MAC address: FF:FF:FF:...
[4297978.184000] eth1: wv_hw_config(): Can't configure the modem

---

### Post by Lambert on 2006-01-02
Making progress as card is identified and driver loaded for it.

But some things still don't look right.

```
 hans@MakingT:~$ sudo ifconfig
eth1      Link encap:Ethernet  HWaddr 00:00:00:00:00:00
```

did you modify this or is that the HWaddr output was?

I need to research this a little more and figure out how isa cards handle mac addresses.

The manfid and devid I pulled from a site which isn't always correct so good for making that change. You're one sep closer but I'm not sure how many more steps are needed and what's involved in the steps.

---

