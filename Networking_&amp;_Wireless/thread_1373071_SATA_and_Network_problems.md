---
title: "SATA and Network problems"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by philburr on 2010-01-05
This almost started out as yet another samba is slow problem.  But I've narrowed things down a bit.

I have a Promise PDC20376 on board SATA controller.  I just installed a new SATA drive in it.  Also I have an onboard Broadcom BCM4401 ethernet port.  

When I do file transfers which do not involve the SATA drive, so the file transfer is going to the IDE drive, I get transfer rates of about 10 MByte/sec (100 mbit network).  When I transfer to/from the SATA drive it starts out at about 10 MByte/sec  but quickly drops down to under 1MByte/sec and pretty much stays there throughout the remainder of the transfer.  Iperf shows similar transfer as the non-SATA transfer.

I thought it might be a problem with the drive.  hdparm -Tt /dev/sdb shows decent throughput on the drive at around 60 MByte/sec.  No smart problems.  I can transfer files from the IDE to the SATA at comparable rates.

If I do a transfer over the network using the IDE drive I get good throughput.  If I then do non network access to the SATA drive (copying a local file) the network traffic bottoms out.

So I appear to be facing a hardware conflict.

```
$ cat /proc/interrupts
           CPU0
  0:         48   IO-APIC-edge      timer
  1:          4   IO-APIC-edge      i8042
  3:          4   IO-APIC-edge
  4:          4   IO-APIC-edge
  6:          5   IO-APIC-edge      floppy
  7:          0   IO-APIC-edge      parport0
  8:          0   IO-APIC-edge      rtc0
 14:      55196   IO-APIC-edge      ata_piix
 15:          0   IO-APIC-edge      ata_piix
 16:          0   IO-APIC-fasteoi   uhci_hcd:usb2, mga@pci:0000:01:00.0
 17:        101   IO-APIC-fasteoi   Intel 82801DB-ICH4
 18:          0   IO-APIC-fasteoi   uhci_hcd:usb4
 19:          0   IO-APIC-fasteoi   uhci_hcd:usb3
 20:    1686435   IO-APIC-fasteoi   eth4
 22:          2   IO-APIC-fasteoi   acpi, ohci1394
 23:       3694   IO-APIC-fasteoi   sata_promise, ehci_hcd:usb1
NMI:          0   Non-maskable interrupts
LOC:    9708460   Local timer interrupts
SPU:          0   Spurious interrupts
CNT:          0   Performance counter interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:        117   Machine check polls
ERR:          0
MIS:          0
$
```It doesn't appear to be an interrupt conflict.  The SATA is on IRQ 23 and the network on IRQ 20.

I'm out of ideas.  I'm going to try and locate a PCI SATA and/or PCI network card to see if I can resolve it that way but other than that, any suggestions?

phil

---

