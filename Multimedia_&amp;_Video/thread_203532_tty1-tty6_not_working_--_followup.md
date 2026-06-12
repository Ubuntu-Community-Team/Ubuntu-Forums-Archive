---
title: "tty1-tty6 not working -- followup"
date: 2006-06-25
forum: Multimedia &amp; Video
---

### Post by brunets on 2006-06-25
Hi,

During the development of Dapper, there was a thread about X11 messing with ttys which appeared blank after X11 startup :

[http://www.ubuntuforums.org/showthread.php?t=160006]("http://www.ubuntuforums.org/showthread.php?t=160006")

(This forum is now closed so noone can't post there anymore, that's why this message)

Quickly, my config is :
[LIST]
[*]Asus Z71V laptop (Centrino + Nvidia Go 6600)
[*]Ubuntu 6.06
[*]Linux kernel 2.6.15-25-686
[*]Nvidia proprietary drivers 8762
[/LIST]

When the blank tty problem occured, the video configuration was :
[LIST]
[*]vga16 framebuffer on the ttys
[*]nvidia 8762 driver on X11
[/LIST]

I figured out that :
[LIST]
[*]The nvidia driver ("nvidia" in xorg.conf) prevents the ttys from working properly when they are configured with "vga16fb" framebuffer.
[*]When switching X11 configuration to using "nv" driver, everything works properly.
[*]Configuring the console to use "vesafb" rather than "vga16fb" makes the nvidia proprietary driver (and the Ubuntu user) happy.
[/LIST]

Therefore, in order to make it work properly I just add the following parameters in my grub configuration (/boot/grub/menu.lst) :
```
video=vesafb vga=0x318 
```

This makes my console work in 1024x768 24bit VESA mode.

I hope this can help other Ubuntu users...

Stéphane

---

