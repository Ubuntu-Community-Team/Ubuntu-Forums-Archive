---
title: "Network Issues"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by Liliitha on 2008-12-18
I recently uploaded my old Gutsy Gibbon to Hardy Heron.  In Gusty Gibbon I could get my internet working by typing sudo modprobe ndiswrapper in the terminal.  That worked fine, althought I had to do it everytime I turned on the computer.  Now I type it in, and it doesn't work.  In the modules folder, under lib there is no ndiswrapper in there anymore.  I have ndiswrapper on my desktop.  I went to put it into the modules folder but it said I do not have access even though it is on the main administrative account.  Any fixes for this?

---

### Post by Iowan on 2008-12-18
I presume somehow you'll need to "sudo" it - either by operating from CLI, or  ???.  I haven't yet made the jump from Gutsy.

---

### Post by Liliitha on 2008-12-18
> **Iowan said:**
> I presume somehow you'll need to "sudo" it - either by operating from CLI, or  ???.  I haven't yet made the jump from Gutsy.

Yeah, I would assume something with sudo in terminal as it seems I am completely unable to transfer the file to lib/mod.  Any other ideas?

---

### Post by Liliitha on 2008-12-18
Well I have no idea how to unlock the file systems...  I cannot transfer files to the computer at all.  Any ideas on how to unlock the "locked" main files would be **greatly** appreciated.

---

### Post by Liliitha on 2008-12-18
I recently uploaded my old Gutsy Gibbon to Hardy Heron. In Gusty Gibbon I could get my internet working by typing sudo modprobe ndiswrapper in the terminal. That worked fine, althought I had to do it everytime I turned on the computer. Now I type it in, and it doesn't work. In the modules folder, under lib there is no ndiswrapper in there anymore. I have ndiswrapper on my desktop. I went to put it into the modules folder but it said I do not have access even though it is on the main administrative account. Any fixes for this?

---

### Post by albinootje on 2008-12-18
> **Liliitha said:**
> I recently uploaded my old Gutsy Gibbon to Hardy Heron.  In Gusty Gibbon I could get my internet working by typing sudo modprobe ndiswrapper in the terminal.  That worked fine, althought I had to do it everytime I turned on the computer.  Now I type it in, and it doesn't work.  In the modules folder, under lib there is no ndiswrapper in there anymore.  I have ndiswrapper on my desktop.  I went to put it into the modules folder but it said I do not have access even though it is on the main administrative account.  Any fixes for this?

Ndiswrapper depends on a kernel-module. That has to be loaded properly.
Can you post the output of :
```

lsmod|grep ndiswrapper
ndiswrapper -l
lspci

```
It's also possible that you need to download firmware.

---

### Post by superprash2003 on 2008-12-19
is it a broadcom?

---

### Post by Liliitha on 2008-12-20
> **superprash2003 said:**
> is it a broadcom?

Yeah it was a Broadcom.  It read the Linksys router but it did not use it.  The network manager said it was locked, I unlock it and the internet still doesn't work.  Then I go back to the network manager and it unchecked the Linksys box again and locked it once more.  I say "was" because I formatted my hard drive.  I downloaded the newer version of Ubuntu and wish to start from scratch, I think the first disk I used to install Ubuntu was damaged as some of the important files were missing.

---

### Post by superprash2003 on 2008-12-21
have you tried sys->admin->hardware drivers? [http://prash-babu.blogspot.com/2008/11/how-to-configure-broadcom-wireless-in.html](http://prash-babu.blogspot.com/2008/11/how-to-configure-broadcom-wireless-in.html)

---

