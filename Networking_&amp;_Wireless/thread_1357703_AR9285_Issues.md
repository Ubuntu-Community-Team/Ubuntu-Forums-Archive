---
title: "AR9285 Issues"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by X5-655 on 2009-12-17
I have a Compaq CQ61-313us laptop, and am having wireless issues with it.  I am booting with the AMD64 9.10 Ubuntu USB live disk, and I can enter my wifi key, and get 4 seconds of surfing, but then the wifi light on the laptop starts flashing blue and amber, and then I loose connection, and can't connect, though it says it's connected..

I am at a loss, as I am a linux user, stuck with Windows 7..  I really want to go back to linux, (as my old laptop was always ubuntu)..

In Windows 7, the wifi is always 100% strong..

But, I'm not so sure my particular AR9285 is wireless N though.  I have an N router, and Windows after an update, says it's N, but it only connects 54Mbps.  Compaq insists my wifi is G only, and not N, which makes me believe this wifi card is custom of some sorts..

Any fix for flakey AR9285 wifi connections?

EDIT:  I should mention, this model laptop is EFI equipped..
EDIT2:  Nvm, 150mbps on windows 7.  So I DO have N..

---

### Post by coffeecat on 2009-12-17
I have an Acer laptop with the Atheros AR928X wireless chipset. The connection was flaky at first in Karmic - very similar to what you are experiencing - until, that is, I installed the packages, linux-backports-modules-karmic-generic and linux-backports-modules-wireless-karmic-generic. These brought in wireless drivers backported from (I guess) the 2.6.32 kernel. So (I guess) there is something wrong with the Atheros drivers in the default 2.6.31 kernel which comes with Karmic.

Trouble is - that's not going to help you unless you do a hard drive install. Also - no guarantee this will work with your AR9285 chipset, but the backported modules seem to have helped users of other Atheros chipsets, so hopefully it might.

Would you consider doing a HD installation and trying this? You'll obviously need to use an ethernet connection to install the modules packages. And you'd be well-advised to keep the ethernet connection until you've done a full update. Those backports packages are metapackages which bring in modules to match whichever kernel you are running: 2.6.31-14 for 2.6.31-14, and so on. Karmic came with the -14 kernel, but we've been through -15 and are now up to -16.

**Edit:** did you get AR9285 from lspci, or is that what Windows7 is telling you? If from W7, can you post the terminal output of:

```
lspci | grep "Wireless"
```Here's mine for comparison:

> 06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

As far as N and G are concerned, my AR928X is N, but my old router is G, so I can't tell you whether you'll get N speeds.

---

### Post by X5-655 on 2009-12-17
Windows 7 doesn't have lspci ;)  Windows 7 says it, and so does Compaq..

I'll try the backported driver.  Can I try that without installing, just to test it first?  Because I have to wipe out my EFI system folder if I install Ubuntu onto the HD, unless Ubuntu supports EFI now on the AMD64 distribution..

---

### Post by coffeecat on 2009-12-18
> **X5-655 said:**
> Windows 7 doesn't have lspci ;)  Windows 7 says it
> **coffeecat said:**
> did you get AR9285 from lspci, **[SIZE=6]or[/SIZE]** is that what Windows7 is telling you? 

:wink: :p

What I was trying to find out was whether you had run lspci from the live CD. I've sometimes found discrepancies in what Windows and what lspci (or lshw) tell me about the hardware. I don't have an encyclopaedic knowledge of Atheros chipsets (shame! :wink:) so I was wondering whether AR9285 and AR928X were different or just synonyms for the same.

> **X5-655 said:**
> I'll try the backported driver. Can I try that without installing, just to test it first? Because I have to wipe out my EFI system folder if I install Ubuntu onto the HD, unless Ubuntu supports EFI now on the AMD64 distribution..

I thought about that. With a HD install you just do a reboot, but that wouldn't work for a live session. What you could try in the live session is to install the packages using a wired connection (they'll get installed to RAM but will be lost when you power down), and then replace the old version of the driver with the new one, with:

```
sudo rmmod ath9k
sudo modprobe ath9k
```You probably only need to do the rmmod if you've already connected wirelessly. If you haven't, you'll simply get an "ERROR: Module ath9k does not exist in /proc/modules" but it won't do any harm.

As far as EFI is concerned, sorry, the only experience I have of EFI is booting up my Mac Mini, and I've only ever run Linux in VirtualBox on that. According to [Wikipedia]("http://en.wikipedia.org/wiki/Extensible_Firmware_Interface#Operating_systems"):
> Linux has been able to use EFI at boot time since early 2000, using the elilo EFI boot loader or, more recently, EFI versions of GRUB... so it looks as though you ought to be able to with 9.10, seeing as it comes with grub 2, which is meant to be the best thing since sliced bread, or at least legacy grub - according to the grub devs. :) But how you do it, I don't know.

Good luck!

**Edit:** googling various combinations of 'Windows 7 Karmic EFI' doesn't bring much up of use (perhaps my google-fu is depleted this morning) except this:

[http://voices.canonical.com/tag/efi/](http://voices.canonical.com/tag/efi/)

Do tell us how you get on, and **very** best of luck! :-s

---

### Post by X5-655 on 2009-12-27
i never got around to it, but win7 has been having connection problems too, with the slightest interfearance, despite being full bars..  I think i may just replace the mini pci-e card with something like broadcom.

---

### Post by coffeecat on 2009-12-27
> **X5-655 said:**
> I think i may just replace the mini pci-e card with something like broadcom.

Broadcom??!!! :shock: You can get Intel mini pci-e cards. Are you sure you don't want to get Intel? They *should* just work out of the box. Whatever - that would be my choice. The Intel 5100 wireless chipset in my other laptop works just fine in Ubuntu.

---

### Post by X5-655 on 2009-12-27
I'll try intel if it'll work.  has to be n though..

---

### Post by griffinjones on 2009-12-28
First off, you need to get the new driver package. I have basically the same wireless card and it was dropping the connection every 5-10 seconds. Basically we want that little blue wireless light on the front of the computer to constantly have a solid blue output (without editing the parameters of the light itself, catch my drift?)

After you decompile and make install etc the driver tarball, restart that **** and yeah.

---

### Post by X5-655 on 2009-12-28
I just wish there was a way to do this and test it without erasing Windows, confirm it works, then erase Windows and reinstall Ubuntu to take the entire HD (minus the HP diagnostic/EFI system partition).

---

### Post by X5-655 on 2010-01-20
I tried to install the backports..  Got errors of it not finding the second package..

sudo apt-get install linux-backports-modules-wireless-karmic-generic


that's the one that it can't find..  i tried sudo apt-get update still no dice..

---

### Post by X5-655 on 2010-01-21
I give up.  I tried and tried the backports but it just won't install.

---

