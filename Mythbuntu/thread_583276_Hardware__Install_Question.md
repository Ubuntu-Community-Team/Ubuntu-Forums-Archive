---
title: "Hardware / Install Question"
date: 2007-10-20
forum: Mythbuntu
---

### Post by mljohns4 on 2007-10-20
My current mythtv box is a 2.66 Ghz Intel Core 2 Duo with a P35 Bearlake chipset. I have been successfully running Gentoo's AMD64 arch on this setup, and was wondering if it is possible to do the same with Mythbuntu, that is, run the AMD64 arch of Mythbuntu. I recently downloaded the Mythbuntu AMD64.iso and attempted to perform an install, but I'm only able to get to point where the installer is attempting to load Linux (ie.. Decompressing Linux) during the boat process. At that point my monitor goes into powersave mode and there is no harddrive activity. Any comments or advice regarding this issue?

Thanks
Mike Johnson

---

### Post by superm1 on 2007-10-20
APIC, ACPI and friends.  Try turning them off on the CD boot paramaters.

---

### Post by mljohns4 on 2007-10-20
So why would I have to pass such parameters to my kernel at boot in order to disable ACPI during an Install? I'm not even sure the install process is able to get to the point of loading ACPI modules. The installer literally displays on the screen "Kernel Alive" and then shortly thereafter "Decompressing Linux" and thats it, nothing more.... Hopefully I'm not coming across as being an "a$$", but I just want to make sure that I have described it correctly..

Mike

---

### Post by superm1 on 2007-10-20
This is just what i've seen some guys have to do with buggy acpi implementations to get things to boot.  If you search for a few other threads, they have reported similar issues that the bootup just seems to hang there.

I wish there was a cleaner solution :(


Also, a bit more low tech, but have you done a disk check?  The disk can check its integrity from that boot menu.

---

### Post by apauna on 2007-10-21
The disk thing caused me problems the first time I burned Mythbuntu RC. Created a new disk and it installed great!

---

