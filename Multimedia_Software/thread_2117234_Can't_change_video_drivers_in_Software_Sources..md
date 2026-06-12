---
title: "Can't change video drivers in Software Sources."
date: 2013-02-17
forum: Multimedia Software
---

### Post by Illusionistik on 2013-02-17
Originally installing Ubuntu it used the nouvou driver (open) and I couldn't even get to my desktop. After finding the temporary way to disabling it then swapping to a proprietary driver (nVidia) problem was fixxed.

I tried to install a game through PlayonLinux and it crashed on me, error message said something along the lines of Directx and Shader 2.0. I then tried switching from the 5 other drivers in the Software Sources to see if one of them were better.

Now it is stuck on the open driver (nouveou) which I can tell is buggy like my cursor is blinking and resolution is off. 

The problem is that I cannot switch back to any of the other drivers it just instantly reverts back to the nouveou one.

[http://img827.imageshack.us/img827/1484/sdasdg.png](http://img827.imageshack.us/img827/1484/sdasdg.png)

---

### Post by papibe on 2013-02-17
Hi Illusionistik.

Close the Software Center, and try 'Additional Drivers' or 'Hardware Drivers'.

Let us know how it goes.
Regards.

BTW, there's no driver with DirectX support. What you do is to solve the problem within Wine, or PlayOnLinux, by configuring or adding libraries.

---

