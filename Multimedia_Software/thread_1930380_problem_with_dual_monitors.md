---
title: "problem with dual monitors"
date: 2012-02-23
forum: Multimedia Software
---

### Post by Dr.Joker on 2012-02-23
Hi guys,

I'm having a very annoying problem. I have two monitors, and I cannot get them to run at the same time. My graphics card is nVidia GTS 450, and I have the additional proprietary drivers installed. If I run the built-in ubuntu display program, it only shows me one monitor. If I run the nvidia-settings program, I cannot get both of the monitors to run. I can disable one and turn on the other, and it will work great, but if I try to get them both to work, one will show a completely white screen, and I cannot move anything there, except my cursor. Any ideas on how to fix this? I've been trying for hours with no success.

---

### Post by BicyclerBoy on 2012-02-23
You can **not** use the 'built-in' display prefs tool with the proprietary video drivers.

use nvidia-settings (from the GUI menu or terminal)
- make your settings
- optional: save to xorg.conf file (button)
- save & exit
- logout/login

The above program should fix your problem when you save & exit.
Try the optional line if it does not work.

The desktop experience you desire (windows like) is probably twinview.

Separate X screens is an option but you have to learn how to use it & separate X screens does not work well with newer unity desktop manager.

---

### Post by Dr.Joker on 2012-02-23
Thanks for your reply. Like I said before I did use nvidia-settings. However, I can only set one monitor at a time to work - the other one will show a completely white screen. When I try to use twinview, both monitors show just the background wallpaper, with no menus or ability to start any application, making the computer completely unusable. I have to press Ctr + Alt + F1 and then edit the xorg.conf file to turn of twinview before I can do anything. Any other ideas?

---

### Post by BicyclerBoy on 2012-02-24
Are you sure your version of the nVidia driver supports the card ?

Post your /var/log/Xorg.0.log...login with twinview enabled if possible.

The dual screen behaviour that is "can't move anything between screens except mouse cursor" is normal separate X screens since *buntu 8.04.
Separate X screens is reported to not work properly with unity.

Could be be your desktop effects manager does not work with twinview.
Try gnome classic session or lubuntu desktop.

Check system log files or dmesg after desktop does not draw.
Hopefully <ctrl>+<alt>+<t> starts a terminal..

unity --reset

---

