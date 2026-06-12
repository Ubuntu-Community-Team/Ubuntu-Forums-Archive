---
title: "Want to install Natty... but partition issues :("
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by RJ12 on 2011-04-01
Ok, so I downloaded the new Beta 1 of Ubuntu 11.04 Natty, and ran the Live USB... it is amazing!!! It seems to be pretty stable on my machine and I want to install it on my computer. But I have hit a snag... I am currently running Windows 7 and I can't get it to let me shrink the partition to a reasonable amount of space (will only let me shrink 150mb). I have an external hard drive that I think I could install it to (can you do that), other than that, I don't know what to do... I have heard that you shouldn't use GParted to shrink a Vista/7 Partition.

Thanks for all of your help guys! Natty is going to be such a great release!!

---

### Post by sillav on 2011-04-01
It's a multiple step process.

1. Back up your data.
2. Turn off swap (on XP you set it to use 0 MB, not sure about 7)
3. Defrag
4. Shrink as much as possible.
5. Reboot with Gparted, resize to about 60%, so if you've got a 320 GB drive, and 80 GB is used, that leave 240 GB, 60% of that is about 150 GB. 
6. Reboot into Windows, defrag again.
7. Repeat steps 5 and 6 until desired size.
8. Reboot into Windows and turn swap back on.

---

### Post by RJ12 on 2011-04-01
Would it be easier to install to my external USB drive?

---

### Post by ranch hand on 2011-04-01
Yes you can install to an external.  Do NOT let the installer install grub on the MBR of your internal.  Grub should detect and boot your MS install from the external.  For some reason that works better than trying to boot from one internal to another.

I would check your bios and see if you can disable the internal during installation.  Then you have no chance of screwing anything on your internal at all.

Make sure that you change the bios so that it boots from the usb device first.  That way if the external is off or not hooked up you will boot from the internal and if the external is there you will boot from it.

---

### Post by RJ12 on 2011-04-01
> **ranch hand said:**
> Yes you can install to an external.  Do NOT let the installer install grub on the MBR of your internal.  Grub should detect and boot your MS install from the external.  For some reason that works better than trying to boot from one internal to another.

I would check your bios and see if you can disable the internal during installation.  Then you have no chance of screwing anything on your internal at all.

Make sure that you change the bios so that it boots from the usb device first.  That way if the external is off or not hooked up you will boot from the internal and if the external is there you will boot from it.

Natty still has that "Advanced" option at the end of installation to change GRUB right? My laptop doesn't have an option to disable the internal drive and I don't feel comfortable opening it up to pull it out. But I do have a Windows Installation Disc to reinstall the Windows Boot Loader should I need it.

---

### Post by ranch hand on 2011-04-01
I have no idea what the image has on it in the install department at all.  It will not boot on my box at all.

Just make sure that you read every little thing on the installer on every page.  Don't miss a thing and it should do what you want.  They claim they are making it easier but from what I read about it all that seems to be going on is making it easier to make a mistake.  Anybody ought to be alright though as long as you make sure you read the whole thing and don't make assumptions.

---

### Post by RJ12 on 2011-04-01
Alright, Thanks! I will be sure to read the fine print and everything. I should be installing later tonight and will let you guys know how it goes. I think I will also go pop on IRC and see if anyone knows about the Advanced options.

---

### Post by RJ12 on 2011-04-02
Well, it ended up working perfectly!! I just went to manual partitioning and I had an option to choose where to install the Boot Loader.

Thanks for all the help guys, I really like Natty!

---

### Post by ranch hand on 2011-04-02
This is truly great news.

---

