---
title: "No sound on Left  earphone/ speaker."
date: 2008-09-04
forum: Multimedia Software
---

### Post by EternalBuntu on 2008-09-04
My problem I was having is that I was only getting sound from the right headphone or speaker. So I went to synaptic  package manager and marked alsa for removal and I removed it. I then restarted my computer and now I have full functioning sound from both speakers/ headphones.Now my question to anyone that can help is that do I have something to worry about because I removed alsa??? Sound works perfectly, so is alsa really gone or did I come up with a freak fix?? Can someone help Im totally new to Ubuntu and but like it alot.

---

### Post by Crafty Kisses on 2008-09-05
> **EternalBuntu said:**
> My problem I was having is that I was only getting sound from the right headphone or speaker. So I went to synaptic  package manager and marked alsa for removal and I removed it. I then restarted my computer and now I have full functioning sound from both speakers/ headphones.Now my question to anyone that can help is that do I have something to worry about because I removed alsa??? Sound works perfectly, so is alsa really gone or did I come up with a freak fix?? Can someone help Im totally new to Ubuntu and but like it alot.

Post the results of this command: ```
lspci
```

---

### Post by EternalBuntu on 2008-09-05
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:02.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)

---

### Post by EternalBuntu on 2008-09-05
Oh man now I restarted and came up with no sound. So I rebooted again and now Im back to my original problem which is sound only coming from the right side. I triple checked to make sure it wasnt the sound card and it works perfectly in windows. Im stuck bah............

---

### Post by EternalBuntu on 2008-09-05
bump

---

### Post by EternalBuntu on 2008-09-05
sound only coming from the right side still havent figured it out.

---

### Post by tspan on 2008-09-06
Perhaps left channel somehow got muted. Did you check left channels with gnome-volume-control?

If you did not, check for all non-capture mixer devices with (File -> Change Device). Prior to that, check that important tracks are visible in mixer window with (Edit -> Preferences).

---

### Post by EternalBuntu on 2008-09-06
> **tspan said:**
> Perhaps left channel somehow got muted. Did you check left channels with gnome-volume-control?

If you did not, check for all non-capture mixer devices with (File -> Change Device). Prior to that, check that important tracks are visible in mixer window with (Edit -> Preferences).

Double checked everything you said and still no luck, sound only coming from right side of speaker.  The sound chip is a Via VT1723 Ice Ensemble with 7.1. I will keep trying different things.

This is sucks for me. :(

---

### Post by erikthedrink on 2009-09-08
When you click on the speaker icon, choose "Choose Controls" and see if there is a separate volume control for the right speaker.  If not, use a hardware cheat and pull the headphone jack slightly out to hear a mono signal out of both speakers.:confused:

---

### Post by madnux on 2010-11-05
Same here:
- lspci

05:01.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)

Ubuntu 10.10, only right channel works, all the settings are fine. Triple, Quadruple Check.

:S

---

### Post by marshcast on 2011-03-12
I have same problem here, but using Intel ac97 82801ER...

it would appear the sound is being mixed to mono and sent only to 1 speaker - this bit tells me that it's not a channel vol issue too.

this the same for others (the mixed channel thing)?

---

