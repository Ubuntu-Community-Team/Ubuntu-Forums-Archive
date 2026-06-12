---
title: "Windows + Ubuntu Disks Configuration"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by trunks14 on 2007-05-06
Well, i decided to install ubuntu to the HD, but my family still uses Windows XP (I'm 17 :P), so i have two IDE disks, i have Pri Master for Windows and Pri Slave for Ubuntu (no SATA and fancy stuff :( ), well it seemed to work pretty fine, the GRUB bootloader is easy and everything, but then it started to give me some problems, maybe what i thought i knew about jumper settings is actually incorrect, for example, the Ubuntu HD had the jumper set to slave, and the windows drive's was set to master, but it wouldn't recognize the Master HD ¬¬, after some time of configuration changes i put it like this:

-Pri Master with Windows and Jumper set to Master
-Pri Slave with Ubuntu and jumper set to cable select

and it worked, well maybe i'm just stupid but i don't know why it works like this, even more confusing, why did the first configuration seem to work when i installed ubuntu.

Maybe  not so-Ubuntu related but i wish i knew why this happens, also, what possibilities do i have if my family complains about the GRUB menu?

I'll have to buy my own computer soon :lolflag:

(oops i din't notice i posted it in multimedia, could somebody move it please :)?)

---

### Post by doina100 on 2007-05-06
Howdy,

Well first of all it depends on your computer whether it will work properly with cable select.  Usually compaq and HP use cable select.  Most others use jumpers.

If you have 2 drives on one cable then normally they are set to master and slave.  Some drives are set to master with slave present.

If you go to your terminal and man grub it will tell you how to confirm your settings in menu.lst.

Zack

---

### Post by mohnkern on 2007-05-07
Can't answer the problem about the problems of the two drives.

However, I've got a similar issue with the family members not liking the Grub menu.  (We've got three Pc's, and I refuse not to have a dual boot Ubuntu/XP install.

Go to /boot/grub and edit menu.lst

after ## ## End Default Options ##

you'll see entries for each grub item.  each one contains several lines, so just move the Windows XP one to the top.

You can also set the Timeout value at the top.  It defaults to 10 seconds.  (If you don't start to select a boot option in 10 seconds, it boots the one at the top), and you can move it to 5 seconds, or 3 seconds.  I wouldn't make it any less than 5 seconds.


Hope this helps

---

