---
title: "Realtek RTL8187 USB adapter (Alfa AWUSO36H)"
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by zipeppe on 2011-01-19
Hello friends

I got this USB 1W adapter for my laptop and works perfectly with windows.

The adapter has been moved to my Linux box Ubuntu 10.10 kernel updated to  2.6.35-22-generic. 

No way to have the USB adapter working.

Here's the **lsusb -v** output:

```

Bus 001 Device 005: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x8187 RTL8187 Wireless Adapter
  bcdDevice            1.00
  iManufacturer           1 Manufacturer_Realtek_RTL8187_
  iProduct                2 RTL8187_Wireless
  iSerial                 3 00C0CA47807A
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 Wireless Network Card
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              5 Bulk-IN,Bulk-OUT,Bulk-OUT
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)


```

I have downloaded the latest driver from Realtek (rtl8187L_linux_26.1040.0820.2010.release), it compiles and installs without error. The new module is **r8187l** and once loaded I can see  all the infos as shown by the **modinfo r8187l** command:

```

filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/r8187l.ko
description:    Linux driver for Realtek RTL8187 WiFi cards
author:         Andrea Merello <andreamrl@tiscali.it>
version:        V 1.1
license:        GPL
license:        GPL
author:         Copyright (C) 2004 Intel Corporation <jketreno@linux.intel.com>
description:    802.11 data/management/control stack
license:        GPL
description:    HostAP crypto
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: TKIP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: CCMP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: WEP
author:         Jouni Malinen
srcversion:     10F6B365E854ECA375AD262
alias:          usb:v0846p6A00d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p6100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8187d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p8187d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.35-22-generic SMP mod_unload modversions 686 
parm:           ifname:charp
parm:           devname: Net interface name,ath%d=default
parm:           channels: Channel bitmask for specific locales. NYI (int)

```

This is what happens when the USB adapter has plugged in the USB port:

**tail -f /var/log/messages**
```
Jan 19 17:15:13 ibm kernel: [16034.688034] usb 1-4: new high speed USB device using ehci_hcd and address 8
Jan 19 17:15:13 ibm kernel: [16034.830722] rtl8187L: Reported EEPROM chip is a 93c46 (1Kbit)
Jan 19 17:15:13 ibm kernel: [16034.976572] rtl8187L: Card MAC address is aa:bb:cc:dd:ee:ff
Jan 19 17:15:14 ibm kernel: [16035.157400] rtl8187L: Card reports RF frontend Realtek 8225
Jan 19 17:15:14 ibm kernel: [16035.157406] rtl8187L: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO Realtek
Jan 19 17:15:15 ibm kernel: [16036.293147] rtl8187L: This seems a new V2 radio: rtl8225_zebra2
Jan 19 17:15:15 ibm kernel: [16036.293289] rtl8187L: PAPE from CONFIG2: 0
Jan 19 17:15:15 ibm kernel: [16036.315788] rtl8187L: EEPROM Customer ID: FF
Jan 19 17:15:15 ibm kernel: [16036.315791] 
Jan 19 17:15:15 ibm kernel: [16036.317615] =====================>rtl8180_proc_init_one
Jan 19 17:15:15 ibm kernel: [16036.317662] rtl8187L: Driver probe completed
Jan 19 17:15:15 ibm kernel: [16036.317665] 
Jan 19 17:15:15 ibm kernel: [16036.319549] rtl8187L: Now Radio On
Jan 19 17:15:15 ibm kernel: [16036.346664] udev[4636]: renamed network interface wlan0 to *wlan3*
Jan 19 17:15:15 ibm kernel: [16036.350387] rtl8187L: rtl8180_open process
Jan 19 17:15:15 ibm kernel: [16036.951288] rtl8187L: Card successfully reset
Jan 19 17:15:19 ibm kernel: [16040.865573] ADDRCONF(NETDEV_UP): wlan3: link is not ready

```

After that a new *wlan3* interface is available and up:

**ifconfig**
```

wlan3     Link encap:Ethernet  HWaddr aa:bb:cc:dd:ee:ff  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Despite the fact everything seems ok, it does not authenticate to the AP:

```

Jan 19 17:20:57 ibm kernel: [16378.712824] rtl8187L: rtl8180_open process
Jan 19 17:20:58 ibm kernel: [16379.311822] rtl8187L: Card successfully reset
Jan 19 17:21:02 ibm kernel: [16383.103034] rtl8187L: EE:cannot submit RX command. URB_STATUS ffffff8d
Jan 19 17:21:02 ibm kernel: [16383.144359] ADDRCONF(NETDEV_UP): wlan3: link is not ready
Jan 19 17:21:02 ibm kernel: [16383.222010] Linking with Alice
Jan 19 17:21:02 ibm kernel: [16383.299369] Linking with Alice
Jan 19 17:21:02 ibm kernel: [16383.476027] rtl8187L: rtl8180_close process
Jan 19 17:21:02 ibm kernel: [16383.515076] rtl8187L: Now Radio Off
Jan 19 17:21:04 ibm kernel: [16385.296485] pci 0000:02:1d.0: wake-up capability enabled by ACPI
Jan 19 17:21:04 ibm kernel: [16385.319061] pci 0000:02:1d.0: wake-up capability disabled by ACPI
Jan 19 17:21:04 ibm kernel: [16385.333547] tg3 0000:03:01.0: BAR 0: set to [mem 0xfb100000-0xfb10ffff 64bit] (PCI address [0xfb100000-0xfb10ffff]
Jan 19 17:21:04 ibm kernel: [16385.451896] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jan 19 17:21:04 ibm kernel: [16385.508221] rtl8187L: rtl8180_open process
Jan 19 17:21:05 ibm kernel: [16386.107423] rtl8187L: Card successfully reset
Jan 19 17:21:08 ibm kernel: [16389.900888] rtl8187L: EE:cannot submit RX command. URB_STATUS ffffff8d
Jan 19 17:21:08 ibm kernel: [16389.942568] ADDRCONF(NETDEV_UP): wlan3: link is not ready
Jan 19 17:21:09 ibm kernel: [16390.069536] rtl8187L: rtl8180_close process
Jan 19 17:21:09 ibm kernel: [16390.080971] rtl8187L: Now Radio Off
Jan 19 17:21:09 ibm kernel: [16390.160122] rtl8187L: rtl8180_open process
Jan 19 17:21:09 ibm kernel: [16390.759342] rtl8187L: Card successfully reset
Jan 19 17:21:13 ibm kernel: [16394.571051] rtl8187L: EE:cannot submit RX command. URB_STATUS ffffff8d
Jan 19 17:21:13 ibm kernel: [16394.615896] ADDRCONF(NETDEV_UP): wlan3: link is not ready
Jan 19 17:21:15 ibm kernel: [16396.476506] pci 0000:02:1d.0: wake-up capability enabled by ACPI
Jan 19 17:21:15 ibm kernel: [16396.540668] pci 0000:02:1d.0: wake-up capability disabled by ACPI
Jan 19 17:21:15 ibm kernel: [16396.556531] tg3 0000:03:01.0: BAR 0: set to [mem 0xfb100000-0xfb10ffff 64bit] (PCI address [0xfb100000-0xfb10ffff]
Jan 19 17:21:15 ibm kernel: [16396.674461] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jan 19 17:21:15 ibm kernel: [16396.815095] Linking with Alice
Jan 19 17:21:15 ibm kernel: [16396.934716] Linking with Alice
Jan 19 17:21:16 ibm kernel: [16397.035215] Linking with Alice
Jan 19 17:21:16 ibm kernel: [16397.121407] Linking with Alice
Jan 19 17:21:18 ibm kernel: [16399.185095] Linking with Alice
Jan 19 17:21:20 ibm kernel: [16401.228033] Linking with Alice
Jan 19 17:21:22 ibm kernel: [16403.392532] Linking with Alice
Jan 19 17:21:24 ibm kernel: [16405.553519] Linking with Alice
Jan 19 17:21:26 ibm kernel: [16407.622068] Linking with Alice
Jan 19 17:21:27 ibm kernel: [16408.549306] Linking with Alice
Jan 19 17:21:27 ibm kernel: [16408.636663] Linking with Alice
Jan 19 17:21:29 ibm kernel: [16410.684522] Linking with Alice
Jan 19 17:21:31 ibm kernel: [16412.729700] Linking with Alice
Jan 19 17:21:33 ibm kernel: [16414.776039] Linking with Alice
Jan 19 17:21:35 ibm kernel: [16416.889520] Linking with Alice
Jan 19 17:21:37 ibm kernel: [16418.936041] Linking with Alice
Jan 19 17:21:38 ibm kernel: [16419.883367] Linking with Alice
Jan 19 17:21:38 ibm kernel: [16419.982706] Linking with Alice
Jan 19 17:21:41 ibm kernel: [16422.028018] Linking with Alice
Jan 19 17:21:43 ibm kernel: [16424.198123] Linking with Alice
Jan 19 17:21:45 ibm kernel: [16426.244029] Linking with Alice
Jan 19 17:21:47 ibm kernel: [16428.354505] Linking with Alice
Jan 19 17:21:49 ibm kernel: [16430.400526] Linking with Alice
Jan 19 17:21:50 ibm kernel: [16431.342248] Linking with Alice
Jan 19 17:21:50 ibm kernel: [16431.420856] Linking with Alice
Jan 19 17:21:52 ibm kernel: [16433.464523] Linking with Alice
Jan 19 17:21:54 ibm kernel: [16435.508029] Linking with Alice
Jan 19 17:21:56 ibm kernel: [16437.588533] Linking with Alice
Jan 19 17:21:58 ibm kernel: [16439.656031] Linking with Alice
Jan 19 17:21:59 ibm kernel: [16440.033541] rtl8187L: rtl8180_close process
Jan 19 17:21:59 ibm kernel: [16440.044829] rtl8187L: Now Radio Off
Jan 19 17:21:59 ibm kernel: [16440.136956] rtl8187L: rtl8180_open process
Jan 19 17:21:59 ibm kernel: [16440.736072] rtl8187L: Card successfully reset
Jan 19 17:22:03 ibm kernel: [16444.548912] rtl8187L: EE:cannot submit RX command. URB_STATUS ffffff8d
Jan 19 17:22:03 ibm kernel: [16444.589943] ADDRCONF(NETDEV_UP): wlan3: link is not ready
Jan 19 17:22:03 ibm kernel: [16444.667259] Linking with Alice
Jan 19 17:22:03 ibm kernel: [16444.744868] Linking with Alice
Jan 19 17:22:03 ibm kernel: [16444.913553] rtl8187L: rtl8180_close process
Jan 19 17:22:03 ibm kernel: [16444.959319] rtl8187L: Now Radio Off
Jan 19 17:22:05 ibm kernel: [16446.736489] pci 0000:02:1d.0: wake-up capability enabled by ACPI
Jan 19 17:22:05 ibm kernel: [16446.758547] pci 0000:02:1d.0: wake-up capability disabled by ACPI
Jan 19 17:22:05 ibm kernel: [16446.772253] tg3 0000:03:01.0: BAR 0: set to [mem 0xfb100000-0xfb10ffff 64bit] (PCI address [0xfb100000-0xfb10ffff]
Jan 19 17:22:05 ibm kernel: [16446.890334] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jan 19 17:22:05 ibm kernel: [16446.939588] rtl8187L: rtl8180_open process
Jan 19 17:22:06 ibm kernel: [16447.538813] rtl8187L: Card successfully reset
Jan 19 17:22:10 ibm kernel: [16451.335764] rtl8187L: EE:cannot submit RX command. URB_STATUS ffffff8d
Jan 19 17:22:10 ibm kernel: [16451.380756] ADDRCONF(NETDEV_UP): wlan3: link is not ready
Jan 19 17:22:10 ibm kernel: [16451.473531] rtl8187L: rtl8180_close process
Jan 19 17:22:10 ibm kernel: [16451.484855] rtl8187L: Now Radio Off
Jan 19 17:22:10 ibm kernel: [16451.577481] rtl8187L: rtl8180_open process
Jan 19 17:22:11 ibm kernel: [16452.176720] rtl8187L: Card successfully reset
Jan 19 17:22:14 ibm kernel: [16455.964438] rtl8187L: EE:cannot submit RX command. URB_STATUS ffffff8d
Jan 19 17:22:15 ibm kernel: [16456.005529] ADDRCONF(NETDEV_UP): wlan3: link is not ready
Jan 19 17:22:16 ibm kernel: [16457.876484] pci 0000:02:1d.0: wake-up capability enabled by ACPI
Jan 19 17:22:16 ibm kernel: [16457.932299] pci 0000:02:1d.0: wake-up capability disabled by ACPI
Jan 19 17:22:16 ibm kernel: [16457.949034] tg3 0000:03:01.0: BAR 0: set to [mem 0xfb100000-0xfb10ffff 64bit] (PCI address [0xfb100000-0xfb10ffff]
Jan 19 17:22:17 ibm kernel: [16458.067284] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jan 19 17:22:17 ibm kernel: [16458.202238] Linking with Alice
Jan 19 17:22:17 ibm kernel: [16458.457183] Linking with Alice
Jan 19 17:22:17 ibm kernel: [16458.473024] rtl8187L: rtl8180_close process
Jan 19 17:22:17 ibm kernel: [16458.517039] rtl8187L: Now Radio Off

```

This is using Wicd Network Manager which drives perfectly other USB dongles. For instance, it's ok using a **rt2870sta** adapter:

```

Jan 19 17:29:59 ibm kernel: [16920.111672] -->RTUSBVenderReset
Jan 19 17:29:59 ibm kernel: [16920.112671] <--RTUSBVenderReset
Jan 19 17:30:01 ibm kernel: [16922.410728] Key1Str is Invalid key length(0) or Type(0)
Jan 19 17:30:01 ibm kernel: [16922.410765] Key2Str is Invalid key length(0) or Type(0)
Jan 19 17:30:01 ibm kernel: [16922.410800] Key3Str is Invalid key length(0) or Type(0)
Jan 19 17:30:01 ibm kernel: [16922.410837] Key4Str is Invalid key length(0) or Type(0)
Jan 19 17:30:01 ibm kernel: [16922.411484] 1. Phy Mode = 0
Jan 19 17:30:01 ibm kernel: [16922.411487] 2. Phy Mode = 0
Jan 19 17:30:01 ibm kernel: [16922.527178] 3. Phy Mode = 0
Jan 19 17:30:01 ibm kernel: [16922.566216] MCS Set = 00 00 00 00 00
Jan 19 17:30:01 ibm kernel: [16922.581168] <==== rt28xx_init, Status=0
Jan 19 17:30:01 ibm kernel: [16922.593164] 0x1300 = 000a4200
Jan 19 17:30:01 ibm kernel: [16922.697132] ERROR!!! RTMPSetTimer failed, Halt in Progress!
Jan 19 17:30:04 ibm kernel: [16925.058655] -->RTUSBVenderReset
Jan 19 17:30:04 ibm kernel: [16925.059651] <--RTUSBVenderReset
Jan 19 17:30:06 ibm kernel: [16927.355781] Key1Str is Invalid key length(0) or Type(0)
Jan 19 17:30:06 ibm kernel: [16927.355818] Key2Str is Invalid key length(0) or Type(0)
Jan 19 17:30:06 ibm kernel: [16927.355854] Key3Str is Invalid key length(0) or Type(0)
Jan 19 17:30:06 ibm kernel: [16927.355891] Key4Str is Invalid key length(0) or Type(0)
Jan 19 17:30:06 ibm kernel: [16927.356612] 1. Phy Mode = 0
Jan 19 17:30:06 ibm kernel: [16927.356615] 2. Phy Mode = 0
Jan 19 17:30:06 ibm kernel: [16927.471222] 3. Phy Mode = 0
Jan 19 17:30:06 ibm kernel: [16927.510158] MCS Set = 00 00 00 00 00
Jan 19 17:30:06 ibm kernel: [16927.525174] <==== rt28xx_init, Status=0
Jan 19 17:30:06 ibm kernel: [16927.549146] 0x1300 = 000a4200
Jan 19 17:30:08 ibm kernel: [16929.408482] pci 0000:02:1d.0: wake-up capability enabled by ACPI
Jan 19 17:30:08 ibm kernel: [16929.430738] pci 0000:02:1d.0: wake-up capability disabled by ACPI
Jan 19 17:30:08 ibm kernel: [16929.448053] tg3 0000:03:01.0: BAR 0: set to [mem 0xfb100000-0xfb10ffff 64bit] (PCI address [0xfb100000-0xfb10ffff]
Jan 19 17:30:08 ibm kernel: [16929.566369] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jan 19 17:30:11 ibm kernel: [16932.026225] -->RTUSBVenderReset
Jan 19 17:30:11 ibm kernel: [16932.027227] <--RTUSBVenderReset
Jan 19 17:30:13 ibm kernel: [16934.381286] Key1Str is Invalid key length(0) or Type(0)
Jan 19 17:30:13 ibm kernel: [16934.381322] Key2Str is Invalid key length(0) or Type(0)
Jan 19 17:30:13 ibm kernel: [16934.381357] Key3Str is Invalid key length(0) or Type(0)
Jan 19 17:30:13 ibm kernel: [16934.381394] Key4Str is Invalid key length(0) or Type(0)
Jan 19 17:30:13 ibm kernel: [16934.382041] 1. Phy Mode = 0
Jan 19 17:30:13 ibm kernel: [16934.382044] 2. Phy Mode = 0
Jan 19 17:30:13 ibm kernel: [16934.499717] 3. Phy Mode = 0
Jan 19 17:30:13 ibm kernel: [16934.539728] MCS Set = 00 00 00 00 00
Jan 19 17:30:13 ibm kernel: [16934.554672] <==== rt28xx_init, Status=0
Jan 19 17:30:13 ibm kernel: [16934.566736] 0x1300 = 000a4200
Jan 19 17:30:14 ibm kernel: [16935.049627] BIRIdx(0): RXDMALen not multiple of 4.[14386], BulkInBufLen = 76)
Jan 19 17:30:15 ibm kernel: [16936.731754] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=3)
Jan 19 17:30:23 ibm kernel: [16944.399777] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 142
Jan 19 17:30:23 ibm kernel: [16944.400087] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)

```

What can I try to make my RTL8187 up and running?

---

### Post by zipeppe on 2011-01-20
Up 8-[

---

### Post by zipeppe on 2011-01-23
up

---

### Post by panosst on 2011-04-24
Did you manage to make it work? 
(I have the ecxact same problem with a rtl8187l usb device)

---

### Post by dangerous666 on 2011-10-26
Exactly the same issue here since Natty. Did you figure out how to make it work?

---

