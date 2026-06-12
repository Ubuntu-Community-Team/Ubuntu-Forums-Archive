---
title: "Hard drive issue after 10.10 beta install"
date: 2010-09-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by lasthour1 on 2010-09-24
Hi all,

I'm a pretty experienced Windows guy, but I figured I'd give Ubuntu a go. I installed it to a separate 60GB partition on my 250GB hard drive. Ubuntu booted fine, but Windows didn't boot. It would blue screen while trying every time. I followed a few things I found searching for a solution, and I ended up getting rid of GRUB somehow. Now, when I try to reinstall Windows 7, it doesn't detect any hard drives at all. Solutions? Thanks

---

### Post by mp035 on 2010-09-24
What filesystem was windows installed on FAT or NTFS?

---

### Post by lasthour1 on 2010-09-24
Windows 7 was on my NTFS partition. The Ubuntu install was on a Ext3 journaling partition.

---

### Post by bodhi.zazen on 2010-09-24
> **lasthour1 said:**
> Hi all,

I'm a pretty experienced Windows guy, but I figured I'd give Ubuntu a go. I installed it to a separate 60GB partition on my 250GB hard drive. Ubuntu booted fine, but Windows didn't boot. It would blue screen while trying every time. I followed a few things I found searching for a solution, and I ended up getting rid of GRUB somehow. Now, when I try to reinstall Windows 7, it doesn't detect any hard drives at all. Solutions? Thanks

Moved to the Maverick (testing) section as 10.10 is still in pre-release.

---

### Post by VMC on 2010-09-24
> **lasthour1 said:**
> Hi all,

I'm a pretty experienced Windows guy, but I figured I'd give Ubuntu a go. I installed it to a separate 60GB partition on my 250GB hard drive. Ubuntu booted fine, but Windows didn't boot. It would blue screen while trying every time. I followed a few things I found searching for a solution, and I ended up getting rid of GRUB somehow. Now, when I try to reinstall Windows 7, it doesn't detect any hard drives at all. Solutions? Thanks

First off you don't have to re-install Windows. It's there intact just in "hiding". If all else fails you could re-install Windows boot loader, using there recovery disk.

With that said, and not knowing how proficient you are with Linux, download Boot_Info_Script (click on my "blue" link below)
Then bring the output of that back here. You need to use the "sudo" command like so:
```
sudo ./boot_info_script055.sh
```, once you download the file, and run it using the command, it will dump the results in a file named RESULTS.txt.

---

### Post by lasthour1 on 2010-09-24
Hi VMC,

I tried using the recovery disk, but it too didn't detect my hard drive. I know it's not malfunctioning, because under Ubuntu I can see and open it just fine. Basically, it's invisible to everything but Ubuntu and Ultimate Boot CD.

And about the boot info script, can I run it under a live CD? I can't seem to get into my Ubuntu install on my HDD, because of Lilo, which I think replaced GRUB2.

---

### Post by VMC on 2010-09-24
> **lasthour1 said:**
> Hi VMC,

I tried using the recovery disk, but it too didn't detect my hard drive. I know it's not malfunctioning, because under Ubuntu I can see and open it just fine. Basically, it's invisible to everything but Ubuntu and Ultimate Boot CD.

And about the boot info script, can I run it under a live CD? I can't seem to get into my Ubuntu install on my HDD, because of Lilo, which I think replaced GRUB2.

I didn't mean to recover the Windows install, just its boot, as in /fixmbr. but don't go that route yet.

Yes you can run boot_info_script under the livecd. It will find all the booting info. then just open the RESULTS.txt file copy & print it back here.

---

