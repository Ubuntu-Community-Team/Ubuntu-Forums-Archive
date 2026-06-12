---
title: "ATI Surroundview 3+ monitor support (780G IGP &amp; 3450 HD)"
date: 2008-08-07
forum: Multimedia Software
---

### Post by tgui on 2008-08-07
This evening I picked up a ATI 3450 HD with the hopes of putting a third LCD screen to work using the ATI surroundview BIOS option using my integrated 780G graphics as a discrete card paired up with said purchased card.

First, my relevant system info.

- Gigabyte GA-MA78GM-SH2 motherboard with onboard ATI 3200 HD graphics.
- Visiontek 3450 HD graphics card.

My steps to failure.

1) Installed new graphics card, enabled BIOS surroundview, reinstalled Ubuntu, installed ATI Catalyst drivers. I got a usable screen but amdcccle SEGFAULTs therefore no multi screen config.

2) Turned surroundview OFF in the bios, played it safe and reinstalled Ubuntu and ATI Catalyst. Much dual screen fun was had.

3) Rebooted and turned surroundview ON in BIOS. Xorg failed to load fglrx driver. I think its because it was being confused by the new PCI graphics card (IGP) and associated address.

In short, has anyone had any luck getting a 780G integrated graphics motherboard to work with a discrete graphics card (ala 3450 HD) in "Surroundview" mode with more than 2 monitors? Without amdcccle SEGFAULTing?

Thanks!
-Eric-

---

### Post by markbuntu on 2008-08-08
I don't know about using surroundview but have you looked in

aticonfig --help

for the proper command options for setting up two cards?
If you have the ati 8.7 driver, there is a set of dual card options there.

---

### Post by tgui on 2008-08-09
> **markbuntu said:**
> I don't know about using surroundview but have you looked in

aticonfig --help

for the proper command options for setting up two cards?
If you have the ati 8.7 driver, there is a set of dual card options there.

I have  been playing with the aticonfig utility, it seems promising. Though, when I configure my second video card the net result is no working Xorg.

It is a nice utility though and I'll post more as I dig further.

Any personal experience with multiple ATI video cards?

---

### Post by markbuntu on 2008-08-10
Not personally but I saw a thread around here somewhere that some guy has 4 HD3650 cards working. He has his xorg.conf file posted and a bunch of pictures. 
It was something like

How many dual video cards can I have in Ubuntu?

or something like that.

---

### Post by tgui on 2008-08-19
Upon further investigation it seems that the drive gui amdcce (sp?) just gets confused. When surroundview is turned on in the BIOS lspci detects two distinct video cards which is to be expected. When actually going through the paces of setting up Xorg for multiple cards, the driver throws a fit. I don't have the error with me now, but it was something along the lines of card type bios not detected.

aticonfig command line is the only way to configure things, short of hand coding up an xorg.conf.

This just leads me to believe that the driver from ATI doesn't officially support multiple cards, that or the way the on board video is presented as a discrete video card is messed up. I feel that the driver is just stepping on its own toes trying to manage multiple instances of its various parts when supporting a second ATI card.

I'll post the real error tonight.

Thoughts?

---

### Post by markbuntu on 2008-08-19
Well I saw at phoronix that ati has demonstrated this. Maybe you need to wait for another driver update, they are pretty regular, 8.8 should be out soon. Have you tried it with surroundview turned off?

---

### Post by tgui on 2008-08-20
```
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Radeon HD 3200 Graphics" (Chipset = 0x9610)
(--) fglrx(0): (PciSubVendor = 0x1458, PciSubDevice = 0xd000)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xfdae0000
(--) fglrx(0): I/O port at 0x0000ee00
(==) fglrx(0): ROM-BIOS at 0x000c0000
(EE) fglrx(0): Invalid video BIOS signature!
(EE) fglrx(0): GetBIOSParameter failed
(EE) fglrx(0): PreInitConfig failed

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x6a) [0x48402a]
1: /lib/libc.so.6 [0x7f6bcd8e5100]
2: /usr/lib/xorg/modules/drivers//fglrx_drv.so(amdPcsDeleteKey+0x44) [0x7f6bcbc75824]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so(amdPcsFree+0x1b) [0x7f6bcbc749eb]
4: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPreInit+0x24f) [0x7f6bcbc5257f]
5: /usr/bin/X(InitOutput+0xa20) [0x4697c0]
6: /usr/bin/X(main+0x29f) [0x4369bf]
7: /lib/libc.so.6(__libc_start_main+0xf4) [0x7f6bcd8d11c4]
8: /usr/bin/X(FontFileCompleteXLFD+0x279) [0x435ed9]

Fatal server error:
Caught signal 11.  Server aborting
```

Here is the xorg.log error after using aticonfig to setup BOTH video cards.

---

### Post by tgui on 2008-08-20
> **markbuntu said:**
> Well I saw at phoronix that ati has demonstrated this. Maybe you need to wait for another driver update, they are pretty regular, 8.8 should be out soon. Have you tried it with surroundview turned off?

ATI has demonstrated a working Linux surround view? Or, demonstrated this error?

Oh, I wait for every release, LOL.... I can always get the PCIE 3450 working regardless of the surround view option. If the surround view is on though, I can only use aticonfig to only get xorg.conf setup, not the GUI.

Its just a pain in the butt.

I'm not trying to beat a dead horse, just document. I'm sure there are others wanting an easy way to utilize 3+ monitors with a similar setup.

---

### Post by markbuntu on 2008-08-20
ATI demonstrated a working system with an onboard card and a plugin, both ati of course. I don't know if they were using surround view. Some day, I would like to be able to turn on my onboard video and use it with my HD3650 for another monitor but I only have 2 monitors right now so I don't feel any pressing need to pursue the problem. The latest news is here, the 8.8 driver is out today:

[http://www.phoronix.com/scan.php?page=home](http://www.phoronix.com/scan.php?page=home)

---

### Post by zdea on 2008-10-11
I have nearly the same setup as you (780 + 3450) just different brands and I'm definately waiting for this to work. I have been fiddling with it for some time now with 0 progress. I recently installed 8.9 and gave it a go again and for the first time I could actually run the amdcccle application without a seg fault (I always have had surroundview on). And I even was able to enable the third display! However it showed up as "unknown device" and told me to reboot. I crossed my fingers hoping for magic and I got it but not the good kind. When I rebooted was very dissapointed. Not only did it not work but now the "unknown device" representing my 3200 gpu had dissapeared completely! No way to get it back either that I can see. aticonfig still reports the 3200 but amdcccle refuses to admit it's existence. Of course all this works fine in Vista but of course... what good is that right? :popcorn:

---

### Post by zdea on 2008-11-18
Anybody still interested or have any success with this issue?

---

### Post by tgui on 2008-11-20
> **zdea said:**
> Anybody still interested or have any success with this issue?

I never got it to work. :(

---

### Post by zdea on 2008-12-06
Darn... that sucks because it seems like matters are only getting worse. With the release of 8.10 Ubuntu is unable to boot at all, choosing instead to simply hang very quickly. Of course perhaps triple monitors is the least of 780g owner's worries as 8.10 has brought in a whole host of other issues ranging from ALSA sound loss to the Atheros ethernet controller no longer working. I'm also forced to add nolapic/noapic kernel flags to get beyond issues with the sata controller. All in all for me the upgrade was a complete disaster.:sad: These issues also appear to be present on the live cd.

---

### Post by buellman on 2008-12-12
The new fglrx driver 8.12 seems to support Hybrid-Crossfire. I would like to test it but if I enable surroundview on my M3A-H/HDMI + HD 3470 all I get is a [Kernel Panic]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/305165").

Hope you have more luck than me.
Greets. Buellman

---

### Post by zdea on 2008-12-16
> **buellman said:**
> The new fglrx driver 8.12 seems to support Hybrid-Crossfire. I would like to test it but if I enable surroundview on my M3A-H/HDMI + HD 3470 all I get is a [Kernel Panic]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/305165").

Hope you have more luck than me.
Greets. Buellman

I noticed this and have been playing around with it. However this is the situation thus far...

8.12 claims to support surroundview (what I'm interested in).
Ubuntu 8.10 and the kernels with it have the atheros gigabit ethernet driver and ati hd audio busted in them so I can't upgrade.
Ubuntu 8.04 works with audio and ethernet.
Both Ubuntu versions crash with kernel panic when Surroundview is enabled in bios unless acpi=off is set as a kernel option and regardless of Surroundview I must specify the noapic parameter.

---fun. There is a bug report on the subject of the kernel panic issue out there [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/305165](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/305165)
Hope someone fixes it soon. I guess I can't be too mad because the latest ati drivers (8.12) break surroundview on vista as well due to not being able to disable Hybrid Crossfire.

---

### Post by buellman on 2008-12-17
> **zdea said:**
> I noticed this and have been playing around with it. However this is the situation thus far...

8.12 claims to support surroundview (what I'm interested in).
Ubuntu 8.10 and the kernels with it have the atheros gigabit ethernet driver and ati hd audio busted in them so I can't upgrade.
Ubuntu 8.04 works with audio and ethernet.
Both Ubuntu versions crash with kernel panic when Surroundview is enabled in bios unless acpi=off is set as a kernel option and regardless of Surroundview I must specify the noapic parameter.

---fun. There is a bug report on the subject of the kernel panic issue out there [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/305165](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/305165)
Hope someone fixes it soon. I guess I can't be too mad because the latest ati drivers (8.12) break surroundview on vista as well due to not being able to disable Hybrid Crossfire.
This is actually my bugreport. I am Martin :-)
To answer your question: no. Noone has answered me sofar.

But your other problems:
the ethernet-card of my M3A-H/HDMI does work without any special configuration. It works at least with normal 100Mbit. I can't test Gigabit as I have no other PC that would support Gigabit.
I don't know if HDMI audio work because I have no Soundsystem what would make use of it.

I got Hybrid-Crossfire enabled with the new 8.12 driver from ATI but had to acpi=off in grub so it does work. At least it seems to work. Have not tried to much as it sucks for me to turn off acpi.

Maybe you should enhance my bugreport so that the ppl over there make notice of it!

Greets. Buellman

---

### Post by zdea on 2008-12-20
LOl, small world I guess. Yeah I don't know what else to contribute to the bug report as it just plain doesn't work... can't do much investigating with a kernel panic with my meager linux talents.

---

### Post by Willleung on 2009-03-29
I had the same set up too (780G + 3450) never got the big desktop to work on 3 monitors, 8.10 couldn't even boot on it.

---

### Post by buellman on 2009-03-29
[http://bugzilla.kernel.org/show_bug.cgi?id=11541#c90](http://bugzilla.kernel.org/show_bug.cgi?id=11541#c90)

--> Maybe it will be fixed with 2.6.29.1

Greets. Buellman

---

### Post by tgui on 2009-06-22
Update:

The new 9.6 drivers are out. I installed and got some half assed version of surround view to work.

Thats about where the good news ends. :( If any ATI linux driver devs read this, please understand that I respect what difficult work you do with I'd imagine limited resources.

But... the new drivers are just a polished turd when compared to NVIDIA. Though I had my 3 monitors working, balancing the different resolutions was just too much for the ATI driver GUI to handle. More often than not, screen orientation and resolution changes made in the GUI were reported completed but never reflected in the xorg.conf.

I then went the aticonfig route using --initial --dual-head enabling monitors, querying the 2 adapters with similar results.

Finally I dug through the xorg.conf by hand and still had issues with xinerama and 3 screens of different resolutions. Virtual screens of appropriate dimensions were ignored.

In the end the next morning I went to Micro Center and bought a low profile NVIDIA 9400gt for $45 and was up and running with more speed and ease in literally 5 minutes. I've not tried using my 3rd monitor with this card (DVI HDMI VGA ports) but will still be happy if I'm stuck with only 2 monitors in the end.

I took the cowards way out. Perhaps I took the grown mans way out given my 6 hours messing with ATI crap drivers surely would be worth more than $45. 

If anyone has success with 3+ monitors of DIFFERENT resolutions please post up an xorg.conf. Till then NVIDIA for me :)

---

### Post by buellman on 2009-06-22
As I understand the problem: you have to change things via aticonfig or AMDCCCLE. The point is that changes in xorg.conf seem to have no effect to the actual beahvior.
So for now you have two instances which would like to know about the changes you make: /etc/X11/xorg.conf and /etc/ati/amdpcsdb. First you can edit like allways and second you have to edit via aticonfig or AMDCCCLE. That means: if you change something via aticonfig or via AMDCCCLE the changes will be transferd to the xorg.conf and everything should work like expected by the options you selected. But as I understand it will not work the other way around. Means: changes in xorg.conf will not be reflected by amdpcsdb.

So that is what I do today to get for example Hybrid Crossfire to work. I make all my changes through aticonfig and that seems to work.

If you have more detailed questions you maybe would like to look at [Phoronix-Forum]("http://phoronix.com/forums/index.php"). There is a section "AMD/ATI Linux" where such things will be discused and actually are some ATI Devs. arround.

Good luck.
Buellman

---

### Post by tgui on 2009-06-22
> **buellman said:**
> As I understand the problem: you have to change things via aticonfig or AMDCCCLE. The point is that changes in xorg.conf seem to have no effect to the actual beahvior.
So for now you have two instances which would like to know about the changes you make: /etc/X11/xorg.conf and /etc/ati/amdpcsdb. First you can edit like allways and second you have to edit via aticonfig or AMDCCCLE. That means: if you change something via aticonfig or via AMDCCCLE the changes will be transferd to the xorg.conf and everything should work like expected by the options you selected. But as I understand it will not work the other way around. Means: changes in xorg.conf will not be reflected by amdpcsdb.

So that is what I do today to get for example Hybrid Crossfire to work. I make all my changes through aticonfig and that seems to work.

If you have more detailed questions you maybe would like to look at [Phoronix-Forum]("http://phoronix.com/forums/index.php"). There is a section "AMD/ATI Linux" where such things will be discused and actually are some ATI Devs. arround.

Good luck.
Buellman

Hand changes to xorg.conf are in fact immediately reflected, at least with the new driver. Many xserver kills and restarts confirm this "feature" ;)

For those attempting multiple monitors, XRandR12 gets in the way. Before any major xorg changes this needs to be disabled in: "/etc/ati/amdpcsdb" . I don't have the machine in front of me now, a google search will reveal how to do this.

Buellman, I posted in Phoronix long ago with these issues, to no avail.

Ohhh well :)

---

### Post by buellman on 2009-06-22
> **tgui said:**
> Hand changes to xorg.conf are in fact immediately reflected, at least with the new driver. Many xserver kills and restarts confirm this "feature" ;)
Oh... I didn't know that. Thanks for the info!
> **tgui said:**
> Buellman, I posted in Phoronix long ago with these issues, to no avail.

Ohhh well :)
:-D

---

