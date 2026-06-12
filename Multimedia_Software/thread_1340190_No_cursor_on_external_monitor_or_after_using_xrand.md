---
title: "No cursor on external monitor or after using xrandr"
date: 2009-11-28
forum: Multimedia Software
---

### Post by boert89 on 2009-11-28
Hello,

after updating to Ubuntu Karmic I am not able to use my external monitor any more. I've got an Asus Netbook that originially had installed Ubuntu netbook remix, but I've undone the changes, so apart from the 2.6.28-12-netbook-eeepc kernel, it's a normal Ubuntu 9.10 system.

I use xrandr to set the resolution of my external monitor. However, since the update, I cannot see the cursor on the external monitor, but on the LCD. Everything works fine, like clicking, it's just, I cannot see the cursor.
The same occurs at the LCD, when I try to use the --scale option of xrandr to modify the resolution of my LCD.

I was about to file a bug, but i'm not sure whether this is some driver problem or a general x-server problem. Help as to how to solve the problem is therefor as much appreciated as help as to how to track down the problem to a specific device, driver or peace of software.

Thanks for your help,
Bertram

---

### Post by pdeman2 on 2009-12-03
I have exactly the same issue.  I've been looking for a solution for a couple of weeks now with no luck.  I'm not an Ubuntu user, but your post came up on google and it seems to be most relevant to my problems.

I'm using OpenSUSE 11.2 with XRandR version 1.3.2 with the intel video driver and kernel 2.6.31.5-0.1-desktop.

I've been using XRandR for years and I've never had this problem.  It is quite aggravating.  If you file a bug report somewhere I would be willing to make a confirmation.  Outside of that, I really don't have the time to try and help debug this at the moment.

I've found only one other mention of this issue here: [http://bbs.archlinux.org/viewtopic.php?id=83285](http://bbs.archlinux.org/viewtopic.php?id=83285)

---

### Post by boert89 on 2009-12-04
My problem is, I don't really know what to file the bug for. Is this a driver problem or does xorg mess something up? There might be a connection to the last ubuntu system upgrade which move some graphics processing and rendering from the graphic card to the kernel afaik. The problem didn't occur before.
One temporarily solution I've found is to switch to the console  (CTRL + ALT + F1) and then back to xorg display (CTRL + ALT + F7). This is not a permanent fix of course, but at least you can use xrandr now again.

---

### Post by sru69 on 2009-12-04
Concerning OpenSUSE 11.2 there is a bug report at

[https://bugzilla.novell.com/show_bug.cgi?id=544930](https://bugzilla.novell.com/show_bug.cgi?id=544930)

Please vote for this bug ;-)

---

### Post by boert89 on 2009-12-05
I've filed a bug for Ubuntu. If it affects you, please vote for it.

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/492782](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/492782)

---

