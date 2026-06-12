---
title: "Kernal panic trying boot from install iso"
date: 2012-09-04
forum: Mythbuntu
---

### Post by emedlin18 on 2012-09-04
I have a P4 on an 845g MB running 10.04.  I wanted to start fresh, so I download mythbuntu-12.04.1-desktop-i386.iso and used the startup disk creator to make a bootable usb from the image.  But I get the following when I try to boot from it.  I have tried two different usb drives and checked the md5sum of the iso.  I really don't know what else to check or do.

kernal panic - not syncing: VFS: Unable to mount root fs on unknown-block(2,0)
Pid: 1, comm: swapper/0 Not tainted 3.2.0-29-generic-pae #46-Ubuntu
Then a call trace that I can give if needed.

---

### Post by nickrout on 2012-09-04
> **emedlin18 said:**
> I have a P4 on an 845g MB running 10.04.  I wanted to start fresh, so I download mythbuntu-12.04.1-desktop-i386.iso and used the startup disk creator to make a bootable usb from the image.  But I get the following when I try to boot from it.  I have tried two different usb drives and checked the md5sum of the iso.  I really don't know what else to check or do.

kernal panic - not syncing: VFS: Unable to mount root fs on unknown-block(2,0)
Pid: 1, comm: swapper/0 Not tainted 3.2.0-29-generic-pae #46-Ubuntu
Then a call trace that I can give if needed.

try a different USB stick, some are better at booting than others.

Or put it on a CD and boot from that.

---

### Post by emedlin18 on 2012-09-04
> **nickrout said:**
> try a different USB stick, some are better at booting than others.

Or put it on a CD and boot from that.

I have tried two different usb sticks already, both produce the same kernal panic.  The computer doesn't have a cdrom in it.

---

### Post by nickrout on 2012-09-05
> **emedlin18 said:**
> I have tried two different usb sticks already, both produce the same kernal panic.  The computer doesn't have a cdrom in it.

I use an external CDROM if I get to that point.

---

### Post by Rotak on 2012-09-05
Maybe also try another software to create the boot system on the USB stick. (e.g. UNetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/))

---

### Post by emedlin18 on 2012-09-05
> **nickrout said:**
> I use an external CDROM if I get to that point.

Don't have an external either.

---

### Post by emedlin18 on 2012-09-05
> **Rotak said:**
> Maybe also try another software to create the boot system on the USB stick. (e.g. UNetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/))

I did try LinuxLive USB Creator on Windows 7, but the usb that it created would just hang at the "syslinux 4.04 chs" copyright line.  I assume syslinux 4.04 has a problem as I can get further now and it uses syslinux 3.73 or atleast 3 point something.  I don't really remember the exact version it is using now.  I can try UNetbootin, but after trying two programs already I don't have much faith in it working.

Why do different usb creators create different results, but if you burn the iso to a disk it is always the same no matter what burning software you use?  Can you not just "burn" the iso to a usb stick, so the file layout is the same as what would be if you burned it to a disk.

---

### Post by Rotak on 2012-09-05
Well, I suppose the problem is mostly the USB stick, resp. to make it bootable. Reading the ISO is always the same job, though. I also experienced, that some programs failed to create bootable images on USB sticks. Therefore, the only solution is to try different software... And if that doesn't help, try different USB sticks.

---

### Post by emedlin18 on 2012-09-05
Already tried a different usb drive, no luck.

---

### Post by emedlin18 on 2012-09-06
I used gparted to recreated the partition on the usb drive and used UNetbootin to create the bootable usb drive.  That worked.  It appeared to install mythbuntu on my larger faster thumb drive (poor mans SSD).  Although it did give an error at the end about not reinstalling some rpms that it had removed.  Also when I tied to boot off of it, it gave me a geom error.  I am going to do the reinstall again with my internal HD's disabled in bios to see if that helps any.  If I still have a problem I will be making a new post related to that problem.  Thanks for the help.

I really don't see why different boot usb creators produce different files on the usb drive, but cd's will always have the same files.

---

