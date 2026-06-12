---
title: "WIFI not working on toshiba satellite C845"
date: 2013-03-04
forum: Networking &amp; Wireless
---

### Post by Hiperboreo93 on 2013-03-04
Hi. I'm a begginer in ubuntu. I just installed de latest version (64 bits), but the wifi wont show any networks. I read that is a common problem but did not find the solution for my specific model (C845 SP4333KL). From what i read in other threads I put some commands on the console and showed this.

Thanks in advance for your help

commands:
gianni@Gianni-trabajo:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: Toshiba America Info Systems Device fb50
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device fb50
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: Toshiba America Info Systems Device fb50
    Flags: bus master, medium devsel, latency 0, IRQ 41
    Memory at 90600000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
    Subsystem: Toshiba America Info Systems Device fb50
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at 90614000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device fb50
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at 90619000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
    Subsystem: Toshiba America Info Systems Device fb50
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at 90610000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 90500000-905fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 90400000-904fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device fb50
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at 90618000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
    Subsystem: Toshiba America Info Systems Device fb50
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Toshiba America Info Systems Device fb50
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 40
    I/O ports at 4088 [size=8]
    I/O ports at 4094 [size=4]
    I/O ports at 4080 [size=8]
    I/O ports at 4090 [size=4]
    I/O ports at 4060 [size=32]
    Memory at 90617000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
    Subsystem: Toshiba America Info Systems Device fb50
    Flags: medium devsel
    Memory at 90615000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 4040 [size=32]
    Kernel modules: i2c-i801

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8723
    Subsystem: Realtek Semiconductor Co., Ltd. Device 0723
    Flags: bus master, fast devsel, latency 0
    I/O ports at 3000 [size=256]
    Memory at 90500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

03:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
    Subsystem: Toshiba America Info Systems Device fb50
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at 90400000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

gianni@Gianni-trabajo:~$ lspci | grep Network
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8723
gianni@Gianni-trabajo:~$ 
gianni@Gianni-trabajo:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

gianni@Gianni-trabajo:~$ 
gianni@Gianni-trabajo:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 08:9e:01:5d:2b:54  
          Direc. inet:192.168.0.105  Difus.:192.168.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::a9e:1ff:fe5d:2b54/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:11664 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:7393 errores:0 perdidos:0 overruns:0 carrier:1
          colisiones:0 long.colaTX:1000 
          Bytes RX:9798763 (9.7 MB)  TX bytes:961895 (961.8 KB)

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:624 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:624 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:70038 (70.0 KB)  TX bytes:70038 (70.0 KB)

gianni@Gianni-trabajo:~$ sudo su
[sudo] password for gianni: 
root@Gianni-trabajo:/home/gianni#

---

