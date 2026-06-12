---
title: "Scrambled-green webcam image on 64bit 12.10 ubuntu"
date: 2013-05-08
forum: Multimedia Software
---

### Post by gonzobilbao on 2013-05-08
Hi


I am running linuxmint 14 (12.10 based) , 64 bit edition. My webcam video quality is really poor, it shows "swept", grainy and blue-green output. Before I used to run a 32 bit ubutnu, and the quality was perfect. However this is not the case with the 64bit flavour. I believe is a problem with v4l, but I have not been able to fix it. These are some of the outputs I get in skype

```
Gtk-Message: Failed to load module "atk-bridge"
`menu_proxy_module_load': /usr/bin/skype: undefined symbol: menu_proxy_module_load

(skype:12585): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': /usr/bin/skype: undefined symbol: menu_proxy_module_load

(skype:12585): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': /usr/bin/skype: undefined symbol: menu_proxy_module_load

(skype:12585): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': /usr/bin/skype: undefined symbol: menu_proxy_module_load

(skype:12585): Gtk-WARNING **: Failed to load type module: (null)

libv4l2: error dequeuing buf: Invalid argument

libv4l2: error dequeuing buf: Resource temporarily unavailable (repeats numerous times during conversation)

libv4l2: error dequeuing buf: Invalid argument

```


I cannot get cheese to work fine either. In both cases I have tried to improve the quality using guvcview and v4l control panel, but it does not solve the problem. My computer is a hp 1050ca, using hp truevision webcam

Any help?
Thanks

---

### Post by gonzobilbao on 2013-05-15
bump!!

---

