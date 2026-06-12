---
title: "Can you paste your xorg.conf for English keyboard with Spanish characters"
date: 2007-01-24
forum: Multimedia &amp; Video
---

### Post by joseantmm on 2007-01-24
Hi. My laptop, an IBM Thinkpad T23, has an English keyboard but I need it to be able to write Spanish accented characters with the help of the right alt key. I copy below my xorg.conf for the keyboard, which is not achieving it. If anybody can copy here his/hers, I could solve this problem. Thanks.

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "thinkpad"
Option "XkbLayout" "es"
Option "XkbVariant" "sundeadkeys"
Option "XkbOptions" "lv3:ralt_switch"

---

### Post by melusyne on 2007-01-24
Hi,
if you work with gnome, then you can use the "compose" mode if you can't get a correct layout : 

in the menu System settings -> Keyboard, Options, Compose  (or something like this)
set a key as your "compose" : for example left Win key, or anything you don't need

Then you'll be able to compose many special characters with <compose>+key combination
(n + tilde for example)

I don't use it myself but i'm struggling against keyboard also, and just read some stuff about it :)

Regards

---

