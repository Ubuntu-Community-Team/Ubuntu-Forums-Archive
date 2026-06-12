---
title: "Installing Linksys WPC11 v.4/ RTL8180 Wireless Card"
date: 2006-04-27
forum: Networking &amp; Wireless
---

### Post by monomaniacpat on 2006-04-27
Hi guys, 

after a couple of months of dithering about I finally made some progress in installing this PCMCIA card. However, having followed [these](http://www.cwelug.org/cgi-bin/wiki.cgi?Wpc11v4#source) instructions, I hit the following snag:

```
patrick@ubuntu:~$ sudo pump -k
patrick@ubuntu:~$ sudo pump -i wlan0
Operation failed.

```

I would very much appreciate some help here, as I can't find out what the problem is.

Thanks,

mono.

---

### Post by monomaniacpat on 2006-04-28
I managed to finish the install instructions by running 

```
patrick@ubuntu:~$ sudo pump -k
patrick@ubuntu:~$ sudo iwconfig wlan0 mode managed essid Big_Mutha key **********
patrick@ubuntu:~$ pump -i wlan0
```

However, having

```
wlan0 up eth0 down
```

I cannot disconnect my wired connection without going offline...

Little help?

---

### Post by monomaniacpat on 2006-04-28
Here are some diagnostics:

```
patrick@ubuntu:~$ dmesg
ci_hcd 0000:00:1d.0: remove, state 1
[4301164.242000] usb usb1: USB disconnect, address 1
[4301164.356000] uhci_hcd 0000:00:1d.0: USB bus 1 deregistered
[4301164.359000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[4301164.359000] uhci_hcd 0000:00:1d.2: remove, state 1
[4301164.359000] usb usb2: USB disconnect, address 1
[4301164.359000] usb 2-1: USB disconnect, address 2
[4301164.682000] uhci_hcd 0000:00:1d.2: USB bus 2 deregistered
[4301164.688000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[4301167.724000] Stopping tasks: ====================================================================================================|
[4301167.749000] IDE device ACPI handler is NULL
[4301167.749000] IDE device ACPI handler is NULL
[4301169.108000] ACPI: PCI interrupt for device 0000:02:01.1 disabled
[4301169.108000] ACPI: PCI interrupt for device 0000:02:01.0 disabled
[4301169.109000] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
[4301169.109000] Back to C!
[4343359.463000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4343359.463000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[4343359.464000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4343359.468000] video bus notify
[4343361.057000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4343361.058000] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4343361.058000] ACPI: PCI Interrupt 0000:02:01.2[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4343361.093000] IDE device ACPI handler is NULL
[4343361.114000] IDE device ACPI handler is NULL
[4343361.118000] Restarting tasks... done
[4343362.722000] alps.c: Enabling hardware tapping
[4343363.001000] input: DualPoint Stick on isa0060/serio1
[4343363.015000] input: AlpsPS/2 ALPS DualPoint TouchPad on isa0060/serio1
[4343363.761000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4343363.761000] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
[4343363.761000] 0000:02:00.0: 3Com PCI 3c905C Tornado at 0xec80. Vers LK1.1.19
[4343363.816000] USB Universal Host Controller Interface driver v2.2
[4343363.822000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4343363.822000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4343363.822000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801CA/CAM USB (Hub #1)
[4343363.949000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4343363.949000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[4343364.004000] hub 1-0:1.0: USB hub found
[4343364.004000] hub 1-0:1.0: 2 ports detected
[4343364.007000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4343364.007000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4343364.007000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801CA/CAM USB (Hub #3)
[4343364.121000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 2
[4343364.121000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[4343364.160000] hub 2-0:1.0: USB hub found
[4343364.160000] hub 2-0:1.0: 2 ports detected
[4343364.355000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[4343364.563000] input: USB HID v1.11 Mouse [Microsft Microsoft Wireless Optical Desktop\uffff 2.20] on usb-0000:00:1d.2-1
[4343364.682000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4343366.048000] rtl8180: Configuring chip resources
[4343366.048000] PCI: Enabling device 0000:03:00.0 (0000 -> 0003)
[4343366.048000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4343366.048000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[4343366.048000] rtl8180: Memory mapped space @ 0x40800000
[4343366.048000] rtl8180: Hardware frame sequence numbers disabled
[4343366.053000] rtl8180: MAC controller is a RTL8180 (v. F)
[4343366.053000] rtl8180: This is a CARDBUS NIC
[4343366.053000] rtl8180: Reported EEPROM chip is a 93c56 (2Kbit)
[4343366.060000] rtl8180: Card MAC address is 00:0c:41:b2:10:21
[4343366.069000] rtl8180: EEPROM version 102
[4343366.070000] rtl8180: RfParam: 4
[4343366.072000] rtl8180: WW:Card reports RF frontend by MAXIM.
[4343366.072000] rtl8180: WW:This driver has EXPERIMENTAL support for this chipset.
[4343366.072000] rtl8180: WW:use it with care and at your own risk and
[4343366.072000] rtl8180: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO andreamrl@tiscali.it
[4343366.072000] rtl8180: Energy threshold: a
[4343366.072000] rtl8180: PAPE from CONFIG2: 2
[4343366.072000] rtl8180: Antenna A is default antenna
[4343366.072000] rtl8180: Antenna diversity is enabled
[4343366.072000] rtl8180: Carrier sense 1
[4343366.072000] rtl8180: 40-bit WEP is NOT supported in hardware
[4343366.072000] rtl8180: 104-bit WEP is NOT supported in hardware
[4343366.072000] rtl8180: IRQ 11
[4343366.079000] rtl8180: Driver probe completed
[4343366.079000]
[4343367.239000] ACPI: AC Adapter [AC] (on-line)
[4343367.272000] ACPI: Battery Slot [BAT0] (battery absent)
[4343367.386000] ACPI: Battery Slot [BAT1] (battery present)
[4343368.273000] video bus notify
[4343369.061000] ACPI: Lid Switch [LID]
[4343369.061000] ACPI: Power Button (CM) [PBTN]
[4343369.061000] ACPI: Sleep Button (CM) [SBTN]
[4343369.153000] ACPI: Thermal Zone [THM] (38 C)
[4343373.729000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343373.729000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343375.840000] eth0: no IPv6 routers present
[4343517.950000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[4343517.950000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4343521.331000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343521.331000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343565.312000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343565.312000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343658.605000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[4343658.605000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4343659.817000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343659.817000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343663.067000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343663.067000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343666.481000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343666.481000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343748.440000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[4343748.440000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4343749.418000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343749.418000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343753.766000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343753.766000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343756.524000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343756.524000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343759.528000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343759.528000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343763.341000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343763.341000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343772.276000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343772.276000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343780.743000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343780.743000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343788.608000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343788.608000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343795.179000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343795.179000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343798.167000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343798.167000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343800.980000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343800.980000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343804.154000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343804.154000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343807.398000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343807.398000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343808.053000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[4343808.053000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4343908.394000] rtl8180: Bringing up iface
[4343908.602000] rtl8180: Card successfully reset
[4343919.764000] wlan0: no IPv6 routers present
[4343939.147000] rtl8180: Bringing up iface
[4343939.355000] rtl8180: Card successfully reset
[4343949.773000] wlan0: no IPv6 routers present
[4343954.460000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[4343954.460000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4343954.858000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343954.858000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343962.758000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343962.758000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343974.296000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343974.296000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4343995.369000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4343995.369000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4344060.429000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[4344060.429000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4344071.719000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4344071.719000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4344085.838000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4344085.838000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4344134.478000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[4344134.478000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4344138.290000] rtl8180: Bringing up iface
[4344138.373000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4344138.373000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4344138.497000] rtl8180: Card successfully reset
[4344149.586000] wlan0: no IPv6 routers present
[4344166.331000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4344166.331000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4344188.960000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4344188.960000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4344193.106000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4344193.106000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4344193.985000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[4344193.985000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
[4344202.197000] rtl8180: Setting SW wep key
[4344210.697000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344210.697000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344211.197000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344211.197000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344211.697000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344211.697000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344212.197000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344212.197000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344212.697000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344212.697000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344213.197000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344213.197000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344213.697000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344213.697000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344214.197000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344214.197000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344214.386000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4344214.386000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4344214.697000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344214.697000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344215.197000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344215.197000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344215.697000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344215.697000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344216.197000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344216.197000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344216.614000] rtl8180: Bringing up iface
[4344216.697000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344216.697000] rtl8180: WW:No more TX desc, returning 29 of 29
[4344216.828000] rtl8180: Card successfully reset
[4344221.591000] IEEE802.11: Associating with Big_Mutha
[4344221.591000] IEEE802.11: Stopping scan
[4344221.598000] IEEE802.11: Sending authentication request
[4344221.600000] IEEE802.11: Received authentication response
[4344221.600000] IEEE802.11: Sending association request
[4344221.701000] IEEE802.11: Received association response
[4344221.701000] IEEE802.11: Successfully associated
[4344221.701000] rtl8180: Joining the BSS
[4344227.634000] wlan0: no IPv6 routers present
[4344228.259000] rtl8180: Bringing up iface
[4344228.467000] rtl8180: Card successfully reset
[4344228.762000] IEEE802.11: Associating with Big_Mutha
[4344228.762000] IEEE802.11: Stopping scan
[4344228.769000] IEEE802.11: Sending authentication request
[4344228.770000] IEEE802.11: Received authentication response
[4344228.770000] IEEE802.11: Sending association request
[4344228.891000] IEEE802.11: Received association response
[4344228.891000] IEEE802.11: Successfully associated
[4344228.891000] rtl8180: Joining the BSS
[4344238.957000] wlan0: no IPv6 routers present
[4344242.901000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[4344242.901000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[4344275.565000] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
[4344275.565000] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
patrick@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:08:74:3D:8C:D2
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fe3d:8cd2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:565565 (552.3 KiB)  TX bytes:46488 (45.3 KiB)
          Interrupt:11 Base address:0xec80

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:373571 errors:0 dropped:0 overruns:0 frame:0
          TX packets:373571 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:36165074 (34.4 MiB)  TX bytes:36165074 (34.4 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0C:41:B2:10:21
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:41ff:feb2:1021/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:1 dropped:2 overruns:0 frame:0
          TX packets:506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4246 (4.1 KiB)  TX bytes:19902 (19.4 KiB)
          Interrupt:11 Memory:f88c8000-f88c8100

patrick@ubuntu:~$ cat /proc/interrupts
           CPU0
  0:    7477238          XT-PIC  timer
  1:      10596          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  5:      26572          XT-PIC  Intel 82801CA-ICH3
  7:          2          XT-PIC  parport0
  8:          2          XT-PIC  rtc
  9:          3          XT-PIC  acpi
 11:     620636          XT-PIC  ohci1394, yenta, yenta, uhci_hcd:usb1, uhci_hcd:usb2, eth0, wlan0
 12:        254          XT-PIC  i8042
 14:     111710          XT-PIC  ide0
NMI:          0
LOC:          0
ERR:          0
MIS:          0
patrick@ubuntu:~$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"Big_Mutha"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:15:E9:27:09:5E
          Bit Rate=11 Mb/s
          Retry:on   Fragment thr:off
          Link Quality:87/100  Signal level:-42 dBm  Noise level:-243 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

patrick@ubuntu:~$ cat /proc/interrupts
           CPU0
  0:    7556231          XT-PIC  timer
  1:      10654          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  5:      26849          XT-PIC  Intel 82801CA-ICH3
  7:          2          XT-PIC  parport0
  8:          2          XT-PIC  rtc
  9:          3          XT-PIC  acpi
 11:     627293          XT-PIC  ohci1394, yenta, yenta, uhci_hcd:usb1, uhci_hcd:usb2, eth0, wlan0
 12:        254          XT-PIC  i8042
 14:     112491          XT-PIC  ide0
NMI:          0
LOC:          0
ERR:          0
MIS:          0

```

---

### Post by az on 2006-04-28
Why are you using pump?  dhclient ships out-of-the-box with ubuntu and everything is tied to it.  The gnome network tool can configure all your network interfaces for you.

And Dapper already has that driver.  Can you try the live cd to see if you can get online with it?

---

### Post by monomaniacpat on 2006-04-29
I used pump because that was what was used in the page I found. How would I use DHClient? 

Is the gnome network tool 'networking' as found under System>Administration? I put all the settings on with that and had the same problem.

I would rather not use Dapper, as I have all the programs I want already running smoothly under Breezy, but thanks for the tip off.

---

### Post by monomaniacpat on 2006-04-29
Scratch that - I've got it to work using Network Settings! I think my mistake was settingthe WEP key using ASCII instead of Hexadecimal. Now it's working like a charm. So, the final question is - how do I set it to work on start up, or, better still - when I insert the card?

THANKS!!!

---

### Post by monomaniacpat on 2006-04-29
Guys,

I've been getting some help on the IRC channel - here's what I've got for etc/netowork/interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface eth0 inet dhcp

auto wlan0

iface wlan0 inet dhcp
wireless-essid Big_Mutha
wireless-key 
```

It doesn't load the card on startup - what do I need to do to get it to work?

Yours,

mono.

---

### Post by sailor2001 on 2006-04-29
this is what I've been doing:I keep the driver on the desktop.

cd Desktop
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i NET8180.INF
sudo ndiswrapper -l
sudo dhclient 

ctrl+0

most of the time it holds between booting, if not I just do "sudo dhclient"

---

### Post by monomaniacpat on 2006-04-30
Annoyingly, the instructions I was using no longer work. ](*,) 

What could I be doing wrong? I've entered exactly the same commands on two different occassions (once yesterday at about 2pm and then at 5pm) - on one of which it worked and another, it didn't. I have checked /var/log/auth.log to see if I've changed any commands, but it doesn't appear so. Here's the output:

```
Apr 29 14:10:55 localhost sudo:  patrick : TTY=pts/1 ; PWD=/home/patrick/Downloads/rtl8180-0.21/rtl8180-sa2400-dev ; USER=root ; COMMAND=/sbin/insmod ./ieee80211_crypt-r8180.ko
Apr 29 14:11:09 localhost sudo:  patrick : TTY=pts/1 ; PWD=/home/patrick/Downloads/rtl8180-0.21/rtl8180-sa2400-dev ; USER=root ; COMMAND=/sbin/insmod ./ieee80211_crypt_wep-r8180.ko
Apr 29 14:11:25 localhost sudo:  patrick : TTY=pts/1 ; PWD=/home/patrick/Downloads/rtl8180-0.21/rtl8180-sa2400-dev ; USER=root ; COMMAND=/sbin/insmod ./ieee80211-r8180.ko
Apr 29 14:11:37 localhost sudo:  patrick : TTY=pts/1 ; PWD=/home/patrick/Downloads/rtl8180-0.21/rtl8180-sa2400-dev ; USER=root ; COMMAND=/sbin/insmod ./r8180.ko
Apr 29 14:12:05 localhost sudo:  patrick : TTY=pts/1 ; PWD=/home/patrick/Downloads/rtl8180-0.21/rtl8180-sa2400-dev ; USER=root ; COMMAND=/sbin/ifconfig wlan0 up
Apr 29 14:12:40 localhost sudo:  patrick : TTY=pts/1 ; PWD=/home/patrick/Downloads/rtl8180-0.21/rtl8180-sa2400-dev ; USER=root ; COMMAND=/sbin/iwconfig wlan0 essid Free/Libre/OpenSource
Apr 29 14:12:45 localhost sudo:  patrick : TTY=unknown ; PWD=/home/patrick ; USER=root ; COMMAND=validate
Apr 29 14:12:45 localhost sudo:  patrick : TTY=unknown ; PWD=/home/patrick ; USER=root ; COMMAND=/usr/bin/network-admin
Apr 29 14:12:46 localhost sudo:  patrick : TTY=pts/0 ; PWD=/home/patrick ; USER=root ; COMMAND=/bin/sh -c env LANG="en_GB.UTF-8" LANGUAGE="en_GB:en" /usr/share/setup-tool-backends/scripts/network-conf --report
Apr 29 14:17:01 localhost CRON[9122]: (pam_unix) session opened for user root by (uid=0)
Apr 29 14:17:01 localhost CRON[9122]: (pam_unix) session closed for user root

Apr 29 17:33:40 localhost sudo:  patrick : TTY=pts/0 ; PWD=/home/patrick/Downloads/rtl8180-0.21/rtl8180-sa2400-dev ; USER=root ; COMMAND=/sbin/insmod ./ieee80211_crypt-r8180.ko
Apr 29 17:33:55 localhost sudo:  patrick : TTY=pts/0 ; PWD=/home/patrick/Downloads/rtl8180-0.21/rtl8180-sa2400-dev ; USER=root ; COMMAND=/sbin/insmod ./ieee80211_crypt_wep-r8180.ko
Apr 29 17:34:03 localhost sudo:  patrick : TTY=pts/0 ; PWD=/home/patrick/Downloads/rtl8180-0.21/rtl8180-sa2400-dev ; USER=root ; COMMAND=/sbin/insmod ./ieee80211-r8180.ko
Apr 29 17:34:17 localhost sudo:  patrick : TTY=pts/0 ; PWD=/home/patrick/Downloads/rtl8180-0.21/rtl8180-sa2400-dev ; USER=root ; COMMAND=/sbin/insmod ./r8180.ko
Apr 29 17:34:52 localhost sudo:  patrick : TTY=pts/0 ; PWD=/home/patrick/Downloads/rtl8180-0.21/rtl8180-sa2400-dev ; USER=root ; COMMAND=/sbin/ifconfig wlan0 up
Apr 29 17:35:03 localhost sudo:  patrick : TTY=pts/0 ; PWD=/home/patrick/Downloads/rtl8180-0.21/rtl8180-sa2400-dev ; USER=root ; COMMAND=/sbin/iwlist wlan0 scan
Apr 29 17:35:26 localhost sudo:  patrick : TTY=pts/0 ; PWD=/home/patrick/Downloads/rtl8180-0.21/rtl8180-sa2400-dev ; USER=root ; COMMAND=/sbin/iwconfig wlan0 essid Free/Libre/OpenSource
Apr 29 17:35:30 localhost sudo:  patrick : TTY=unknown ; PWD=/home/patrick ; USER=root ; COMMAND=validate
Apr 29 17:35:30 localhost sudo:  patrick : TTY=unknown ; PWD=/home/patrick ; USER=root ; COMMAND=/usr/bin/network-admin
Apr 29 17:35:31 localhost sudo:  patrick : TTY=pts/1 ; PWD=/home/patrick ; USER=root ; COMMAND=/bin/sh -c env LANG="en_GB.UTF-8" LANGUAGE="en_GB:en" /usr/share/setup-tool-backends/scripts/network-conf --report

```

At the point where I open network-admin, on both occassions, I go to my wireless connection, enable it (entering my WEP key (I've tried it with it off) and instead of quickly activating the connection (like it did the first time), it spends an absolute age, eventually saying 'active', but the 'link' light on my card doesn't come on (meaning it hasn't been enabled.)

```
patrick@ubuntu:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:15:E9:27:09:5E
                    ESSID:"Big_Mutha"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:22 Mb/s
                    Quality=96/100  Signal level=-46 dBm  Noise level=-256 dBm
                    Encryption key:on

```

In total I had it working using this technique after at least two restarts (enabling it both times) and since 5pm yesterday I have been unsuccesful. I have now make installed the modules, and since this is proving fruitless, I would like someone to tell me how to uninstall the modules and unmake the source files, so I can try this from the beginning. Unless, of course, someone can tell me why it isn't working...?

:-?

P.s. Sailor2001: I've never managed to get ndiswrapper to detect the hardware.

---

### Post by monomaniacpat on 2006-04-30
Just to clarify the steps I have taken:

Having made the files as mentioned [here](http://www.cwelug.org/cgi-bin/wiki.cgi?Wpc11v4#source), I would then do the following:

```
insmod ./ieee80211_crypt-r8180.ko
insmod ./ieee80211_crypt_wep-r8180.ko
insmod ./ieee80211-r8180.ko
insmod ./r8180.ko
lsmod | grep r8180
	ieee80211_crypt_wep_r8180     5120  1
	r8180                  57868  0
	ieee80211_r8180        32004  1 r8180
	ieee80211_crypt_r8180     5508  2 ieee80211_crypt_wep_r8180,ieee80211_r8180
ifconfig wlan0 up
iwlist wlan0 scan
	wlan0     Scan completed :
          Cell 01 - Address: 00:15:E9:27:09:5E
                    ESSID:"Big_Mutha"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:22 Mb/s
                    Quality=96/100  Signal level=-46 dBm  Noise level=-256 dBm
                    Encryption key:on
iwconfig wlan0 essid Free/Libre/OpenSource
```

Then go to network settings and enable the connection. Now that I have make installed I no longer insmod, as they are already inserted, but I get the same response from grep and no success enabling the connection. I also now have the wireless connection in network setting from startup, but it just doesn't work.

---

### Post by monomaniacpat on 2006-05-01
I've now tried deleting all the modules from the kernel and remaking them. It makes no difference. Also of note is the fact that pump no longer works successfully and I have returned to the old problem of 'Operation failed'.

Little help?

---

### Post by sailor2001 on 2006-05-01
the instructions I gave you: when I put them in the terminal, I get from ndiswrapper "can't find driver" or something like that. I just ignore that script and keep going and sudo dhclient finds it at the end.

---

### Post by monomaniacpat on 2006-05-01
What does dhclient actually do?

I just get this output from it:

```
patrick@ubuntu:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 8496
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0c:41:b2:10:21
Sending on   LPF/wlan0/00:0c:41:b2:10:21
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/lo/
Sending on   LPF/lo/
Listening on LPF/eth0/00:08:74:3d:8c:d2
Sending on   LPF/eth0/00:08:74:3d:8c:d2
Sending on   Socket/fallback
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 6
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.2 -- renewal in 1489 seconds.

```

What have I actually achieved?

---

### Post by sailor2001 on 2006-05-01
you're probably on-line.. check your browser

---

### Post by monomaniacpat on 2006-05-01
Not with my wireless card I'm not.](*,)

---

### Post by sailor2001 on 2006-05-01
check to see if you have right chipset  [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

---

### Post by monomaniacpat on 2006-05-02
I don't know what actually changed - as far as I'm aware I did all the same things again, but now ndiswrapper claims the hardware is present (a significant step forward.)

However, the device does not appear under network settings - how do I get my wireless up and running? Thanks.

EDIT: I have inserted ndiswrapper, but there are still 'no wireless extensions'

---

### Post by monomaniacpat on 2006-05-02
I have now got the second 'link' light to go on again. However, it still takes forever to  enable and I can't disable eth0 successfully. I don't know why the second link light now comes on. Here's what I was doing prior to success:

```
patrick@ubuntu:~$ sudo lshw
Password:
     *-network
          description: Wireless interface
          product: RTL8180L 802.11b MAC
          vendor: Realtek Semiconductor Co., Ltd.
          physical id: 1
          bus info: pci@03:00.0
          logical name: wlan0
          version: 20
          serial: 00:0c:41:b2:10:21
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=ndiswrapper link=no multicast=yes wireless=IEEE 802.11b
          resources: ioport:4000-40ff iomemory:40800000-408001ff irq:11
  *-battery
       product: 0001J433
       vendor: SANYO
       physical id: 1
       slot: Right Module Bay
       capacity: 66000mWh
       configuration: voltage=14.8V
patrick@ubuntu:~$
patrick@ubuntu:~$ sudo lsmod | grep rtl
patrick@ubuntu:~$ sudo lsmod | grep ndis
ndiswrapper           114376  0
usbcore               104316  4 ndiswrapper,usbhid,uhci_hcd
patrick@ubuntu:~$ sudo modprobe - ndiswrapper
FATAL: Module _ not found.
patrick@ubuntu:~$ sudo modprobe -r ndiswrapper
patrick@ubuntu:~$ sudo lsmod | grep ndis
patrick@ubuntu:~$ cd ~/Downloads/rtl8180-0.21/rtl8180-sa2400-dev/
patrick@ubuntu:~/Downloads/rtl8180-0.21/rtl8180-sa2400-dev$ sudo insmod ./ieee80211_crypt-r8180.ko
patrick@ubuntu:~/Downloads/rtl8180-0.21/rtl8180-sa2400-dev$ sudo insmod ./ieee80211_crypt_wep-r8180.ko
patrick@ubuntu:~/Downloads/rtl8180-0.21/rtl8180-sa2400-dev$ sudo insmod ./ieee80211-r8180.ko
patrick@ubuntu:~/Downloads/rtl8180-0.21/rtl8180-sa2400-dev$ sudo insmod ./r8180.ko
patrick@ubuntu:~/Downloads/rtl8180-0.21/rtl8180-sa2400-dev$ sudo lsmod | grep 8180
r8180                  57868  0
ieee80211_r8180        32004  1 r8180
ieee80211_crypt_wep_r8180     5120  0
ieee80211_crypt_r8180     5508  2 ieee80211_r8180,ieee80211_crypt_wep_r8180
patrick@ubuntu:~/Downloads/rtl8180-0.21/rtl8180-sa2400-dev$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"Big_Mutha"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:15:E9:27:09:5E
          Bit Rate=11 Mb/s
          Retry:on   Fragment thr:off
          Encryption key:0145-8ADF-CA   Security mode:restricted
          Link Quality:96/100  Signal level:-46 dBm  Noise level:-252 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

patrick@ubuntu:~/Downloads/rtl8180-0.21/rtl8180-sa2400-dev$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:15:E9:27:09:5E
                    ESSID:"Big_Mutha"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:22 Mb/s
                    Quality=95/100  Signal level=-58 dBm  Noise level=-256 dBm
                    Encryption key:on

```

I am using the open source drivers again.

---

### Post by monomaniacpat on 2006-05-03
OK. Having messed about with my router a fair bit over the last few days, my mum's laptop could no longer access wireless and the only way to get it working again was to restart the router. 

Having done this, I now have wireless access using the open source drivers on my laptop! Unfortunately, I think all the messing about has had a detrimental effect on my operating system (it has been v sluggish), but I'll wait and see. Thanks for your help, guys.

Fingers crossed.

mono.

---

