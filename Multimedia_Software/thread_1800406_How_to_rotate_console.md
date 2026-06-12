---
title: "How to rotate console?"
date: 2011-07-08
forum: Multimedia Software
---

### Post by Luke M on 2011-07-08
ubuntu 11.04

How do you rotate the console?

---

### Post by SeijiSensei on 2011-07-09
If you mean you want to rotate the image on your monitor, and you're using a graphical desktop environment like GNOME or KDE, you can use the **xrandr** utility.  Type "man xrandr" at a terminal prompt for more details.

KDE has a little utility called krandrtray you can install from the repositories for this purpose.  I don't know about GNOME, or Unity for that matter.  However xrandr should work regardless since it addresses the underlying X server on which the desktop environment is built.

---

### Post by Luke M on 2011-07-09
Hit control-alt-F1. The console does not go through xwindows. Yes, I want to rotate the image.

---

### Post by haqking on 2011-07-09
what do you mean rotate the console ?

you want to flip the terminal console upside down you mean ?

---

### Post by Luke M on 2011-07-09
Rotate 90 degrees. Ever seen an LCD monitor before? :-)

---

### Post by haqking on 2011-07-09
> **Luke M said:**
> Rotate 90 degrees. Ever seen an LCD monitor before? :-)


i have seen plenty of LCD monitors before, what has that got do with it, i am using a LCD right now.

are you referring to the aspect ratio ?

it is not clear

---

### Post by Luke M on 2011-07-09
What is not clear? Rotate your monitor 90 degrees and you have a (for example) 1080x1920 display instead of 1920x1080.

---

### Post by haqking on 2011-07-09
> **Luke M said:**
> What is not clear? Rotate your monitor 90 degrees and you have a (for example) 1080x1920 display instead of 1920x1080.

so to be clear, you wish to change the resolution and/or aspect ratio of your console display ?

if that is the case whichs is different terms to rotating it, then you need to edit the /boot/grub/menu.lst and change the vga mode

---

### Post by Luke M on 2011-07-09
No, I want to rotate. Rotate. Rotate. Rotate!

I don't know any monitors that can change resolutions. The image has be rotated at the source.

---

### Post by SeijiSensei on 2011-07-09
Looks like you have to pass a parameter to the kernel at boot:

[http://www.mjmwired.net/kernel/Documentation/fb/fbcon.txt](http://www.mjmwired.net/kernel/Documentation/fb/fbcon.txt)

---

### Post by Luke M on 2011-07-09
Tried that, doesn't work. I think I need to recompile the kernel but I thought I would ask first...

---

### Post by Luke M on 2011-07-11
Looking in /boot/config-2.6.38-8-generic, I see:

# CONFIG_FRAMEBUFFER_CONSOLE_ROTATION is not set

So I guess that is the problem. ubuntu is compiled with the ability to rotate disabled.

---

### Post by Luke M on 2011-07-13
I recompiled the kernel following the instructions here:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

and it worked.

---

