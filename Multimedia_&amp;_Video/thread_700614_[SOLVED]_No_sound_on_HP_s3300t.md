---
title: "[SOLVED] No sound on HP s3300t"
date: 2008-02-18
forum: Multimedia &amp; Video
---

### Post by bkline on 2008-02-18
I just tried installing Gutsy on a new HP Slimline desktop (model s3300t), and Ubuntu is unable to figure out what to do with the sound chip.  Here's what lspci says:

```
00:09.0 Audio device: nVidia Corporation Unknown device 07fc (rev a1)
        Subsystem: Hewlett-Packard Company Unknown device 2a65
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (500ns min, 1250ns max)
        Interrupt: pin A routed to IRQ 7
        Region 0: Memory at efff4000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
                Masking: 00000000  Pending: 00000000

```

How do I go about figuring out which module needs to be loaded to get the sound working?

---

### Post by Yellow Pasque on 2008-02-19
It's probably an nvidia high-def-intel-compliant chip (hda-intel). See if running **sudo update-pciids** before running lspci gives you more current info.

If it is a "High-Def" chip, try this script to get and configure the latest ALSA driver: [http://ubuntuforums.org/showpost.php?p=4360698&postcount=6](http://ubuntuforums.org/showpost.php?p=4360698&postcount=6)

You can also try OSS4 if that doesn't work (link in sig)

---

### Post by bkline on 2008-02-19
> **Temüjin said:**
> It's probably an nvidia high-def-intel-compliant chip (hda-intel). See if running **sudo update-pciids** before running lspci gives you more current info.

If it is a "High-Def" chip, try this script to get and configure the latest ALSA driver: [http://ubuntuforums.org/showpost.php?p=4360698&postcount=6](http://ubuntuforums.org/showpost.php?p=4360698&postcount=6)

You can also try OSS4 if that doesn't work (link in sig)

Thanks for the suggestion.  Unfortunately, the output from lspci is unchanged after running update-pciids.  Any other things I can do?  Is a USB sound "card" my only option (don't think there are any available PCI slots in this box)?

---

### Post by Yellow Pasque on 2008-02-19
The HP site says your codec is a Realtek ALC888S. Try the script I linked to to get the latest version of ALSA. You can also try my OSS4 guide before giving up and spending money on a new soundcard.

PCIe-x1 cards are starting to come out. Your HP has a free PCIe-x1 slot and a free PCIe-x16 slot. Unfortunately, the X-fi only has beta support on Linux right now.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16829102017](http://www.newegg.com/Product/Product.aspx?Item=N82E16829102017)

---

### Post by bkline on 2008-02-19
> **Temüjin said:**
> The HP site says your codec is a Realtek ALC888S. Try the script I linked to to get the latest version of ALSA.

OK, thanks, I'll give it a try.  I've been scolded before for installing packages directly from compiled source code, which I was told causes problems for the package management system.  Is such "advice" not applicable here?

Bob

---

### Post by Yellow Pasque on 2008-02-19
*Shrug
I've completely replaced ALSA with OSS4, I've shoehorned my own custom 2.6.24 kernel in, I've built my own video driver from a git repository and all of these things made my Ubuntu system much better (et al).

If building new ALSA packages doesn't work out, you can 'make uninstall' the packages and reinstall the Ubuntu-supplied versions in Synaptic for good measure.

I wouldn't recommend building from source if a suitable version is available in the repo, but in this case...

---

### Post by bkline on 2008-02-19
Hallelujah!  It worked!  Thanks a million for all your patient help.

Bob

---

### Post by bkline on 2008-02-20
> **Temüjin said:**
> The HP site says your codec is a Realtek ALC888S

I'd love to know how you found that information.  I spent a long time combing through all the specification information I could find for the s3300t on the HP site and never came across it.

Thanks again for your very knowledgeable assistance!

Bob

---

### Post by Yellow Pasque on 2008-02-20
The support and drivers page for your product
[http://h10025.www1.hp.com/ewfrf/wc/product?product=3659715&lc=en&cc=us&dlc=en&submit.y=1&submit.x=7&lang=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/product?product=3659715&lc=en&cc=us&dlc=en&submit.y=1&submit.x=7&lang=en&cc=us)
Under the Product Information category, Motherboard Specifications

HP is one of the better manufacturers in terms of giving you product info. Enjoy your system.

> Thanks again for your very knowledgeable assistance!
You're welcome.

---

### Post by bkline on 2008-02-20
> **Temüjin said:**
> The support and drivers page for your product
[http://h10025.www1.hp.com/ewfrf/wc/product?product=3659715&lc=en&cc=us&dlc=en&submit.y=1&submit.x=7&lang=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/product?product=3659715&lc=en&cc=us&dlc=en&submit.y=1&submit.x=7&lang=en&cc=us)
Under the Product Information category, Motherboard Specifications

Wow!  You're a gold mine of information!

---

