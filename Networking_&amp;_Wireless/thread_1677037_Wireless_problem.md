---
title: "Wireless problem"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by triadb0y on 2011-01-28
I have fujitsu siemens amilo L1310G.i can`t start wireless card.In helpdesk they told me they only support win xp.Can anybody help me ? Tried acerhk but nothing worked

---

### Post by amsterdamharu on 2011-01-28
Could you run the following commands and post the output?

```
sudo lspci -v
sudo lsusb -v
rfkill list
```

To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]


Do you have a working connection to the Internet through cable?

---

### Post by triadb0y on 2011-01-28
```
root@office-laptop:~# sudo lspci -v
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
    Subsystem: Fujitsu Technology Solutions Device 1098
    Flags: bus master, 66MHz, medium devsel, latency 64
    Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: d0100000-d01fffff
    Prefetchable memory behind bridge: d8000000-dfffffff
    Capabilities: [b0] Subsystem: ATI Technologies Inc RS480 PCI Bridge
    Kernel modules: shpchp

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10)
    Subsystem: ATI Technologies Inc IXP SB400 USB Host Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at d0000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10)
    Subsystem: ATI Technologies Inc IXP SB400 USB Host Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at d0001000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20)
    Subsystem: ATI Technologies Inc IXP SB400 USB2 Host Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at d0002000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [dc] Power Management version 2
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
    Subsystem: ATI Technologies Inc IXP SB400 SMBus Controller
    Flags: 66MHz, medium devsel
    I/O ports at 8420 [size=16]
    Memory at d0003000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: ATI Technologies Inc IXP SB400 IDE Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 8430 [size=16]
    Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
    Subsystem: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=02, subordinate=08, sec-latency=64
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d0200000-d02fffff
    Prefetchable memory behind bridge: 1c000000-21ffffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
    Subsystem: Fujitsu Technology Solutions Device 1098
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
    Memory at d0003400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [40] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: ATI IXP AC97 controller
    Kernel modules: snd-atiixp

00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
    Subsystem: Fujitsu Technology Solutions Device 1098
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
    Memory at d0003800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [40] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: ATI IXP MC97 controller
    Kernel modules: snd-atiixp-modem

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
    Subsystem: Fujitsu Technology Solutions Device 1098
    Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 17
    Memory at d8000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 9000 [size=256]
    Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at d0120000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Kernel driver in use: radeon
    Kernel modules: radeonfb, radeon

02:01.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
    Subsystem: Atheros Communications Inc. Device 2052
    Flags: bus master, medium devsel, latency 168, IRQ 23
    Memory at d0200000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ath5k
    Kernel modules: ath5k

02:0b.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
    Subsystem: Fujitsu Technology Solutions Device 1098
    Flags: bus master, medium devsel, latency 168, IRQ 20
    Memory at d0218000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
    Memory window 0: 1c000000-1ffff000 (prefetchable)
    Memory window 1: 24000000-27fff000
    I/O window 0: 00002000-000020ff
    I/O window 1: 00002400-000024ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

02:0b.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Fujitsu Technology Solutions Device 1098
    Flags: bus master, medium devsel, latency 64, IRQ 23
    Memory at d0219000 (32-bit, non-prefetchable) [size=2K]
    Memory at d0210000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

02:0b.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
    Subsystem: Fujitsu Technology Solutions Device 1098
    Flags: bus master, medium devsel, latency 64, IRQ 22
    Memory at d0214000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

02:0b.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
    Subsystem: Fujitsu Technology Solutions Device 1098
    Flags: bus master, medium devsel, latency 64, IRQ 22
    Memory at d021a000 (32-bit, non-prefetchable) [size=256]
    Memory at d0219c00 (32-bit, non-prefetchable) [size=256]
    Memory at d0219800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

02:0d.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
    Subsystem: Fujitsu Technology Solutions Device 1098
    Flags: bus master, fast devsel, latency 64, IRQ 20
    Memory at d0216000 (32-bit, non-prefetchable) [size=8K]
    [virtual] Expansion ROM at 20000000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 2
    Kernel driver in use: b44
    Kernel modules: b44

root@office-laptop:~# 

```
```

root@office-laptop:~# sudo lsusb -v

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
  iManufacturer           3 Linux 2.6.32-24-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:13.1
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
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood        2 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
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
  iManufacturer           3 Linux 2.6.32-24-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:13.0
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
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x0002
    No power switching (usb 1.0)
    Ganged overcurrent protection
  bPwrOn2PwrGood        2 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

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
  iManufacturer           3 Linux 2.6.32-24-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:13.2
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
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts             8
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

```
```

root@office-laptop:~# rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
yes i have broadband connection

---

### Post by amsterdamharu on 2011-01-28
It looks like your card is installed and active (not a usb device).
The thing I found was:
Atheros Communications Inc. AR2413 802.11bg NIC 
And it's using a driver called ath5k

You could try the following command:

```
sudo ifconfig phy0 up
```

Not sure why it's called phy0 normally it's called wlan0.

You could see what networks are available using the following command
```
ifconfig -a
```

---

### Post by triadb0y on 2011-01-28
```
root@office-laptop:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:40:ca:de:66:f3  
          inet6 addr: fe80::240:caff:fede:66f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2823357 (2.8 MB)  TX bytes:452145 (452.1 KB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4000 (4.0 KB)  TX bytes:4000 (4.0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:79.113.55.7  P-t-P:79.113.48.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:2708 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2441 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2688218 (2.6 MB)  TX bytes:380763 (380.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:ab:c7:f3  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```
```

root@office-laptop:~# sudo ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132

```
```

root@office-laptop:~# sudo ifconfig phy0 up
phy0: ERROR while getting interface flags: No such device

```

---

### Post by triadb0y on 2011-01-28
everytime i start ubuntu i find some wireless networks but can`t connect and after that it disables,now in rfkill list says hard blocked : yes

---

### Post by amsterdamharu on 2011-01-28
I don't have your wireless card so have no experience with it but found the following solution from another user:
[http://ubuntuforums.org/showthread.php?t=1311886](http://ubuntuforums.org/showthread.php?t=1311886)
Try the following commands (after sudo bash you can just copy and paste the rest)
```
sudo bash
rmmod ath5k
rfkill block all
rfkill unblock all
modprobe ath5k
rfkill unblock all
ifconfig wlan0 up
exit

```

---

