---
title: "Lost GRUB after install of Win7.  Repair won't work...pls help."
date: 2017-03-04
forum: Mac OSX
---

### Post by rj32 on 2017-03-04
Hello,

Very new to Ubuntu - pls forgive my ignorance.  Followed several guides/videos to attempt to repair Ubuntu boot/Grub.  Runnign rEFInd on 2006 Macbook Pro.  OSX/WIN7/Ubuntu.

Don't know how to get Ubuntu back.  Could i reinstall - or would that knock off Windows then?  Please help ;)

I read that this might help:  [FONT=Helvetica]http://paste2.org/DVEbd1vm

Many Thanks!

rj3[/FONT]

---

### Post by oldfred on 2017-03-04
Moved to Apple Mac sub-forum.

Do not know Mac.
Looks like script is not showing contents of your ESP - efi system partition or sda1.
It also looks like you have hybrid MBR/gpt configuration which was required by older versions of Windows, but you have to be careful to keep that in sync.

Since not showing sda1, you may need to run chkdsk from Windows, or dosfsck from Ubuntu. Do not know Mac and what file repair tool it may use.
And then it looks like you are reinstalling grub to MBR. Your rEFInd application I believe is for UEFI boot and has files in the ESP.

       [URL="http://www.rodsbooks.com/gdisk/hybrid.html"]http://www.rodsbooks.com/gdisk/hybrid.html

[/URL]
 dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185) 

[URL="http://www.rodsbooks.com/gdisk/hybrid.html"]
[/URL]

---

### Post by rj32 on 2017-03-04
Thank you for your reply oldfred ;)

Is there any chance simply reinstalling Ubuntu to the proper partitions might repair problem? Or do you think I would then lose windows bootabliity?  Currently I "can" boot into OSX or Windows.  I have been booting to Ubuntu via the LIVE cd.  Also btw when i did an fdisk via UBUNTU live cd  - it says that sda1 is 200m EFI System...

rj32

---

### Post by oldfred on 2017-03-04
Did you try Windows chkdsk or Ubuntu's dosfsck on sda1? Or whatever Mac's use?

I do not know Mac, and from what I have seen, issues vary a lot from version to version.

I would not think you have to reinstall, but for some that is the easiest solution.

 Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

---

