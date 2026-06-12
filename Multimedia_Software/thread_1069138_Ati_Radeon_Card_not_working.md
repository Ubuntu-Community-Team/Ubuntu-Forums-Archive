---
title: "Ati Radeon Card not working"
date: 2009-02-13
forum: Multimedia Software
---

### Post by Aziris on 2009-02-13
This is my first post, so sorry if its been covered or i sound stupid.
I used to run ubuntu on my laptop but recently built a desktop and wanted to install ubuntu on that. My problem, i think, is with my graphics card which is an ATI Radeon HD 3450 sapphire, the problem is when my computer is loading ubuntu (live cd or Wubi) it gets toward the end and then my monitor says 'not support'. I tried googling for a reason and found someone had the same card and similar problems, they enabled the on board graphics in bios and then installed the restricted drivers for the card inside ubuntu. I tried this but when it loaded up ubuntu using the on board graphics it said 'out of range' and then just sat there.
I really would like to install ubuntu, mainly because i enjoyed it last time and found the whole community really helpful. So if you can help i would really appreciate it, thanks.

---

### Post by steefjeqv on 2009-02-14
Hi,

You can try installing Ubuntu by using the alternate install cd.

After installing, X may not start. But you should be able to login in text mode.
If this is the case, try the following :

sudo dpkg-reconfigure -phigh xserver-xorg

Then edit the xorg.conf you've just created :

sudo nano /etc/X11/xorg.conf

add the following line in the "Device Section" :

Driver "vesa"

This should get you into your graphical desktop.
Vesa is a basic driver which will give you no features. From here, you'll have to install fglrx (the ATI closed source driver), or you can try the radeonhd driver (open source).
 
Greetings,
Steven

---

### Post by batty on 2009-02-14
Hi,

I had to boot Live CD, on the first screen select F4 and choose safe graphic mode.
This lets the Live CD work.I could then install OK, and enabled the ATI driver once Ubuntu was installed.

Dave

---

### Post by steefjeqv on 2009-02-14
Hi Dave,

Great to see your ATI setup working.

F4 starts the live CD with the VESA graphics driver. Why didn't I think of that ?!

Greetings,
Steven

---

### Post by Aziris on 2009-02-14
Cheers for the suggestions I'll try them out when I get back to my computer and let you know if they worked.

---

### Post by Aziris on 2009-02-14
Thank you so much everyone. Finally i managed to install Ubuntu and just in time by the looks, having partitioned and installed ubuntu i tried booting into windows to transfer some files over for the permanent move. Of course Vista dies on me and i couldn't boot or read the data, but hey i have ubuntu on my computer, so i couldn't be happier.
Again though thanks so much, you guys are legends, true Gods on earth.

---

