---
title: "Are there binary drivers for my chipset?"
date: 2006-08-02
forum: Multimedia &amp; Video
---

### Post by Rinnan on 2006-08-02
Not sure if this should go here, or in the "beginners" section.  I'm not a beginner, but this is a beginner question.

I know that ATI and nVidia both have highly accellerated drivers for their chipsets, which they wrote themselves and which are faster in general than their open source alternatives.  

I just bought a new laptop (an Acer Aspire 5601AWLMi).  I don't know the proper name for my chipset, but these two lines from lspci seem relevant:

```
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
```

Furthermore, the relevant lines in my xorg.conf read:

```
Section "Device"
        Identifier      "Intel Corporation Mobile Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection
```

So it seems that the Ubuntu Dapper installer has already set all of this up for me.  3D works and appears fast, but the whole computer is fast, how can I be sure the 3D is truly accellerated?  Also, are binary drivers available for it, just in case I run into a game or something that needs it?  (it's fine as it is for screensavers and simple games).

And what exactly is the common name for this chipset?  I know people don't go around calling it the "Intel Corporation Mobile Integrated Graphics Controller" :p

---

### Post by az on 2006-08-02
Proprietary (binary) drivers are a bad thing.  They are not free-libre software.  They cause your system to crash.  They prevent you from debugging the kernel.

Happily, the i810 chipset is a fully open one, with 100 percent functional hardware acceleration that is GPLed code.  You could not get better performance from a closed-source driver!

It is the most popular video chipset (by number).  No wonder!

---

### Post by soul_rebel on 2006-08-02
there are no binary drivers available for your graphic card (not "chipset"!). You are ok.

Also binary drivers are a bad thing for many reason (closed source, less stable, problems with acpi, bigger memory requirements, etc). Be glad that your laptom works with Free drivers only.

---

### Post by Rinnan on 2006-08-02
I agree that closed-source drivers are a bad thing, and am glad that the driver that I have is both 100% and open-source, that is ideal.  If there had been a closed-source driver, I would have installed it just to see the best my new hardware can do, then reinstalled the open source one (I keep the windows partition on this laptop only for my wife and never use it myself -- it's worth noting that it has had problem after problem including blue-screening only days after the computer was bought (don't try to turn the wireless off and on while in Windows!) -- but under Ubuntu it's rock-solid and VERY fast -- but with serious problems.  Can't wake from sleep, no internal sound are the most serious two)

At least one problem is solved -- my 3d is already at max.  Great.  Now to attack sound and sleep... which seem harder.

By the way, (and I realize that this is experimental and have no intention of keeping it on my machine permenently until it's done... but...)  Does xgl and compiz work with this chipset?  Can I have wobbly windows?  :p

---

