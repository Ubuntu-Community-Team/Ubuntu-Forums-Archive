---
title: "Speakers on hP laptop, Lynx (10.04LTS)"
date: 2010-05-04
forum: Multimedia Software
---

### Post by dpcole72 on 2010-05-04
Hello.  I recently bought a HP G2-144DX (i3-330M CPU, Intel GMA HD video, haven't found audio specs yet :( ).  Installing Ubuntu 10.04LTS was straightforward (and fast, wow!)

I cannot get audio out of the main speakers, but the headphones plugged into the headphone jack work great.  

I booted up the original hard drive with Windows 7 on it. Sounds come through the speakers just fine.

What can I do to get audio to come out of the speakers, to negate the need for headphones?

Thanks much for your help!!

---

### Post by lidex on 2010-05-06
First some info. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

