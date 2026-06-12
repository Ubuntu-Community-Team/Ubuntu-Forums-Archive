---
title: "Install Windows 8.1 on new SSD"
date: 2019-10-10
forum: MINT
---

### Post by 007jack on 2019-10-10
Hi, I am recovering drives and upgrading my computer.

Running Linux Mint from USB.

All drives from my old Windows 8.1 install are recognized.  I want to install windows 8.1 fresh on my new SSD (call it D).

I have my Win 8.1 ISO file on USB and sitting on D if needed.

After I install I want to move some of the old windows files from C to D and then reformat C and install Linux on C.  D is 500gb SSD and C is only 256gb so I want to do it like this.

Where to start?

Linux newb here.

---

### Post by wildmanne39 on 2019-10-10
*Thread moved to **MINT a more appropriate sub-forum**.*

---

### Post by yancek on 2019-10-11
> I have my Win 8.1 ISO file on USB and sitting on D if needed.

You will need to put it on a USB or DVD and if you are not sure how to do it I would suggest finding a windows forum or going to the microsoft site.

Windows 8 defaults to install UEFI if you have a GPT drive.  Check if your drive is GPT because if it is, you will need windows installed UEFI and also Mint.

 Better to get the data you want off and to another drive first.

Are you familiar with Linux drive/partition naming conventions?  There will not be  C or D seen from Mint, drives are named as sda, sdb, etc, partitions sda1, sda2, etc.  You will need to familiarize yourself with this so you do not overwrite the wrong disk which should not reall be a problem as they are differnt sizes and you should be able to see that with the proper commands.

>    D is 500gb SSD and C is only 256gb so I want to do it like this.

You  are referring to hard drives here and you will need to have or create free or unallocated space on them from the windows Disk Management tool so that you have somewhere to install Mint.  A default windows system cannot create a Linux filesystem so you will need to use the Mint installer to do that, the standard being ext4.

If your windows install is UEFI, I would suggest doing an online search for dual booting windows 8 with Mint UEFI before proceeding. 
  .

---

