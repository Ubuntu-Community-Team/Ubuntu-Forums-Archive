---
title: "Mythbuntu 14.04.1  i386 ISO has 64bit kernel"
date: 2014-10-16
forum: Mythbuntu
---

### Post by derekdjohnson on 2014-10-16
I downloaded mythbuntu-14.04.1-desktop-i386.iso burned it to a usb drive, but when booting I am getting a, "This kernel requires an x86-64 CPU, but only detected an i686 CPU. Unable to boot – please use a kernel appropriate for your CPU".  I downloaded it twice to make sure I selected the right one.  I am trying to install the 32bit version on a 32bit Pentium 4 system. Has anyone else installed the i386 iso?

---

### Post by tgm4883 on 2014-10-16
> **derekdjohnson said:**
> I downloaded mythbuntu-14.04.1-desktop-i386.iso burned it to a usb drive, but when booting I am getting a, "This kernel requires an x86-64 CPU, but only detected an i686 CPU. Unable to boot – please use a kernel appropriate for your CPU".  I downloaded it twice to make sure I selected the right one.  I am trying to install the 32bit version on a 32bit Pentium 4 system. Has anyone else installed the i386 iso?

I just tested the 32-bit ISO in a 32-bit virtualbox and did not get that error. Can you verify the MD5SUM of the ISO you downloaded?

---

### Post by derekdjohnson on 2014-10-16
> **tgm4883 said:**
> I just tested the 32-bit ISO in a 32-bit virtualbox and did not get that error. Can you verify the MD5SUM of the ISO you downloaded?

It's correct.  96022518d85210af1dda91f8480ef75d

Now I did create the bootable flash drive on a 64bit Ubuntu 12.04 system using "Startup disk creator".  I'm not sure what it is doing.  Maybe it is using my local 64bit files for making the boot disk.  Maybe the report is coming from grub.  I don't know.  I'll try burning it to a CD tonight and give it another go.

---

### Post by derekdjohnson on 2014-10-16
That appears to have been it.  I burned it to a DVD and installed without issue.

---

