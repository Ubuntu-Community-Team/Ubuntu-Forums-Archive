---
title: "Single Boot Mac Pro - turn back into OS X machine?"
date: 2018-03-31
forum: Mac OSX
---

### Post by sterator on 2018-03-31
I've been happy with my 2009 Mac Pro as a single-boot linux box, but now thinking of selling the computer. I have a USB Stick to install El Capitan - which will run on this Mac, but I'm not sure how to install OS X on a Mac which was made into a single-boot Linux Machine.

Has the Mac's BIOS been altered? How do I re-macify it?

Thank you!

---

### Post by gsahli on 2018-04-09
Sorry I didn't see this sooner, to answer...
First, startup from the USB stick - hold the Option/Alt key immediately after the gong sound, and hold it until you see the visual boot selector screen. Select the USB stick and click on the right-arrow to start.
Now, use the Disk Utility (utilities menu choice) to create one partition and format the drive for HFS+ (Mac OS Extended, journaled). Then install.

---

### Post by coffeecat on 2018-04-09
*Thread moved to **Mac OSX**.*

---

### Post by sterator on 2018-05-27
Thank you for the reply. What happens when, upon hearing the chime, with the USB OS X installer plugged in, and Option held down, I don't get an option to install OS X but only an EFI boot icon - which only leads to booting Ubuntu?

Thank you!

---

### Post by caberry9 on 2018-09-18
I would bet you have to try Recovery with fresh install

Reboot with Command (&#8984;) – Option (&#8997;) – R

---

### Post by sterator on 2018-09-18
thank you.

though it&#8217;s been a few months, this is what I believe I did - hope this helps other Mac users..

I used the Snow Leopard disk (yes, from 2009!) to do a disk utility reformat, then installed Snow. Then using a USB installer, I nuke and paved into El Capitan. This may sound like too many steps, but under Ubuntu, the Mac simply didn&#8217;t even &#8220;see&#8221; the El Capitan installer.

I knew that the Snow Leopard disk had utilities on it that the Mac would have no choice but to acknowledge.

***Note***: this is not the end of my using Linux. I shall use it in future, but not on a Mac. This community and Ubuntu are solid gold in my book!

---

### Post by crjackson on 2019-03-08
For the record, you can install OS/X by booting the install media from a USB Thumb Drive, without bootpicker (in case you have no EFI GPU installed).

Remove all BOOTABLE drives from the mac (or wipe out all bootable OS&#8217;s), insert macOS install media in the USB Port (with power off), then just power on the Mac and it will boot to the USB Thumb drive. From there select your target (blank) HDD/SSD and install as normal.

When you are done, you can reinsert any other bootable drives you wish.

Hope that clears it up...

---

