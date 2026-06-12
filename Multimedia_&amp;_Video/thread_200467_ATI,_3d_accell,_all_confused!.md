---
title: "ATI, 3d accell, all confused!"
date: 2006-06-20
forum: Multimedia &amp; Video
---

### Post by bohboh on 2006-06-20
I have an ATI Radeon 9200 PRO graphics card.

It works fine, but i have read in many places that i need to install drivers to get 3d acceleration to work. Is that true?

1. How can i find out if 3d acceleration is enabled?
2. Is there a tutorial amongst all of them that will point me in the right direction as to how to install drivers for my specific graphics card.
3. What benefits will i see?

Please help, the more i read the less i know. :lol:

---

### Post by xXx 0wn3d xXx on 2006-06-20
To find out if fglrx accel. is enabled do the following in terminal:
> fglrxinfo
This should not say Mesa if it does fglrx is not enabled.
> glxgears -printfps
You should get 500+ fps with this command.

Now how to fix it...follow [ this tutorial ](http://ubuntuforums.org/showthread.php?t=143283&highlight=fixing+mesa+issue) to make it work.

The benefits include:
Better framerates and better looking applications
Applications might start and feel faster
Movies and graphically intense games/apps will run + look better

---

### Post by bohboh on 2006-06-20
[QUOTE=xXx 0wn3d xXx]To find out if fglrx accel. is enabled do the following in terminal:

This should not say Mesa if it does fglrx is not enabled.

You should get 500+ fps with this command.

Now how to fix it...follow [ this tutorial ](http://ubuntuforums.org/showthread.php?t=143283&highlight=fixing+mesa+issue) to make it work.

The benefits include:
Better framerates and better looking applications
Applications might start and feel faster
Movies and graphically intense games/apps will run + look better[/QUOTE]

You absolute :KS 

That has made it so much simpler, gonna give it a whirl now!

---

### Post by bohboh on 2006-06-20
fglrx returned:
```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

Which means i dont have it installed. So i assume that "glxgears -printfps" will only return 500fps when i do have fglrx installed?

---

### Post by Galban on 2006-06-20
[QUOTE=bohboh]fglrx returned:
```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

Which means i dont have it installed. So i assume that "glxgears -printfps" will only return 500fps when i do have fglrx installed?[/QUOTE]

I'm sorry to tell you that, you dont have 3D acceleration [-X , and even after you install xorg-driver-fglrx you will very probably get Mesa or API's errors doing fglrxinfo. You have to get rip of the Mesa's libGL version present in your /usr/lib/ that looks like  "libGL.so.1.xlibmesa" and remplace it with one coming from the ATi's installer. Do search of libGL.so.1.xlibmesa in this forum to get help about.

---

### Post by bohboh on 2006-06-20
[QUOTE=Galban]I'm sorry to tell you that, you dont have 3D acceleration [-X , and even after you install xorg-driver-fglrx you will very probably get Mesa or API's errors doing fglrxinfo. You have to get rip of the Mesa's libGL version present in your /usr/lib/ that looks like  "libGL.so.1.xlibmesa" and remplace it with one coming from the ATi's installer. Do search of libGL.so.1.xlibmesa in this forum to get help about.[/QUOTE]

So when you say i dont have 3d acell, you mean my card doesnt support it? or that i need to follow the instructions here to get it.

[http://www.ubuntuforums.org/showthread.php?t=197471&highlight=libGL.so.1.xlibmesa]("http://www.ubuntuforums.org/showthread.php?t=197471&highlight=libGL.so.1.xlibmesa")

---

### Post by xXx 0wn3d xXx on 2006-06-20
Your card most likely supports 3d acceleration (DRI) but you do not have it enabled. You can follow the instructions at either linux to get 3d accel. working.

---

### Post by bohboh on 2006-06-20
[QUOTE=xXx 0wn3d xXx]Your card most likely supports 3d acceleration (DRI) but you do not have it enabled. You can follow the instructions at either linux to get 3d accel. working.[/QUOTE]

I followed the tut, and when i reboot it fails. In xorg.log it says:

```

(II) LoadModule: "fglrx"
(WW) Warning, couldn't open module fglrx
(II) UnloadModule: "fglrx"
(EE) Failed to load module "fglrx" (module does not exist, 0)

```

I installed fglrx, i am certain of that. Where does it look for it?

---

### Post by acankat on 2006-06-20
LOL:D I'wouldnt be so confused :D. This is the little suprise of our beloved ATI to all loyal linux user:). 

hundreds of dollars are not enough for 3D acceleretion:) we have to struggle for it:D

---

