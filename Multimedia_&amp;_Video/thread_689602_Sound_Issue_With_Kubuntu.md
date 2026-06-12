---
title: "Sound Issue With Kubuntu"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by nullfactor on 2008-02-06
I have the Intel HD (ICH7) chipset that seems to give just about everybody a hard time, from time to time.  I was able to overcome the sound issue by disabling acpi when Gnome was my default windows manager.

I wanted to give KDE a try, so I switched over to Kubuntu... truthfully, I like KDE a ton better... it just FEELS better.  The problem is, if I boot with ACPI on, everything works fine... except, of course, my sound.  So, I disabled ACPI.  When I did and tried to boot into KDE, the furthers I could get was a single-user command line.  When I attempt to start X, at that point, it boots to single-user mode and then locks up.

Any ideas with this?

If you need more info, let me know.  Thanks.

---

### Post by nullfactor on 2008-02-06
Never mind... I figured it out.

I usually disable ACPI by editing the kernel when booting.  Instead, I just edited the /grub/boot/menu.lst file and tacked ACPI=off to the end of the kernel within the file.

It worked.

---

