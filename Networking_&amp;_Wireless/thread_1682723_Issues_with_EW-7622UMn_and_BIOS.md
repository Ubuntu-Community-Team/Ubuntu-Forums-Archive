---
title: "Issues with EW-7622UMn and BIOS"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by Orpheon on 2011-02-06
I recently bought this Edimax EW-7622UMn wireless stick because I needed one and it said it supported Linux.
There was an included linux driver that actually compiled rather well. At first I had problems with a missing wlan0 in iwconfig, but I solved that now. My new problem consists of this output after "sudo ifconfig wlan0 up":

SIOCSIFFLAGS: Resource temporarily unavailable

This is what google spit out:

----

The Netgear LNX100TX has a known issue with the tulip driver on a PNP
bios -- it gets an invalid IRQ assignment.  Confirm this by checking
/proc/interrupts.

The solution is to set the IRQ via BIOS, either directly (if possible)
for the PCI slot, or by disabling PNP altogether.

I ran across this very problem tonight.  Card's now happily configured
with IRQ 10.

----

A few other people said pretty much the same thing, namely to disable Plug and Play(PnP) in the BIOS.
I just can't find it!!!
Please tell me how to find the disable button or how to solve this problem without the BIOS.

Thank you.

Misc. information:
I have a Ultra Durable 3 classic something motherboard (not sure) and here is my /proc/interrupts:


           CPU0       CPU1       CPU2       CPU3       
  0:         24          0          0          2   IO-APIC-edge      timer
  1:          0          0          0          2   IO-APIC-edge      i8042
  7:          0          0          0          0   IO-APIC-edge      parport0
  8:          0          0          0          1   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 16:          0          0      10840          0   IO-APIC-fasteoi   ahci
 17:          0          0        222          0   IO-APIC-fasteoi   pata_jmicron, hda_intel
 18:          0       7701          0          0   IO-APIC-fasteoi   ehci_hcd:usb1
 19:          0        152          0          0   IO-APIC-fasteoi   ata_piix, ata_piix
 23:          0          0      20389          0   IO-APIC-fasteoi   ehci_hcd:usb2
 40:      11917          0          0          0  HPET_MSI-edge      hpet2
 41:          0      10314          0          0  HPET_MSI-edge      hpet3
 42:          0          0       9336          0  HPET_MSI-edge      hpet4
 43:          0          0          0      10355  HPET_MSI-edge      hpet5
 49:          0          0       5247          0   PCI-MSI-edge      eth0
 50:          0          0          0        697   PCI-MSI-edge      hda_intel
NMI:          0          0          0          0   Non-maskable interrupts
LOC:         59         44         26          9   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:          0          0          0          0   Performance monitoring interrupts
PND:          0          0          0          0   Performance pending work
RES:        446        471        449        439   Rescheduling interrupts
CAL:         76         80         84         87   Function call interrupts
TLB:        270        289        252        138   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:          3          3          3          3   Machine check polls
ERR:          3
MIS:          0

---

### Post by Orpheon on 2011-02-07
*Bump*
I really need help (please).

---

