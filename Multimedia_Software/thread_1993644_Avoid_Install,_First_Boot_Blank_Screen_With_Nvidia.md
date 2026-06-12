---
title: "Avoid Install, First Boot Blank Screen With Nvidia 550ti Card"
date: 2012-06-02
forum: Multimedia Software
---

### Post by buzzingrobot on 2012-06-02
Just a note to say that the combination of a 3.2/3.3 series kernel,  the open source Nouveau driver for Nvidia cards, and the Nvidia 550ti (and probably some other Nvidia cards)  results in users booting into the infamous blank screen with a blinking  cursor.  

This is a kernel issue apparently, and not a Nouveau bug.  I believe the 3.4 kernel deals with it.

Because the Nouveau driver is used on the 12.04 install images, and is  installed by default, and because 12.04 uses a 3.2 kernel, users will  also boot into the same blank screen when they boot into both an install CD or USB  stick, and the first boot following an installation.

I have a 550ti card.  I handle this by triggering the Grub menu when I  boot the install CD/USB. I follow the displayed instructions to edit the  kernel options. (Make sure the cursor is on the first line the menu.  Press "e" and move the cursor just beyond the last word in the entry  that begins "linux   /boot/vmlinuz...." . The line will wrap and very probably ends  with "splash" or "$vt_handoff". There is a second, similar line for the  "Recovery" option. That's not the one you want.)

I've found that I need to add "nouveau.noaccel=1 nomodeset" here as the  kernel options that will allow the installCD/USB to boot into a display I  can actually see.  You don't need to do anything to save these  options.  Just tap "F10" and the boot will proceed.

You will boot into a low-resolution display.  Don't worry. You'll get the correct resolution when you install the Nvidia driver.

After I have installed 12.04, I repeat this at the first boot.  Then,  the first thing I do is launch "Additional Drivers" and install the  Nvidia driver.  If you don't know how to find "Additional Drivers" just  wait a minute or so and the system will prompt you.

After the Nvidia driver is installed, reboot and proceed with downloading the usual batch of updates.

"Additional Drivers" uses language to describe the two available drivers  that I find to be confusing. The first driver listed is "recommended",  while the language used to describe the second entry can be taken to  mean that it includes only updates to the recommended driver.  That is  not the case.  The "Recommended" driver is the Nvidia driver that was  available when 12.04 was released.  The second entry installs the  current stable Nvidia driver that was not available at the time of  12.04's release.  I've not had any problems using the current driver.

I've found that the Alternative 12.04 install image will successfully boot into the ncurses, i.e., text-based, install routine, so these steps are not necessary for the install.  However, the Nouveau driver is still installed on your machine.  Editing the kernel options are still necessary to have a successful first boot after the install.

---

