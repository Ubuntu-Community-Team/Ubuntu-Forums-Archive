---
title: "Samba help"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by jgpcexpert on 2009-05-13
Ok, I don't consider myself a noob anymore but I am having Samba issues. I've got an XP machine and an Ubuntu 9.04 machine and my wife has an Ubuntu 8.04 machine. My XP mahcine has a printer hooked up to it that I want to use and a ton of files I would like to share on the other machines. I can get the XP machine to recognize that the other 2 machines are on my home network but I cannot get them to actually share. I do have file sharing turned on and have created shared folders on all machines. I also have Samba installed on both Ubuntu machines. From my Ubuntu machine, I can get it to see the Windows network but I cannot get it to see the XP machine.
 
Any suggestions would be greatly appreciated. Also, I know I have stumbled accross this before but I have forgotten how, but how to you change the workgroup name in Ubuntu?

---

### Post by superprash2003 on 2009-05-13
when you try to add the printer and when you need to enter the location , type its full address link , like x.x.x.x/printername instead of searching for it,
for reference : [http://www.prash-babu.com/2008/07/how-to-connect-to-network-printer-in.html](http://www.prash-babu.com/2008/07/how-to-connect-to-network-printer-in.html)

---

### Post by Iowan on 2009-05-13
> **jgpcexpert said:**
>  From my Ubuntu machine, I can get it to see the Windows network but I cannot get it to see the XP machine.You *might* need to install Winbind and edit /etc/nsswitch.conf by adding "wins" just before "dns" on the "hosts:" line.

---

