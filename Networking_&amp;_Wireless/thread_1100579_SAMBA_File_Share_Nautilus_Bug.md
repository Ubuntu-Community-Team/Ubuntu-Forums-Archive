---
title: "SAMBA File Share Nautilus Bug"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by ieduarte73 on 2009-03-19
Hello,

I am now working on a project to switch M$Win computers to Ubuntu, and everything is going fine, but a SAMBA Share, I have the following line added to my fstab:

\\myserver\share /media/sambashare cifs credentials=/usr/samba/share/credential, noexec 0 0

So I get the filesystem to be mounted, but I can't get Read/Write on the volume through Nautilus, the options Create Directory and Create File are grayed out, and I can't write to it using Nautilus.

If I go to the CLI I can do everything on the share, write, erase, copy, ..., or if I enter the address on Nautilus like this:

\\myserver\share

Then it mounts the share and I can do everything with that share, but I still can't write on the automounted one.

Any ideas

Thanks

---

### Post by bgiannes on 2009-03-19
make sure that the permissions on that folder is set to RW

that folder should be set to 0777

---

### Post by ieduarte73 on 2009-03-19
I did that on the OpenSUSE 10 machine that has the directory, I have changed the directories and all its contained files to 0777 and I still have the same problem.

I think this is some sort of Nautilus bug, because, I have full read-write permissions if I mount the share manually, as opposed to auto mounted through fstab.

---

### Post by ieduarte73 on 2009-03-19
Something else:  I have changed the permissions on the /media/share folder as well.

If I access to this automounted share through the Command Line, I get read-write permissions, it only fails when I browse through the Nautilus.

---

