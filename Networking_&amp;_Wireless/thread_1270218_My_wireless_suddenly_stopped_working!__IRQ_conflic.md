---
title: "My wireless suddenly stopped working!  IRQ conflict?"
date: 2009-09-19
forum: Networking &amp; Wireless
---

### Post by Brionius on 2009-09-19
Hi folks, 
Thanks very much in advance for any help you can provide!

I recently installed Ubuntu 9.04 on my Toshiba Satellite A10.  I've been using it for several weeks, and it's been working great - no problems with the wireless card at all.

All of a sudden, this morning, I brought my computer back from suspend, and the wireless wouldn't connect to the internet!  It kept trying to connect to my home network, and occasionally asked for the password.  Then after restarting, it stopped even finding networks to connect to.  My ethernet connection is working fine, which is how I'm posting this.

When I tried

```
sudo ifconfig wlan0 up
```I got this:

SIOCSIFFLAGS: Resource temporarily unavailable

I checked online for solutions to this problem, and found several people who had the exact same problem (with different hardware).  The solutions all seemed to involve fixing an IRQ conflict by disabling "PnP OS" in the BIOS.  Here is my /proc/interrupts file:

```

:~$ cat /proc/interrupts
           CPU0       CPU1       
  0:       1002      85253   IO-APIC-edge      timer
  1:         12       6111   IO-APIC-edge      i8042
  8:          0          1   IO-APIC-edge      rtc0
  9:          0         13   IO-APIC-fasteoi   acpi
 12:        139      73151   IO-APIC-edge      i8042
 14:         28       8011   IO-APIC-edge      pata_atiixp
 15:          0          0   IO-APIC-edge      pata_atiixp
 16:         11       2860   IO-APIC-fasteoi   ohci_hcd:usb2, HDA Intel
 17:          1          2   IO-APIC-fasteoi   ohci_hcd:usb3, ohci_hcd:usb5
 18:         97      23938   IO-APIC-fasteoi   ohci_hcd:usb4, ohci_hcd:usb6, ath, radeon@pci:0000:01:05.0
 19:          0          0   IO-APIC-fasteoi   ehci_hcd:usb1
 20:          0          3   IO-APIC-fasteoi   ohci1394
 21:          0          0   IO-APIC-fasteoi   mmc0
 22:         46      20032   IO-APIC-fasteoi   ahci
2300:          4       3187   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:      52300      30608   Local timer interrupts
RES:      35368      16502   Rescheduling interrupts
CAL:         74         48   Function call interrupts
TLB:        970        694   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0


```So, to my inexperienced eyes, there appears to be no IRQ conflict.  But then I'm a noob, so I don't trust my judgement :|

I also checked my computer's BIOS settings, and I couldn't find anything called "PnP OS", or similar.

I don't want to be tethered to the wall for the rest of my computer's life!  I want to be free!
Any ideas, o Ubuntu masters?  Thank you!!!

PS:  Let me know what other system information would be useful for solving this, and I will happily post it.  Thanks!

---

### Post by Brionius on 2009-09-19
Oops - got my computer model number wrong.

My laptop is a Toshiba Satellite A215.

---

### Post by Brionius on 2009-09-19
Wow...I just shut down and started up (as opposed to restarted) my computer, and the wireless now works fine....I'd still be curious to know what was going on, or if there is some other solution other than shutting down completely.  But I guess the problem has been solved.

---

