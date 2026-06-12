---
title: "Natty gives me a white flashing login box"
date: 2010-12-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2010-12-23
Just did an upgrade and start up now gives me a white flashing box on the normal background. There is nowhere to enter my password and my user name is not displayed. Doing cntrl-Alt-F3 gives me a text login which is OK.

Anyone else found this?

---

### Post by Amroozy on 2010-12-23
same problem after last update..

---

### Post by Peter09 on 2010-12-23
Both my test systems giving me this error now.

---

### Post by Harry33 on 2010-12-23
Could this one be the bug you are experiencing:
bug #693737
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/693737](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/693737)

---

### Post by yellerKat on 2010-12-23
> **Harry33 said:**
> Could this one be the bug you are experiencing:
bug #693737
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/693737](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/693737)

From your link:

> Downgrading GTK+2.0 to version 2.23.2-0ubuntu4 did fix this.
I did not have to downgrade the new GTK+3.0 packages.

What's the best way to go about downgrading GTK+2.0?

PS are you the same Harry? :smile:

---

### Post by Harry33 on 2010-12-23
> **yellerKat said:**
> From your link:
What's the best way to go about downgrading GTK+2.0?
PS are you the same Harry? :smile:

The safest way I know is to go and download the deb packages from Launchpad:
[https://launchpad.net/ubuntu/+source/gtk+2.0/2.23.2-0ubuntu4](https://launchpad.net/ubuntu/+source/gtk+2.0/2.23.2-0ubuntu4)
Just choose the architecture first.
Packages:
gir1.2-gtk-2.0
gtk2-engines-pixbuf
libgail18
libgtk2.0-0
libgtk2.0-bin
libgtk2.0-common

Then (all apps closed) in terminal go to the folder you downloaded them,
To see the packages, run: dir
Then run (where x is the exact name of the package):
sudo dpkg -i x1.deb x2.deb ...

PS. Yes I am the same person.

---

### Post by yellerKat on 2010-12-23
Thank you!

---

### Post by heathman001 on 2010-12-23
Same problem here. dmesg shows this message repeating with different pids:
ptrace of non-child pid <nnnn> was attempted by: gdm

---

### Post by TheSe7enthProphet on 2010-12-23
> **Harry33 said:**
> The safest way I know is to go and download the deb packages from Launchpad:
[https://launchpad.net/ubuntu/natty/+source/gtk+2.0/2.23.3-1ubuntu2](https://launchpad.net/ubuntu/natty/+source/gtk+2.0/2.23.3-1ubuntu2)
Just choose the architecture first.
Packages:
gir1.2-gtk-2.0
gtk2-engines-pixbuf
libgail18
libgtk2.0-0
libgtk2.0-bin
libgtk2.0-common

Then (all apps closed) in terminal go to the folder you downloaded them,
To see the packages, run: dir
Then run (where x is the exact name of the package):
sudo dpkg -i x1.deb x2.deb ...

PS. Yes I am the same person.

After doing this, I'm still getting the flashing log in box.

My process:

Downloaded the files on a different computer
Put on USB drive
Ctrl+Alt+F1 to get text log in, logged in as root
Mounted USB drive with mount -t msdos /dev/sdb /media/sdb
Ran the dpkg -i <packages> (All successful)
Rebooted
Flashing login

---

### Post by Harry33 on 2010-12-23
> **TheSe7enthProphet said:**
> After doing this, I'm still getting the flashing log in box.
...


I am sorry I gave you the link to the new buggy GTK+2.0 (version 2.32.3-1ubuntu2).
It should have been the link to the older, working version 2.23.2-0ubuntu4.

Here is the correct link:
[https://launchpad.net/ubuntu/+source/gtk+2.0/2.23.2-0ubuntu4](https://launchpad.net/ubuntu/+source/gtk+2.0/2.23.2-0ubuntu4)

---

### Post by TheSe7enthProphet on 2010-12-23
> **Harry33 said:**
> I am sorry I gave you the link to the new buggy GTK+2.0 (version 2.32.3-1ubuntu2).
It should have been the link to the older, working version 2.23.2-0ubuntu4.

Here is the correct link:
[https://launchpad.net/ubuntu/+source/gtk+2.0/2.23.2-0ubuntu4](https://launchpad.net/ubuntu/+source/gtk+2.0/2.23.2-0ubuntu4)

Aha! Thanks, much! Worked perfect :)

---

