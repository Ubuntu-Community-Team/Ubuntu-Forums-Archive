---
title: "wired network connection for compaq nc6220"
date: 2013-05-02
forum: Networking &amp; Wireless
---

### Post by acinoi on 2013-05-02
Hi!

I've just installed Ubuntu 12.04 and I have a problem with my wired network connection.
Wireless connection works without a problem.

Do I need to install the network card?  If the answer is Yes, from where I can get the driver because I went on the official website and I was unable to find the driver for Linux operating system.

Any help would be appreciated.  Thanks!

Those are my outputs commands:

cat /etc/network/interfaces
auto lo
iface lo inet loopback


ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:12:f0:19:90:b3  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe19:90b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:784877 errors:3 dropped:3 overruns:0 frame:0
          TX packets:495191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1014015027 (1.0 GB)  TX bytes:213401411 (213.4 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1904 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:184323 (184.3 KB)  TX bytes:184323 (184.3 KB)



 lspci -nn | grep Network
02:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)

lshw -C Network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth0
       version: 05
       serial: 00:12:f0:19:90:b3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.0.11 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:d0000000-d0000fff

---

### Post by chili555 on 2013-05-02
We see no wired ethernet card. Please run and post:```
lspci -nn | grep 0200
lsusb
```

---

### Post by acinoi on 2013-05-02
Thanks for the reply!

lspci -nn | grep 0200
<no output>

lsusb 
Bus 003 Device 002: ID 03f0:011d Hewlett-Packard Bluetooth 1.2 Interface [Broadcom BCM2035]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by chili555 on 2013-05-02
We still see no ethernet device. I wonder if it has been removed or else it is electrically defective. Does it work with any other operating system?

---

### Post by acinoi on 2013-05-02
Yes, it did work. I had windows xp on it and because of receiving a blue screen I decided to move on ubuntu.

Why do I see the wireless connection working on eth0 and not on wlan0?


 iwconfig lo        no wireless extensions.


eth0      IEEE 802.11bg  ESSID:"virginmediancutza"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 74:44:01:F4:8F:D0   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:189A-8909-5B71-FF0F-E0E8-C647-E1D4-0E50   Security mode:open
          Power Management:off
          Link Quality=83/100  Signal level=-47 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:20

---

### Post by chili555 on 2013-05-02
> Why do I see the wireless connection working on eth0 and not on wlan0?Because different drivers name the interface different things and, over the years, this has changed. The relatively old ipw2200 driver names its interface eth(whatever is next available). In your case, since eth0 was not already used by the wired ethernet, your wireless took it.

The current Broadcom STA driver also names its interface eth(whatever is next available) and it usually ends up being eth1.

We might see if there are interesting errors in dmesg:```
dmesg | grep -i error
```Or ACPI problems:```
dmesg | grep -i acpi
```Is this a laptop? What brand and model?

---

### Post by acinoi on 2013-05-02
Thanks for the given information!
Yes, this is a laptop. 

**HP Compaq nc6220**

dmesg | grep -i error
[   16.827113] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro

dmesg | grep -i acpi
[    0.000000] BIOS-e820: [mem 0x000000007f7efc00-0x000000007f7fafff] ACPI NVS
[    0.000000] ACPI: RSDP 000fe270 00014 (v00 HP    )
[    0.000000] ACPI: RSDT 7f7efc84 00034 (v01 HP     0944     24070920 HP   00000001)
[    0.000000] ACPI: FACP 7f7efc00 00084 (v02 HP     0944     00000002 HP   00000001)
[    0.000000] ACPI: DSDT 7f7efd50 08370 (v01 HP       nc6200 00010000 MSFT 0100000E)
[    0.000000] ACPI: FACS 7f7fae80 00040
[    0.000000] ACPI: APIC 7f7efcb8 0005A (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: MCFG 7f7efd14 0003C (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: SSDT 7f7f80c0 00371 (v01 HP       HPQPpc 00001001 MSFT 0100000E)
[    0.000000] ACPI: Local APIC address 0xfec01000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfec01000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.019766] ACPI: Core revision 20120320
[    0.088004] PM: Registering ACPI NVS region [mem 0x7f7efc00-0x7f7fafff] (46080 bytes)
[    0.088004] ACPI: bus type pci registered
[    0.089791] ACPI: Added _OSI(Module Device)
[    0.089794] ACPI: Added _OSI(Processor Device)
[    0.089797] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.089800] ACPI: Added _OSI(Processor Aggregator Device)
[    0.091839] ACPI: EC: Look up EC in DSDT
[    0.112087] ACPI: Interpreter enabled
[    0.112102] ACPI: (supports S0 S3 S4 S5)
[    0.112126] ACPI: Using IOAPIC for interrupt routing
[    0.116395] ACPI: Power Resource [C1D0] (on)
[    0.117247] ACPI: Power Resource [C1A9] (on)
[    0.118076] ACPI: Power Resource [C1C8] (on)
[    0.123479] ACPI: Power Resource [C251] (off)
[    0.123561] ACPI: Power Resource [C252] (off)
[    0.123644] ACPI: Power Resource [C253] (off)
[    0.123723] ACPI: Power Resource [C254] (off)
[    0.124438] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.124716] ACPI: No dock devices found.
[    0.124725] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.129307] ACPI: PCI Root Bridge [C002] (domain 0000 [bus 00-ff])
[    0.139935] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.141344] ACPI: PCI Interrupt Routing Table [\_SB_.C002._PRT]
[    0.141581] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C06D._PRT]
[    0.141744] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C006._PRT]
[    0.141823] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C0DE._PRT]
[    0.141937]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.141942]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.141944] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.157375] ACPI: PCI Interrupt Link [C0DA] (IRQs *10 11)
[    0.157497] ACPI: PCI Interrupt Link [C0DB] (IRQs 10 *11)
[    0.157613] ACPI: PCI Interrupt Link [C0DC] (IRQs 10 *11)
[    0.157729] ACPI: PCI Interrupt Link [C0DD] (IRQs *10 11)
[    0.157845] ACPI: PCI Interrupt Link [C0F0] (IRQs *10 11)
[    0.157960] ACPI: PCI Interrupt Link [C0F1] (IRQs 10 *11)
[    0.158076] ACPI: PCI Interrupt Link [C0F2] (IRQs *10 11)
[    0.158125] ACPI Exception: AE_NOT_FOUND, Evaluating _PRS (20120320/pci_link-184)
[    0.158662] ACPI: bus type usb registered
[    0.158858] PCI: Using ACPI for IRQ routing
[    0.184380] pnp: PnP ACPI init
[    0.184417] ACPI: bus type pnp registered
[    0.184688] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.189438] pnp 00:01: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.190284] pnp 00:02: Plug and Play ACPI device, IDs PNP0501 PNP0500 (active)
[    0.190506] pnp 00:03: Plug and Play ACPI device, IDs IFX0101 (active)
[    0.190568] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.190638] pnp 00:05: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.190690] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.190754] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.190822] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.190883] pnp 00:09: Plug and Play ACPI device, IDs SYN010e SYN0100 SYN0002 PNP0f13 (active)
[    0.191157] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.192109] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.192496] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.192514] pnp: PnP ACPI: found 13 devices
[    0.192516] ACPI: ACPI bus type pnp unregistered
[    0.192520] PnPBIOS: Disabled by ACPI PNP
[    0.327608] ACPI: AC Adapter [C175] (on-line)
[    0.327723] ACPI: Sleep Button [C1F1]
[    0.327834] ACPI: Lid Switch [C1F2]
[    0.327902] ACPI: Power Button [PWRF]
[    0.328056] ACPI: Fan [C255] (off)
[    0.328133] ACPI: Fan [C256] (off)
[    0.328207] ACPI: Fan [C257] (off)
[    0.328284] ACPI: Fan [C258] (off)
[    0.328337] ACPI: Requesting acpi_cpufreq
[    0.720083] ACPI: acpi_idle registered with cpuidle
[    0.771776] ACPI: Thermal Zone [TZ1] (74 C)
[    0.785966] ACPI: Thermal Zone [TZ2] (50 C)
[    0.794179] ACPI: Thermal Zone [TZ3] (31 C)
[    0.797918] ACPI: Thermal Zone [TZ4] (40 C)
[    0.797960] ACPI: Battery Slot [C177] (battery present)
[    0.798267] ACPI: Battery Slot [C176] (battery absent)
[    0.819162] ACPI: Battery Slot [C176] (battery absent)
[    1.234213] ACPI: Battery Slot [C177] (battery present)
[   16.944318] ACPI: Video Device [C05A] (multi-head: yes  rom: no  post: no)
[   19.691142] ACPI Warning: 0x00001060-0x0000107f SystemIO conflicts with Region \_SB_.C002.C003.C093 1 (20120320/utaddress-251)
[   19.691150] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   19.691157] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \_SB_.C002.C003.C08B 1 (20120320/utaddress-251)
[   19.691163] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   19.691167] ACPI Warning: 0x00001100-0x0000113f SystemIO conflicts with Region \_SB_.C002.C003.C09B 1 (20120320/utaddress-251)
[   19.691172] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   19.691263] snd_intel8x0 0000:00:1e.2: power state changed by ACPI to D0
[   19.691299] snd_intel8x0 0000:00:1e.2: power state changed by ACPI to D0
root@alice-HP-Compaq-nc6220-PY394ES-ABB:~# dmesg | grep -i error
root@alice-HP-Compaq-nc6220-PY394ES-ABB:~# dmesg | grep -i acpi
[    0.000000] BIOS-e820: [mem 0x000000007f7efc00-0x000000007f7fafff] ACPI NVS
[    0.000000] ACPI: RSDP 000fe270 00014 (v00 HP    )
[    0.000000] ACPI: RSDT 7f7efc84 00034 (v01 HP     0944     24070920 HP   00000001)
[    0.000000] ACPI: FACP 7f7efc00 00084 (v02 HP     0944     00000002 HP   00000001)
[    0.000000] ACPI: DSDT 7f7efd50 08370 (v01 HP       nc6200 00010000 MSFT 0100000E)
[    0.000000] ACPI: FACS 7f7fae80 00040
[    0.000000] ACPI: APIC 7f7efcb8 0005A (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: MCFG 7f7efd14 0003C (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: SSDT 7f7f80c0 00371 (v01 HP       HPQPpc 00001001 MSFT 0100000E)
[    0.000000] ACPI: Local APIC address 0xfec01000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfec01000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.019766] ACPI: Core revision 20120320
[    0.088004] PM: Registering ACPI NVS region [mem 0x7f7efc00-0x7f7fafff] (46080 bytes)
[    0.088004] ACPI: bus type pci registered
[    0.089791] ACPI: Added _OSI(Module Device)
[    0.089794] ACPI: Added _OSI(Processor Device)
[    0.089797] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.089800] ACPI: Added _OSI(Processor Aggregator Device)
[    0.091839] ACPI: EC: Look up EC in DSDT
[    0.112087] ACPI: Interpreter enabled
[    0.112102] ACPI: (supports S0 S3 S4 S5)
[    0.112126] ACPI: Using IOAPIC for interrupt routing
[    0.116395] ACPI: Power Resource [C1D0] (on)
[    0.117247] ACPI: Power Resource [C1A9] (on)
[    0.118076] ACPI: Power Resource [C1C8] (on)
[    0.123479] ACPI: Power Resource [C251] (off)
[    0.123561] ACPI: Power Resource [C252] (off)
[    0.123644] ACPI: Power Resource [C253] (off)
[    0.123723] ACPI: Power Resource [C254] (off)
[    0.124438] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.124716] ACPI: No dock devices found.
[    0.124725] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.129307] ACPI: PCI Root Bridge [C002] (domain 0000 [bus 00-ff])
[    0.139935] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.141344] ACPI: PCI Interrupt Routing Table [\_SB_.C002._PRT]
[    0.141581] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C06D._PRT]
[    0.141744] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C006._PRT]
[    0.141823] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C0DE._PRT]
[    0.141937]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.141942]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.141944] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.157375] ACPI: PCI Interrupt Link [C0DA] (IRQs *10 11)
[    0.157497] ACPI: PCI Interrupt Link [C0DB] (IRQs 10 *11)
[    0.157613] ACPI: PCI Interrupt Link [C0DC] (IRQs 10 *11)
[    0.157729] ACPI: PCI Interrupt Link [C0DD] (IRQs *10 11)
[    0.157845] ACPI: PCI Interrupt Link [C0F0] (IRQs *10 11)
[    0.157960] ACPI: PCI Interrupt Link [C0F1] (IRQs 10 *11)
[    0.158076] ACPI: PCI Interrupt Link [C0F2] (IRQs *10 11)
[    0.158125] ACPI Exception: AE_NOT_FOUND, Evaluating _PRS (20120320/pci_link-184)
[    0.158662] ACPI: bus type usb registered
[    0.158858] PCI: Using ACPI for IRQ routing
[    0.184380] pnp: PnP ACPI init
[    0.184417] ACPI: bus type pnp registered
[    0.184688] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.189438] pnp 00:01: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.190284] pnp 00:02: Plug and Play ACPI device, IDs PNP0501 PNP0500 (active)
[    0.190506] pnp 00:03: Plug and Play ACPI device, IDs IFX0101 (active)
[    0.190568] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.190638] pnp 00:05: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.190690] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.190754] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.190822] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.190883] pnp 00:09: Plug and Play ACPI device, IDs SYN010e SYN0100 SYN0002 PNP0f13 (active)
[    0.191157] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.192109] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.192496] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.192514] pnp: PnP ACPI: found 13 devices
[    0.192516] ACPI: ACPI bus type pnp unregistered
[    0.192520] PnPBIOS: Disabled by ACPI PNP
[    0.327608] ACPI: AC Adapter [C175] (on-line)
[    0.327723] ACPI: Sleep Button [C1F1]
[    0.327834] ACPI: Lid Switch [C1F2]
[    0.327902] ACPI: Power Button [PWRF]
[    0.328056] ACPI: Fan [C255] (off)
[    0.328133] ACPI: Fan [C256] (off)
[    0.328207] ACPI: Fan [C257] (off)
[    0.328284] ACPI: Fan [C258] (off)
[    0.328337] ACPI: Requesting acpi_cpufreq
[    0.720083] ACPI: acpi_idle registered with cpuidle
[    0.771776] ACPI: Thermal Zone [TZ1] (74 C)
[    0.785966] ACPI: Thermal Zone [TZ2] (50 C)
[    0.794179] ACPI: Thermal Zone [TZ3] (31 C)
[    0.797918] ACPI: Thermal Zone [TZ4] (40 C)
[    0.797960] ACPI: Battery Slot [C177] (battery present)
[    0.798267] ACPI: Battery Slot [C176] (battery absent)
[    0.819162] ACPI: Battery Slot [C176] (battery absent)
[    1.234213] ACPI: Battery Slot [C177] (battery present)
[   16.944318] ACPI: Video Device [C05A] (multi-head: yes  rom: no  post: no)
[   19.691142] ACPI Warning: 0x00001060-0x0000107f SystemIO conflicts with Region \_SB_.C002.C003.C093 1 (20120320/utaddress-251)
[   19.691150] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   19.691157] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \_SB_.C002.C003.C08B 1 (20120320/utaddress-251)
[   19.691163] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   19.691167] ACPI Warning: 0x00001100-0x0000113f SystemIO conflicts with Region \_SB_.C002.C003.C09B 1 (20120320/utaddress-251)
[   19.691172] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   19.691263] snd_intel8x0 0000:00:1e.2: power state changed by ACPI to D0
[   19.691299] snd_intel8x0 0000:00:1e.2: power state changed by ACPI to D0

---

### Post by chili555 on 2013-05-02
> Thanks for the given information!
Yes, this is a laptop.

**HP Compaq nc6220**
Old Chili is busy wiping a few layers of grime of his spectacles. It's right there in the title, isn't it! Wow.

This looks a bit unusual:> [ 0.157375] ACPI: PCI Interrupt Link [C0DA] (IRQs *10 11)
[ 0.157497] ACPI: PCI Interrupt Link [C0DB] ([COLOR="#FF0000"]IRQs 10 *11[/COLOR])
[ 0.157613] ACPI: PCI Interrupt Link [C0DC] (IRQs 10 *11)
[ 0.157729] ACPI: PCI Interrupt Link [C0DD] (IRQs *10 11)
[ 0.157845] ACPI: PCI Interrupt Link [C0F0] (IRQs *10 11)
[ 0.157960] ACPI: PCI Interrupt Link [C0F1] (IRQs 10 *11)
[ 0.158076] ACPI: PCI Interrupt Link [C0F2] (IRQs *10 11)My similar entry looks like:> [    0.392280] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.392336] ACPI: PCI Interrupt Link [LNKB] ([COLOR="#FF0000"]IRQs 3 4 5 6 7 9 10 *11[/COLOR])
[    0.392382] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.392436] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.392491] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.392546] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.392591] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.392645] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
I am not sure this has anything to do with ethernet, but you might check in the BIOS and set the IRQs to AutoSelect, if such a setting is available. Please see attached. I don't see anything else very alarming. Please let us see:```
lspci -nn
```

---

### Post by acinoi on 2013-05-02
I was unable to find something relating to IRQs in the BIOS, but I have attached some pictures that I thought fit. 

```
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
02:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
02:06.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
02:06.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
02:06.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
02:06.5 Communication controller [0780]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Smart Card Controller [104c:8035]
```

---

### Post by chili555 on 2013-05-02
I'm a little suspicious of LAN/WLAN Switching. I recommend you search the manual for details. I doubt there is any harm in trying it both ways. Is there any change in that or any of the settings you showed us if you reset the BIOS to defaults?

In your *lspci*,we still see no ethernet device.

EDIT: [http://h30499.www3.hp.com/t5/Notebook-HP-ProBook-EliteBook/nc6230-What-is-LAN-WLAN-Switching/td-p/594982](http://h30499.www3.hp.com/t5/Notebook-HP-ProBook-EliteBook/nc6230-What-is-LAN-WLAN-Switching/td-p/594982)> It only allows one or the other of wireless or wired LAN to work at the same time. It is for power saving and in my opinion is best left off unless you exclusively use wireless or wired and want to squeeze out the last second of battery life. However, you already have it disabled.

---

### Post by acinoi on 2013-05-02
Yes, there is a change when I set WLAN on enable. My wireless network connection will stop working and the output from lspci -nn is the same as usual. 
 
Now my BIOS is set on default and my wireless connection works.

> 
 lspci -k
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 0944
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company NC6220
	Kernel driver in use: i915
	Kernel modules: intelfb, i915
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 308a
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
	Subsystem: Hewlett-Packard Company Device 0944
	Kernel driver in use: uhci_hcd
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
	Subsystem: Hewlett-Packard Company Device 0944
	Kernel driver in use: uhci_hcd
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
	Subsystem: Hewlett-Packard Company Device 0944
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 0944
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Compaq NC6220
	Kernel driver in use: snd_intel8x0
	Kernel modules: snd-intel8x0
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 0944
	Kernel modules: snd-intel8x0m
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
	Subsystem: Hewlett-Packard Company Device 0944
	Kernel modules: lpc_ich, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 0944
	Kernel driver in use: ata_piix
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
	Subsystem: Hewlett-Packard Company nc6120/nx8220/nw8240
	Kernel driver in use: ipw2200
	Kernel modules: ipw2200
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
	Subsystem: Hewlett-Packard Company Device 0944
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
	Subsystem: Hewlett-Packard Company Device 0944
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1
02:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
	Subsystem: Hewlett-Packard Company Device 0944
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
02:06.5 Communication controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Smart Card Controller
	Subsystem: Hewlett-Packard Company Device 0944




---

