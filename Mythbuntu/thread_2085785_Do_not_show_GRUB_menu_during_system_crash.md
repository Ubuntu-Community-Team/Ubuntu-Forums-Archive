---
title: "Do not show GRUB menu during system crash"
date: 2012-11-19
forum: Mythbuntu
---

### Post by wilsonmak on 2012-11-19
Hi all,

I use Mythbuntu 10.10 for a Video Display Project.
I found that if the system boots up and I accidentally switch off the PC in that moment, the GRUB menu will pop up for the next boot up.

Is there a way to prevent this? It's because I have an application that  does not have a keyboard.  I need to press "Enter" to continue to boot  up the box.  Or other way to continue boot up without pressing "Enter"  key.

Or is it related to grub settings as below.  Any clues?

P.S.  I have already set ALL required parameters = 0?  Any others to set?

/etc/default/grub
====================================================
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash quiet vga=795"

Thanks,
Wilson

---

### Post by nickrout on 2012-11-20
> **wilsonmak said:**
> Hi all,

I use Mythbuntu 10.10 for a Video Display Project.
I found that if the system boots up and I accidentally switch off the PC in that moment, the GRUB menu will pop up for the next boot up.

Is there a way to prevent this? It's because I have an application that  does not have a keyboard.  I need to press "Enter" to continue to boot  up the box.  Or other way to continue boot up without pressing "Enter"  key.

Or is it related to grub settings as below.  Any clues?

P.S.  I have already set ALL required parameters = 0?  Any others to set?

/etc/default/grub
====================================================
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash quiet vga=795"

Thanks,
Wilson

Try changing GRUB_TIMEOUT to 1 - zero may mean "don't timeout at all" - 1 should wait 1 second.

---

### Post by alien878 on 2012-11-20
I think this is what you want:

[https://help.ubuntu.com/community/Grub2#Last_Boot_Failed_or_Boot_into_Recovery_Mode](https://help.ubuntu.com/community/Grub2#Last_Boot_Failed_or_Boot_into_Recovery_Mode)

---

### Post by wilsonmak on 2012-11-21
Great! It works!

Thank you so much, 
Wilson

---

### Post by nickrout on 2012-11-21
> **wilsonmak said:**
> Great! It works!

Thank you so much, 
Wilsonfor future reference could you specify exactly what worked? These forums show up like a rash on google, so knowing what your fix is will help others :)

---

### Post by wilsonmak on 2012-11-23
Yup! 


Edit /etc/grub.d/00_header and change line 241 (this line is in the make_timeout() function)

set timeout=0

GRUB menu won't pop up for the next reboot if boot up is failed.

But another problem comes up....

I simulate the system crash during boot up process.
Now sometimes it shows:

mounting /dev on /root/dev failed
mounting  /sys on /root/sys failed
mounting /proc on /root/proc failed
....
....
(initramfs) _

Please see attached for details.

Yes, I can fix this with a recovery disk + fsck -a /dev/sda1

Actually, I force the system to check disk on every boot and it should fix itself if having errors as I enable autofix as below:

/etc/default/rcS
FSCKFIX=yes

Any clues?  Besides, what else I should set if I want the system to fix file system corruption automatically.

Thanks,
Wilson

---

### Post by alien878 on 2012-11-23
I would suggest you try and avoid accidently shutting down your PC like this.  As you found out, hard power cycles can corrupt the disk.  You are lucky fsck was able to fix it.  Disk journaling has its limits...

Note:  You can't fix this by adding fsck to the boot.... If the disk is corrupt, there is nothing to boot that will run fsck.  Booting from another disk is about the only way to fix it.  Safe mode may work, but it depends on how bad things are corrupt.

---

### Post by wilsonmak on 2012-11-23
Thanks for your suggestion!
Under normal use, I won't try to have a sudden power off.

Actually, it's used for a video display project hanged on the wall in a building that might have sudden power failure (it was happened a few times before).  Unfortunately, there is no UPS.

I know it's hard to prevent this file corruption completely.  At least I like to find a way to automatically fix it if file corruption happens.  
 
Thanks,
Wilson

---

### Post by alien878 on 2012-11-23
Is this a "demo" type system that should always boot to the same state (i.e. doesn't need to save data to disk)?  You might consider putting the system on a live CD and removing the disks all together.  A bit of work, but it will make it a lot more tolerant of abuse.

---

### Post by wilsonmak on 2012-11-23
It needs to save data and update new content.  So I can't use LIVE CD approach - and there is no CD ROM on that box as well.  But it's a good idea.    

Cheers,
Wilson

---

