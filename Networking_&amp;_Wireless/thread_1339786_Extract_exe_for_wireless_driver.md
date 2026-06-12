---
title: "Extract exe for wireless driver"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by jmalone767 on 2009-11-27
I'm upset because my newest laptop is a sony Vaio VGN-NW235F and after installing Ubuntu I thought the wireless driver would be as simple as it usually is while using ndiswrapper, but no.

I installed it like normal and it is working but I downloaded the driver off of sony's website, its an EXE which is fine, usually I can use cabextract, 7zip, or unshield to extract it but all three have failed in this case. Also when attempting to install it in wine it says that I must have Windows vista and then closes. 

Any ideas/ utilities I can use to extract this EXE to get the inf that ndiswrapper needs?

If it helps Im running Jaunty 9.04

---

### Post by nerdy_kid on 2009-11-27
i think 

```

unzip


``` will do the trick

[edit]
wine has a setting to 'fake' windows vista...

---

### Post by jmalone767 on 2009-11-27
No here's the output
```

john@john-laptop:~/Desktop$ unzip MRDWLL-00203583-764.EXE 
Archive:  MRDWLL-00203583-764.EXE
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of MRDWLL-00203583-764.EXE or
        MRDWLL-00203583-764.EXE.zip, and cannot find MRDWLL-00203583-764.EXE.ZIP, period.
```


Awesome! I never knew you could change the Version of Windows.... but didn't solve the problem as I get a new error message saying "the update was not intended for use with this computer"

---

### Post by andyeeflacure on 2009-11-27
Hi..
  I have read your comment and as per that i am looking for the solution...  so as soon as i am find it on google... 
Thanks for sharing the post...

---

### Post by nerdy_kid on 2009-11-28
hmm

please post the output of
```

lspci -v -k

```

---

### Post by jmalone767 on 2009-11-28
```
john@john-laptop:~$ lspci -v -k
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Sony Corporation Device 906b
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Sony Corporation Device 906b
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at e140 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Sony Corporation Device 906b
    Flags: bus master, fast devsel, latency 0
    Memory at d0400000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Sony Corporation Device 906b
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at e0e0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: Sony Corporation Device 906b
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at e0c0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: Sony Corporation Device 906b
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at e0a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
    Subsystem: Sony Corporation Device 906b
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at d4e04c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Sony Corporation Device 906b
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at d4e00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: d3900000-d4cfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: d2500000-d38fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=0a, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: d0500000-d24fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Sony Corporation Device 906b
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at e080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Sony Corporation Device 906b
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at e060 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Sony Corporation Device 906b
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at e040 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: Sony Corporation Device 906b
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d4e04800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=32
    Memory behind bridge: d4d00000-d4dfffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Sony Corporation Device 906b
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
    Subsystem: Sony Corporation Device 906b
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
    I/O ports at e130 [size=8]
    I/O ports at e120 [size=4]
    I/O ports at e110 [size=8]
    I/O ports at e100 [size=4]
    I/O ports at e020 [size=32]
    Memory at d4e04000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Sony Corporation Device 906b
    Flags: medium devsel, IRQ 5
    Memory at d4e05000 (64-bit, non-prefetchable) [disabled] [size=256]
    I/O ports at e000 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
    Subsystem: Sony Corporation Device 906b
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at d3920000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at d000 [size=256]
    Expansion ROM at d3900000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Foxconn International, Inc. Device e017
    Flags: bus master, fast devsel, latency 0, IRQ 4
    Memory at d2500000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel modules: ath9k

0b:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
    Subsystem: Sony Corporation Device 906b
    Flags: bus master, medium devsel, latency 32, IRQ 16
    Memory at d4d00000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

0b:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
    Subsystem: Sony Corporation Device 906b
    Flags: bus master, medium devsel, latency 32, IRQ 17
    Memory at d4d00900 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

0b:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
    Subsystem: Sony Corporation Device 906b
    Flags: bus master, medium devsel, latency 32, IRQ 4
    Memory at d4d00800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
```


UPDATE:
I installed Karmic 9.10 (because I herd it had the correct driver support, also to match my desktop) but the issue was not fixed. I read that my current kernel 2.6.31-15 supports AR9285 wireless cards but I still can't get anything. I really am out of ideas. Please any suggestions would be greatly appreciated.

---

### Post by jmalone767 on 2009-11-29
For anyone who stumbles across this thread in the future I found the solution here

[html]http://ubuntuforums.org/showthread.php?p=8405808#post8405808[/html]the credit goes to fingiblename.

---

### Post by opt1k on 2009-11-29
If you are hell bent on using ndiswrapper you can install wine and run the install for the driver and get the files you need from ~/.wine

also refer to this thread with information about backports, it appears your issue is common.
[http://ubuntuforums.org/showthread.php?t=1179951](http://ubuntuforums.org/showthread.php?t=1179951)

---

### Post by nerdy_kid on 2009-11-29
glad it works for you now!

have fun...

---

