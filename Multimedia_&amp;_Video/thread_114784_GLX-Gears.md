---
title: "GLX-Gears?"
date: 2006-01-09
forum: Multimedia &amp; Video
---

### Post by 0x001A4 on 2006-01-09
I used to use SuSe and when I wanted to benchmark my framerate i just went to a terminal and typed # glx-gears

Is there anything like that in Ubuntu? or how can I get glx-gears in ubuntu?

---

### Post by snowjunkie on 2006-01-09
[QUOTE=0x001A4]I used to use SuSe and when I wanted to benchmark my framerate i just went to a terminal and typed # glx-gears

Is there anything like that in Ubuntu? or how can I get glx-gears in ubuntu?[/QUOTE]

It's glxgears in (K)ubuntu.

---

### Post by tommie-lie on 2006-01-09
To make glxgears print the framerate, you have to add a parameter in newer versions of glxgears (at least in the version used by Breezy Badger): "glxgears -printfps".
Also note that glxgears is not a real graphics benchmark. It does not stress shaders very much. And with that few polygons, you don't even let the render pipelines go to their limits. You mainly check for memory bandwith while rendering to the off-screen bitmap rather than anything else. glxgears is only a vague check for a working hardware acceleration (that is, if your graphics card can render faster than the CPU at all).

---

### Post by 0x001A4 on 2006-01-09
Well thats all I wanted it for. I installed the Nvidia driver and just wanted to see if it worked :s

Thanks alot.

---

