---
title: "Can I run Samba (music files) without logging into Ubuntu first?"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by infocom on 2008-12-23
I have setup Samba and use SWAT to configure the shares. I have a USB hard drive on Ubuntu with all my Music, and my XP and Xbox machine's music library is set to this. All works OK. 

Except I need to login in to Ubuntu as my user before XP and Xbox can access the directory. Does anyone know how to fix this?

Thanks

P.S. This is because I want the directory accessible without logging into Ubuntu. This is because my machine is tucked away in another room and I have it to shutdown and start up automaticaly, so its only on in the day, and shuts down at night, and I dont have to do anything with it, except now I have to login which spoils the whole thing.

---

### Post by andguent on 2008-12-23
When you say "log in", I assume you mean a GUI/Gnome login. Is this correct?

Try the following for me so we can get a better picture of what you have going on.
* Do a Ctrl-Alt-F1 to get a text login (Note: Ctrl-Alt-F7 should get you back to the GUI). Can you post the output of the **mount** command before and after logging in to the GUI? We want to compare the differences, as I assume something Gnome related is auto detecting your external drive.
** Note: Try a **mount >> /tmp/mymountouput.txt** to save it so you don't have to type the whole thing manually. See that text file for output.

* Also, can we have the output of the following:
** **fdisk -l** (that is a lowercase letter L, not a numeral one)
** **testparm**
** **cat /etc/fstab**

---

### Post by superprash2003 on 2008-12-23
you would need to mount those 2 drives automatically by placing them into your fstab file..

---

