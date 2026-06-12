---
title: "Sound dropouts/glitches when video is busy"
date: 2010-12-16
forum: Multimedia Software
---

### Post by adoudoux on 2010-12-16
Hi,

I am struggling on this for several days now, so I hope someone can help me!

I am experiencing problems with sound in Maverick on my Dell Inspiron i6400. When the video gets busy while playing sound, the sound gets highly degraded (dropouts, glitches, clicks and cracklings). For example, it happens when an advert animation is playing on a webpage, or when scrolling a document/a webpage. It especially happens when scrolling a document in evince. This is a frustrating issue since I basically cannot work while playing music! My sound chipset is a Intel HDA ICH7.

An important point is that it only happens when I use a "large" screen resolution (eg 1920x1080), and not when the resolution equals or is below 1280x800. Therefore I think this is related to the video side. The two CPU's cores (Intel T2050@1.60GHz) never reach 100% load when the problem arises. The memory is not full either. I use Compiz and various desktop effects, but the problem still remains without it. My video card is an ATI Mobility Radeon X1300 with 256 Mb of RAM (using the default free driver shipped with Ubuntu). Also, the video is fluid and flawless so I do not understand where the problem comes from. This might be related to a priority/ordering issue, I do not know.

The most relevant bug report I found is the following one:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/479375](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/479375)

but I am not sure my problem is a bug, it might just be a configuration issue. After all, I am not using a very fresh computer!

I can provide any useful further information.

Thanks in advance for your help!

---

### Post by adoudoux on 2011-01-11
OK, I managed to fix this VERY annoying issue!

Basically, I disabled the Kernel Mode Setting (KMS) on the radeon driver by adding a file named radeon-kms.conf in /etc/modprobe.conf/ containing the following single line:

[FONT=Courier New]options radeon modeset=0[/FONT]

As a result, my /proc/interrupts changed from:

[FONT=Courier New]           CPU0       CPU1       
  0:      25490          0   IO-APIC-edge      timer
  1:          9          1   IO-APIC-edge      i8042
  8:          1          0   IO-APIC-edge      rtc0
  9:          2          0   IO-APIC-fasteoi   acpi
 12:        135          0   IO-APIC-edge      i8042
 14:       8622          0   IO-APIC-edge      ata_piix
 15:        580          0   IO-APIC-edge      ata_piix
 17:         57        690   IO-APIC-fasteoi   eth0
 18:          0          0   IO-APIC-fasteoi   mmc0, r852
 19:          1          0   IO-APIC-fasteoi   firewire_ohci
 20:          2          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
 22:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 23:        178       2349   IO-APIC-fasteoi   uhci_hcd:usb5
 43:       5443          0   PCI-MSI-edge      radeon
 44:        146        221   PCI-MSI-edge      hda_intel
 45:          0          0   PCI-MSI-edge      iwl3945
NMI:          0          0   Non-maskable interrupts
LOC:       6457      18086   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:      16902      16910   Rescheduling interrupts
CAL:         53         52   Function call interrupts
TLB:        773        385   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          1          1   Machine check polls
ERR:          1
MIS:          0

[/FONT]to:

[FONT=Courier New]           CPU0       CPU1       
  0:     245102          0   IO-APIC-edge      timer
  1:          9          1   IO-APIC-edge      i8042
  8:          1          0   IO-APIC-edge      rtc0
  9:          2          0   IO-APIC-fasteoi   acpi
 12:        135          0   IO-APIC-edge      i8042
 14:      16566          0   IO-APIC-edge      ata_piix
 15:      13159          0   IO-APIC-edge      ata_piix
 16:      24026          0   IO-APIC-fasteoi   radeon@pci:0000:01:00.0
 17:         60     174938   IO-APIC-fasteoi   eth0
 18:          0          0   IO-APIC-fasteoi   mmc0, r852
 19:          2          0   IO-APIC-fasteoi   firewire_ohci
 20:          2          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
 22:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 23:        171      20506   IO-APIC-fasteoi   uhci_hcd:usb5
 43:        147       1061   PCI-MSI-edge      hda_intel
 44:          0          0   PCI-MSI-edge      iwl3945
NMI:          0          0   Non-maskable interrupts
LOC:      63454     186406   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:     368385     300095   Rescheduling interrupts
CAL:         48         56   Function call interrupts
TLB:      41225      69595   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          4          4   Machine check polls
ERR:          1
MIS:          0[/FONT]

We can see that as a consequence the radeon is not using MSI anymore. That might be the reason why it is working now, I don't know...

---

