---
title: "Ubuntu wont finish loading with my graphics card installed... Help"
date: 2009-07-30
forum: Multimedia Software
---

### Post by cuzimjoesmith on 2009-07-30
ok i have a dual boot with xp and ubuntu. everything works fine when i use the onboard graphics and the vga connected to that.
 
but when i install my graphics card ( which is - Nvidia Geforce 8400 GS 512 mb PCI) it doesnt work. when ubuntu gets to the loading screen it gets to about 20% then i get this :
 
unable to execute "/sbin/getty" for tty3: stale NFS file hande.
 
-joe-

---

### Post by cuzimjoesmith on 2009-07-30
Come on someone please help!

---

### Post by cuzimjoesmith on 2009-07-30
Help!!!!!

---

### Post by steefjeqv on 2009-07-31
Hi ,

If you're able to boot in recovery mode (text mode), then try the following command :

sudo dpkg-reconfigure -phigh xserver-xorg

This allows you to reconfigure you X server (graphics, keyboard, mouse,...).

Greetings,
Steven

---

