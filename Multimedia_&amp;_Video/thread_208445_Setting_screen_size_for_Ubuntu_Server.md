---
title: "Setting screen size for Ubuntu Server"
date: 2006-07-03
forum: Multimedia &amp; Video
---

### Post by wuhaa on 2006-07-03
Hi,

I just installed Ubuntu Server 6.06. I would like to make the size of the screen bigger (text is comming up cluttered) There is no x installed on this (*server).
Please help.


Thank you :)

---

### Post by Ctrl+Alt+Del on 2006-07-03
What you are looking for is a framebuffer. in order to get for example 1024x768 you will have to add the statement vga=791 to your /boot/grub/menu.lst.
It should look like: kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/sda2 ro vga=791 quiet splash

But be aware of the fact that is might break hybernation if you use it.

---

