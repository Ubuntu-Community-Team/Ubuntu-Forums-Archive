---
title: "xorg.conf BusID - onboard video with ATI Radeon 7000"
date: 2008-01-09
forum: Multimedia &amp; Video
---

### Post by transporter_ii on 2008-01-09
I know I'm not the only one to ever run into this, but here is the deal.

I have a 6.06 LTS system with a working Radeon 7000. Works perfect as far as I'm concerned.

Got a new computer with a VIA card in it, and VIA Chrome 9 support SUCKS. I thought I would just order a card that I know works, because after all, I have a WORKING one in the next room.

Low and behold, 6 - 7 hours of editing xorg.conf, and the heck a Radeon 7000 works with 7.10 (which I had to have because of my SATA hard drive controller drivers aren't in 6.06 LTS).

But then I discovered something:

01:00.0 VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)
04:04.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

The board I have has onboard VGA with no way that I can find to disable it in BIOS, but I can change the video device from onboard to PCI, which I did. And I can hook my monitor to my PCI ATI card and actually use it (to some degree...see below).

But every attempt at using the any ATI driver (open source or whatever), the system hangs at running local boot scripts.

I don't know what is going on, but I think some things are seeing the VIA video card instead of the ATI video card. I edited xorg.conf to have an "ati" driver and a busID of:

  BusID		"PCI:4:4:0"

This setting works and the system boots, but if I go to System, Screen & Graphics, it shows to have a generic VESA driver loaded instead of the ATI driver...and I have no 3D.

Is the above BusID correct for the "04:04.0 VGA compatible controller."

Is there anything else I need to change to make sure Ubuntu only sees the ATI card besides the BusID?

Thanks,

Jay

---

### Post by transporter_ii on 2008-01-09
> I don't know what is going on, but I think some things are seeing the VIA video card instead of the ATI video card. I edited xorg.conf to have an "ati" driver and a busID of:

And the reason I say that, is because I downloaded Envy and tried to have it auto detect my ATI card, but it fails to see it. I think it is seeing the VIA card, which would explain exactly why a program made specifically to find ATI cards, can't.

Jay

---

### Post by Thanoulis on 2008-01-09
I believe that you do not need the "ati" driver. After all that's why the "vesa" driver is loaded.Make a manual/Envy compile of the driver and see how it goes...

---

### Post by transporter_ii on 2008-01-09
Ok, in my system with a working ATI Radeon 7000, the driver is "ati," and I have 3D in it. Of course the generic VESA driver works fine, I'm typing this message on it right now and my monitor is plugged into the ATI 7000 card as I type this message.

The one little problem with the set up is, I ordered the card because I thought 3D would work with it because I actually have a 6.06 LTS system with the **SAM**E card  that **WORKS WITH 3D!**

Now correct me if I'm wrong, but shouldn't an ATI card actually need some type of ATI driver to get 3D support? Because, I can tell you from painful experience, it doesn't have it with the Generic VESA driver. 

Jay

---

