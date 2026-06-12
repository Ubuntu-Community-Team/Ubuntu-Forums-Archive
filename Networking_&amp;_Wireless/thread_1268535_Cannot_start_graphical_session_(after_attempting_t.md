---
title: "Cannot start graphical session (after attempting to install apps for HTC Magic)"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by adm1968 on 2009-09-17
Found a link to set up tethering for my HTC Magic
[http://www.asgrim.com/2009/07/24/tethering-your-htc-magic-android-phone-in-ubuntu-9-04-jaunty-jackalope/](http://www.asgrim.com/2009/07/24/tethering-your-htc-magic-android-phone-in-ubuntu-9-04-jaunty-jackalope/)

My graphical session will not start any more (just after following one of the instructions):

sudo gedit /etc/environment

Error message

/etc/gdm/Xsession: Beginning session setup ...
/etc/profile: 26: id: Permission denied [:26: Illegal number:
/etc/gdm/Xsession: 192: ls: Permission denied
/etc/gdm/Xsession: Executing default failed, will try to run
exec:205: x-terminal-emulator: Permission denied

Any way to solve this?
Any help greatly appreciated!!

---

### Post by adm1968 on 2009-09-18
[FONT="Georgia"]Does this sound as if I will have to reinstall?
Is there a way to open a session and undo the command introduced last?

Cheers![/FONT]

---

### Post by puppywhacker on 2009-09-18
You have a rights issue. Somehow X windows is not allowed to read the files it needs. The link you pasted doesn't seem to cause this at all.

You need some serious troubleshooting to get this to float, so a reinstall is the easiest way out.

---

### Post by adm1968 on 2009-09-18
> **puppywhacker said:**
> You have a rights issue. Somehow X windows is not allowed to read the files it needs. The link you pasted doesn't seem to cause this at all.

You need some serious troubleshooting to get this to float, so a reinstall is the easiest way out.
[FONT="Georgia"]This is what I figured out, but it does seem suspicious that a graphical session cannot be opened _just after_ applying the said command (sudo gedit /etc/environment). Sessions were closed and opened quite a few times before that command was launched, with no issues at all

Thanks![/FONT]

---

### Post by adm1968 on 2009-09-18
[FONT="Georgia"]Well, voilà!
No need to reinstall:
Used Ubuntu in LiveCD mode, edited /etc/environment (to delete the line included for the PATH), and everything is now back to normal, with a nice graphical session opened

Many thanks for your help![/FONT]

---

