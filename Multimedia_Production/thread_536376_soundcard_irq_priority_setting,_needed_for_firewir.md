---
title: "soundcard irq priority setting, needed for firewire?"
date: 2007-08-27
forum: Multimedia Production
---

### Post by nalmeth on 2007-08-27
Following the advice found on [this page]("http://tapas.affenbande.org/wordpress/?page_id=40"), I'm trying to raise the IRQ priority of my firewire Presonus Firepod

> ...But we also want the soundcard IRQ handler run at a higher prio than jack, as the soundcard irq is what ultimately drives jackd. Thus we can use the chrt utility to change this (my soundcard is on IRQ 4 in my system - make sure you check in /proc/interrupts what&#8217;s yours):

 chrt -f -p 82 `pidof &#8220;IRQ-4&#8243;`

 A priority of 82 is well above jackd. jackd also runs threads besides its main loop. Namely a watchdog at priority 10 above its main loop (80 in this example), and all clients&#8217; process() threads will run with a priority 1 smaller than the main loop (69).

The device doesn't show in /proc/interrupts
```
$ cat /proc/interrupts 
           CPU0       CPU1       
  0:        630          0   IO-APIC-edge      timer
  1:      53702          0   IO-APIC-edge      i8042
  6:          5          0   IO-APIC-edge      floppy
  7:          0          0   IO-APIC-edge      parport0
  8:          3          0   IO-APIC-edge      rtc
  9:          1          0   IO-APIC-fasteoi   acpi
 12:    2675079          0   IO-APIC-edge      i8042
 14:    2932922          0   IO-APIC-edge      libata
 15:          0          0   IO-APIC-edge      libata
 16:          0          0   IO-APIC-fasteoi   uhci_hcd:usb1, ehci_hcd:usb5
 17:     425442          0   IO-APIC-fasteoi   uhci_hcd:usb2, libata
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
 19:   61401648          0   IO-APIC-fasteoi   uhci_hcd:usb4, nvidia
 20:   11386385          0   IO-APIC-fasteoi   eth0
 21:  157867983          0   IO-APIC-fasteoi   ohci1394
 22:    3198192          0   IO-APIC-fasteoi   Intel ICH6
NMI:          0          0 
LOC:  738219384  677048337 
ERR:          0
MIS:          0
```How do I found out which IRQ # my firewire card is? Is this step necessary or even useful?

---

### Post by Stochastic on 2007-09-17
I would guess that # 21 "ohci1394" is the firewire connection.  Out of curiosity, how do you find the mic preamps on the firepod?  do they add much character to the mix or are they clean and clear?  I just bought a Focusrite Saffire and I'm thinking of trading it in for a Firepod.  Not that there's anything wrong with the Saffire, but I'm wondering if I made the right choice.

---

### Post by Stochastic on 2007-09-19
-deleted post-

---

### Post by nalmeth on 2007-09-19
Stochasti, thanks for the reply, I had given up on this thread. 

The preamps on the firepod probably give a more 'clean and clear' sound rather than adding character, though I haven't had much opportunity to explore.
The offer a lot of headroom, and all in all they are the best that I have used (when my firepod WAS working well)

---

