---
title: "Is it my router or adapter?"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by rcayea on 2010-05-10
Hey everyone,

I am yet another wireless confused person on these forums. I don't expect someone to solve my problem for me, but I was hoping someone could point me to a good website or a set of commands to help me determine if my constant internet dropping every 5-10 minutes or so is my router or adapter.

I have a wrt160n router and a asus pci adapter. 

thanks for any tips,
Randy

---

### Post by tgalati4 on 2010-05-10
Most likely problem: interference.  PCI cards have the antenna mounted on the back.  Try raising the machine or turning it around so that there is a clean line-of-site between the router antenna and the pci card.  You can sometimes use an extension cable to move the antenna to a better location.

Sometimes it's an interrupts problem.  Post the output of:

cat /proc/interrupts

If that is the case, then move the card to a different slot.

---

### Post by rcayea on 2010-05-10
rcayea@empty-net-goal:~$ 
thanks for the reply...here is the info requested...

cat /proc/interrupts
       ```

```    CPU0       CPU1       
  0:      11437      13695   IO-APIC-edge      timer
  1:          2          0   IO-APIC-edge      i8042
  4:          1          1   IO-APIC-edge    
  8:          0          1   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          4          0   IO-APIC-edge      i8042
 16:        450       5767   IO-APIC-fasteoi   uhci_hcd:usb3, pata_marvell, wlan0, nvidia
 17:          1         81   IO-APIC-fasteoi   CMI8738-MC8
 18:       1908        292   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb5, uhci_hcd:usb8
 19:      11940       1936   IO-APIC-fasteoi   ata_piix, ata_piix, uhci_hcd:usb7
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 23:       1704         18   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb6
 28:          0          0   PCI-MSI-edge      eth0
 29:        204       1358   PCI-MSI-edge      hda_intel
NMI:          0          0   Non-maskable interrupts
LOC:       6412       5003   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:       1593       2230   Rescheduling interrupts
CAL:       1060        146   Function call interrupts
TLB:       1519       1481   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          1          1   Machine check polls
ERR:          1
MIS:          0```

```

---

### Post by rcayea on 2010-05-11
Bump... Can anyone help me out with the requested information posted?  thanks.

---

### Post by rcayea on 2010-05-11
Anyone? Thanks in advance.

---

### Post by rcayea on 2010-05-11
I totally printed the output wrong. If anyone would like to help, this is how the output actually looks...

[PHP]           CPU0       CPU1       
  0:     877866     879452   IO-APIC-edge      timer
  1:          2          0   IO-APIC-edge      i8042
  4:          1          1   IO-APIC-edge    
  8:          0          1   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          4          0   IO-APIC-edge      i8042
 16:        479     360117   IO-APIC-fasteoi   uhci_hcd:usb3, pata_marvell, wlan0, nvidia
 17:          1      19279   IO-APIC-fasteoi   CMI8738-MC8
 18:       2862        295   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb5, uhci_hcd:usb8
 19:     187471       1899   IO-APIC-fasteoi   ata_piix, ata_piix, uhci_hcd:usb7
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 23:      58800         19   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb6
 28:          0          0   PCI-MSI-edge      eth0
 29:        207       1357   PCI-MSI-edge      hda_intel
NMI:          0          0   Non-maskable interrupts
LOC:     355895     475036   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:      74870     105410   Rescheduling interrupts
CAL:        387       1311   Function call interrupts
TLB:      10592      11520   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:         16         16   Machine check polls
ERR:          1
MIS:          0
[/PHP]

---

### Post by tgalati4 on 2010-05-11
Your wlan0 (wireless) shares interrupt 16 with a lot of other devices.  Perhaps move it do a different slot.

 16:        479     360117   IO-APIC-fasteoi   uhci_hcd:usb3, pata_marvell, wlan0, nvidia 

Your interrupt count seems high (360117) but it's also shared with your graphics card (nvidia).

Your rescheduling interrupts are high.  They should be low.  Something seems to be tripping up the data bus.

RES:      74870     105410   Rescheduling interrupts

---

### Post by rcayea on 2010-05-11
Thank you much for the info. I will look into a high interrupt count and the other info you offered. 

thanks!

---

