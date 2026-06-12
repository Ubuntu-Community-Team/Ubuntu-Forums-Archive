---
title: "FN and F4 keys don't toggle video output"
date: 2010-08-10
forum: Multimedia Software
---

### Post by shayno90 on 2010-08-10
Running x86 64bit Ubuntu Lucid Lynx 10.04 on Compaq Presario CQ61-405SA.

I don't know if this problem occured before the grub update or after but the FN and F4 keys to toggle the video output to tv etc. is not working.

Anybody have the same problem and is there a solution?

---

### Post by JonasDK on 2010-08-10
Have they ever worked for you?
Because from my experience only a couple fn-function keys work in Ubuntu...

---

### Post by shayno90 on 2010-08-10
I only installed Ubuntu 10.04 at the weekend and I never tested it until I updated the kernel. I am guessing there is no fix for FN and F4 toggle video if it doesn't work for you either!

---

### Post by Cavsfan on 2010-08-10
System > Preferences > Keyboard Shortcuts
You should find it in there somewhere.

Or you can Add it.

---

### Post by shayno90 on 2010-09-01
> **Cavsfan said:**
> System > Preferences > Keyboard Shortcuts
You should find it in there somewhere.

Or you can Add it.

Nope it is not in the short cuts or can be added to work. Works in  WIndows 7 though when I toggle into it but not Ubuntu!

Anyone have anymore ideas?

---

### Post by shayno90 on 2011-09-16
Any development on this issue of FN and F4 toggle video?

---

### Post by shayno90 on 2011-11-22
Laptop still doesn't toggle while on Ubuntu to output via HDMI. However it seems to automatically go into HDMI mode while connected during the boot process or following a restart from Windows in Ubuntu after having toggled HDMI mode in Windows.

---

### Post by shayno90 on 2012-02-20
The HDMI connection works on the laptop when toggled through "Systems"  --> "Monitors" but depending on the TV HDMI connection, the  appropriate Linux graphics module may not work or the TV HDMI port may  be the issue. The F4 key still doesn't function to allow you to toggle.  Despite a shortcut being setup as below:

sudo gnome-keybinding-properties
Name: Toggle video
Key: Fn+F4

As there is no default option in the keyboard shortcuts menu, you have  to try and add the above shortcut but it does not work in any case.

---

