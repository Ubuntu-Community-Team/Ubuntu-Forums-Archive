---
title: "Problem Getting Onboard sound to work"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by abyssius on 2008-01-23
When I installed Ubuntu 7.10 from the live CD, both my wireless card and the onboard sound was disabled. I was eventually able to get wireless networking to function via NDISwrapper. However, all my attempts at getting the onboard sound to work have failed. I followed the very clear instructions in [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting). 

First, I issued the command:
aplay -l
**** List of PLAYBACK Hardware Devices ****

Next, I used the command, lspci -v, which listed my sound card:

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: ASRock Incorporation Unknown device 7012
        Flags: medium devsel, IRQ 20
        I/O ports at e800 [size=256]
        I/O ports at ec00 [size=128]
        Capabilities: <access denied>

Noting that Ubuntu recognized that a audio controller existed, I checked to see if the ALSA driver for my sound card existed. The closest match I found:

driver: snd-intel8x0
description:  Intel 82801AA,82901AB,i810,i820,i830,i840,i845,MX440; SiS 7012; Ali 5455

Next, following the advice on the ALSA site, I entered the command:

sudo modinfo soundcore
filename:       /lib/modules/2.6.22-14-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:        
vermagic:       2.6.22-14-generic SMP mod_unload 586 

Returning to the troubleshooting instructions, I entered:
sudo modprobe snd snd-intel8X0

No error messages occurred.

Next, I entered:

sudo nano /etc/modules

I added: snd-intel8x0, and saved the file.

I then rebooted the system. Upon reboot, the disabled icon for sound was gone! I was able to access the mixer. Everything looked alright. However, there's no sound. I tried playing an audio CD and got the following error message.

Error playing CD.

Reason: Internal GStreamer error: state change failed.  Please file a bug at [http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer](http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer).

I'm not sure where to go from here. Any advice?

Found a recommended alternative driver on ALSA site: snd-card-intel8x0

Tried that. Same results.

Some more info:
 cat /proc/interrupts
           CPU0       
  0:        142   IO-APIC-edge      timer
  1:       2188   IO-APIC-edge      i8042
  5:          0   IO-APIC-edge      MPU401 UART
  6:          5   IO-APIC-edge      floppy
  8:          3   IO-APIC-edge      rtc
  9:          0   IO-APIC-fasteoi   acpi
 12:     159973   IO-APIC-edge      i8042
 14:      12031   IO-APIC-edge      libata
 15:      13301   IO-APIC-edge      libata
 16:          8   IO-APIC-fasteoi   ohci_hcd:usb1
 17:          0   IO-APIC-fasteoi   ohci_hcd:usb2
 18:          1   IO-APIC-fasteoi   ohci_hcd:usb3
 19:     152264   IO-APIC-fasteoi   ehci_hcd:usb4
 20:          0   IO-APIC-fasteoi   SiS SI7012
NMI:          0 
LOC:     515601 
ERR:          0
MIS:          0

cat /proc/asound/cards
 0 [SI7012         ]: ICH - SiS SI7012
                      SiS SI7012 with unknown codec at irq 20
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x300, irq 5

Is IRQ 20 and unknown codec the issue?

---

### Post by Metaljaz on 2008-01-24
Try the below link to install some extras you may need. You will see a link that says “ubuntu-restricted-extras” click on it and follow instructions:

[http://ubuntu-tutorials.com/2007/08/17/ubuntu-restricted-extras-all-that-extra-stuff-all-in-one-place/](http://ubuntu-tutorials.com/2007/08/17/ubuntu-restricted-extras-all-that-extra-stuff-all-in-one-place/)

Or open the Terminal, and execute the following command:

sudo apt-get install ubuntu-restricted-extras

Maybe install something that is missing. Let us know.

---

### Post by abyssius on 2008-01-26
Thanks Metaljaz

As far as I can tell, it seems that the addition of gstreamer0.10-plugins-ugly  seems to have fixed my problem.

---

