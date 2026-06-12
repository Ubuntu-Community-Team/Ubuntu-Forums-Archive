---
title: "Can't get 9.10 iso to boot"
date: 2009-12-27
forum: Mythbuntu
---

### Post by IceCap on 2009-12-27
I'm upgrading my Mythbuntu setup (8.4.1 been running for about a year) with a video card and a fresh install of 9.10.  Problem is that I can't get the 9.10 iso to boot.  The 8.4.1 disk still boots fine so I don't think it is a hardware issue.
  I've checked the MD5 sum and the iso downloads fine (I've actually downloaded it 3 times) and the CDs burn fine (according to the check) from 3 different computer (Mac Mini Leopard, G4 Tiger and a PC running XP).
  What happens is that I get to the selection screen (boot without affecting HDs, installs, etc.) but both the install and the live environment freeze shortly after the the computer starts reading from the CD (the CD stops spinning and the pulsating logo stops pulsating, the soft ON/OFF button doesn't work anymore, only the reboot button).
  I have the CD drive (actually DL DVD burner) on the same IDE bus as the brand new Seagate HD.  I had both set as "cable select" with the HD as the slave and the CD drive as the master and another time I had the HD as master and the CD drive as slave by jumping it that way (same results).  It looks like the installer is choking in the exact same place since the logo always becomes frozen when it is dim (almost the dimmest).  I tried the 9.04 cd that I had with same results (well, there is no pulsating logo it just freezes after about the same time).  When I originally installed the 8.4.1 version I do remember that 8.10 would not boot for some reason (not sure if it is the same thing).

  So since I'm not sure that anyone can actually help with this since I don't seem to be able to get any useful information where it is choking (anyway to see what is going on when booting the iso?), I was wondering about just installing xubuntu (hoping that its iso will boot) and then MythTV through the package manager.  What will I miss if I do that?  Anything that I really need to know about that route?

  BTW, I also checked the memory and it was fine.  Pentium 4 2.4GHz, 1.2GB memory, PVR-350, NVidia 7600.

  Thanks

  IceCap

---

### Post by nickrout on 2009-12-27
> **IceCap said:**
> I'm upgrading my Mythbuntu setup (8.4.1 been running for about a year) with a video card and a fresh install of 9.10.  Problem is that I can't get the 9.10 iso to boot.  The 8.4.1 disk still boots fine so I don't think it is a hardware issue.
  I've checked the MD5 sum and the iso downloads fine (I've actually downloaded it 3 times) and the CDs burn fine (according to the check) from 3 different computer (Mac Mini Leopard, G4 Tiger and a PC running XP).
  What happens is that I get to the selection screen (boot without affecting HDs, installs, etc.) but both the install and the live environment freeze shortly after the the computer starts reading from the CD (the CD stops spinning and the pulsating logo stops pulsating, the soft ON/OFF button doesn't work anymore, only the reboot button).
  I have the CD drive (actually DL DVD burner) on the same IDE bus as the brand new Seagate HD.  I had both set as "cable select" with the HD as the slave and the CD drive as the master and another time I had the HD as master and the CD drive as slave by jumping it that way (same results).  It looks like the installer is choking in the exact same place since the logo always becomes frozen when it is dim (almost the dimmest).  I tried the 9.04 cd that I had with same results (well, there is no pulsating logo it just freezes after about the same time).  When I originally installed the 8.4.1 version I do remember that 8.10 would not boot for some reason (not sure if it is the same thing).

  So since I'm not sure that anyone can actually help with this since I don't seem to be able to get any useful information where it is choking (anyway to see what is going on when booting the iso?), I was wondering about just installing xubuntu (hoping that its iso will boot) and then MythTV through the package manager.  What will I miss if I do that?  Anything that I really need to know about that route?

  BTW, I also checked the memory and it was fine.  Pentium 4 2.4GHz, 1.2GB memory, PVR-350, NVidia 7600.

  Thanks

  IceCap

Try some of the options like noacpi and safe graphics mode

---

### Post by IceCap on 2009-12-27
I tried all of them.  Same results (I actually couldn't find any information about the F6 options but I tried all of them).

  And I just tried xubuntu 9.10 with the same results.  Is there any way I can run the iso installer in verbose mode to see what is going on?

  I also tried it with the ethernet cable plugged in, same results.

  I'm going to unplug the hard drive.  Maybe that is messing up the installer (I can't see how that could be given that 8.0.4.1 booted up fine).

  I guess I could try to get 8.04.1 installed and then upgrade all the way to 9.10 but that just appears clumsy.

Thanks

  IC

---

### Post by benlyboy on 2009-12-27
Hi there
It may not be related to what you have going on, though it kinda sounds like what happened to me when I tried to install myth a few month ago. 

It would freeze or would come up with a warning that it couldn't find a file. The disk tested good, and I downloaded the iso a few times. no luck.

In the end I switched from CD-WR to CDR and all went well from there.

As I said, may not be what your dealing with but I thought mention it just in case.

---

### Post by IceCap on 2009-12-27
Yeah, maybe my media is bad.  It is CDR, not CDRW but still a cheapo CDR.

  Right this minute I'm burning Ubuntu 9.10.  Maybe my hardware is somehow incompatible with xubuntu installer (since 8.10 came out).  It that works, I'll just install MythTV 0.22 from the package manager and configure it manually.

  I'll post my results here later.

  IC

---

### Post by IceCap on 2009-12-27
Tried Ubuntu 9.10 with the same results.  Also tried Mythbuntu 9.10 burned to a better/different CDR media (it's a HP media, not sure if it is any better) same thing.
  Disconnected the hard drive, same thing.

  Found an older Ubuntu 8.04 CDR that I had used last year on a laptop (same media that I have been using and it was burned on my G4) and it boots fine.

  I'm convinced that there is something about my hardware setup that Ubuntu (and derivatives) 8.10 and later doesn't like and the installer craps out.  It doesn't really matter for me right now, I'm going to install Xubuntu (or Ubuntu) 8.04 and then upgrade to 9.10 via internet and then install MythTV (hopefully it isn't an issue with the kernel).

  Thanks

 IC

---

### Post by IceCap on 2009-12-27
I downloaded Xubuntu 8.04.1 burned it on the same media and it installed fine.  So it really looks to me that there is something about my hardware which 8.10 and later versions don't like.  We'll see if the upgrade to 8.10 over the network breaks the system.

Update:  Upgrading to 8.10 hangs the system at boot.  Looks like it is X windows.  It just gets to the cross-hair mouse pointer and that's it.

   IC

---

### Post by lanierbrian on 2009-12-28
IceCap,

I had an experience similar to your first post while attempting to install Mythbuntu to my new Zotac Mag.  Same thing, multiple downloads and CDs, good MD5SUM check.  Finally installed Ubuntu 9.10 on the machine and then did fresh install over that with Mythbuntu which worked.  Unfortunately, I'm a newbie and getting Mythbuntu to install was about the only thing that has gone right with this, I'm about to throw in the towel and install Windows 7.

---

### Post by db260179 on 2009-12-31
In case you haven't tried, download mythbuntu from the torrent.

Downloading from the ftp,http servers failed for some reason?

Once downloaded, boot in safe recovery mode, see if anything obvious comes up.

What hardware are u using? Processor,video card etc

---

### Post by tells1977 on 2009-12-31
I have the same issue.  I have the following hardware configuration:

CPU: AMD|A64 X2 5050E 2.6G AM2 RT
Memory: 4GB [SIZE=1][COLOR=#cc0000][FONT=arial][COLOR=#37329b][COLOR=Black]OCZ DDR2 PC2-6400 SLI-Ready Edition 4GB Dual Channe[/COLOR]l[/COLOR][/FONT][/COLOR][/SIZE]
Motherboard: GA-M78SM-S2H
Video:  Geforce 8200 (built into motherboard)
Tuners:  Haupauge HVR-1800, PVR 150
Audio Chipset:       Realtek ALC888
Hard Drive: 1TB Western Digital 16M SATA2 WD10EACS
Keyboard:  Logitech Wireless diNovo
Mouse: Dell Gyration Remote

---

