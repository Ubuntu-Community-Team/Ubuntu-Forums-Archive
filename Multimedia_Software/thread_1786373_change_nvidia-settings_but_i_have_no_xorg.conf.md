---
title: "change nvidia-settings but i have no xorg.conf"
date: 2011-06-19
forum: Multimedia Software
---

### Post by FrAggLE-Rock on 2011-06-19
Hi

i tried to change some things with sudo nvidia-settings
but when i try to save my settings and click on "save to x configuration file"

i have to choose where i want to save it

my first thought was to the etc/x11/xorg.conf

but in this folder x11 is no xorg.conf file


So now my question where do i save my changes???

im running ubuntu natty x64
gpu: nvidia gt 330m
manually installed driver: nvidia 270.4106

Hope someone can help me with this

---

### Post by FrAggLE-Rock on 2011-06-20
bump sorry but i really need this

---

### Post by FrAggLE-Rock on 2011-06-20
got it

if someone has the same problem

1. i ran gksudo nvidia-xconfig
that creats a xorg.conf

2. gksudo nvidia-settings

then you can save whatever you changed.

---

