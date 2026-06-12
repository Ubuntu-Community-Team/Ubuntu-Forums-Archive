---
title: "alternate cd install failed on select and install - but core system in place what now"
date: 2008-09-02
forum: Mythbuntu
---

### Post by bob808 on 2008-09-02
I tried installing mythbuntu 8.10 alpha 4 but could not get the livecd to boot, it dumped me on a command prompt.

I downloaded the alternative cd and it recognised everything and installed the core os onto my hard drive.

It then gave me the screen asking what additional components I wanted to install - I picked SSH, Samba and the mythbuntu components, and straight away it errored me and said that it failed at this point and let me go back to the menu.  I tried again but same problem.

I was able to install grub and I now have a bootable system that puts me into a text command prompt on boot... I can login with my chosen username and password and have net connection.  What do I need to install (using sudo apt-get) to give me the full mythbuntu suite?  I assume I need things like mythbuntu-desktop but surely there is more than that?

If anyone can list the items I would need to apt-get to give me the working desktop and mythbuntu frontend and backend that would be great, and to let me know how to get it to auto boot into a desktop too!

Thanks

bob808

---

### Post by Alfaroid on 2008-09-03
Try:

sudo apt-get mythtv mythbuntu-desktop

This should install complete mythtv and the desktop used bij Mythbuntu.

Greetz,

Alfaroid

---

