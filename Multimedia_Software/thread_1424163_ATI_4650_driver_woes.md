---
title: "ATI 4650 driver woes"
date: 2010-03-07
forum: Multimedia Software
---

### Post by mnementh666 on 2010-03-07
I'm at the banging-head-on-the-keyboard stage...
I've installed both x64 and 32-bit versions of Ubuntu/Mint, both KDE and Gnome.  

All varieties work great, until I try to install the driver for the vid card.  Both the driver installed by the Hardware Drivers and the full-on ATI drivers (latest available) cause issues.

The issues result in a completely scrambled screen, and hard lock of the system. I have to physically turn off the unit to reboot.

The vid card works beautifully in XP, so there must be some random driver thing going on, I think.  

I'll have full postings of the X.Org log later today, as I'm at work currently.

And finally, I've had the card working with full acceleration in a previous version (9.04?) of Ubuntu, with no issues, but it took some tweaking in the xorg.conf file to get it to work.  I'm mostly just posting to see if someone else can help me get the right settings (assuming that's the issue)...

Thanks y'all.

---

### Post by linux4life88 on 2010-03-10
Did you download the ATI proprietary drivers from the repositories? I have the same exact graphics card in my laptop and I went to ATI's website recently and downloaded the new 10.2 drivers off of their website and they worked fine.

---

### Post by mnementh666 on 2010-03-25
:redface: Feeling foolish now.  I have discovered that flashing my HIS brand 4850 with an MSI brand 4850 BIOS does weird things...
I had completely forgot that I'd done that.  After flashing back a factory BIOS, all is well.

---

