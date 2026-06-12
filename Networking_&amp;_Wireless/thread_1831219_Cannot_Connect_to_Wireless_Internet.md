---
title: "Cannot Connect to Wireless Internet"
date: 2011-08-23
forum: Networking &amp; Wireless
---

### Post by JoshuaMiller0 on 2011-08-23
Hi. Recently I've been aving some problems connecting to my wireless internet on Ubuntu.
 
On Windows Vista I never had any problems connecting to our wireless on my laptop. At first on Ubuntu I had no problems connecting (same plan and settings) but now I suddenly cannot connect no matter what I do.
 
My connection I am trying to connect as no changed at all as my Dad says he has not done anything to it. On Ubuntu I have not changed any setting and in fact I was using the internet, was suddenly disconected and I canpt reconnect.
 
I have no problems with being too far away as I have etsted frim various distances including right ext to it. (Ubuntu tells me I have 3-5 bars or range too)
 
The way my wireless conection works is that my Dad has to specifaically tell the connection (I think he does it online but I am not sure) that my computer has permission to connect.
 
The wireless also has a password, it has not changed and I DEFINATELY have it correct.
 
Other people seem to be able to connect very easily on many different devices.
 
I am using Ubuntu version 10.04
 
Please help me and tell me if you need more information. :)

---

### Post by poolet on 2011-08-23
Hello,

Open up a new terminal and type::

```
lshw -C network 
```

```
ifconfig 
```

```
lspci -v
```

```
lsusb -v 
```

```
lsmod
```

at the end paste the output here....

---

### Post by shubham1 on 2011-08-23
can you tell the settings used in your connection go to edit connection then choose wirles and choose your option and click edit to get settings.tell me the ipv6 settings and ipv4 and method used in both.

---

### Post by sharmadepal on 2011-08-25
I have ubuntu 11.04 installed on my compaq 621 laptop and meego installed on samsung N100 netbook.netbook is able to connect & downlaod the software updates from usb modem on latop but i am not able to open any website on the netbook.Netbook is connected through wifi to laptop all the time but websites are not getting opened.  plz help on this one.

---

### Post by Tovarich_Volk on 2011-09-03
I have this same problem. Ubuntu (10.10) worked fine when I was running it on top of Windows. No that I'm using 10.04 I am having issues with this. Firstly, I managed to get the Atheros 5001 driver to work via NDISwrapper, then about a week ago something died, and I got a brief NDISwrapper error message before booting into X. I have since grown completely frustrated and re-installed from a USB key, where the was turned on. now that it is on the hard drive, the hardware is definately turned off, and I have a terminal redout of the above listed commands as follows:

```
shawn@Amato:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:6f:81:20
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=192.168.4.163 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:26 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:c2000000-c200ffff

shawn@Amato:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:72:6f:81:20  
          inet addr:192.168.4.163  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe6f:8120/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:151159 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72925 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:139157797 (139.1 MB)  TX bytes:7431465 (7.4 MB)
          Interrupt:26 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

shawn@Amato:~$ 

shawn@Amato:~$ lspci -v
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
	Subsystem: Hewlett-Packard Company Device 360a
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
	Subsystem: Hewlett-Packard Company Device 360a
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 1a00 [size=256]

00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
	Subsystem: Hewlett-Packard Company Device 360a
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 3080 [size=64]
	I/O ports at 3040 [size=64]
	I/O ports at 3000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
	Subsystem: Hewlett-Packard Company Device 360a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at c0080000 (32-bit, non-prefetchable) [size=512K]

00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
	Subsystem: Hewlett-Packard Company Device 360a
	Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 360a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 360a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at c0007000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 360a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at c0008000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 360a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at c0007400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 360a
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 30c0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
	Subsystem: Hewlett-Packard Company Device 360a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device 360a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 25
	I/O ports at 30f0 [size=8]
	I/O ports at 30e4 [size=4]
	I/O ports at 30e8 [size=8]
	I/O ports at 30e0 [size=4]
	I/O ports at 30d0 [size=16]
	Memory at c0004000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
	Subsystem: Hewlett-Packard Company Device 360a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 26
	Memory at c0009000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 30f8 [size=8]
	Memory at c0007c00 (32-bit, non-prefetchable) [size=256]
	Memory at c0007800 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: c1000000-c1ffffff
	Prefetchable memory behind bridge: 00000000c4000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Memory behind bridge: c2000000-c20fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
	Flags: fast devsel

02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
	Subsystem: Hewlett-Packard Company Device 360a
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at c1000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at c4000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 4000 [size=128]
	[virtual] Expansion ROM at c6000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau

07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at c2000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath5k

shawn@Amato:~$ 
shawn@Amato:~$ lsusb -v

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
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
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
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
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x0158 Mass Storage Device
  bcdDevice           58.87
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              5 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
shawn@Amato:~$ 
shawn@Amato:~$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_nvhdmi     4760  1 
snd_hda_codec_conexant    28873  1 
snd_hda_intel          25805  2 
snd_hda_codec          85759  3 snd_hda_codec_nvhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
snd_timer              23649  2 snd_pcm,snd_seq
softcursor              1565  1 bitblit
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 11104  0 
nvidia              10832442  30 
snd                    71283  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_core              45423  0 
soundcore               8052  1 snd
vga16fb                12757  1 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
i2c_nforce2             6099  0 
edac_mce_amd            9278  0 
vgastate                9857  1 vga16fb
shpchp                 33711  0 
psmouse                65040  0 
serio_raw               4918  0 
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
ndiswrapper           244800  0 
usb_storage            50377  0 
forcedeth              55624  0 
ahci                   38030  3 
pata_amd               11962  0 
shawn@Amato:~$ 

```


The GTK front end for NDIS wrapper has the driver installed (netathw.inf),Yet the device still appears as 'UNCLAIMED'.-- I have also tried several differant versions of this driver which NDIS GTK claims to be incorrect.  Any help?

---

### Post by Tovarich_Volk on 2011-09-06
Anything?

---

### Post by JoshuaMiller0 on 2011-10-04
> **poolet said:**
> 

at the end paste the output here....

```
josh@josh-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:4d:70:63
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:26 ioport:3000(size=256) memory:90410000-90410fff(prefetchable) memory:90400000-9040ffff(prefetchable) memory:90420000-9043ffff(prefetchable)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:4e:33:75:17
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wirelesserrors:
       configuration: broadcast=yes driver=ath5k ip=192.168.1.105 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:92600000-9260ffff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: ham0
       serial: 7a:79:05:8e:bc:f8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=tun driverversion=1.6 firmware=N/A ip=5.142.188.248 multicast=yes
josh@josh-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:4d:70:63  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 .0.0.1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 Base address:0xe000 

ham0      Link encap:Ethernet  HWaddr 7a:79:05:8e:bc:f8  
          inet addr:5.142.188.248  Bcast:5.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::7879:5ff:fe8e:bcf8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1404  Metric:1
          RX packets:202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:76338 (76.3 KB)  TX bytes:7268 (7.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127
```.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30488 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30488 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10234782 (10.2 MB)  TX bytes:10234782 (10.2 MB)

wlan0     Link encap:Ethernet  HWaddr 00:23:4e:33:75:17  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4eff:fe33:7517/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27488 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22921105 (22.9 MB)  TX bytes:2838517 (2.8 MB)

josh@josh-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5110 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, fast devsel, latency 0
	Memory at 92500000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 50e0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 50c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 50a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at 94705c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 94700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00004fff
	Memory behind bridge: 93700000-946fffff
	Prefetchable memory behind bridge: 0000000090400000-00000000914fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 92600000-936fffff
	Prefetchable memory behind bridge: 0000000091500000-00000000924fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 5080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 5060 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 5040 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at 94705800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
	I/O ports at 5108 [size=8]
	I/O ports at 511c [size=4]
	I/O ports at 5100 [size=8]
	I/O ports at 5118 [size=4]
	I/O ports at 5020 [size=32]
	Memory at 94705000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: medium devsel, IRQ 11
	Memory at 94706000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 5000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: fast devsel, IRQ 11
	Memory at 94704000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 360b
	Flags: bus master, fast devsel, latency 0, IRQ 26
	I/O ports at 3000 [size=256]
	Memory at 90410000 (64-bit, prefetchable) [size=4K]
	Memory at 90400000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at 90420000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137b
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at 92600000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k

```
josh@josh-laptop:~$ lsmod
Module                  Size  Used by
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_conexant    22705  1 
binfmt_misc             6587  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
arc4                    1153  2 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ppdev                   5259  0 
snd_seq_dummy           1338  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
vga16fb                11385  0 
snd_rawmidi            19056  1 snd_seq_midi
vgastate                8961  1 vga16fb
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
ath5k                 121632  0 
joydev                  8740  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              205402  1 ath5k
snd_timer              19098  2 snd_pcm,snd_seq
ath                     7611  1 ath5k
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  17 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  288963  2 
cfg80211              126112  3 ath5k,mac80211,ath
soundcore               6620  1 snd
drm_kms_helper         29329  1 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
led_class               2864  1 ath5k
drm                   163651  3 i915,drm_kms_helper
psmouse                63677  0 
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
lp                      7028  0 
serio_raw               3978  0 
output                  1871  1 video
parport                32635  2 ppdev,lp
intel_agp              24375  2 i915
agpgart                31724  2 drm,intel_agp
usbhid                 36110  0 
hid                    67288  1 usbhid
usb_storage            39841  0 
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169
josh@josh-laptop:~$
```[/CODE]

---

### Post by JoshuaMiller0 on 2011-10-04
> **shubham1 said:**
> tell me the ipv6 settings and ipv4 and method used in both.

IPv4:
Automatic (DHCP)

IPv6:
Ignore

(This was done while I was connected and I seem to be disconnected after 'X' ammount of time and then I am unable to reconnect)

---

### Post by wildmanne39 on 2011-10-04
Hi, please run these commands when you are not able to connect with your wireless so we can see what it going on.
```
nm-tool
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
dmesg | egrep 'ath|firm|wlan0'
```
Thank you

---

### Post by briandeyoung on 2011-10-04
I have a similar problem.  Here are my results:


ubuntustudioasus:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             unmanaged
  Default:           no
  HW Address:        00:26:C7:CE:3D:BC

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            jme
  State:             unmanaged
  Default:           no
  HW Address:        BC:AE:C5:9E:97:57

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


ubuntustudioasus:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
ubuntustudioasus:~$ sudo iwlist scan
[sudo] password for jeikemeijer: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

ubuntustudioasus:~$ dmesg | egrep 'ath|firm|wlan0'
[    1.848264] device-mapper: multipath: version 1.2.0 loaded
[    1.848267] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.021735] elantech: assuming hardware version 2, firmware version 4.1.2
[   14.424579] iwlagn 0000:02:00.0: loaded firmware version 128.50.3.1 build 13488
ubuntustudioasus:~$

---

### Post by wildmanne39 on 2011-10-04
Hi briandeyoung, please start your own thread and describe your problem, you can give me a link here, because your wireless card is not the same as the original poster and I will get confused.
Thank you

---

### Post by JoshuaMiller0 on 2011-10-06
> **wildmanne39 said:**
> Hi, please run these commands when you are not able to connect with your wireless so we can see what it going on.

OK will do. I haven't had any problems connecting recently so next  time I do I'll be sure to do this!

Note-to-self: *Save commands onto comp so I can access them when internet is down!*

---

