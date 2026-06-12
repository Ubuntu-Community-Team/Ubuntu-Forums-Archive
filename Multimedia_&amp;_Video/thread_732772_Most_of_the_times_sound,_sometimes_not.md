---
title: "Most of the times sound, sometimes not"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by jyrgen on 2008-03-23
i have two soundcards in my desktop PC, SB Live and RME

sometimes the RME (DIGI PAD 96/8) is not recognized,
after rebooting it's okay, which is an annoying fix... 

IRQs with sound working:

  0:        188   IO-APIC-edge      timer
  1:        177   IO-APIC-edge      i8042
  6:          5   IO-APIC-edge      floppy
  7:          0   IO-APIC-edge      parport0
  8:          2   IO-APIC-edge      rtc
  9:          0   IO-APIC-fasteoi   acpi
 10:          0   IO-APIC-edge      MPU401 UART
 14:      20313   IO-APIC-edge      ide0
 15:       2950   IO-APIC-edge      ide1
 16:        163   IO-APIC-fasteoi   ohci_hcd:usb1
 17:          0   IO-APIC-fasteoi   ohci_hcd:usb2
 18:       8823   IO-APIC-fasteoi   ehci_hcd:usb3
 19:        383   IO-APIC-fasteoi   eth1
 20:        487   IO-APIC-fasteoi   RME96
 21:      12240   IO-APIC-fasteoi   nvidia
 22:        201   IO-APIC-fasteoi   EMU10K1


IRQs with sound not working


  0:        188   IO-APIC-edge      timer
  1:       1574   IO-APIC-edge      i8042
  6:          5   IO-APIC-edge      floppy
  7:          0   IO-APIC-edge      parport0
  8:          2   IO-APIC-edge      rtc
  9:          0   IO-APIC-fasteoi   acpi
 10:          0   IO-APIC-edge      MPU401 UART
 14:      29551   IO-APIC-edge      ide0
 15:      29151   IO-APIC-edge      ide1
 16:        163   IO-APIC-fasteoi   ohci_hcd:usb1
 17:          0   IO-APIC-fasteoi   ohci_hcd:usb2
 18:       8820   IO-APIC-fasteoi   eth1
 19:      36086   IO-APIC-fasteoi   ehci_hcd:usb3
 20:     126625   IO-APIC-fasteoi   nvidia
 21:       2043   IO-APIC-fasteoi   EMU10K1
 22:          0   IO-APIC-fasteoi   RME96


strangely the sound card are swapping places (by coincidence ?)

how can i fix it ?

thanks, jyrgen

---

