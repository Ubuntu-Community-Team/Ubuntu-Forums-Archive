---
title: "fglrx vs open drivers - informations and temperature control"
date: 2013-04-02
forum: Multimedia Software
---

### Post by Jaoyur on 2013-04-02
Hi,

I have ubuntu 12.04.2 and kde. I have fglrx 13.1 latest drivers. Sometimes I have freezes at starup, it's very annoying, and I discovered it's bug : [http://ati.cchtml.com/show_bug.cgi?id=691](http://ati.cchtml.com/show_bug.cgi?id=691)
So maybe I should remove fglrx proprietary drivers and go back to mesa open drivers. The problem is: when I first tried open drivers my gpu was used to work at 70C° (158 Fahrenheit) instead I have max 39C° (102 Fahrenheit) with flgrx drivers.
I think it's about temperature and fan control. 
If I decide to remove fglrx I want to be sure that I will not have problems, so I'd like to know:
1) Is there a way to have same very good temperatures (like with fglrx drivers) with open drivers?
2) Is there a good updated ppa to have latest open drivers versions in order to keep them updated?
3) At this moment my plymouth works well with fglrx, is there any change I have to do to make it works with open drivers?
4) Last question: do you think it's a good idea to use open drivers?

edit:
My machine specs:
- gpu: msi/ati r6870 hawk
- cpu: i5-2500k sandy bridge
- motherboard: P8P67 PRO

Thanks a lot.

---

### Post by QIII on 2013-04-02
Hello!

Can you tell us a little about your machine's specs?

Thanks.

---

### Post by Jaoyur on 2013-04-02
done.

---

### Post by Jaoyur on 2013-04-04
any help?

---

### Post by Jaoyur on 2013-04-05
I did this:
I have removed fglrx drivers:
```
sudo     apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
```
and after reboot I have kde-plasma desktop crash and the Resolution is 1280x1024 but my maximum right resolution is 1920x1080 and I can't change it in kde settings menu.
I have also removed xorg.conf (it was in a guide)
```
sudo rm /etc/X11/xorg.conf
```
and then I did
```
sudo dpkg-reconfigure xserver-xorg
```

After reboot I have kde plasma-desktop crash every time and the  Resolution is 1280x1024 but my maximum right resolution is 1920x1080 and  I can't change it in kde settings menu.
I also cannot use opengl in kde effects menu.

Same resolution problem with any other desktop (unity 3d/2d and gnome classic).

The output of: glxinfo | grep render
```
direct rendering: Yes
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x301)
    GL_NV_conditional_render, GL_AMD_draw_buffers_blend, 
```

The output of: glxinfo | grep -i opengl:
```
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x301)
OpenGL version string: 2.1 Mesa 9.0
OpenGL shading language version string: 1.20
OpenGL extensions:
```
I have also added ppa "ubuntu-x-swat/x-updates" and upgrade my system, but it did not solve the problem.

here is my Xorg.0.log:
[http://pastebin.com/raw.php?i=mPxeD99w](http://pastebin.com/raw.php?i=mPxeD99w)

How can I solve it? please help

---

### Post by jack_walker on 2013-08-13
[FONT=arial][COLOR=#000000]Hi,

I still have same problem.
Here is the error log from "Developer Information" section of the KDE Crash Assistant:
[/COLOR][[COLOR=#000000]http://pastebin.com/raw.php?i=8stmVCky[/COLOR]]("http://pastebin.com/raw.php?i=8stmVCky")[COLOR=#000000]

I hope you can help me, I also purged virtualbox because I thought the virtualbox's driver was used after uninstalling fgrlx. But I have no fgrlx and the monitor resolution is still low (1280x1024) and it should be 1920x1080 and I still have plasma crash.

[/COLOR][/FONT]This is my xorg.conf: 
[http://pastebin.com/raw.php?i=D6MPUEZv](http://pastebin.com/raw.php?i=D6MPUEZv)

This is my Xorg.0.log:
[http://pastebin.com/raw.php?i=dWDVe03t](http://pastebin.com/raw.php?i=dWDVe03t)


I tried to add these following lines to "Monitor" section.:
```
Modeline     "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
Option          "PreferredMode" "1920x1080_60.00"

```
and the following line to "Display" section:
```
Modes   "1920x1080" "1280x1024" "1024x768"

```
but it didn't solve it.

I also upgraded to 13.04 and have kde 4.10.5.
[FONT=arial][COLOR=#000000]
Thanks[/COLOR][/FONT]

---

