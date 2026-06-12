---
title: "maverick boots but no gdm"
date: 2010-08-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by pulpo69 on 2010-08-07
i updated today to maverick.
but i can't get into gnome, after booting i only get the message:
error: unknown command "load_video". vga=771 is deprecated
use set gfxpayload-800x600x8,800x600 before linux command.

Any idea what the problem is and how to solve it?

---

### Post by ranch hand on 2010-08-07
I had a problem with grub on an install the other day that was similar.

If you hit the shift key you should get the menu up and try booting to recovery.  Use the log in (first option) and use the text login.  After you do that you get a prompt.  Type   startx   there. 

If that does not get up in, fire up your Live CD (9.10 or higher) and take a look at your installations /boot/grub.  Should have alot of file (the 10.10 install I am on right now has 196).  I bet yours does not.

If that is the case you will need to Chroot in and purge grub-pc and grub-common, making sure that /boot/grub is completely gone.  Also go to /var/cache/archives/apt and make sure there are no grub files there.  Then reinstall those same packages.

---

### Post by pulpo69 on 2010-08-08
thanks for your advice ranchhand,
my grub.cfg has 146 lines.
i can now boot to gdm (thre was a graphic-card-driver problem too, that
i could solve.
now booting gives me the same error: unknown command "load_video". vga=771 is deprecated
use set gfxpayload-800x600x8,800x600 before linux command.
when comes up plymouth (i believe), but ugly looking and when the goes black for about 10 seconds and then gdm comes up.
i'm a little afraid handling with grub but it seems i've to follow your advice to have all as it should be.

---

### Post by oldfred on 2010-08-08
Did you do an upgrade that would have copied entries from old grub?

vga=799 is a deprecated boot option
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)

Look at grub and see if the upgrade added to splash & quiet a vga entry.

gksudo gedit /etc/default/grub

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by ranch hand on 2010-08-08
> **pulpo69 said:**
> thanks for your advice ranchhand,
my grub.cfg has 146 lines.
i can now boot to gdm (thre was a graphic-card-driver problem too, that
i could solve.
now booting gives me the same error: unknown command "load_video". vga=771 is deprecated
use set gfxpayload-800x600x8,800x600 before linux command.
when comes up plymouth (i believe), but ugly looking and when the goes black for about 10 seconds and then gdm comes up.
i'm a little afraid handling with grub but it seems i've to follow your advice to have all as it should be.
Grub.cfg is different on each drive as folks set things up differently.

I was talking about the /boot/grub directory.  Grub.cfg is in that directory but so are a lot of other very critical files (196 total).  Several are video related.

---

### Post by MarkieB on 2010-08-09
no longer participating in ubuntuforums.org

---

