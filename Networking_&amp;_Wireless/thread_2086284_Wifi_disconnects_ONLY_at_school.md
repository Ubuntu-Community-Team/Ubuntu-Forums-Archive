---
title: "Wifi disconnects ONLY at school"
date: 2012-11-20
forum: Networking &amp; Wireless
---

### Post by VulpesLagopus on 2012-11-20
Hello everybody,

After installing Ubuntu on my computer I had problems with wifi it disconnected from networks in an aleatory way. Then Wild Man helped me and now I have no problems with connection at home or at my friends.
Now the problem is that at school it disconnects me quite regularly. When it disconnects me it doesn't see any wireless network (which is impossible we have four of them), and then tries to reconnect me and succeed. And after five minutes it's the same scenario.
The signal of the wifi is strong enough pretty much everywhere

sudo watch -n 10 iwlist wlan0 scan :

```
wlan0     Scan completed :
          Cell 01 - Address: 28:93:FE:4E:0F:90
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm
                    Encryption key:on
                    ESSID:"epfl"
                    Bit Rates:6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 48 Mb/s
                    Bit Rates:54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000af1356824
                    Extra: Last beacon: 3104ms ago
                    IE: Unknown: 00046570666C
                    IE: Unknown: 01080C12169824304860
                    IE: Unknown: 030106
                    IE: Unknown: 0706434820010D14
                    IE: Unknown: 0B050D001E8D5B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32016C
                    IE: Unknown: 9606004096000500
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401

```lspci -v :

```
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
    Subsystem: Dell Device 0552
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=06, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d0000000-d1ffffff
    Prefetchable memory behind bridge: 00000000a0000000-00000000bfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 0552
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at d2000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: Dell Device 0552
    Flags: bus master, medium devsel, latency 0, IRQ 42
    Memory at d2700000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
    Subsystem: Dell Device 0552
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at d2714000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Dell Device 0552
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at d2719000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
    Subsystem: Dell Device 0552
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at d2710000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d2600000-d26fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Memory behind bridge: d2500000-d25fffff
    Prefetchable memory behind bridge: 000000009fb00000-000000009fbfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    Memory behind bridge: d2400000-d24fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Dell Device 0552
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d2718000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
    Subsystem: Dell Device 0552
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Dell Device 0552
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
    I/O ports at 4088 [size=8]
    I/O ports at 4094 [size=4]
    I/O ports at 4080 [size=8]
    I/O ports at 4090 [size=4]
    I/O ports at 4060 [size=32]
    Memory at d2717000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
    Subsystem: Dell Device 0552
    Flags: medium devsel, IRQ 10
    Memory at d2715000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 4040 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: NVIDIA Corporation Device 0fd1 (rev ff) (prog-if ff)
    !!! Unknown header type 7f

01:00.1 Audio device: NVIDIA Corporation Device 0e1b (rev ff) (prog-if ff)
    !!! Unknown header type 7f
    Kernel driver in use: snd_hda_intel

07:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
    Subsystem: Dell Device 0552
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at d2600000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

08:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)
    Subsystem: Bigfoot Networks, Inc. Device 2003
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at d2500000 (64-bit, non-prefetchable) [size=512K]
    Expansion ROM at 9fb00000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

09:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
    Subsystem: Dell Device 0552
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at d2401000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: rts_pstor
    Kernel modules: rts_pstor

09:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
    Subsystem: Dell Device 0552
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d2400000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
```The only difference I see is that at home I have a WPA encryption and at school a WPA&WPA2 Entreprise encryption.

So if someone has any ideas, please help.

Thank you in advance

---

### Post by nothingspecial on 2012-11-22
*Thread moved to **Networking & Wireless**.*

---

