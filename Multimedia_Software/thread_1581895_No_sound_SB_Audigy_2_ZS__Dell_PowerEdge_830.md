---
title: "No sound: SB Audigy 2 ZS / Dell PowerEdge 830"
date: 2010-09-25
forum: Multimedia Software
---

### Post by EchoBeach on 2010-09-25
Hi
I have a Dell PowerEdge 830 Dual Pentium on which I installed 10.04.
I have installed (slotted in) an SB Audigy 2 ZS card, from another PC, but it doesn't appear to be working.
The donor PC suffered a graphics card failure that killed the motherboard.  
I can't tell whether the sound card is actually faulty.  Did the sound card ought to work without any 'fiddling'?
Regards
Echo

---

### Post by cchhrriiss121212 on 2010-09-25
Try out aplay -l in a terminal window, if that does not yield results then try lspci -v.

---

### Post by lkjoel on 2010-09-25
> **EchoBeach said:**
> Hi
I have a Dell PowerEdge 830 Dual Pentium on which I installed 10.04.
I have installed (slotted in) an SB Audigy 2 ZS card, from another PC, but it doesn't appear to be working.
The donor PC suffered a graphics card failure that killed the motherboard.  
I can't tell whether the sound card is actually faulty.  Did the sound card ought to work without any 'fiddling'?
Regards
Echo
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by EchoBeach on 2010-09-27
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [Unknown]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy [Audigy 1 [Unknown]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [Unknown]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by EchoBeach on 2010-09-27
lspci
00:00.0 Host bridge: Intel Corporation E7230/3000/3010 Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation E7230/3000/3010 PCI Express Root Port
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 PCI bridge: Intel Corporation 6702PXH PCI Express-to-PCI Bridge A (rev 09)
03:01.0 SCSI storage controller: Adaptec AHA-3960D / AIC-7899A U160/m (rev 01)
03:01.1 SCSI storage controller: Adaptec AHA-3960D / AIC-7899A U160/m (rev 01)
03:02.0 Ethernet controller: Intel Corporation 82546EB Gigabit Ethernet Controller (Copper) (rev 01)
03:02.1 Ethernet controller: Intel Corporation 82546EB Gigabit Ethernet Controller (Copper) (rev 01)
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 11)
06:00.0 Multimedia audio controller: Creative Labs SB Audigy (rev 05)
06:05.0 VGA compatible controller: XGI Technology Inc. (eXtreme Graphics Innovation) Z7/Z9 (XG20 core)

Thanks Chris.
Any thoughts?
Echo

---

### Post by EchoBeach on 2010-09-27
lkjoel
Thanks for the links.
I'm not sure what route to take.
Echo

---

### Post by cchhrriiss121212 on 2010-09-27
It seems to be recognised, so you may just need to set volume levels using alsamixer, they might be muted.

lkjoel is recommending you use OSS4 instead of ALSA. I would say to stick with ALSA, until you are sure it won't function.

---

### Post by Elfy on 2010-09-27
I'd certainly check to see if there's an analogue/digital switch needs setting - mine used to default to digital. Use alsamixer as cchhrriiss121212 suggests

---

### Post by EchoBeach on 2010-09-27
Cchhrriiss121212
Alsamixer seemed to say everything was 'average'.
'beep', after I'd installed it, gave me nothing.
Echo

---

