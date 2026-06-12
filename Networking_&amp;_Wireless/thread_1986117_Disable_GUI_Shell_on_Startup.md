---
title: "Disable GUI Shell on Startup"
date: 2012-05-24
forum: Networking &amp; Wireless
---

### Post by anXieTyPB on 2012-05-24
Hello.

I tested LTSP today and I found out that a valid GUI Shell for Xorg must be installed in order to work, which is somehow logical.

The problem is that the server itself should not boot into a GUI shell. 

How do I achieve that the server is booting into text mode only while keeping the possibility for thin clients to still log in into a GUI shell?

---

### Post by ratcheer on 2012-05-24
Try editing /etc/init/lightdm.conf and commenting out the "start on" command.

Tim

---

### Post by anXieTyPB on 2012-05-25
This didnt work for me.

In addition to that, changing boot options for the kernel in /etc/default/grub to "text" didnt stop booting into the GUI aswell.

Any other options or methods available?

Update:

Solved: i simply had to disable gnome display manager on startup: sudo update-rc.d -f gdm remove

---

### Post by ratcheer on 2012-05-25
Well, I had no idea your system is using gdm instead of lightdm. Most fairly current Ubuntu installations use lightdm, depending on what DE they run.

Tim

---

