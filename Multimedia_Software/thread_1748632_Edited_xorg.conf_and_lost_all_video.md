---
title: "Edited xorg.conf and lost all video"
date: 2011-05-03
forum: Multimedia Software
---

### Post by decipheringchaos on 2011-05-03
I'm new to Linux. I have Natty Narwhal and everything was working. Then I moved it to my HDTV, and I had overscan issues. Following some advice I found online, I edited /etc/X11/xorg.conf with new information including a ModeLine.

Upon restart, I get my BIOS screen, the Ubuntu splash, then... nothing. The display goes to sleep. I can ping the computer, and everything seems to work except I have no video.

I did backup my xorg.conf file, but I don't know how to get to it without a display. Hindsight tells me I should have given myself a way to remotely control my computer before messing with xorg, but you live and learn.

I've read online that there is a way from the login screen to get to Terminal without loading the desktop environment, but I can't get to the login screen.

I've also tried using a Linux LiveCD to access my filesystem, and that works to view files, but I have no root privileges.

Is there...
...a way to get to Terminal without loading the login screen?
...a way to give myself root access to my harddrive from a LiveCD?
...something else to try?

Thanks.

---

### Post by tjones00 on 2011-05-04
After you created an xorg.conf did you turn off KernelModeSetting (KMS) by editing the grub profile in /etc/default/grub replacing quiet splash with nomodset then update the kernel images with update grub and initramfs?

Choosing the recovery image at grub should get you to a command line regardless of your xorg.conf as well if you just want to revert the changes.

Another way to do it is once you think the o/s is loaded but the screen is just blank press ctrl+alt+f2 that will switch to a different tty "console" login.

Login then shutdown X (sudo service gdm stop) and go about your command line business.

---

