---
title: "Conflict between ISA network card and ISA sound card"
date: 2007-08-17
forum: Multimedia &amp; Video
---

### Post by cjaird on 2007-08-17
I can get my either my ISA network card or my ISA soundcard to work, but can't get them both working together.  

Typing "sudo modprobe ne" gets the network card working fine.  But if I then type "sudo modprobe sb" I get this: 
FATAL: Error inserting sb (/lib/modules/2.6.15-28-386/kernel/sound/oss/sb.ko): No such device

For reference, typing "cat /proc/interrupts" gives:
         CPU0
  0:    3711075          XT-PIC  timer
  1:       4135          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  5:      50918          XT-PIC  NE2000
  7:          1          XT-PIC  parport0
  8:          4          XT-PIC  rtc
 10:          0          XT-PIC  ohci_hcd:usb1, ohci_hcd:usb2, ehci_hcd:usb5
 11:          0          XT-PIC  ohci_hcd:usb3, uhci_hcd:usb4
 12:     265029          XT-PIC  i8042
 14:      50062          XT-PIC  ide0
 15:     260080          XT-PIC  ide1
NMI:          0
LOC:          0
ERR:          0
MIS:          0

If I reboot and type "sudo modprobe sb" then the sound works fine, but typing "sudo modprobe ne" then gives an error message!  

Any help much appreciated.

Thanks,
Chris

---

### Post by vidarjb on 2007-08-22
If this is an old soundblaster ISA soundcard, you should be able to set the IRQ channel with a jumper switch on the card, as was possible on most of the old ISA soundcards.

I think they are set to use IRQ 12 from the factory.. The easiest way, to avoid conflicts are probably to set jumper, so it uses another IRQ.

Best of luck!

Vidar

---

### Post by cjaird on 2007-09-09
Thanks Vidar.  

I actually managed to solve this by:
1.) Hitting "delete" during boot-up and altering the BIOS settings so that IRQ channels 5 & 9 were reserved for ISA cards.
2.) Adding the following two lines to the /etc/modules file:
     sb
     ne

Chris

---

