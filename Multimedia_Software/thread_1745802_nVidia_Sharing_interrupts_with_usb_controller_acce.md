---
title: "nVidia Sharing interrupts with usb controller: acceptable?"
date: 2011-05-01
forum: Multimedia Software
---

### Post by Atamisk on 2011-05-01
Hello, 

I'm getting random system hangs and display issues when using my computer with my nVidia graphics card. On a lark, i checked /proc/interrupts and noticed that the nvidia device is sharing an interrupt with one of my USB boards, as well as my integrated sound card. i managed to move my sound card by editing my alsa-base and adding: 

```
options snd-hda-intel enable_msi=1
```

This helps mostly, but i'm still getting intermittant issues. is there any way to shift the interrupt of my gfx card (or usb controller) to avoid this potential conflict? i know the devices should be able to co-exist, but i've seen several people having issues when an nVidia card shares interrupts. 

Interrupt list: 
```
           CPU0       CPU1       CPU2       CPU3       
  0:         24          5          0          1   IO-APIC-edge      timer
  1:          0          0          1          1   IO-APIC-edge      i8042
  8:          0          1          0          0   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 12:          2          1          0          1   IO-APIC-edge      i8042
 16:     141412         90       4860         87   IO-APIC-fasteoi   ehci_hcd:usb1, nvidia
 23:      23479       1414       1349       1256   IO-APIC-fasteoi   ehci_hcd:usb2
 41:      13574         15         17         18   PCI-MSI-edge      eth0
 42:       7767       1094      11001       1094   PCI-MSI-edge      ahci
 43:        100         82         79         81   PCI-MSI-edge      hda_intel
 44:         36         37         33         35   PCI-MSI-edge      hda_intel
NMI:          0          0          0          0   Non-maskable interrupts
LOC:     196197     151353     206103     113049   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:          0          0          0          0   Performance monitoring interrupts
IWI:          0          0          0          0   IRQ work interrupts
RES:       5820       7308       9504       5492   Rescheduling interrupts
CAL:       2622       1776       3385       3593   Function call interrupts
TLB:       1675       1327       1954       1510   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:          7          7          7          7   Machine check polls
ERR:          3
MIS:          0
```

Thanks, 
-Aaron

---

### Post by Atamisk on 2011-05-01
I found the paramater for enabling msi for the nv driver:


options nvidia-current NVreg_EnableMSI=1

I will continue troubleshooting!

Thanks, 
-Aaron

---

