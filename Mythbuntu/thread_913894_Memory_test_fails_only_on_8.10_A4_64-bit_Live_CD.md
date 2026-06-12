---
title: "Memory test fails only on 8.10 A4 64-bit Live CD???"
date: 2008-09-08
forum: Mythbuntu
---

### Post by Calmor on 2008-09-08
I have a machine that was previously running Mythbuntu 8.10 Alpha 4 AMD64.  It is a newer ASUS motherboard with 2GB of Kingston RAM and 64-bit AMD processor, previously running an IDE HDD (as master) and IDE DVD-RW drive (as slave).  I never had any boot-up or memory issues running this configuration.

I came into a few external hard drives for cheap, which I then tore apart to use as internal SATA drives.  I now currently have a 250GB SATA on /dev/sda1 and a 1TB SATA on /dev/sdb1.  The IDE DVD-RW drive was moved to master, and the IDE HDD removed.

After setting up the new SATA drives in a Ubuntu 8.04 AMD64 LiveCD environment (the 250GB had things on it which I moved to the 1TB), I tried to install using the Mythbuntu 8.10A4 AMD64 disk.  My thought was to use the 250GB drive as a system drive and the 1TB drive to store TV shows / DVD rips.  

Unfortunately, any attempt to install, check CD for defects, or boot into the live environment dropped me to the initramfs prompt.  Upon running Memtest, it fails at 20% with never-ending errors until the PC locks up.

I re-downloaded the 8.10A4 disk, checked the md5sum after burning, and all was well, but still the same problem.  I burnt the latest memtest86 (3.4) and the system passed with flying colors.  Ubuntu 8.04 AMD64 and Mythbuntu 8.04 x86 disks both boot up and pass the memory test.

I tried to remove one stick of RAM, then the other, but the test failed at the same point with either one in.

Am I missing something?  The only system configuration change was the removal of the IDE HDD for the SATA drives and the move from slave to master of the installation drive (DVD-RW drive).

---

### Post by mrand on 2008-09-08
> **Calmor said:**
> I have a machine that was previously running Mythbuntu 8.10 Alpha 4 AMD64.  It is a newer ASUS motherboard with 2GB of Kingston RAM and 64-bit AMD processor, previously running an IDE HDD (as master) and IDE DVD-RW drive (as slave).  I never had any boot-up or memory issues running this configuration.

I came into a few external hard drives for cheap, which I then tore apart to use as internal SATA drives.  I now currently have a 250GB SATA on /dev/sda1 and a 1TB SATA on /dev/sdb1.  The IDE DVD-RW drive was moved to master, and the IDE HDD removed.

After setting up the new SATA drives in a Ubuntu 8.04 AMD64 LiveCD environment (the 250GB had things on it which I moved to the 1TB), I tried to install using the Mythbuntu 8.10A4 AMD64 disk.  My thought was to use the 250GB drive as a system drive and the 1TB drive to store TV shows / DVD rips.  

Unfortunately, any attempt to install, check CD for defects, or boot into the live environment dropped me to the initramfs prompt.  Upon running Memtest, it fails at 20% with never-ending errors until the PC locks up.

I re-downloaded the 8.10A4 disk, checked the md5sum after burning, and all was well, but still the same problem.  I burnt the latest memtest86 (3.4) and the system passed with flying colors.  Ubuntu 8.04 AMD64 and Mythbuntu 8.04 x86 disks both boot up and pass the memory test.

I tried to remove one stick of RAM, then the other, but the test failed at the same point with either one in.

Am I missing something?  The only system configuration change was the removal of the IDE HDD for the SATA drives and the move from slave to master of the installation drive (DVD-RW drive).

Have you tried the non-Mythbuntu 8.10A4 disk?  If not, could you?

Thanks,

[INDENT]   Marc[/INDENT]

---

### Post by Calmor on 2008-09-08
> **mrand said:**
> Have you tried the non-Mythbuntu 8.10A4 disk?  If not, could you?

Thanks,

[INDENT]   Marc[/INDENT]

Marc,

I looked on the cdimage site and it seems they've taken Alpha 4 down and posted Alpha 5 for all flavors (K-X-Ed-Ubuntu).  Do you want me to try Mythbuntu 8.10A4 x86 (if it's still available) or possibly Ubuntu 8.10A5?  I'd be happy to try any live CD or complete install on my machine.  Also, if you want complete specs, I'll get you lspci/lsusb output or whatever else you may need.

Thanks for the help!

---

### Post by bmwman on 2008-09-08
I had the same problem with my brand new mobo/cpu/ram that i recently bought. No matter what I did it was booting to ramfs error and drops to command line. I've tried 8.04,8.04.1, 8.10 and they did all the same. I had to send the mobo back because i thought it was not compatible since it was spanking new model just released the previous week. I got the previous model and it worked fine. Memory test still fails if I run it but my machine has been working perfect for over a month now. I don't know why it was failing.

---

### Post by Calmor on 2008-09-08
Which mainboard did you have?  My board is an ASUS M2A-VM HDMI.  I'm not sure why 8.10a4 had the problem only with the SATA drives though, since it worked just fine with the IDE drive.  I'm tempted to put it back in and see if it suddenly works...

---

### Post by Calmor on 2008-09-08
Ok, I just tested 8.10a4 32-bit (x86), and it booted into a LiveCD session just fine, no memory issues or dropping to the initramfs prompt as it had before, so it seems, at least with my hardware, that the problem lies in the 64-bit disc.
 
Another point of possible interest, when the 64-bit LiveCD does drop to the initramfs prompt, the hdd activity light remains on, solid and constant.

---

### Post by bmwman on 2008-09-08
> **Calmor said:**
> Which mainboard did you have?  My board is an ASUS M2A-VM HDMI.  I'm not sure why 8.10a4 had the problem only with the SATA drives though, since it worked just fine with the IDE drive.  I'm tempted to put it back in and see if it suddenly works...

I had GIGABYTE GA-EG43M-S2H which has the latest Nvidia chipset. I probably could have made it work but I returned it for GA-73PVM-S2H. I'm very satisfied with the performance. It's just that the HDMI is kinda waste since Nvidia doesn't support audio over HDMI and only video. That's what I wanted to do but found that the hard way it won't work, at least until they make some drivers. I've never used a 64bit OS. Is that much better or not really?

---

### Post by Calmor on 2008-09-10
> **bmwman said:**
> I had GIGABYTE GA-EG43M-S2H which has the latest Nvidia chipset. I probably could have made it work but I returned it for GA-73PVM-S2H. I'm very satisfied with the performance. It's just that the HDMI is kinda waste since Nvidia doesn't support audio over HDMI and only video. That's what I wanted to do but found that the hard way it won't work, at least until they make some drivers. I've never used a 64bit OS. Is that much better or not really?

I don't even remember which chipset this thing has.  I know it has ATI graphics onboard, and I thought I remembered a BIOS option for audio over HDMI.  I think it might have worked in Windows, but I've been out of the game for quite a while.

As for the 64-bit OS, I don't know if it makes a huge difference to be honest.  The biggest positive seemed to be the use of over 4GB of RAM (but this machine only has 2GB anyway).  On top of that, I think it's supposed to be a bit faster at some large-number processing tasks... I think that includes large video files but I could be way off-base.  The downside to the 64-bit OS is the lack of Adobe product support (flash, Acrobat Reader) and a sub-optimal Java implementation.  I have Hardy 64-bit on my laptop too, and have never had driver issues.

Basically, if you're looking for a big boost in performance, it's not there.  If you already have a 32-bit OS and it's doing the job, and you don't have 4GB+ of RAM, I don't see any reason to switch.

I think I'm just going to try to borrow an Nvidia card and see if MythTV works with it.  If so, I'll try to barter my ATI 2600XT for a lesser-but-HD-capable Nvidia GPU, and stick with 8.04.1

---

