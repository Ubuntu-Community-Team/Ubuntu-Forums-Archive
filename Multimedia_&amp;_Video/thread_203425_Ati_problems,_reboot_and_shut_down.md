---
title: "Ati problems, reboot and shut down"
date: 2006-06-25
forum: Multimedia &amp; Video
---

### Post by seamoon on 2006-06-25
Hi,

Seems like I'm having some problems with my Ati Radeon 9800 pro card and Ubuntu. When rebooting or shutting down all I get is a black screen, but the computer never actually switches off, forcing me to do a manual reboot. Same thing happens when trying to change screen resolution - black screen.

I've downloaded ATI's latest installer and followed the guide at
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
to install them, step by step, but in the end when running fglrxinfo I'm always greeted with

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

](*,) 

Anyone with a similar ATI-card that has actually got things to work or has had a similar problem with rebooting etc? Can it be something else besides the video drivers causing this?

Someone, pleeeease #-o 

Best regards,

Simon

---

### Post by seamoon on 2006-06-26
No one knows?
So I'm really alone with this problem... This sux. [-(

---

### Post by 3rdalbum on 2006-06-27
[QUOTE=seamoon]No one knows?
So I'm really alone with this problem... This sux. [-([/QUOTE]

You're not alone with this problem. Not only am I having the same problem, but the bug has been reported on Launchpad, and both the X.org devs and ATI are working toward a fix.

I haven't found a workaround yet. I'm also having the same problem when I try to switch to a virtual terminal once logged into a DE. If anyone has found a way to log out or shut down successfully, or a temporary fix, please post!

---

### Post by jkwarras on 2006-06-27
I'm having the same problem. I can't:

- switch to another session: black screen and PC freezes
- shutdown: black screen and PC freezes, so manual shutdown after that.
- logout: it works sometimes, but no more than once. If I enter another session and logout again it goes to a black screen and PC freezes.

BTW, I use fglrx and an ATI x7xxx CPI card. I hope that these problems will get solved soon...

---

### Post by jkwarras on 2006-07-06
Solved :)

See here: [http://ubuntuforums.org/showpost.php?p=1221148&postcount=5](http://ubuntuforums.org/showpost.php?p=1221148&postcount=5)

---

