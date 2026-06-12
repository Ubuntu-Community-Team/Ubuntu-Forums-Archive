---
title: "CPU usage during glxgears"
date: 2006-02-12
forum: Multimedia &amp; Video
---

### Post by poyner on 2006-02-12
Hi all, I've got what should hopefully be a simple question. Should the CPU use be 100% during 3D operations? 

Background. 
My fglrxinfo shows: ```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 2.0.5582 (8.21.7)

```
and my glxgears gives about 2700 fps but when i have glxgears running the CPU graph max's out at 100%. Is this normal or do I have a problem somewhere? 

Thanks

---

### Post by joft on 2006-02-12
Hi,

I can't tell you if something is wrong, but I can say that glxgears consumes around 91% CPU on my computer/laptop (nvidia) (running glxgears and looking at "top").

So I'd say there is nothing to worry about. I think you should be able to switch windows, start other programs, .... while glxgears is running. If that's not possible (=> if glxgears really blocks everthing) something maybe wrong.

---

