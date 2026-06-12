---
title: "Installing NVIDIA graphics card"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by kaiser84 on 2007-12-25
I am running Ubuntu 7.10 for a 64-bit AMD processor.  For Christmas, I got a NVIDIA GeForce PCI-express graphics card.  I popped the graphics card in, and then powered on the computer.  The computer went through the normal startup.  Then, right before Ubuntu usually starts up and asks for a login, the screen goes blank and the monitor goes into power saving mode.  

How do I make it so that Ubuntu runs with the new graphics card?

I am new to Ubuntu, and this is my first post on the forum.  If my question is really easy, please don't make fun of me.  

Thanks.

---

### Post by taurus on 2007-12-25
Boot into recovery mode from GRUB menu and reconfigure your X server again for the new card.

```
dpkg-reconfigure -phigh xserver-xorg
```
Then, you can reboot with

```
shutdown -r now
```

---

### Post by evensteven69 on 2008-04-06
Yes, this solved it for me.

---

### Post by fjf on 2008-04-06
Or download envy:  [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

