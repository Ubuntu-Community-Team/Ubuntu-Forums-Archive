---
title: "Problem with video"
date: 2013-06-13
forum: Multimedia Software
---

### Post by basgonggrijp on 2013-06-13
Hello there,

I have just made my first steps in switching to Ubuntu but keep running into the same problem. I am not able to lift the resolution of my monitor. It stays at 640*480 and it doesn't recognize my big television either. I have updated and installed an Nvidia driver that was suggested to me.

Somebody feel like making my day?

grts

Bas

---

### Post by papibe on 2013-06-13
Hi basgonggrijp.

Could you post the result of these commands?
```
lspci -nnk | grep -iA2 vga

lsmod | grep -E '(nvidia|nou)'

xrandr 
```
Regards.

---

