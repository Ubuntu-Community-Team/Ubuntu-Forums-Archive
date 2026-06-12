---
title: "[SOLVED] ISO file crashes without error message"
date: 2008-10-18
forum: Multimedia Software
---

### Post by Andy Moon on 2008-10-18
_My computer_

Dell Inspiron 1525n
Ubuntu 8.04 
Kernel Linux 2.6.24-21-generic
Wine 1.0
VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

_The problem_

Im trying to run a video game, designed for Windows. Im trying to run the ISO of the game CD, with Wine 1.0.

Problem is: the only thing I can access is the autorun main window. When I click on "Install" button, the main window closes and nothing happens. I've tried to run the game in a shell :
wine xxx.iso

But same problem. i ve got no error message when the window crashes.

How I mount the ISO image in a shell :
sudo mount -t iso9660 -o loop xxx.iso /media/iso

Thanks for any help,

Andy

---

### Post by cariboo on 2008-10-18
Have you checked here:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

To see if your game actually works in wine?

Jim

---

### Post by Andy Moon on 2008-10-18
Hello Cariboo,

Yes I forgot to mention that I have checked the Wine HQ DB for that game. It says everything should work perfectly out of the box. They just talk about one fix needed :a Windows DLL that must be copied in Windows folder. Ive done that already.

Thanks :)

---

### Post by Andy Moon on 2008-11-09
Hello,

Sorry for the delay in my answering.

The solution for me was to burn the ISO to a CD.

Thanks and long live Open Source

Andy

---

