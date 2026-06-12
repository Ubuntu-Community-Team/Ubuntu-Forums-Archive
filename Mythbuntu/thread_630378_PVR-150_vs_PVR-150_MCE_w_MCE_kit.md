---
title: "PVR-150 vs PVR-150 MCE w/ MCE kit"
date: 2007-12-03
forum: Mythbuntu
---

### Post by Kawayanan on 2007-12-03
I am planning on building a MythTv box and had a question about the possible remotes.  I am looking at the PVR-150 line and wanted to know what people thought the pro's and con's of the two different remote options were.

First, the [PVR-150]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116625")  -  Hauppauge remote that plugs into the PCI card.  Has both sensor and blaster.  Are there limitations here?  Does this for example only recognize the included remote? (wouldn't pass on other unknown IR codes)

Second, the [PVR-150 MCE with MCE kit]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116631").  More expensive.  Has a different remote and a separate USB sensor and blaster (doesn't plug into the tuner card).  Is this a better setup (better remote?...more versatile?...etc.?).

Are the two equally easy (hard?) to set up?  Are there things you can do with one that you can't do with the other?

Lastly, I currently have a Leadtek WinFast TV2000 XP Deluxe I have been using in my computer.  It lacks a hardware encoder, and I was planning on getting the PVR-150 for my new box but might add this card too (for a second tuner).  Unfortunately, I currently cannot get it working with a test Mythbuntu install on my current computer.  If I got this card working and went with a PVR-150 MCE (no remote - cheaper), would I be hobbled by using the Leadtek remote (through the Leadtek card)?

Thanks for the help.

Kawayanan

---

### Post by superm1 on 2007-12-03
> **Kawayanan said:**
> I am planning on building a MythTv box and had a question about the possible remotes.  I am looking at the PVR-150 line and wanted to know what people thought the pro's and con's of the two different remote options were.

First, the [PVR-150]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116625")  -  Hauppauge remote that plugs into the PCI card.  Has both sensor and blaster.  Are there limitations here?  Does this for example only recognize the included remote? (wouldn't pass on other unknown IR codes)

Second, the [PVR-150 MCE with MCE kit]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116631").  More expensive.  Has a different remote and a separate USB sensor and blaster (doesn't plug into the tuner card).  Is this a better setup (better remote?...more versatile?...etc.?).

Are the two equally easy (hard?) to set up?  Are there things you can do with one that you can't do with the other?

Lastly, I currently have a Leadtek WinFast TV2000 XP Deluxe I have been using in my computer.  It lacks a hardware encoder, and I was planning on getting the PVR-150 for my new box but might add this card too (for a second tuner).  Unfortunately, I currently cannot get it working with a test Mythbuntu install on my current computer.  If I got this card working and went with a PVR-150 MCE (no remote - cheaper), would I be hobbled by using the Leadtek remote (through the Leadtek card)?

Thanks for the help.

Kawayanan

Well both kits should work fine.  The one with the integrated remote and blaster is supported by the lirc_i2c driver.  The one with the usb remote is supported by lirc_mceusb2.

If it was my choice, i'd choose the mce kit.  Here's why:
1) Myself and 2 other developers use one of these mceusb2 based remotes (If it doesn't work for us at some point, these are probably one of the first things that would get fixed since its our hardware)
2) Do a quick search for Hauppauge remote stuff in this forum.  You'll see a range of random odd problems people have run into.  The biggest one is that not all the buttons end up mapped as expected.  There is a new version of mythbuntu-lirc-generator in gutsy-backports that should address this, but no guarantees that it is 100%.

---

