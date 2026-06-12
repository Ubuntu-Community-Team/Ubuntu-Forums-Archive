---
title: "Resolution in NVidia X Server reverts on reboot."
date: 2009-04-28
forum: Multimedia Software
---

### Post by mrzubi on 2009-04-28
I am running Ubuntu 9.04, I have a widescreen monitor, and I would like it to boot into 1600 x 900 resolution without having to go into NVidia X Server every time I boot the computer to change it from 1024x768 to 1600x900. 

When I try to save the X Configuration File I get the error:

"Unable to create new X config backup file '/etc/x11/xorg.conf.backup'."

If I need to post my xconf I dont really know how to do that :/

Plaese Haaalp.

---

### Post by norwoods on 2009-04-28
run the following in a terminal to get administrative authority to change xorg.conf:
gksu nvidia-settings

---

### Post by mrzubi on 2009-04-28
I got a lot of errors when I tried that.

:*(

There are more errors but i didnt want to clog up the screen here.


> ERROR: Cannot open display 'zubi:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 21 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 22 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 23 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 24 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 25 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 26
       of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).





---

### Post by mrzubi on 2009-04-29
any ideas? Every time i re-boot it reverts to 1024x768.

---

### Post by norwoods on 2009-04-30
you get a Terminal by starting (on the menu bar) Applications-->Accessories-->Terminal
you get admin privileges by starting a program with sudo or gksu for gnome programs:
gksu nvidia-settings

---

