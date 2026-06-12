---
title: "Toshiba l650 11f I want to enable my wireless and Don't know How?"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by Basimoooo777 on 2010-10-01
Hi all please if anyone can help me 
I think my wireless card is detected but there's no driver for it please if anyone can help me to get that driver and how to install it 
and here are some commands I think it will  be helpful to be get helped [B]
*dmesg | grep wlan*
[/B]```

This one doesn't return anything

```

[I][B]uname -rm
[/B][/I] ```

2.6.32-25-generic i686

```

***cat /etc/issue***
```

Ubuntu 10.04.1 LTS \n \l

```

[B][I]lshw -C Network
[/I][/B]```

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c1
       serial: 00:26:6c:51:ef:3f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A ip=192.168.1.3 latency=0 multicast=yes
       resources: irq:34 memory:d5000000-d503ffff ioport:3000(size=128)
  *-network
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=brcm80211 latency=0
       resources: irq:17 memory:d4000000-d4003fff

```

[B][I]lsusb
[/I][/B]```

Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 10f1:1a2a  
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

[I][B]lspci -nn
[/B][/I]```

00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Redwood [Radeon HD 5600 Series] [1002:68c1]
01:00.1 Audio device [0403]: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] [1002:aa60]
02:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
3f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
3f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
3f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)

```

Thanks in advance
Sincerely, Ahmed Basseem

---

### Post by Basimoooo777 on 2010-10-02
please all of you anyone reply I'm really in a great problem

---

### Post by bkratz on 2010-10-02
Here is a thread about that device, I think it will help you

[http://www.uluga.ubuntuforums.org/showthread.php?p=8992826](http://www.uluga.ubuntuforums.org/showthread.php?p=8992826)

---

### Post by Basimoooo777 on 2010-10-02
> **bkratz said:**
> Here is a thread about that device, I think it will help you

[http://www.uluga.ubuntuforums.org/showthread.php?p=8992826](http://www.uluga.ubuntuforums.org/showthread.php?p=8992826)
Thanks too much dearest really it's solved all the problem. Thanks bkratz. u helped me too much
Yours 
Ahmed Basseem

---

### Post by bkratz on 2010-10-02
Congratulations, sure glad to hear you are up and going. Please return to the thread tools and mark the thread [solved] in case it helps someone else.

---

