---
title: "[SOLVED] How to Control Sound Using Keyboard"
date: 2008-10-05
forum: Multimedia Software
---

### Post by nikRbokR on 2008-10-05
I'm using a Dell Inspiron 600m laptop.

I do not remember how to set up the sound so that I can control the computer sound by using the controls on the keyboard.

Could someone please help me out.  All I remember is System>Preferences>Sound.  Which selections do I do below for Default Mixer Tracks(all?),

---

### Post by kdcoetzee on 2008-10-05
I know you can set it up with Xmodmap and with xev

install xev with 

```
 sudo apt-get install x11-utils 
```

then run this command.

```
 xev | sed -n 's/^.*keycode *\([0-9]\+\).*$/keycode \1 = /p' 
```

press the multimedia keys and look at the output.
if there is no output you will need to search though the raw output

```
 xev 
```

and then enter the code you got into 

```
 sudo vi /etc/X11/Xmodmap 
```

This is how myne looks 

```

keycode 160 = XF86AudioMute
keycode 176 = XF86AudioRaiseVolume
keycode 174 = XF86AudioLowerVolume

```


Or try what these guys say. I have a HP notebook and using Gentoo.
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell]("https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell")

---

### Post by hac13 on 2008-10-05
I was able to set this up using System>Preferences>Keyboard Shortcuts with the actions volume up, down and mute in the sound category.

---

### Post by Kinetic Being on 2008-10-05
> **hac13 said:**
> I was able to set this up using System>Preferences>Keyboard Shortcuts with the actions volume up, down and mute in the sound category.


Yup, I just did this last night.

Does anyone know how to change the pop-up that comes up whenever you change the volume? Its really big and in the middle of the screen, and if there was a way to either move it or make it smaller or even just turn it off, that would be great.

---

### Post by kdcoetzee on 2008-10-05
> **hac13 said:**
> I was able to set this up using System>Preferences>Keyboard Shortcuts with the actions volume up, down and mute in the sound category.

Speechless, Well I learn something as well. multiple ways of doing thing in Linux.

---

