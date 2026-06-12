---
title: "Any solution to no sound on VT1708/A Azalia HDAC?"
date: 2011-04-09
forum: Multimedia Software
---

### Post by ventrikolo on 2011-04-09
Here's my ALSA-log
[http://www.alsa-project.org/db/?f=66d25fcbe12a29b205f7dfb13f6ed659a46d64f0](http://www.alsa-project.org/db/?f=66d25fcbe12a29b205f7dfb13f6ed659a46d64f0)

Been googling around for ages not finding any working solution for my problem.
Installed Ubuntu 10.10 and I have no sound. I have a integrated soundcard by the name of VT1708/A Azalia HDAC and a lot of people seemed to experienced no sound with the same card. But I never found a solution so now my question goes out to anyone here in the forum. Does anyone have a solution? I need sound on my computer and Ubuntu is freakin' awesome I don't want to switch back for this reason

---

### Post by Yellow Pasque on 2011-04-09
[https://bugzilla.kernel.org/show_bug.cgi?id=16921#c5](https://bugzilla.kernel.org/show_bug.cgi?id=16921#c5)

---

### Post by ventrikolo on 2011-04-09
didn't work either... maby i'm doing it wrong in GRUB?

---

### Post by lidex on 2011-04-10
Pts was dealing with an ioremap error here:
[http://ubuntuforums.org/showthread.php?t=1593095&page=3](http://ubuntuforums.org/showthread.php?t=1593095&page=3)
The 2.6.35.xx kernels seem problematic for some.

As for your grub edit, did you put the changes in /etc/default/grub
and run the update-grub command?

---

