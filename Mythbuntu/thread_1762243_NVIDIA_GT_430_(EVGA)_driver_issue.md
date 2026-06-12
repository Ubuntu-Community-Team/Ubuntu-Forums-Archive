---
title: "NVIDIA GT 430 (EVGA) driver issue"
date: 2011-05-18
forum: Mythbuntu
---

### Post by davidstoll on 2011-05-18
I can't seem to get this card to boot to X when using the Nvidia current drivers.  I think it's my xorg.conf, but I can't get into X to tweak it.  I always have to SSH in and revert to the failsafe version.

nvidia-xconfig
doesn't seem to work.  It creates a new xorg.conf, but I still can't fully boot into X.  I do see the login flash for a second, but that's about it.

Can someone please post an xorg.conf that would work or give me a hint as to how to get this thing running?

I'm running Mythbuntu 10.04 32bit.

I can download the Nvidia drivers right from the Nvidia site, but I don't know how to get to a command prompt without the .run file thinking that X is running.  It tells me I have to exit all X sessions.  But I can't use ctrl+alt+f1 because X isn't loaded...I can only ssh into this partially X booted machine.

Thanks so much.

---

### Post by ian dobson on 2011-05-20
Hi,

I think you can stop the X Server with:-

sudo stop gdm

or just rename /etc/init/gdm.conf to /etc/init/gdm.conf.sav and then reboot. The gdm.conf file starts the X interface so renaming the file should stop X starting on boot.


Regards
Ian Dobson

---

### Post by davidstoll on 2011-05-20
Hi, thanks for the info, but I just can't get my xorg.conf configured so X will boot correctly.

Somehow I have another thread going.  My browser crashed on my first post, so I didn't think it went through, so I posted again...oops.

Anyway, I don't suppose you might be able to jump over here and give me any thoughts...?

[http://ubuntuforums.org/showthread.php?p=10840608#post10840608](http://ubuntuforums.org/showthread.php?p=10840608#post10840608)



> **ian dobson said:**
> Hi,

I think you can stop the X Server with:-

sudo stop gdm

or just rename /etc/init/gdm.conf to /etc/init/gdm.conf.sav and then reboot. The gdm.conf file starts the X interface so renaming the file should stop X starting on boot.


Regards
Ian Dobson

---

