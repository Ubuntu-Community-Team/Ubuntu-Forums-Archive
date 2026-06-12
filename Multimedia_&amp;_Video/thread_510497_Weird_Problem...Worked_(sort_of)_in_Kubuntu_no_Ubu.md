---
title: "Weird Problem...Worked (sort of) in Kubuntu no Ubuntu...Dual-head, multi-head"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by myk.dinis on 2007-07-26
Ok, I'm going to throw some logs and settings and stuff up here...can someone please explain to me why my xorg.conf keeps probing my pci bus and coming up with my vid card on the wrong ID...  I can't use my dual head because of this...and Like I said in the topic...it worked in Kubuntu but the xrandr extensions are incompatible with xinerama so it freaked out...it worked but everytime I started up it told me that xrandr couldn't work for some bizarre reason (I later learned xrandr andxinerama are incompatible...) So, I switched to ubuntu and I turned off xrandr but now it xorg doesn't understand that I moved my video card (moved it after I found out that it kept probing the wrong address, thought the card might be loose or bad pci slot or whatever)...lspci shows this:

Begin-----------------------------------------------------------------------------
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)
02:08.0 VGA compatible controller: ATI Technologies Inc Rage 128 RE/SG
02:09.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 64)
02:0a.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
End------------------------------------------------------------------------------

Which puts my ATI vid card at 02:08.0

In my xorg.conf I specified the BusId as "PCI:2:08:0"
But...Xorg.20.log (the most recent xorg log) show's this ---

(--) PCI: (2:10:0) ATI Technologies Inc Rage 128 RE/SG rev 0, Mem @ 0x44000000/26, 0x40000000/14, I/O @ 0x1000/8

If I'm reading it right it says probed PCI and found this device here...
If it's not really probing and finding it then where is it looking for this information?

Blah...

But any help would be greatly appreciated...

Myk

---

### Post by myk.dinis on 2007-07-27
Well, I solved it myself...

If you wan to know what I did you can send me a personal message on ehre and I'll post it...

Pretty much there are certain flags that "some" of the gui's set up for you but don't tell you about...

blech...

tired...time for bed...
no pc for 96 hrs...

going camping...

I don't know if I'll survive...

:)

---

