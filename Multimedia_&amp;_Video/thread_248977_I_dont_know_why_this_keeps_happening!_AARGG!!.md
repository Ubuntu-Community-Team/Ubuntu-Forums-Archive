---
title: "I dont know why this keeps happening! AARGG!!"
date: 2006-09-01
forum: Multimedia &amp; Video
---

### Post by solarwind on 2006-09-01
I installed Dapper, properly installed the fglrx drivers for my ati card (the drivers work, that is confirmed), but after i installed the fglrx drivers, KDE loses the ability to keep icons aligned. In the right click menu, i selected "keep icons aligned", but they are not aligning! I am able to freely move them about, and they wont lock to grid! 

I then reinstalled Dapper and again installed the fglrx drivers, and the same thing happened. The icons are not locking to grid and I am able to freely move them around. This has happend for each install of dapper.

Help!

Thanks in advance!

---

### Post by solarwind on 2006-09-01
Note: I am using a Dell Inspiron 6000 Laptop with intergrated ATI Radeon x300 mobility pci x16 graphics.

---

### Post by solarwind on 2006-09-02
Ok. I searched around and this is a bug in KDE. The details can be found here:

[http://bugs.kde.org/show_bug.cgi?id=114766](http://bugs.kde.org/show_bug.cgi?id=114766)


My issue was solved (along with many others) by simply deleting:

/home/username/.kde/share/config/kickerrc

Then simiply reboot (or log out and log back in) and the icons will align to grid again.

Note: You will lose settings your settings in the kicker so you will have to reconfigure your panel size, what icons were there in the quicklaunch, and so on.

I think someone should sticky this.

---

