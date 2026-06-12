---
title: "atmel pcmcia wifi card"
date: 2006-01-26
forum: Networking &amp; Wireless
---

### Post by dr.lnx on 2006-01-26
hi, i want my pcmcia wifi cart to work... 
i tested the atmel drivers but they didn't work, one time i rebooted and i've seen the  wifi card with iwconfig, but when i reboot another time the card was no more there
what can i do?

lshw:
```
 *-pcmcia
                description: CardBus bridge
                product: PCI4510 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@06:04.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:c8005000-c8005fff irq:16
              *-network
                   description: ATMEL
                   physical id: 0
                   version: AT76C502AR
                   slot: Socket 0

```

cardmgr:
```
cardmgr[12078]: error in file 'config' line 2501: syntax error, unexpected $undefined
cardmgr[12078]: open_sock(socket 0) failed: Device or resource busy
cardmgr[12078]: another cardmgr is already running?

```

cardinfo seems ok, but i can't seed the card in iwconfig

tanks and sorry for my english

---

### Post by Lambert on 2006-01-26
There's firmware that needs to be installed to make the atmel driver work.
You can find it on the install cd or in the repositories.

[http://packages.ubuntu.com/breezy/net/atmel-firmware](http://packages.ubuntu.com/breezy/net/atmel-firmware)

---

### Post by dr.lnx on 2006-01-26
i have atmel_fwl installed but what is the right firmware to choose? where is it? and another thing, atmel_fwl requir (as paramether) the device, i can't seed the device(eth2) what should i run as command?

---

### Post by Lambert on 2006-01-26
The package name is atmel-firmware 

Put your install cd back in and open up synaptic and search for it

or

sudo apt-get install atmel-firmware

or 

the link I gave you in previous post just download from that page and

sudo dpkg -i package_name.deb

---

### Post by dr.lnx on 2006-01-26
i have installad atmel-firmware but i have NOT the device eth2
```
atmel_fwl eth2 /usr/lib/hotplug/firmware/atmel_at76c502.bin
atmel_fwl: eth2 is not an Atmel interface.

```
i can't run that program becouse i have NOT the device eth2 or wlan0

---

### Post by Lambert on 2006-01-26
What's the model # and manufacture of this card?

It looks like the card isn't being inserted into the bus as it should have a physical id and pci bus location.

What do you get when running this command

lspci -v

---

### Post by dr.lnx on 2006-01-26
my card is an ATMEL PCMCIA AT76C502AR so my lspci -v is
```
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] #09 [2109]

0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Po rt (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: c0100000-c01fffff
        Prefetchable memory behind bridge: d0000000-d7ffffff
        Capabilities: [88] #0d [0000]
        Capabilities: [80] Power Management version 2
        Capabilities: [90] Message Signalled Interrupts: 64bit- Queue=0/0 Enable -
        Capabilities: [a0] #10 [0141]

0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: c4000000-c7ffffff
        Prefetchable memory behind bridge: 00000000d8000000-00000000dbf00000
        Capabilities: [40] #10 [0141]
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable -
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at 1800 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1820 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1840 [size=32]

0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1860 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB 2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at c0000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #0a [20a0]

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3) (prog-if 01 [Subt ractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=07, sec-latency=32
        Memory behind bridge: c8000000-c80fffff
        Capabilities: [50] #0d [0000]

0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH 6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1c00 [size=256]
        I/O ports at 1880 [size=64]
        Memory at c0000800 (32-bit, non-prefetchable) [size=512]
        Memory at c0000400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: medium devsel, IRQ 20
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: [50] Power Management version 2

0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0

0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03 ) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 18f0 [size=16]
        Capabilities: [70] Power Management version 2

0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Contro ller (rev 03)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: medium devsel, IRQ 11
        I/O ports at 20a0 [size=32]

0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 546 2 (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems: Unknown device ff05
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 3000 [size=256]
        Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #10 [0001]
        Capabilities: [80] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable -

0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4351 (rev 10)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at c4000000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 4000 [size=256]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Vital Product Data
        Capabilities: [5c] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable -
        Capabilities: [e0] #10 [0011]

0000:06:02.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
        Subsystem: Intel Corp.: Unknown device 2741
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at c8004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2

0000:06:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controlle r (rev 03)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at c8005000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 40000000-403ff000 (prefetchable)
        Memory window 1: 40400000-407ff000
        I/O window 0: 00005000-000050ff
        I/O window 1: 00005400-000054ff
        16-bit legacy interface ports at 0001

0000:06:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controlle r (rev 01) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at c8006000 (32-bit, non-prefetchable) [size=2K]
        Memory at c8000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

root@lippo:/home/rix/uni/assembly/progetto# lspci -v
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] #09 [2109]

0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: c0100000-c01fffff
        Prefetchable memory behind bridge: d0000000-d7ffffff
        Capabilities: [88] #0d [0000]
        Capabilities: [80] Power Management version 2
        Capabilities: [90] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
        Capabilities: [a0] #10 [0141]

0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: c4000000-c7ffffff
        Prefetchable memory behind bridge: 00000000d8000000-00000000dbf00000
        Capabilities: [40] #10 [0141]
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at 1800 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1820 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1840 [size=32]

0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1860 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at c0000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #0a [20a0]

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=07, sec-latency=32
        Memory behind bridge: c8000000-c80fffff
        Capabilities: [50] #0d [0000]

0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1c00 [size=256]
        I/O ports at 1880 [size=64]
        Memory at c0000800 (32-bit, non-prefetchable) [size=512]
        Memory at c0000400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: medium devsel, IRQ 20
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: [50] Power Management version 2

0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 0

0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 18f0 [size=16]
        Capabilities: [70] Power Management version 2

0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: medium devsel, IRQ 11
        I/O ports at 20a0 [size=32]

0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5462 (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems: Unknown device ff05
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 3000 [size=256]
        Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #10 [0001]
        Capabilities: [80] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4351 (rev 10)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at c4000000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 4000 [size=256]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Vital Product Data
        Capabilities: [5c] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable-
        Capabilities: [e0] #10 [0011]

0000:06:02.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
        Subsystem: Intel Corp.: Unknown device 2741
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at c8004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2

0000:06:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 03)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at c8005000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 40000000-403ff000 (prefetchable)
        Memory window 1: 40400000-407ff000
        I/O window 0: 00005000-000050ff
        I/O window 1: 00005400-000054ff
        16-bit legacy interface ports at 0001

0000:06:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller (rev 01) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at c8006000 (32-bit, non-prefetchable) [size=2K]
        Memory at c8000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2


```

---

### Post by Lambert on 2006-01-26
I'm away from my linux box but look in /etc/pcmcia

Do you have a folder called atmel.conf

If so post the contents of that file here.

It might also be in /etc/pcmcia/config

What I 'm looking for is something like this.

```

card "ATMEL 11 Mbps Wireless RFMD PCMCIA Card"
  version "ATMEL", "AT76C502AR"
  bind "atmel_cs"

```


If you don't see it anywhere, you can try adding this to the /etc/pcmcia/config.opts (do not touch the config file, make sure you're editing the config.opts folder.) Then reboot and run lshw command to see if you have a physical id and location on the pci bus for the device.

Also when you plug the card in look in /var/log/messages for any output and post that here.

---

### Post by dr.lnx on 2006-01-26
this is my config file atmel.conf
```

device "pcmf502"
  class "network" module "pcmf502"

device "pcmf502r"
  class "network" module "pcmf502r"

device "pcmf502r3"
  class "network" module "pcmf502r3"

device "pcmf504"
  class "network" module "pcmf504"

device "pcmf504_2958"
  class "network" module "pcmf504_2958"

device "pcmf504A_2958"
  class "network" module "pcmf504A_2958"

device "pcmf502rd"
  class "network" module "pcmf502rd"

device "pcmf502re"
  class "network" module "pcmf502re"

card "ATMEL 11 Mbps Wireless PCMCIA Card"
  version "ATMEL", "AT76C502"
  bind "pcmf502"

card "ATMEL 11 Mbps Wireless RFMD PCMCIA Card"
  version "ATMEL", "AT76C502AR"
  bind "pcmf502r"

card "ATMEL 11 Mbps Wireless 504 PCMCIA Card"
  version "ATMEL", "AT76C504"
  bind "pcmf504"

card "ATMEL 11 Mbps Wireless 504A PCMCIA Card"
  version "ATMEL", "AT76C504A"
  bind "pcmf504A_2958"

card "ATMEL 11 Mbps Wireless 504+2958 PCMCIA Card"
  version "ATMEL", "AT76C504_R"
  bind "pcmf504_2958"

card "ATMEL 11 Mbps Wireless RFMD Revision D PCMCIA Card"
  version "ATMEL", "AT76C502AR_D"
  bind "pcmf502rd"

card "ATMEL 11 Mbps Wireless RFMD Revision E PCMCIA Card"
  version "ATMEL", "AT76C502AR_E"
  bind "pcmf502re"
 
card "ATMEL 11 Mbps SiteCom PCMCIA Card"
  manfid 0xd601, 0x0007
  bind "pcmf502r"

card "Belkin F5D6020"
  version "Belkin", "11Mbps-Wireless-Notebook-Network-Adapter"
  manfid 0x01bf, 0x3302
  bind "pcmf502re"

card "3Com 3CRWE62092B 11Mbps WLAN PC Card"
  manfid 0x0101, 0x0696
  bind "pcmf502r3"

card "3Com 3CRWE62092B 11Mbps WLAN PC Card"
  manfid 0x0101, 0x0620
  bind "pcmf502r3"

card "3Com 3CRSHPW_96 Wireless LAN PC Card"
  manfid 0x0101, 0x696
  bind "pcmf502r3"

card "SMC 2632W V2 11Mbps 802.11b WLAN Card"
  version "SMC", "2632W-V2"
  manfid 0x01bf, 0xb301
  bind "pcmf502r"

card "11WP611AL-E"
  version "11WAVE", "11WP611AL-E"
  manfid 0x0000, 0x0000
  bind "pcmf502rd"

```

is it correct? or i have to write somting else?

---

### Post by dr.lnx on 2006-01-26
ok, i have add the line you suggest me to atmel.conf, now i can see eth2 but if i try
iwconfig eth2 mode monitor it says
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth2 ; Invalid argument.

---

### Post by dr.lnx on 2006-01-26
i hace tryed this command too
 atmel_fwl eth2 /usr/lib/hotplug/firmware/atmel_at76c502.bin
but with no result

---

### Post by Lambert on 2006-01-26
Post the output of these commands

lshw (just the section on the card)
iwconfig
ifconfig

Did you get atmel-firmware installed? I'd like somebody to confirm if it's needed on breezy as I  believe it is but could be wrong.

---

### Post by dr.lnx on 2006-01-26
lshw:
```
*-pcmcia
                description: CardBus bridge
                product: PCI4510 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@06:04.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:c8005000-c8005fff irq:16
              *-network
                   description: ATMEL
                   physical id: 0
                   version: AT76C502AR
                   slot: Socket 0
                   resources: irq:3

```

iwconfig
```
eth2      IEEE 802.11-DS  ESSID:""
          Mode:Managed  Frequency:2.427 GHz  Access Point: FF:00:00:00:00:00
          Bit Rate:11 Mb/s
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig
```
eth2      Link encap:Ethernet  HWaddr 00:04:DB:01:15:23
          inet6 addr: fe80::204:dbff:fe01:1523/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100
```

ethernet??? why?

---

### Post by Lambert on 2006-01-26
I'm going to have to  bow out of this for now as I'm not that familiar with atmel. And looking at your output I'm not real sure what's happening at the moment.

1. I didn't see yet where you answered if you installed atmel-firmware from the repos. This might be necessary.
2. Your card doesn't look to be identifying properly to lshw. I'm expecting to see a physical id and pci bus location along with configuration parameters. But it appears to be showing up with iwconfig.
3. I'm wondering what 802.110ds is also, not sure here. I did see a search that mentioned something about firmware problem when this shows but ???? that's where my curiosity about atmel-firmware comes in
4. I'm curious if the driver that comes with breezy is correct for this device and you need to compile and install a different one, but this is where my knowledge on atmel lacks

I hope someone else with atmel experience sees this or you can find something with google.

Use as many combinations of search terms as you can with what you have.

atmel 802.11-ds
802.11-ds at76c502
at76c502 debian

Also did you remove card and replug and see what /var/log/messages show?

Sorry I couldn't offer more...:(

---

### Post by dr.lnx on 2006-01-27
anyone could help me resolv the problem?

---

### Post by Lambert on 2006-01-28
Didn't see any response yet, so a bump for you and a little trick I read you can try.


Why are we doing this? to change a setting with pcmcia_core which might help your card to be recognized (not sure if this is your problem, just something to try)

> 
The pcmcia_core module has the cis_speed parameter for changing the
     memory speed used for accessing a card's Card Information Structure
     (CIS).  On some systems, increasing this parameter (i.e., slowing
     down card accesses) may fix card recognition problems 
1. Remove the card from the slot along with anything else you might have in another pcmcia slot.
2. then type these commands from the terminal. each command needs root privledge so run as root or prefix with sudo

```
modprobe -r pcmcia
modprobe -r yenta_socket
modprobe -r rsrc_static
modprobe -r pcmcia_core

``` 
These unload all these modules 

Now to reload them but with a slight change to pcmcia_core

```
 modprobe pcmcia_core cis_speed=600
modprobe pcmcia
modprobe yenta_socket
modprobe rsrc_static

``` 

As I said, this might do nothing but now plug your card in and re-run lshw to see if it's different and try to configure your device/interface. If nothing, consider going through this again and try increasing the cis_speed a little higher, maybe cis_speed=1200 but don't get caught in an infinite loop of increasing this, after a couple times if no change then it's not your problem.

---

