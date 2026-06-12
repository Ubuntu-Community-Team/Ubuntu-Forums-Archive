---
title: "nvidia fan shutdown"
date: 2005-10-21
forum: Multimedia &amp; Video
---

### Post by crudh on 2005-10-21
Hi

I have a NVIDIA 7800GT and I recently switched from Gentoo to Ubuntu.

In Gentoo my nvidia fan slowed down to such a low speed that I didn't even hear it when GDM was loaded (so does Windows). But in Ubuntu it only slows down for a second when GDM is starting up, then when GDM is loaded it starts going full speed again.

This is very annoying. Anyone know if there are any settings I could change to fix this?

Thanks!

---

### Post by Haku on 2005-11-27
I am also having a problem with my 7800GT's Fan. Second it starts up GDM the fan on the card starts to spin full blast. Shoved my PC into the corner and I can still hear it. Are there any tools out there that can tweak this?

---

### Post by crudh on 2005-11-27
The cvs version of nvclock has support for some 7800-cards. Didn't get it to make much difference myself though.

But I ended up going back to Gentoo and now my card is almost silent again. I guess it's because of something I compiled into the kernel in Gentoo that isn't available in the stock Ubuntu kernel.

---

### Post by Haku on 2005-11-27
It looks like the thermal sensor thinks the card is running too hot, though I highly doubt it is. Maybe the drivers don't know how to read the temp correctly.


Perhaps there are newer drivers out there. I'm still new to Linux so I get lost with this kind of stuff. Seems like I have 7667.

---

### Post by crudh on 2005-11-28
I have 7676 and the thermal monitor works fine. I am not sure about when I was running Ubuntu, but I think mine was broken just as yours.

---

### Post by ngms27 on 2005-11-28
The fan is controlled my bios though you can control via Software aswell.

Its probably due to the CPU load being greater on Ubuntu thus creating more heat...

JonnyT

---

### Post by crudh on 2005-11-28
[QUOTE=ngms27]The fan is controlled my bios though you can control via Software aswell.

Its probably due to the CPU load being greater on Ubuntu thus creating more heat...

JonnyT[/QUOTE]

The CPU load is not greater on Ubuntu. So it's not that. My guess is that Ubuntu lacks something in the built kernel.

---

### Post by Haku on 2005-11-28
I removed all of the old nvidia drivers and downloaded 7676 from nVidia. After installing these the fan problem was fixed and now the card is pretty quiet (same as running Win XP)

Used this thread as a guide. [http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia)

---

### Post by crudh on 2005-11-28
Nice!

---

