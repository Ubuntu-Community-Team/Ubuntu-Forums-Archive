---
title: "new monitor not displaying correctly"
date: 2011-08-24
forum: Multimedia Software
---

### Post by seagull man on 2011-08-24
Hi all,

I hope that somebody can help me as I have searched everywhere and can't find a solution to my issue.

Basically I bought myself a new 27" ViewSonic monitor, connected it to my ATI HD3870 via a DVI-HDMI adaptor and HDMI cable.

The monitor initially had an issue displaying its native resolution of 1920x1080 such that when set to this resolution the desktop would be larger than the displayed area. Also my internet stopped working correctly.

I suspected this might be an irq conflict so I disabled a few things in my BIOS (I believe this reshuffled the irqs as shown on POST screen) and relocated my wi-fi card to another slot. Can't remember which one, but one of these seems to have fixed the internet issue. However the display remains the same.

I have tried adjusting the scaling in Catalyst Control Centre, which allows me to fit the desktop to the screen, but it is not clear (looks like it is scaling from a resolution that doesn't match the screen).

I can't work out what is wrong. Not sure if it is any use but here is the contents of my /proc/interrupts:

           CPU0       CPU1       CPU2       CPU3       
  0:         25          0          6          0   IO-APIC-edge      timer
  1:          0          0          2          0   IO-APIC-edge      i8042
  7:          1          0          0          0   IO-APIC-edge    
  8:          0          0          1          0   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 12:          0          0          4          0   IO-APIC-edge      i8042
 14:          0          0          0          0   IO-APIC-edge      pata_atiixp
 15:          0          0          0          0   IO-APIC-edge      pata_atiixp
 16:        148          0        702          3   IO-APIC-fasteoi   ohci_hcd:usb3, ohci_hcd:usb4, hda_intel
 17:          0          0          0          0   IO-APIC-fasteoi   ehci_hcd:usb1
 18:      20417          0         40          1   IO-APIC-fasteoi   ohci_hcd:usb5, ohci_hcd:usb6, ohci_hcd:usb7
 19:       5630          1       5653          6   IO-APIC-fasteoi   ehci_hcd:usb2
 21:      33735          0        409          1   IO-APIC-fasteoi   0000:02:07.0
 22:      12377          0       8592          3   IO-APIC-fasteoi   ahci, firewire_ohci
 41:          0          0         82          2   PCI-MSI-edge      hda_intel
 42:          0          0      75154         46   PCI-MSI-edge      fglrx[0]@PCI:1:0:0
NMI:          0          0          0          0   Non-maskable interrupts
LOC:      85146      77705     114584      43787   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:          0          0          0          0   Performance monitoring interrupts
IWI:          0          0          0          0   IRQ work interrupts
RES:     152031     186607      79037      50925   Rescheduling interrupts
CAL:       1853       2581       1835       2826   Function call interrupts
TLB:        759       1223       1055        813   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:          6          6          6          6   Machine check polls
ERR:          1
MIS:          0

Thanks in advance.

---

### Post by realzippy on 2011-08-24
> **seagull man said:**
> looks like it is scaling from a resolution that doesn't match the screen

So let's check the resolution your graphics card produces.
Run

```
xrandr -q
```

and post the ouput

---

### Post by tjones00 on 2011-08-24
Sounds like a virtual desktop issue to me. And yes xrandr -q is needed.


The virtual desktop is the total area your card can handle. When you attach another display to a card the new display area + the original display area must be within the total area of your virtual desktop (the total imaginary display your video card can handle). This is typically limited by the ram on the card.

---

### Post by seagull man on 2011-08-25
Thanks for responses guys. I did have an issue at some point regarding total desktop size, but now I am only using the one monitor and that issue no longer seems to apply.

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 1920 x 1920
DFP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 597mm x 336mm
   1920x1080      60.0*+   50.0     30.0     25.0  
   1776x1000      60.0 +   50.0     30.0     25.0  
   1680x1050      60.0 +   50.0  
   1400x1050      60.0 +   50.0  
   1280x1024      60.0 +   75.0     50.0  
   1440x900       60.0 +   50.0  
   1280x960       60.0 +   50.0  
   1280x800       60.0 +   50.0  
   1152x864       60.0 +   75.0     50.0  
   1280x768       60.0 +   50.0  
   1280x720       60.0 +   50.0  
   1024x768       60.0 +   75.0     70.1     50.0  
   1152x648       60.0 +   50.0  
   800x600        60.0 +   72.2     75.0     56.2     50.0  
   720x480        60.0 +   50.0  
   640x480        60.0 +   75.0     72.8     50.0  
   1600x1200      60.0  
   720x576        50.0  
DFP2 connected (normal left inverted right x axis y axis)
   1680x1050      59.9 +
   1400x1050      60.0 +
   1440x900       59.9 +
   1280x800       60.0 +   75.0  
   1152x648       60.0 +
   1280x1024      75.0     60.0  
   1280x960       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       74.9     59.9  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     70.0     60.3     56.2  
   720x480        60.0  
   640x480        75.0     72.8     60.0  
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)
CV disconnected (normal left inverted right x axis y axis)

---

### Post by seagull man on 2011-08-26
please help..

---

### Post by realzippy on 2011-08-27
Wish I could,but xrandr clearly shows that you are running
1920x1080 at 60 Hz....
So maybe a catalyst issue.(test other version?)
I am no expert for the proprietary ati driver at all.
Maybe "problem with fglrx/HDMI" would be a better thread title to get the 
catalyst geeks in the boat.

Also read in the forum that sometimes HDMI adapter/cable makes trouble/video corruption.
An short test would be to start the LiveCD and see if the free ati driver
has this problem also,to see if the cable/adapter cause the issue.
Sorry,but good luck!

---

### Post by seagull man on 2011-09-04
OK stupid problem - it was just that I hadn't set my monitor to PC. It was on TV mode.

---

### Post by realzippy on 2011-09-04
So set thread as solved please.. (threadtools)

---

