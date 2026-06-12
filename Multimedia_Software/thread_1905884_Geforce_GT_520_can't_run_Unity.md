---
title: "Geforce GT 520 can't run Unity?"
date: 2012-01-07
forum: Multimedia Software
---

### Post by AVH on 2012-01-07
Is it possible that a card this new can't run Unity? I ran the support test and got these results

```
ubuntu@ubuntu:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no
ubuntu@ubuntu:~$ 
```video card = PNY Geforce GT 520
MB = Gigabyte GA-965P-DS3

---

### Post by MoreOrLess on 2012-01-07
> OpenGL renderer string: Software Rasterizer
You don't have the driver installed correctly. Once you fix that, the GT520 will run Unity just fine.

---

### Post by AVH on 2012-01-07
I ran this from the Live CD. Does that make a difference?

---

### Post by MoreOrLess on 2012-01-07
> **AVH said:**
> I ran this from the Live CD. Does that make a difference?
Yes. The LiveCD uses the open-source nvidia driver (nouveau) which is just starting to support 3D on nvidia "Fermi" cards.

---

### Post by AVH on 2012-01-08
Thanks. I think I will take Unity for a spin then.

---

### Post by inobe on 2012-01-08
there are ways to test rendering in a live environment, the proprietary nvidia driver can be installed.  

last time i did this was a few distributions back, can't really recall how, but it was easy.

i'm sure a forum or google search would reveal this.

---

