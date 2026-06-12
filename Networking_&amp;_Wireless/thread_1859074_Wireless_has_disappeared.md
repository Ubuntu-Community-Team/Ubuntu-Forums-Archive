---
title: "Wireless has disappeared"
date: 2011-10-13
forum: Networking &amp; Wireless
---

### Post by alt.kat on 2011-10-13
Hi,

I'm a terrible newbie when it comes to Ubuntu, but I've always been able to muddle along until now. The problem is that my internal wireless card seems to have disappeared from the face of the earth, as has its hardware driver. This thing has been in my computer for years now and I've never had a problem with it, the flip-side being that I no longer have any idea what make it is. I've tried searching for driver updates and updating everything in sight, but nothing seems to work. Could anyone spare some advice for an utterly bewildered newbie? I'm using my mobile to tether my desktop to the wireless network in the house right now and it's not ideal.

Thank you so much (in advance) for attempting to help.

alt.kat

Just found that it is a Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express, or at least that is what the terminal tells me.

---

### Post by westie457 on 2011-10-13
> **alt.kat said:**
> Hi,

I'm a terrible newbie when it comes to Ubuntu, but I've always been able to muddle along until now. The problem is that my internal wireless card seems to have disappeared from the face of the earth, as has its hardware driver. This thing has been in my computer for years now and I've never had a problem with it, the flip-side being that I no longer have any idea what make it is. I've tried searching for driver updates and updating everything in sight, but nothing seems to work. Could anyone spare some advice for an utterly bewildered newbie? I'm using my mobile to tether my desktop to the wireless network in the house right now and it's not ideal.

Thank you so much (in advance) for attempting to help.

alt.kat

Just found that it is a Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express, or at least that is what the terminal tells me.

Hello, welcome to the Forum.

Could you please post the terminal output of ```
lspci -vnn
```
There probably will be others needed as well so this is the start.

---

### Post by alt.kat on 2011-10-13
This is what I get:

00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
    Subsystem: Dell Device [1028:01ad]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge [0604]: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port [8086:2771] (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe900000-feafffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: fe800000-fe8fffff
    Prefetchable memory behind bridge: 0000000040000000-00000000401fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: fe700000-fe7fffff
    Prefetchable memory behind bridge: 0000000040200000-00000000403fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
    Subsystem: Dell Device [1028:01ad]
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at ff80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
    Subsystem: Dell Device [1028:01ad]
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at ff60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
    Subsystem: Dell Device [1028:01ad]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at ff40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
    Subsystem: Dell Device [1028:01ad]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at ff20 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01) (prog-if 20)
    Subsystem: Dell Device [1028:01ad]
    Flags: bus master, medium devsel, latency 0, IRQ 21
    Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Capabilities: <access denied>

00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller [8086:27de] (rev 01)
    Subsystem: Dell Device [1028:01ad]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at ec00 [size=256]
    I/O ports at e8c0 [size=64]
    Memory at febffa00 (32-bit, non-prefetchable) [size=512]
    Memory at febff900 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device [1028:01ad]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell Device [1028:01ad]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
    I/O ports at fe00 [size=8]
    I/O ports at fe10 [size=4]
    I/O ports at fe20 [size=8]
    I/O ports at fe30 [size=4]
    I/O ports at fea0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
    Subsystem: Dell Device [1028:01ad]
    Flags: medium devsel, IRQ 10
    I/O ports at e8a0 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV380 [Radeon X600 (PCIE)] [1002:5b62]
    Subsystem: ATI Technologies Inc Device [1002:0b02]
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at fe9e0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at dc00 [size=256]
    Expansion ROM at fea00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeonfb, radeon

01:00.1 Display controller [0380]: ATI Technologies Inc RV380 [Radeon X600] [1002:5b72]
    Subsystem: ATI Technologies Inc Device [1002:0b03]
    Flags: bus master, fast devsel, latency 0
    Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
    Subsystem: Dell Device [1028:01ad]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fe8f0000 (64-bit, non-prefetchable) [size=64K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: tg3
    Kernel modules: tg3

---

### Post by westie457 on 2011-10-13
Hi you are right it does seem to have disappeared.

Some more commands to run please ```
rfkill list all
``` and ```
lshw -C network
```
This time could you put the output between [code] tags by clicking on the # at the top of the message pane. This makes the information easier to read.

Thank you.

---

### Post by alt.kat on 2011-10-14
Thank you for all your help, clearly saint-like patience is a forte of linux masters!

Here is the code, the first command came up with nothing though:

```
katharine@alexis:~$ rfkill list all
katharine@alexis:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:13:72:75:27:39
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=5751-v3.44a latency=0 multicast=yes
       resources: irq:16 memory:fe8f0000-fe8fffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 0e:f4:a2:48:8b:8e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.184 multicast=yes

```

Thanks again.

---

### Post by westie457 on 2011-10-14
Hello again.
This part of your last post ```
 *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 0e:f4:a2:48:8b:8e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.184 multicast=yes
``` I do not understand.

Is it because you have a mobile phone connected or do you have a rare instance of an usb wireless chip hard-wired to the motherboard.
If it is the phone then I think that in all probability the wireless module might have died or there is a broken wire somewhere.
If the latter is true could you post the output of ```
lsusb
```

Thank you

PS thank you for the compliment of being a Linux Master. In all honesty though I am really a newbie at this, just a glutton for punishment. lol

---

### Post by alt.kat on 2011-10-15
I have a mobile phone connected right now, so that explains that. But why would the wireless card just die? WHY? How could it do this to me etc...

Just in case:  

```
katharine@alexis:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 041e:3040 Creative Technology, Ltd SoundBlaster Live! 24-bit External SB0490
Bus 002 Device 002: ID 045e:0750 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 019: ID 04e8:6863 Samsung Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Commence weeping ad infinitum.

---

