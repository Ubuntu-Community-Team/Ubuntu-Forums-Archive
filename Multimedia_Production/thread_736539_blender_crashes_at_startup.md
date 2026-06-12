---
title: "blender crashes at startup?"
date: 2008-03-26
forum: Multimedia Production
---

### Post by badfish591 on 2008-03-26
i am running ubuntu 7.10 and blender 2.45, i have installed it through the package manager but it crashes as soon as i run it( screen flashes grey like its about to open for like a millisecond then nothing). when i try and run it from terminal i get this

badfish591@badfish591-desktop:~$ blender
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.5.1.
Checking for installed Python... got it!
Segmentation fault (core dumped)


any help would be awesome, i have only been using linux for about a month. thanks

---

### Post by eye208 on 2008-03-27
If you are using Nvidia or ATI graphics, make sure the display driver is installed properly and direct rendering is enabled.

If you use Compiz, disable it. It doesn't play well with other OpenGL applications.

---

### Post by badfish591 on 2008-03-27
I have a ATI Radeon RV100 QY [Radeon 7000/VE] which is older than crap, but ubuntu won't run the cd, my display is my 26 inch samsung tv, so the only driver i could find on the list is plug 'n' play  lcd, is that my problem? and i dont know how to enable direct rendering. sry for the noob questions

---

### Post by knotenplatzer on 2008-03-30
This appears to bug 123437 ([https://launchpad.net/bugs/123437](https://launchpad.net/bugs/123437))

A workaround appears to be disabling "DRI" (see the bug report).

You may want to subscribe to the bug report, but please don't add a "me too", if you cannot provide more information (e.g. like does it work in Hardy).

Hope that helps.

---

### Post by mahela007 on 2008-03-31
i have the same problem.. Exactly what happens to me.
how do i solve it?
EDIT: I also have an ATI radeon 7500 graphics card. very old... 
        how do i disable compiz?

---

### Post by badfish591 on 2008-04-03
> **knotenplatzer said:**
> This appears to bug 123437 ([https://launchpad.net/bugs/123437](https://launchpad.net/bugs/123437))

A workaround appears to be disabling "DRI" (see the bug report).

You may want to subscribe to the bug report, but please don't add a "me too", if you cannot provide more information (e.g. like does it work in Hardy).

Hope that helps.

i have read this article, but i am having trouble editing the xorg.conf file, from the GUI i don't have the permission to edit it.... which i expected, but when i try and do it through terminal by typing

sudo gedit /etc/x11/xorg.conf 

it opens gedit in a new window but the file is completely blank, i believe it actually says new file on the bottom of the screen, i'm at a loss here because thats the path to the file as far as i know...... what am i doing wrong here?

---

### Post by eye208 on 2008-04-04
> **badfish591 said:**
> sudo gedit /etc/x11/xorg.conf 

it opens gedit in a new window but the file is completely blank, i believe it actually says new file on the bottom of the screen, i'm at a loss here because thats the path to the file as far as i know...... what am i doing wrong here?
Linux filesystems are case-sensitive. The proper name is /etc/X11/xorg.conf. You can also use GEdit's file open dialog instead of passing the name on the command line.

---

### Post by badfish591 on 2008-04-04
Thank you eye208, thats what i get for being a retard, i can now edit the file, unfortunately it does not help, my problem must be one other than the DRI issue in the bug report.
 thank you for the info knotenplatzer unfortunately i believe i am suffering from some other problem.

---

### Post by hessiess on 2008-04-05
if you can, buy a nvidia card

---

### Post by badfish591 on 2008-04-05
yeah switching video cards will be what is gonna have to happen. i assembled the computer from several dead ones, so i would have liked to make it work with what i had, but oh well

---

