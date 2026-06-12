---
title: "Is this a major bug (Intel Graphics) in Ubuntu 11.04 or a config problem?"
date: 2011-04-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kio_http on 2011-04-07
[COLOR="DarkRed"]Major Intel Graphics Driver Bug or config problem?[/COLOR]

Under Kubuntu 10.10, I am able to over do on eye-candy and still run the system at full speed on my 1.6 Ghz Laptop with 2Gb Ram as in screen-shot.

On Kubuntu 11.04 however desktop composition seems slower and many features like blurred glass do not work. I have seen quite a few posts on the Internet about people experiencing this issue.

Taking a look into the matter I discovered that the bug cannot be solved by neither Kubuntu developers nor KDE developers.

Both Maverick and Natty were using the same version of KDE (latest KDE SC v 4.6.2)

**The output of Kwin on Maverick is**

[I][FONT="Century Gothic"]OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GME GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.9-devel
Driver: Intel
GPU class: i915/i945
OpenGL version: 1.4
Mesa version: 7.9
X server version: 1.9
Linux kernel version: 2.6.35
Direct rendering: yes
Requires strict binding: yes
GLSL shaders: no
Texture NPOT support: yes[/FONT][/I]

The output of Kwin on Natty is

[I][FONT="Century Gothic"]OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GME x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.11-devel
Driver: Intel
GPU class: i915/i945
OpenGL version: 1.4
Mesa version: 7.11
X server version: 1.10
Linux kernel version: 2.6.38
Direct rendering: no
Requires strict binding: yes
GLSL shaders: no
Texture NPOT support: yes
kwin(10066): glCheckFramebufferStatus failed: "GL_NO_ERROR"
[/FONT][/I]
Note the difference in direct rendering.

I notice if I disable Direct Rendering in KDE system settings in Maverick, it tends to reproduce a behavior similar to KDE in Natty.

Note: Many simpler desktop effects do work in Natty however overall performance in 3d acceleration etc is slower than in Maverick. Compiz users may not even notice the problem because of the lack of things like blurred glass etc.

Should I file a bug report for xserver-xorg-video-intel?

Is it likely that this issue will be fixed by final?

---

### Post by Elfy on 2011-04-07
moved to natty

---

### Post by kio_http on 2011-04-07
Any updates?

---

### Post by jorgebirck on 2011-04-20
Same here in my Dell V130 i3 Intel HD. OpenGL very slow (Kwin and Compiz)

---

### Post by testarap on 2011-04-20
Have you tried System > Administration > Additional Driver.

---

### Post by jorgebirck on 2011-04-22
Yes.
"No additional drivers"

---

### Post by buzzmandt on 2011-04-22
intel graphics offer no "additional drivers", intel graphics are supposed to "just work".

now, both my laptops running natty k are functioning well. this one is.

```
OpenGL vendor string:                   Tungsten Graphics, Inc
OpenGL renderer string:                 Mesa DRI Mobile IntelÂ® GM45 Express Chipset GEM 20100330 DEVELOPMENT 
OpenGL version string:                  2.1 Mesa 7.10.2
OpenGL shading language version string: 1.20
Driver:                                 Intel
GPU class:                              i965
OpenGL version:                         2.1
GLSL version:                           1.20
Mesa version:                           7.10.2
X server version:                       1.10.1
Linux kernel version:                   2.6.38
Direct rendering:                       yes
Requires strict binding:                yes
GLSL shaders:                           yes
Texture NPOT support:                   yes

```

---

### Post by benerivo on 2011-04-22
It might be related to this issue...

[http://www.phoronix.com/scan.php?page=news_item&px=OTM1NQ](http://www.phoronix.com/scan.php?page=news_item&px=OTM1NQ)

---

### Post by jorgebirck on 2011-04-23
buzzmandt, same info here.

But Kwin is choppy...

---

### Post by tlcstat on 2011-04-23
Greetings,
My GM45 Intel Graphics are fully support and fully working. Natty 11.04/Unity
Toshiba L305 4Gig Ram 1200M mapped to video.

tlcstat

---

### Post by jorgebirck on 2011-04-24
GLX Gears shows 54.133 FPS

kwin --replace
OpenGL vendor string:                   Tungsten Graphics, Inc
OpenGL renderer string:                 Mesa DRI Intel(R) Ironlake Mobile GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string:                  2.1 Mesa 7.10.2
OpenGL shading language version string: 1.20
Driver:                                 Intel
GPU class:                              i965
OpenGL version:                         2.1
GLSL version:                           1.20
Mesa version:                           7.10.2
X server version:                       1.10.1
Linux kernel version:                   2.6.38
Direct rendering:                       yes
Requires strict binding:                yes
GLSL shaders:                           yes
Texture NPOT support:                   yes


KWin is slow..

---

### Post by 67GTA on 2011-04-24
I don't know if it is related, but I have to disable "Use Vsync" in the Desktop Effects> Advanced section. This causes it to be pretty snappy. Also try changing the animation speed to fast or instant in the desktop effects section.

---

### Post by jorgebirck on 2011-04-25
No changes.

---

### Post by tlcstat on 2011-04-25
Greetings,

Original Post by **67GTA**
> I don't know if  it is related, but I have to disable "Use Vsync" in the Desktop  Effects> Advanced section. This causes it to be pretty snappy. Also  try changing the animation speed to fast or instant in the desktop  effects section.
 		                   		  		  		 		 			 				__________________

Could you post a screen shot of that section. I can seem to find it.
TIA
tlcstat

---

### Post by fifth on 2011-04-25
> **tlcstat said:**
> Greetings,

Original Post by **67GTA**

 		                   		  		  		 		 			 				__________________

Could you post a screen shot of that section. I can seem to find it.
TIA
tlcstat

System Settings -> Desktop Effects -> Advanced ... last check box on the bottom under Open GL settings

---

### Post by 67GTA on 2011-04-25
[attach]190011[/attach]

[attach]190012[/attach]

[attach]190013[/attach]

---

### Post by tlcstat on 2011-04-25
Greetings,
Original post by > 67GTA

Thanks, evidentially we aren't using the same desktop. Clearly not a Unity System Panel.
I did find a vsync setting for open gl in the compiz panel however. After I disabled it there seemed to be an improvement. 
tlcstat

---

### Post by tekstr1der on 2011-04-25
> **tlcstat said:**
> Thanks, evidentially we aren't using the same desktop.  Clearly not a Unity System Panel.


This thread is about kwin performance on kubuntu. If you have compiz performance issues under ubuntu/unity (and I do as well), you should start another thread.

---

### Post by tlcstat on 2011-04-25
Greetings
Original post by **tekstr1der**
> This thread is about kwin performance on kubuntu. If you have compiz performance issues under ubuntu/unity (and I do as well), you should start another thread.

[> [URL="http://ubuntuforums.org/showthread.php?t=1723748"]Is this a major bug (Intel Graphics) in [SIZE=3]**Ubuntu**[/SIZE] 11.04 or a config problem?]("http://ubuntuforums.org/showthread.php?t=1723748") [/URL]

Sorry, I must have read the heading wrong!

---

### Post by jorgebirck on 2011-04-25
No changes yet. Kwin still slow in my Dell V130 i3. Maybe a driver issue?

---

### Post by mfraser on 2011-04-26
I've managed to get things going again by adding the xorg-edgers fresh X crack PPA. Netbook seems more responsive now and all effects work. Just need to figure out why I only have a text splash screen on boot up, but a graphic one on shutdown!

---

