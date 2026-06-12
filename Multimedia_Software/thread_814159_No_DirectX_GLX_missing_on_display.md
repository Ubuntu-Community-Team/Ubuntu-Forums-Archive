---
title: "No DirectX GLX missing on display"
date: 2008-05-31
forum: Multimedia Software
---

### Post by MrEnder on 2008-05-31
Ok first off I must state I am decent with computers but very new to Linux and that I'm sorry if I posted this in the wrong area.

My problem is I can't play WoW on Ubuntu

First I downloaded Wine and tried to open up WoW using wine. It opened but it was so slow and boxy that it would not even load properly. I knew this was a video card problem. I found the restricted drivers area and installed the Nvidia Legacy drivers.

This allowed to me log into WoW but on a 800x600 res and not my normal 1024x768

So after searching around a few forums I followed some directions on how to get it to a higher res. I'll be completely honest and say I had no idea what I was doing just rather following directions. I am not good with the terminal what so ever.

So this got me to 1024x768 res which was awesome I was quite pleased. I then opened up wine and logged into my portable hard drive and tried to open it up. It tried to load but I got this error.

"World of Warcraft was unable to start up 3D accelerator. Please make sure DirectX 9.0c is installed and your video drivers are up-to-date."

So then it was back to google searching around the net for solutions. I eventually came across something that told me to check my directX in the terminal.

Here is what I got

Xlib: extension "GLX" missing on display ":0.0".

So now I've hit a dead end and don't know what to do.

HELP!!!

Thanks
Shelby

P.S. Just please make sure you tell me how to do all of this in the easiest way possible and make sure you mention how to use those little terminal things that make no sense what so ever. I'm use to computer for dummies (Windows) ><

---

### Post by MrEnder on 2008-06-01
I'm still having the problem does anyone have an answer for me?

---

### Post by MrEnder on 2008-06-01
Sigh I still really need an answer

---

### Post by Xiong Chiamiov on 2008-06-01
Open your xorg file for writing
```

gksudo gedit /etc/X11/xorg.conf

```
and add this in it:
```

Section "Module"
    Load           "glx"
EndSection

```

If the Module section is already there, then just add the line starting with "Load" into it.

---

