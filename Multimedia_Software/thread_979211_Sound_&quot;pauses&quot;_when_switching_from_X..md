---
title: "Sound &quot;pauses&quot; when switching from X."
date: 2008-11-11
forum: Multimedia Software
---

### Post by spike1 on 2008-11-11
Hardy heron, up to date with current updates.

Has anyone else encountered this niggle?
Sometimes I like to listen to an mp3 or bbc radio.
Trouble is, if I switch from X to a virtual console, the sound "pauses". This seems to happen all the time except in mplayer if I specifically tell it to use alsa with the -ao switch.

I've noticed this with games too, the sound doesn't just pause in this case, the whole game appears to freeze or "go to sleep" until I return to X.

There HAS to be a way out of this, it never used to happen on my old SuSE box.

Is there an app to replace (sound daemon perhaps?) or an environment variable I can set to alter this behaviour?

Thanks.

I'll tag the lspci output to the end, just in case it's relevant.

[FONT="Courier New"]00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
02:02.0 Multimedia video controller: Brooktree Corporation Bt849A Video capture (rev 12)
02:03.0 Communication controller: NetMos Technology PCI 9835 Multi-I/O Controller (rev 01)[/FONT]

---

