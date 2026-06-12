---
title: "WiFi card not recognized"
date: 2011-07-07
forum: Networking &amp; Wireless
---

### Post by austerus on 2011-07-07
Hello,

I have a Edimax EW-7711IN b/g/n PCI WiFi adapter and it seems that Ubuntu doesn't recognize it. On the Edimax website it recommends to install DPO_RT3070_LinuxSTA_V2.3.0.2_20100412.tar package which (as I read) is for an USB WiFi adapter.

Could anybody help with an idea?

Thanks!

---

### Post by chili555 on 2011-07-07
Please open a terminal and run and post:```
lspci -nn | grep 0280
```When we find out it's this: Network controller [0280]: RaLink Device [1814:3060] then we'll install rt3562sta: [http://ubuntuforums.org/showthread.php?t=1615304](http://ubuntuforums.org/showthread.php?t=1615304)

See post #7.

---

### Post by austerus on 2011-07-07
Thanks!

I will get right on it!

I was trying it while running the system from USB drive, do you think an install survives a restart? (not sure, first time USB-ing) I will probably end up doing an install to HDD but just curious.

Thanks again!

---

### Post by chili555 on 2011-07-07
I don't know for sure, but I imagine not. So, was that your device?

---

### Post by austerus on 2011-07-08
That's my device, but it seems there are some issues.

The current file for the chipset on the website was DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tgz which I installed. 

I did the blacklists

```

blacklist rt2800pci
 blacklist rt2x00lib
 blacklist rt2x00pci
 blacklist rt2800lib

```and then

```
sudo su echo rt3562sta >> /etc/modules exit
```However, the diagnostic commands you mentioned returned this

```
rt3562sta             869831  0 

```and
```
[   21.512617] 
rt3562sta: module license 'unspecified' taints kernel.
[   21.515709] ===> rt2860_probe
[   21.515720] rt2860 0000:02:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   21.516323] @rt2860_probe MAC address: 00:1f:1f:aa:c8:eb
[   21.516324] <=== rt2860_probe

```I have a network device ra0 but it is marked as "unknown", not as a wireless adapter. :(

---

### Post by chili555 on 2011-07-09
The interface ra0 is what is created when you compile a driver from source from Ralink; that's normal. Whether it says it's a wireless device or not, it is. Let's see if it scans for networks:```
sudo iwlist ra0 scan
```Your readings look pretty solid; nothing screams 'error' or 'fixme.'

Do you see networks when you click the Network Manager icon?

I am USBing myself for the first time, Debian Squeeze. It is interesting to learn a new trick or two.

---

### Post by austerus on 2011-07-09
I found it cool that the ubuntu tool lets me create a drive on the usb to save modifications.
 
 About the scan command, it tells me "ra0 interface does not support scanning".

---

### Post by chili555 on 2011-07-09
Let's have a look at:```
lsmod | grep -e rt2 -e rt3
dmesg | grep -e rt2 -e rt3
```I made some changes on my Debian USB, but haven't tested it yet.

---

### Post by austerus on 2011-07-09
Hello,

The output to those two commands in what I posted earlier (sorry, should've mentioned that)
lsmod | grep -e rt2 -e rt3
gives

rt3562sta             869831  0
and

dmesg | grep -e rt2 -e rt3gives
[   21.512617]  rt3562sta: module license 'unspecified' taints kernel. [   21.515709] ===> rt2860_probe [   21.515720] rt2860 0000:02:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22 [   21.516323] @rt2860_probe MAC address: 00:1f:1f:aa:c8:eb [   21.516324] <=== rt2860_probe
thanks!

---

### Post by austerus on 2011-07-09
Heh,

All solved now, just had to do a little edit to change HAS_WPA_SUPPLICANT and HAS_NATIVE_WPA_SUPPLICANT to y and remake/install. 

Still thanks to you though, the solution was around here in the forums. Seems you saved quite a few unfortunate souls who got stuck with the ralink chipset.

Thanks a lot man!

---

### Post by jbrid on 2011-07-31
I am having a similar issue to austerus but his fix did not work for me. I have done a remake/install several times now and can't get the device up.

The modprobe command seems to work OK, but I get this error when I try to bring up ra0:

```

$ sudo modprobe rt3562sta
$ sudo ifconfig ra0 inet up
ra0: ERROR while getting interface flags: No such device

```

Here's some other info:

```

$ lsmod | grep -e rt2 -e rt3
rt3562sta             869831  0 
$ dmesg | grep -e rt2 -e rt3
[   84.441955] rt3562sta: module license 'unspecified' taints kernel.

```

ifconfig and iwconfig do not mention anything about ra0.

I have added rt2800pci to blacklist.conf. I don't think that matters at this point but I thought I would mention it.

I appreciate any help. I am racking my brain on this one. :mad:

---

### Post by chili555 on 2011-07-31
Do you have the same device? Please run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by jbrid on 2011-07-31
> **chili555 said:**
> Do you have the same device? Please run and post:```
lspci -nn | grep 0280
```Thanks.

I get nothing return from that command.

---

### Post by chili555 on 2011-07-31
That suggests you have no wireless card at all. Let's dig deeper:```
lspci -nn
lsusb
```Thanks.

---

### Post by jbrid on 2011-07-31
> **chili555 said:**
> That suggests you have no wireless card at all. Let's dig deeper:```
lspci -nn
lsusb
```Thanks.

Thanks a lot for your response.

I agree. The last thing I tried was actually taking the card out and putting it in another PCI slot. The BIOS saw it there in both cases.

```

$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port [8086:2771] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2776] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller [8086:27de] (rev 01)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)

```
```

$ lsusb
Bus 005 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by chili555 on 2011-07-31
> The BIOS saw it there in both cases.Does the BIOS have any option to enable or disable that slot? Are the IRQs set for 'Auto Detect?' Is the BIOS set to Plug and Play = yes? What does this tell us?```
dmesg | grep -i -e warn -e error
```

---

### Post by jbrid on 2011-07-31
> **chili555 said:**
> Does the BIOS have any option to enable or disable that slot? Are the IRQs set for 'Auto Detect?' Is the BIOS set to Plug and Play = yes? What does this tell us?```
dmesg | grep -i -e warn -e error
```

The BIOS has an option to disable all of the PCI slots. This is correctly set to enable. 

I could not find any option in there regarding IRQ's.

I could also not find any option in there regarding plug-and-play.

```

$ dmesg | grep -i -e warn -e error
[   15.741356] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   21.128120] EXT4-fs (sda1): re-mounted. Opts: errors=remount
ro,commit=0

```

The wild thing about this is that about 3 hours ago I made it further than this. At that point is what seeing the new wireless card, but I couldn't make a connection. I was having issues similar to the people in [this thread]("http://ubuntuforums.org/showthread.php?t=1612271"). I then determined that I needed to blacklist rt2800pci. After I did that and rebooted, everything disappeared. The card was no longer detected and I started over to no avail.

Thanks.

---

### Post by jbrid on 2011-07-31
As another test I just booted the system to a LiveCD. No dice. lspci and lsusb did not see the card.

---

### Post by chili555 on 2011-07-31
This is a bit of a long shot, but:```
dmesg | grep -i acpi
```It might be lengthy.

---

### Post by jbrid on 2011-07-31
> **chili555 said:**
> This is a bit of a long shot, but:```
dmesg | grep -i acpi
```It might be lengthy.


```


$ dmesg | grep -i acpi
[    0.000000]  BIOS-e820: 00000000bf686c00 - 00000000bf688c00 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf688c00 - 00000000bf68ac00 (ACPI data)
[    0.000000] ACPI: RSDP 000feb00 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 000fd259 0005C (v01 DELL    GX620   00000007 ASL  00000061)
[    0.000000] ACPI: FACP 000fd351 000F4 (v03 DELL    GX620   00000007 ASL  00000061)
[    0.000000] ACPI: DSDT fffd484e 03D69 (v01   DELL    dt_ex 00001000 INTL 20050309)
[    0.000000] ACPI: FACS bf686c00 00040
[    0.000000] ACPI: SSDT fffd86d6 000AA (v01   DELL    st_ex 00001000 INTL 20050309)
[    0.000000] ACPI: APIC 000fd445 00072 (v01 DELL    GX620   00000007 ASL  00000061)
[    0.000000] ACPI: BOOT 000fd4b7 00028 (v01 DELL    GX620   00000007 ASL  00000061)
[    0.000000] ACPI: ASF! 000fd4df 00067 (v16 DELL    GX620   00000007 ASL  00000061)
[    0.000000] ACPI: MCFG 000fd546 0003E (v01 DELL    GX620   00000007 ASL  00000061)
[    0.000000] ACPI: HPET 000fd584 00038 (v01 DELL    GX620   00000007 ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.011528] ACPI: Core revision 20110112
[    0.234099] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.234104] ACPI: bus type pci registered
[    0.239339] ACPI: EC: Look up EC in DSDT
[    0.260312] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.271526] ACPI: Interpreter enabled
[    0.271540] ACPI: (supports S0 S1 S3 S4 S5)
[    0.271596] ACPI: Using IOAPIC for interrupt routing
[    0.375314] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.375331] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.420090] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.498784] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.499559] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[    0.500179] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[    0.500405] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI3._PRT]
[    0.500685] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    1.207579] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    1.208285] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    1.208747] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    1.209202] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    1.209644] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    1.210125] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    1.210572] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    1.211023] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    1.212275] PCI: Using ACPI for IRQ routing
[    1.231404] pnp: PnP ACPI init
[    1.231442] ACPI: bus type pnp registered
[    1.256220] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    1.259207] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.259506] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.259745] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.259967] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    1.260244] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.270601] pnp 00:06: Plug and Play ACPI device, IDs PNP0401 (active)
[    1.274058] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    1.296263] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.300141] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.300152] pnp: PnP ACPI: found 10 devices
[    1.300155] ACPI: ACPI bus type pnp unregistered
[    1.300160] PnPBIOS: Disabled by ACPI PNP
[    1.372025] ACPI: Power Button [VBTN]
[    1.372132] ACPI: Power Button [PWRF]
[    1.372811] ACPI: acpi_idle registered with cpuidle
[   16.724580] parport_pc 00:06: reported by Plug and Play ACPI



```

---

### Post by chili555 on 2011-07-31
> [    0.260312] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignoredThis seems to be an issue: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/795099](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/795099)> what this message is saying is that ***your bios is doing something that the kernel thinks it shouldn't be doing and that the kernel is ignoring this invalid request.*** One workaround is to add "acpi_osi=Linux" to the kernel command-line parameters, but this may result in some change behaviors on your machine (some things may start working or stop working, depending on the bios).Of course, we suspect that your BIOS is trying to activate the PCI slot with the wireless card on it. Would you like to try the quoted boot parameter to see if it helps or hurts?

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by jbrid on 2011-07-31
> **chili555 said:**
> This seems to be an issue: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/795099](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/795099)Of course, we suspect that your BIOS is trying to activate the PCI slot with the wireless card on it. Would you like to try the quoted boot parameter to see if it helps or hurts?

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Bummer!

Thanks for you help on this today. I may try the boot parameter a little later. I don't have much to loose at this point. I am not sure how to do that without grub installed. This machine only has the 1 OS. I suppose I could test it with a LiveCD instead.

This may be an idea:
> 
You may also want to check for a bios update for your machine.

I just need to figure out how to do a BIOS flash without a Windows installation...fun stuff!

I am also considering returning the PCI card and getting a USB adapter that has clearer linux support.

---

### Post by chili555 on 2011-07-31
> I am not sure how to do that without grub installed.If you have Ubuntu installed then you have GRUB installed.

---

### Post by jbrid on 2011-07-31
> **chili555 said:**
> If you have Ubuntu installed then you have GRUB installed.

Right...bad choice of words. I just meant that it is not in use.

---

### Post by bkratz on 2011-07-31
> **jbrid said:**
> Bummer!

Thanks for you help on this today. I may try the boot parameter a little later. I don't have much to loose at this point. I am not sure how to do that without grub installed. This machine only has the 1 OS. I suppose I could test it with a LiveCD instead.

This may be an idea:

I just need to figure out how to do a BIOS flash without a Windows installation...fun stuff!

I am also considering returning the PCI card and getting a USB adapter that has clearer linux support.



Here is a link to do a bios update sans Windows (just in case you need it)..
[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

---

### Post by jbrid on 2011-07-31
Thanks.

I got the BIOS updated from A08 to A11, but it did not improve things at all.

Next is to try the boot option.

---

### Post by jbrid on 2011-08-01
Assuming that I did this correctly, the boot option had not impact. lspci and lsusb still do not show the PCI card.

Here's what I did...

[LIST=1]
[*]Enabled the grub screen.
[*]Pressed 'e' to edit commands before booting
[*]Added a new line at the bottom - "acpi_osi=Linux" (without quotes)
[*]Cntrl-X to boot
[/LIST]

---

### Post by chili555 on 2011-08-01
I have no further suggestions. Sorry.

---

### Post by jbrid on 2011-08-01
No problem. I appreciate you assistance.

---

