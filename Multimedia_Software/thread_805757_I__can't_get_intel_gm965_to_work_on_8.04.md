---
title: "I  can't get intel gm965 to work on 8.04"
date: 2008-05-24
forum: Multimedia Software
---

### Post by nyjetsmann on 2008-05-24
My son installed the Nvidia driver over his Intel chipset. I have changed the driver back but can't get compiz or any 3d working. All worked great out of the box. How do I go back to what once was? Thanks for any help.

---

### Post by overdrank on 2008-05-24
> **nyjetsmann said:**
> My son installed the Nvidia driver over his Intel chipset. I have changed the driver back but can't get compiz or any 3d working. All worked great out of the box. How do I go back to what once was? Thanks for any help.

HI and welcome, you can try and uninstall the nvidia driver then reconfigure your xorg from the terminal with the command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```the terminal is located under applications, accessories. Then restartx with the ctrl, alt, backspace bar all at the same time.

---

### Post by nyjetsmann on 2008-05-24
I tried that to no avail. when I do  glxinfo | grep rendering

I get...

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

I am trying to get World of Warcraft working for him. I am trying real hard to convert him from windows but this is frustrating him.

---

### Post by overdrank on 2008-05-24
> **nyjetsmann said:**
> I tried that to no avail. when I do  glxinfo | grep rendering

I get...

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

I am trying to get World of Warcraft working for him. I am trying real hard to convert him from windows but this is frustrating him.

Hi and you may try 
A new X windows recovery feature is available. If you are unable to boot after attempting changes, you can reboot, choose the restore option in the boot menu, and then select the 'xfix Try to fix X server' option on the Recovery Menu. This should restore your X windows configuration to a usable condition and allow you to boot normally.
Found here
[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

---

