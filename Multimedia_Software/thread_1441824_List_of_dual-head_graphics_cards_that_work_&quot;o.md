---
title: "List of dual-head graphics cards that work &quot;out of the box&quot; with Ubuntu 9.10 or later"
date: 2010-03-29
forum: Multimedia Software
---

### Post by itsterry on 2010-03-29
I'm so bored of trying to make my old Matrox G550 dual-screen work with Ubuntu latest, that I've decided to invest in a new card.

I can't find anywhere a list of dual-head cards that just work "out of the box" with latest Ubuntu (let's call that 9.04 to widen the net a little).

Could anyone point me in the right direction ?

If such a list doesn't exist, please give me your recommendations for those cards that you've found to "just work" plus the Ubuntu version, and I'll see if I can whip up some sort of a list for everyone

Thanks in advance!

---

### Post by Icarus315 on 2010-03-29
My Ati Radeon HD 4670 512MB PCIe card works fine with dual monitors in Ubuntu 9.10 64-bit using proprietary drivers.  It's cheap, reasonable with games but not stellar, and should have proprietary driver support for quite a while to come.

Edit: If you go changing hardware after you've already installed Ubuntu, especially when it comes to X stuff be prepared to be configuring stuff at a console.  I'd try sudo aticonfig --initial and if that didn't work with my level of expertise I'd probably just back up home (while I had X) and reinstall ;)

---

### Post by itsterry on 2010-03-29
Can't speak for the PCIe version, but the AGP version of the HD4650 looks problematic:
[http://ubuntuforums.org/showthread.php?t=1190433](http://ubuntuforums.org/showthread.php?t=1190433)

Looks like I might need to move up to a PCIe machine...

---

### Post by Icarus315 on 2010-03-29
> **itsterry said:**
> Can't speak for the PCIe version, but the AGP version of the HD4650 looks problematic:
[http://ubuntuforums.org/showthread.php?t=1190433](http://ubuntuforums.org/showthread.php?t=1190433)

Looks like I might need to move up to a PCIe machine...

I don't know anything about AGP, I missed that one: I went straight from a PCI (S3 VirgeDX + VooDoo2) to PCIe (Ati X300) setup, I also don't upgrade my hardware very often so AGP came and went while I put up with cob-webs... ;)

---

### Post by cascade9 on 2010-03-29
All the 6xxx and later nVidia cards should support dual-head fine. (the eaerlier ones should as well, but I've never tried) I've only tried it with a few  though- GT6600, 8600GT, 8800GT, 9500GT.

---

### Post by rwong48 on 2010-03-30
I have used a FX 5600 Ultra, 6600GT, 9600 GSO, and 8400 GS with nvidia TwinView just fine. 2 displays, proper window dragging/maximizing, graphics acceleration, all that jazz.

---

### Post by markbuntu on 2010-03-30
All the newer ati agp cards support dual head and will work fine with the latest drivers from the ati site. Since many of these cards were not even available when 9.04 was released the driver available in the 9.04 jockey (hardware manager) is not compatible with them. It is much the same with the nvidia agp cards.

An ati agp card will work fine for you and give decent performance at a cheap price. Just be sure to use the latest driver from ati since many of these agp cards are very new. 

You might want to move to PCIe as a long term upgrade strategy though since agp is on the way out.

---

### Post by rutiezer on 2010-12-08
Could not find a close enough similar question after a search of ubuntu forums. Cross posted in http:[http://ubuntuforums.org/showthread.php?p=10217457#post10217457](http://ubuntuforums.org/showthread.php?p=10217457#post10217457), Matrox Dual Head with 9.10.

Will this Matrox video card, MGA G400/G450, work on 10.04 LTS, 32-bit?
The video card has been working for several years on 8.04.
What do I need to do beside move the video card to the new system, an Asus P5GDC-V? The motherboard has video built-in. 

Can get two used video cards if that would make it easier to get the dual monitor working.

On 8.04 I replaced the file /etc/X11/xorg.conf from the installation with one found at ubuntu forums. Can paste it here if that would help.


~$ lspci| grep VGA
01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400/G450 (rev 82)

~$ sudo lshw -C video
[sudo] password for oem: 
  *-display               
       description: VGA compatible controller
       product: MGA G400/G450
       vendor: Matrox Graphics, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 82
       width: 32 bits
       clock: 33MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: driver=matrox_w1 latency=32 maxlatency=32 mingnt=16 module=matrox_w1

---

