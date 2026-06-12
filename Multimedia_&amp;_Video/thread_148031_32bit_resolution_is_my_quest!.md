---
title: "32bit resolution is my quest!"
date: 2006-03-21
forum: Multimedia &amp; Video
---

### Post by joeyb on 2006-03-21
I loaded the latest Ubuntu and am loving it. I can not believe the ease and style this baby has.  My only glitch is I can not get my Nvidia Gforce MX 4000 to show me 32bit res. I have windows 2000 as my other OS on the same machine and no problem with true color. I have installed the driver and followed the instructions given in this forum. I can get "nvidia-settings" and the flash screen so I know the driver is working. I have tweaked the .conf file for X11 as mentioned. Do I need to hand write in the resolutions? Have I loaded the wrong driver? I loaded the latest Nvidia had to offer btw.

Thanks in advance!

---

### Post by varunus on 2006-03-21
24 bit color in Linux is the same thing as 32 bit color in Windows; Windows counts the ability to go transparent (the alpha channel) as color bits, I think.  24 bit color *is* true color.

---

### Post by joeyb on 2006-03-21
Thanks. That gives me a better grasp of the problem. In windows the screen looks much crisper and sharp. I'm suspecting then a possible config problem with the monitor settings in Ubuntu and/or Gnome.

---

### Post by bored2k on 2006-03-21
[QUOTE=joeyb]Thanks. That gives me a better grasp of the problem. In windows the screen looks much crisper and sharp. I'm suspecting then a possible config problem with the monitor settings in Ubuntu and/or Gnome.[/QUOTE]
Are you using the same resolution and the same refresh rate on both?

---

### Post by varunus on 2006-03-21
[QUOTE=joeyb]Thanks. That gives me a better grasp of the problem. In windows the screen looks much crisper and sharp. I'm suspecting then a possible config problem with the monitor settings in Ubuntu and/or Gnome.[/QUOTE]

You can control your display sharpness using the "nvidia-settings" command (it will open a GUI to control your graphics card).

Most likely, you just need to configure your fonts differently, however.  A lot of people don't like the linux font antialiasing or DPI settings.  Adjust them through System->Preferences->Font.  Try adjusting the antialiasing, hinting, and DPI settings in the advanced tab.

---

### Post by joeyb on 2006-03-22
A big thanks to all!  Well my problem is solved but in an odd way :)  

I loaded KDE for a lark and it's just perfect! Clear, clean and crisp. In fact it's equal or better than the resolution in Windows 2000 - go figure.  I am major impressed with how easy Ubuntu handles package installs. To have a shiny new desktop in less than an hour and no - I repeat no - hitches is nothing short of amazing! I think I'm in love...

---

