---
title: "Activate  B43 driver without wired internet connection?"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by aintpaint on 2009-04-16
All,

I've installed Xubuntu 8.10 (Intrepid) on an old K6-2 laptop (HP N3250 pavilion).  This laptop does not have built-in networking, so the installation used a wired ethernet (Realtek 8139) PCMCIA card.  No problem, everything working (a little slow).  I updated the installation and installed B43-fwcutter then rebooted using Broadcom 4306 wireless PCMCIA card.

The card is recognized, but I need to activate the driver.  The problem is: that to activate the driver, the system wants to download and install the driver.  I can't do this, because the wireless isn't activated, thus, no connection.  Chicken and egg scenario.

Is there a (hopefully simple) way to activate the driver without a functioning internet connection?

When 8.10 is installed on a newer laptop with built-in wireless (Broadcom) and wired networking, there's no problem with this.

Must I go the ndiswrapper route?
Does version 9.04 address this?
Is my situation too old/esoteric to warrant consideration?

Maybe I need to reinstall in a different manner?

'sup with dat?

---

### Post by divague on 2009-04-16
Download this packages:

[http://packages.ubuntu.com/intrepid/ndiswrapper-utils-1.9]("http://packages.ubuntu.com/intrepid/ndiswrapper-utils-1.9")
[http://packages.ubuntu.com/intrepid/ndiswrapper-common]("http://packages.ubuntu.com/intrepid/ndiswrapper-common")

then open a terminal and install them:

```
$cd *directory_where_you_saved_the_files*
$sudo dpkg -i *.deb
```

and follow this guide [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") to install the drivers. (Download the drivers for your wireless card model from that guide)

---

### Post by aintpaint on 2009-04-20
divague, 

Thanks for the link.  I followed the instructions to the letter and was able to activate the wireless card, but immediately ran into another problem with the range of the wireless.  I have seen other threads on this new problem, and based on this and several other issues, did something radical:  I installed an old XP Home/SP1 and was more-or-less satisfied with its performance on this platform.

This particular laptop: K6-2/475 MHz, 256 MB, N3250 HP Pavilion, was designated to be a mare foaling monitor using an IP camera.  The need for this was imminent, and the laptop was under-performing and problematic with every Linux distribution I had tried (I lost count ...). With the older XP installation, the performance was acceptable, the wireless/drivers were working (although awkward to setup in ad-hoc mode).  I knew better than to "upgrade" to SP2 or SP3, because the performance would invoke a serious degradation hit.  Even the DVD playback is acceptable using an old copy of WinDVD (newer WinDVD copies suffered from performance issues).

I am very pleased with the Xubuntu 8.10 installation on another faster (HP ze4430us), 6 year-old, laptop and will keep it there.  It just wasn't working good enough on the ancient 10 year-old Pavilion and its PCMCIA wireless card (Broadcom 4306 Rev03).

I had also tried the latest 9.04 Unbuntu RC, but immediately ran into ERROR 15 after the installation, and reboot.  The Slackware installation was a setup nightmare.  The Linux Mint 6 Fluxbox actually worked best, out-of-the-box, but had the identical wireless issues.  However, it was the only distribution that correctly installed DVD playback (but was unwatchable due to its performance).

Based on this experience, I have formed the opinion that, like other operating systems, Linux has grown bigger, less efficient, and less adaptable to older platforms.  I would have liked to install an older Linux kernel/distribution on the old laptop, but intuitively expected that I would have even more problems, getting everything working.

This was an excellent learning experience, having been away from the Linux scene for a number of years.  I hate Windows, and windows applications, with a passion, and my next desktop WILL be a Linux platform (currently a very old 700 MHz Pentium II custom box with an old ATI RAGE TV card).  There's nothing I use a computer for, at home, that requires anything Windows-related.  A quad-core something-or-other, with networked TV tuner, etc..., when I have the time ...

This forum is a treasure trove of information.

Thanks,

Y'all

---

