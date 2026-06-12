---
title: "Wireless Network IS NOT detected, Wireless card IS (IBM T30 laptop, Atheros AR5001X+)"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by Imran-UK on 2010-01-27
Hey all,

I am using Ubuntu 9.10, a Netgear PCMCIA Wireless WG511T on an IBM T23 (not T30 as in thread title, sorry) laptop.

So I've been reading many threads about Atheros AR5001X+ Wireless Network Adapter not working. I have one of these and the adaptor is detected but my problem is slightly different: the adaptor is detected and appears to be working fine, the only snag is that that my **wireless router **is not detected. Other wireless networks in my vicinity are detected but not my own. Also I have successfully connected to a colleagues 3G wireless dongle nearby and got a working internet connection.

Also when I perform a scan with "iwlist wlan0 scanning" it does not list my wireless router.

As an aside, I also have a HTC G1 which has problems with this wireless router. It appears to get an IP address and connect successfully but when browing web pages it cannot connect. Some of my colleagues have Apple Macs and iPhones which have no problems connecting.

Help!

Some information:

The wireless router is:     

```
Firmware Version
    4.05.04
      Boot Version
    1.03.08
      Hardware
   Belkin F5D7130
```I have highlighted some lines in dmesg output below that might relevant. They refer to setting the card to a USA power profile? I'm in the UK.

```
lspci:
07:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

lspci -v:
07:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
    Subsystem: Netgear Device 5b00
    Flags: bus master, medium devsel, latency 168, IRQ 11
    Memory at c8000000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k

lshw:

           *-pcmcia:1
                description: CardBus bridge
                product: PCI1420 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: irq:11 memory:51000000-51000fff ioport:2800(size=256) ioport:2c00(size=256) memory:f4000000-f7ffffff(prefetchable) memory:c8000000-cbffffff
              *-network
                   description: AR5001-0000-0000
                   product: Wireless LAN Reference Card
                   vendor: Atheros Communications, Inc.
                   physical id: 0
                   version: 00
                   slot: Socket 1

     *-network
          description: Wireless interface
          product: Atheros AR5001X+ Wireless Network Adapter
          vendor: Atheros Communications Inc.
          physical id: 1
          bus info: pci@0000:07:00.0
          logical name: wmaster0
          version: 01
          serial: 00:18:4d:95:40:f0
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list logical ethernet physical wireless
          configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
          resources: irq:11 memory:c8000000-c800ffff

dmesg:

[   21.556268] yenta_cardbus 0000:02:00.0: CardBus bridge found [1014:023b]
[   21.556292] yenta_cardbus 0000:02:00.0: Using INTVAL to route CSC interrupts to PCI
[   21.556298] yenta_cardbus 0000:02:00.0: Routing CardBus interrupts to PCI
[   21.556306] yenta_cardbus 0000:02:00.0: TI: mfunc 0x01d21022, devctl 0x64
[   21.755333] psmouse serio1: ID: 10 00 64
[   21.803100] yenta_cardbus 0000:02:00.0: ISA IRQ mask 0x0438, PCI irq 11
[   21.803110] yenta_cardbus 0000:02:00.0: Socket status: 30000006
[   21.803125] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x6fff
[   21.803135] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x6fff: clean.
[   21.805179] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   21.805187] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf7ffffff
[   21.805547] yenta_cardbus 0000:02:00.1: CardBus bridge found [1014:023b]
[   21.805567] yenta_cardbus 0000:02:00.1: Using INTVAL to route CSC interrupts to PCI
[   21.805573] yenta_cardbus 0000:02:00.1: Routing CardBus interrupts to PCI
[   21.805581] yenta_cardbus 0000:02:00.1: TI: mfunc 0x01d21022, devctl 0x64
[   22.036659] yenta_cardbus 0000:02:00.1: ISA IRQ mask 0x0438, PCI irq 11
[   22.036669] yenta_cardbus 0000:02:00.1: Socket status: 30000020
[   22.036685] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x6fff
[   22.036694] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x2000-0x6fff: clean.
[   22.038701] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   22.038709] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf7ffffff

[   22.728106] pcmcia_socket pcmcia_socket1: pccard: CardBus card inserted into slot 1
[   22.728165] pci 0000:07:00.0: reg 10 32bit mmio: [0x000000-0x00ffff]
[   22.800720] cfg80211: Calling CRDA to update world regulatory domain
[   22.869242] cfg80211: World regulatory domain updated:
[   22.869251]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.869259]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.869266]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.869272]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.869279]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.869285]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.960425] ath5k 0000:07:00.0: enabling device (0000 -> 0002)
[   22.960450] ath5k 0000:07:00.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   22.960555] ath5k 0000:07:00.0: registered as 'phy0'
[   23.103210] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   23.104196] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   23.104627] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   23.104999] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   23.105642] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   23.248146] ath: EEPROM regdomain: 0x0
[   23.248155] ath: EEPROM indicates default country code should be used
[B][   23.248159] ath: doing EEPROM country->regdmn map search
[   23.248167] ath: country maps to regdmn code: 0x3a
[   23.248172] ath: Country alpha2 being used: US[/B]
[   23.248177] ath: Regpair used: 0x3a
[   23.257261] intel8x0_measure_ac97_clock: measured 55908 usecs (2686 samples)
[   23.257270] intel8x0: clocking to 48000
[   23.330592] phy0: Selected rate control algorithm 'minstrel'
[   23.332389] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[B][   23.332414] cfg80211: Calling CRDA for country: US
[   23.339367] cfg80211: Regulatory domain changed to country: US[/B]
[   23.339377]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.339384]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   23.339391]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   23.339397]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.339404]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.339410]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   24.011937] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.648437] [drm] Initialized drm 1.1.0 20060810
[   26.657495] pci 0000:01:00.0: power state changed by ACPI to D0
[   26.657518] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   26.658200] [drm] Initialized savage 2.4.1 20050313 for 0000:01:00.0 on minor 0
[  211.798312] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  211.798323] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  211.798330] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[  211.798650] pcmcia_socket pcmcia_socket1: cs: memory probe 0xf0000000-0xf7ffffff: excluding 0xf0000000-0xf7ffffff
[  211.798688] pcmcia_socket pcmcia_socket1: cs: memory probe 0xc0200000-0xcfffffff: excluding 0xc0200000-0xc09fffff 0xc3a00000-0xcc1fffff 0xcfa00000-0xd01fffff
```

---

### Post by chili555 on 2010-01-27
Please try:```
sudo iw reg set GB
```I believe the ISO / IEC alpha2 for the UK is GB after "Great Britain." If this works, that is, allows you to connect and throws no errors, we can add it to *rc.local* to make it permanent. Please post back so the searchers know what worked, or not.

---

### Post by Imran-UK on 2010-01-28
Thanks for your reply chili, from the dmesg output that command did seem to work and reset the Regulatory domain however I still do not see my wireless access point. I see my neighbouring ones but not my own. I also tried changing various settings with iwconfig wlan0 <param> <value> but to no avail.

I'm almost giving up here. The card was a refurbished product from eBay with a 90 day warranty so it may be a specific error but then why does it connect to my colleagues 3G wireless dongle successfully? Another idea would be to check what channel it is operating on and compare that to what the neighboring wireless networks are using. However, we have other wireless clients in the office here connecting to this network without problems so I doubt that is it.

Frustrating!

---

### Post by chili555 on 2010-01-28
Does this:```
sudo iwlist wlan0 scan
```see your network? How about this:```
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
sudo iwlist wlan0 scan
```Thanks.

---

### Post by Imran-UK on 2010-01-28
Hi Chili,

Still doesn't see my network.

Thanks

---

### Post by Imran-UK on 2010-01-28
A colleague bought in her Linksys Wireless-G PCMCIA card. It is recognized as (abbreviated) "Broadcom BCM4318 [AirForce One 54g] Controller (rev 02)"

A URL in dmesg relating to this device led me to install the package b43-fwcutter. I did so and guess what? It recognises my wireless network and connects flawlessly!

Useful links:
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)
[http://wireless.kernel.org/en/users/Drivers/b43#device_firmware](http://wireless.kernel.org/en/users/Drivers/b43#device_firmware)

I'm going to return the Netgear card so I consider this thread closed for now, thanks for your help Chili.

Update: the Netgear card is since working fine in a Windows XP laptop. The new owner also found that using the Netgear bundled wireless connection manager to be a problem, using the in-built wireless connection manager let her connect to the wireless network with no problems.

---

