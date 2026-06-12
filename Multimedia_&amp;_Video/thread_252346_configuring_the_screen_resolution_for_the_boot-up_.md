---
title: "configuring the screen resolution for the boot-up messages"
date: 2006-09-06
forum: Multimedia &amp; Video
---

### Post by False Data on 2006-09-06
The 6.06 Desktop installer correctly figured out that my older NVidia graphics card will run at 1280x1024, but it missed the fact that my Acer F51 LCD monitor only goes to 1024x768.  (In fact, based on the contents of /etc/X11/xorg.conf, it detected the F51 as a generic monitor, possibly because there was a KVM switch between it and the monitor.)  Anyway, the net result was a very confused monitor.

Editing /etc/X11/xorg.conf fixed the problem once the system gets to the login screen.  So, once the system boots, it's usable.

Unfortunately, the startup and shut-down messages are still unreadable.  What do I have to edit to set the resolution for the boot-up and shut-down screeens?  Or, if there's no way to configure it, how can I send them back to good ol' reliable text?

---

### Post by False Data on 2006-09-06
Oh, and I'm also open to suggestions on a better KVM switch for home use than this cheap Belkin unit that won't switch unless it thinks there's a valid signal--that's a problem if you're trying to switch before powering up so you can catch the GRUB prompt. :-)

---

### Post by False Data on 2006-09-16
After some digging, I found the culprit.  The problem is in grub's default video mode.  There's a thread here: 

[http://www.ubuntuforums.org/forumdisplay.php?s=&daysprune=30&f=75](http://www.ubuntuforums.org/forumdisplay.php?s=&daysprune=30&f=75)

which lists video options to pass to the kernel.  In my case, editing /boot/grub/menu.lst and adding "vga=791" to the "kernel" line for the default boot image fixed the problem.  Adding it to the "defoptions" line ensured it'll stay fixed as the system downloads new kernel updates.

---

