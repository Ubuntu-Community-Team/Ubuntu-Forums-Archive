---
title: "USB Install Gone Wrong; Please Help"
date: 2009-02-28
forum: Mythbuntu
---

### Post by ptmuldoon on 2009-02-28
Well, I've been trying to install a Frontend to a USB pendrive, and really hoping I can recover/repair what just happened.

I installed the front end to a USB drive on my Dell laptop.  The install seemed to go fine.  But Now I can't seem to boot back into my normal HD on the laptop.

If I remove the USB stick, grub attempts to load and fail.  I've even made the HD the the first drive to install and it still looks for grub even though I installed to the pendrive.

With the pendrive attached, grub loads, and it will only boot the pendrive.

So how can I boot back into my windows HD on the laptop?

---

### Post by insineratehymn on 2009-02-28
That depends... did you install Ubuntu on your hard drive? If so, what partitioning option did you pick?

---

### Post by ptmuldoon on 2009-02-28
No, I installed to the 4GB pendrive, and not to the HD, specifically to not touch my C: windows drive, as this is a work laptop.

I think I need to somehow repair the MBR, but not sure yet to accomplish it.

---

### Post by insineratehymn on 2009-02-28
Hmm... without an install I can't see it even touching the MBR. You say you went into bios and checked that all of the drive orders were right?

---

### Post by C.S.Cameron on 2009-02-28
This has happened to me installing to flash drive without disabling my internal HDD first.
To fix you need the Windows set up disk.
Once in the recovery console type 'fixmbr'.
It will give you a warning but if you continue things should end up ok. 
If you can't get a set up disk there is a Linux tool that will also fix a windows MBR.
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)
Using this method has also worked for me.

---

### Post by ptmuldoon on 2009-02-28
So I'm learning :(

My real/BIGGER problem now is that since this is a work issued laptop, that the HD is encrypted using pgp desktop encryption.  I've downloaded there recovery cd now, and have started a decrypted of the drive.

Hopefully after it decrypts (which takes hours), I can hopefully repair the mbr.

---

### Post by ptmuldoon on 2009-03-01
Well. I'm back into my laptop, but I still can not seem to get a USB install to go correctly.

On my home machine.  I've disabled my internal HDD's in my BIOS settings, only enabling a CD and USB as the only boot options.

Yet the installer still finds the internal HD and will require the usb pendrive to boot the HD after re-enabling it, even though I've installed mythbuntu to the pendrive.

So what would be the proper steps short of physically removing the Internal HDD's to install to an external drive?

---

### Post by ptmuldoon on 2009-03-03
Sorry for a minor bump...

But I may give this another shot tonight, and would really like to a frontend installed to a USB pendrive to be able to boot from various machines for testing purposes.

I've disabled the IHDD's in my Bios.  But when running the installion, the installer still finds and installs Grub on to the IHDD's.    Do you really need to physically disable/remove the IHDD to install to pendrive?

---

