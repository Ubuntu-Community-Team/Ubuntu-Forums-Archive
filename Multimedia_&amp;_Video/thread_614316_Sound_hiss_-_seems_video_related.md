---
title: "Sound hiss - seems video related"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by bixbyr on 2007-11-15
Hi,

I'm having a problem somewhat similar to the one detailed in [http://ubuntuforums.org/showthread.php?t=379554:](http://ubuntuforums.org/showthread.php?t=379554:) I'm getting a nasty hiss along with normal sound on my system, and it seems related to movement on screen. Dragging a window produces an audible hiss and something which redraws almost constantly, such as Half Life 2 under wine, is almost unbearable. I tried the solution suggested in that post without any luck, though that might be related to the fact that I don't have the same sound card.

I'm running Ubuntu 7.10, the audio comes from an integrated controller on a Shuttle motherboard. Here is what lshw produces:
  *-multimedia            
       description: Multimedia audio controller
       product: VT8233/A/8235/8237 AC97 Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 11.5
       bus info: pci@0000:00:11.5
       version: 60
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
The system is using ALSA, the other only device listed is Realtek ALC655 rev 0 (OSS Mixer). The problem didn't exist before I recently upgraded my graphics card to a Geforce 8600. I tried to check for an IRQ conflict but couldn't find anything:
cat /proc/interrupts
           CPU0       CPU1       
  0:        153          0   IO-APIC-edge      timer
  1:         10       2698   IO-APIC-edge      i8042
  6:          0          5   IO-APIC-edge      floppy
  7:          0          0   IO-APIC-edge      parport0
  8:          0          3   IO-APIC-edge      rtc
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          0          4   IO-APIC-edge      i8042
 14:         57      12504   IO-APIC-edge      ide0
 18:        211      45998   IO-APIC-fasteoi   sata_via
 19:          0          2   IO-APIC-fasteoi   ohci1394
 20:        108      17665   IO-APIC-fasteoi   uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4, ehci_hcd:usb5
 21:        189      45877   IO-APIC-fasteoi   eth0
 22:        191      98990   IO-APIC-fasteoi   nvidia
 23:        269      51652   IO-APIC-fasteoi   VIA8237
NMI:          0          0 
LOC:     299145     296203 
ERR:          0
MIS:          0

As I said before, the hiss seems related to video movement / updates to the screen. I've tried adjusting various volume controls without noticeably affecting the problem. If anyone has any ideas I'd be really grateful. (I'd say I'm generally an intermediate level user, though I know comparatively little about how audio works).

Thanks a lot
 - Ryan

---

