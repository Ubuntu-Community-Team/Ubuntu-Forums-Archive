---
title: "Version 20.04: Copy paste crash in image editing software (e.g. Gimp, Pinta etcetera)"
date: 2020-10-13
forum: Multimedia Software
---

### Post by xinuzi on 2020-10-13
Hi,

Noticed that selecting and copying in e.g. gimp lets the image editing program crash.

Solution (here) = quit (or uninstall) clipboardmanager qlipper (version 5.1.2). Or don't 
let it boot as a tray icon automatically with system start.

To thoroughly get rid of the intervening thing:

> sudo apt-get purge --auto-remove qlipper

---

