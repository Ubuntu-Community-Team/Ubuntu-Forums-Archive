---
title: "Cinelerra Stoped Working after Ubuntu upgrade"
date: 2007-11-28
forum: Multimedia Production
---

### Post by djmorgan22 on 2007-11-28
HI,
I am a relatively new Ubuntu user and use cinelerra heavily for editing blender 3d animations.

Two days ago I did official Ubuntu update, but now Cinelerra wont work!

 When I run it in a terminal I get the following

[INDENT][COLOR="Red"]cinelerra: symbol lookup error: /usr/lib/libguicast.so.1: undefined symbol: glDeleteShader
[/COLOR][/INDENT]

I have checked and Libguicast.so.1 is in the /usr/libs/ Directory.

I am rununig Ubuntu 7.10 x86 (32bit)

Can anyone help!

---

### Post by markekeller on 2007-11-28
Are you using the fglrx OpenGL driver?  If you are, try switching to the ati driver.  Or you could just try reinstalling/compiling.

---

### Post by Prospero2006 on 2007-12-18
I would suggest downloading the latest version and recompiling from source.

I have it running on and x64 with nvidia drivers. Works well.

Pros

---

