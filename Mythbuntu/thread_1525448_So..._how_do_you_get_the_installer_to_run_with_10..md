---
title: "So... how do you get the installer to run with 10.04"
date: 2010-07-06
forum: Mythbuntu
---

### Post by Gorf on 2010-07-06
So after downloading the install ISO twice (mythbuntu-10.04-desktop-i386.iso) the disk boots the exact same way on multiple pieces of hardware.  It just drops me into a shell with a message that says "Welcome to Ubuntu!" and a URL referencing the documentation. What do I run to get the installer started?

---

### Post by nickrout on 2010-07-06
It should go into an X screen with xfce as your window manager.

If X is not starting you could have a video problem. When the CD first boots there are various help screens, some of which show video options, like starting at a lower res.

Also in the command line you do get dropped to you may be able to find a log of why X didn't start. Try /var/log/Xorg.0.log

---

### Post by Mad_Professor on 2010-07-06
It should say "Welcome to Mythbuntu" then alot of menu options, one of them being install mythbuntu. Something is obviously not correct, or you some how got a no-gui/text only install iso.

I think I came across this problem once before on 10.04, turned out the http mirrors were broken/out of sync, I end up using the torrent link.

---

### Post by superm1 on 2010-07-07
> **Gorf said:**
> So after downloading the install ISO twice (mythbuntu-10.04-desktop-i386.iso) the disk boots the exact same way on multiple pieces of hardware.  It just drops me into a shell with a message that says "Welcome to Ubuntu!" and a URL referencing the documentation. What do I run to get the installer started?

Is this the ISOLinux boot prompt, or a standard Ubuntu shell prompt?

If it's the former, just press enter - it means that your PC(s) can't display the correct VGA mode.

If it's the latter, then try safe graphics mode in the F6 boot menu, or nomodeset in the same menu.

---

