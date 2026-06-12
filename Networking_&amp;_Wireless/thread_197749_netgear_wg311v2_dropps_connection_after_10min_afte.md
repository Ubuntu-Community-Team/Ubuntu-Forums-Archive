---
title: "netgear wg311v2 dropps connection after 10min after bootup"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by tempo500 on 2006-06-16
i have been using the firmware 1.2.0.30 on dapper now for 2 month - pretty stable. since yesturday the connection droppes after bootup (around 10 min). also my system hangs if i use the command sudo rmmod acx. this used to work when the connection dropped - 
cd /lib/firmware/2.6.15-23-386/acx/default
sudo ln --backup -s ../1.2.0.30/* ./

so i tryed the 1.2.1.34 firmware but they have the same issues.

the card worked with the default 2.3.1.31 but i could not get the essid from the router. now (with the 1.2.0.30, 1.2.1.34)when the connection drops i am still left with a working iwconfig info...essid, channel etc are correctly found, but i cant ping the router

dmesg output
[HTML]non working
[4296017.039000] NETDEV WATCHDOG: wlan0: transmit timed out
[4296017.039000] wlan0: FAILED to free any of the many full tx buffers. Switchin g to emergency freeing. Please report!
[4296017.039000] wlan0: tx timeout!
[4296017.039000] wlan0: recalibrating radio
[4296017.138000] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bit s:0x2000 irq_status:0x2000 timeout:99ms cmd_status:0 (Idle)
[4296017.138000] wlan0: issue_cmd(cmd:0x0019) FAILED
[4296017.138000]  [<f8b3d7a7>] acxpci_s_issue_cmd_timeo+0xb7/0x350 [acx]
[4296017.138000]  [<f8b3c76a>] acx_s_recalib_radio+0xea/0x110 [acx]
[4296017.138000]  [<f8b3c7c8>] acx_s_after_interrupt_recalib+0x38/0x130 [acx]
[4296017.138000]  [<f8b3c9e6>] acx_e_after_interrupt_task+0x126/0x1e0 [acx]
[4296017.138000]  [<c012caca>] worker_thread+0x1ba/0x290
[4296017.138000]  [<f8b3c8c0>] acx_e_after_interrupt_task+0x0/0x1e0 [acx]
[4296017.138000]  [<c0118940>] default_wake_function+0x0/0x20
[4296017.138000]  [<c012c910>] worker_thread+0x0/0x290
[4296017.138000]  [<c0130d53>] kthread+0x93/0xa0
[4296017.138000]  [<c0130cc0>] kthread+0x0/0xa0
[4296017.138000]  [<c0101385>] kernel_thread_helper+0x5/0x10
[4296017.138000] wlan0: recalibrating radio

working\

[4294690.283000] acx: found ACX111-based wireless network card at 0000:00:0b.0, irq:11, phymem1:0xCFFFA000, phymem2:0xCFFA0000, mem1:0xf89f4000, mem1_size:8192, mem2:0xf8a80000, mem2_size:131072[/HTML]

iwconfig
[HTML]
wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:82:91:5D
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fe82:915d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:177 errors:49 dropped:0 overruns:0 frame:0
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:20887 (20.3 KiB)  TX bytes:12195 (11.9 KiB)
          Interrupt:11 Base address:0xa000
[/HTML]
ifconfig
[HTML]
wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:82:91:5D
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fe82:915d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1922 errors:666 dropped:0 overruns:0 frame:0
          TX packets:1875 errors:3 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1265460 (1.2 MiB)  TX bytes:310028 (302.7 KiB)
          Interrupt:11 Base address:0xa000

[/HTML]

i hope someone has a solution, because i am really stuck loosing my www connection all the time. PLEASE! thanx philip

ps.: i am using wep

---

### Post by tempo500 on 2006-06-16
ps.:

sudo lspci -vv

[HTML]0000:00:0b.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
        Subsystem: Netgear: Unknown device 4c00
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at cfffa000 (32-bit, non-prefetchable) [size=8K]
        Region 1: Memory at cffa0000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
[/HTML]

something new? please hlp!
[HTML]
[4297227.116000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4297227.116000] acx: found ACX111-based wireless network card at 0000:00:0b.0, irq:11, phymem1:0xCFFFA000, phymem2:0xCFFA0000, mem1:0xf8a40000, mem1_size:8192, mem2:0xf8e40000, mem2_size:131072
[4297227.807000] acx: form factor 0x01 ((mini-)PCI / CardBus), radio type 0x16 (Radia), EEPROM version 0x05, uploaded firmware 'Rev 1.2.1.34' (0x03010101)
[4297227.808000] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 19 and Linux 2.6.15-23-386
[4297227.809000] usbcore: registered new driver acx_usb
[4297228.511000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[4297230.674000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[4297231.659000] wlan0: duplicate address detected!

[/HTML]

---

