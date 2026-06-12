---
title: "Windows 7 and Ubuntu 10.04 networking"
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by ImageJPEG on 2010-10-03
I'm trying to get my Ubuntu computer to connect my Windows 7 shares. I do have Samba installed and it can "see" my Windows 7 computer...however, I cannot connect to the machine.

I think I've heard some issues with the way how Windows 7 deals with networking now and Samba doesn't work with Windows 7 now or something???

If possible, I can always use an NFS server and client for my Windows 7 computer.

---

### Post by ImageJPEG on 2010-10-03
Anybody?

---

### Post by spiky001 on 2010-10-03
Have a look through here [http://www.tomshardware.com/forum/75-63-windows-samba-issue](http://www.tomshardware.com/forum/75-63-windows-samba-issue)

---

### Post by country0129 on 2010-12-29
I'm having a similar problem in accessing the shares from an Ubuntu machine to Windows 7 Pro. I can access the shares Windows >>>======> Ubuntu but not in reverse. It keeps repeating a log in credential screen and won't allow access in reverse. I had Windows Live Essentials, and, when I uninstalled them, everything worked well. BUT, my wife thinks this is HER computer, and she insisted that I install them again. Hence the problem. Does anyone know of a workaround that will allow me to connect to the Windows machine from Ubuntu, keeping WLE?

---

### Post by PatchesTheCaveman on 2010-12-29
Windows Live Essentials make a small change in the way Windows 7 communicates via SMB that breaks the current version of Samba in Ubuntu.  This is a known bug in Samba that has been fixed upstream but not yet in the version Ubuntu ships.  Unless you know how to build the official Samba from source you'll have to wait until Canonical updates their version.

---

### Post by PatchesTheCaveman on 2010-12-29
Actually I might have jumped the gun on that one.

From what I can see from other threads, you should be able to uninstall the Windows Live Sign-In Assistant portion of Windows Live Essentials without uninstalling the rest of the package and that will fix this problem.

---

