---
title: "60fps in glxgears. Direct Rendering: yes :S"
date: 2011-02-10
forum: Multimedia Software
---

### Post by Tronfi on 2011-02-10
Hello people. 

I have a FujitsuSiemens Esprimo U9200 running Ubuntu 10.10. This laptop has a integrated graphic card (Intel GM965/GL960) wich is suppoused to be covered with the intel driver. I can check that direct rendering is enabled:
[INDENT][I]$ glxinfo | grep direct
direct rendering: Yes[/I][/INDENT]

But when I run glxgears, it only gives me 60fps, wich I think is not normal. I have compiz and all that kind of things disabled, of course.

Has anyone an idea of what can be happening?

Thanks in advance!

---

### Post by psusi on 2011-02-10
It is normal if you have vsync enabled and your monitor is running at 60 Hz.

---

### Post by Tronfi on 2011-02-10
> **psusi said:**
> It is normal if you have vsync enabled and your monitor is running at 60 Hz.

I can't change the frequency of refresh in the settings, it only offer me the '60Hz' option. How could I change it?

Thanks.

Edit:

This is what xrand tells me:

[I]$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       59.8*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DVI1 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)[/I]

---

### Post by mcduck on 2011-02-10
> **Tronfi said:**
> I can't change the frequency of refresh in the settings, it only offer me the '60Hz' option. How could I change it?

Thanks.

If you have LCD display, then you can't (and shouldn't even try changing it).

You can of course disable vsync, but I wouldn't bother based on glxgears output, as *glxgears is not a performance test*.

(It actually used to require you to run it using command *glxgears --iacknowledgethatthistoolisnotabechmark*  to show the fps reading at all. I still think they should have kept it that way. :D)

---

### Post by Tronfi on 2011-02-10
> **mcduck said:**
> If you have LCD display, then you can't (and shouldn't even try changing it).

You can of course disable vsync, but I wouldn't bother based on glxgears output, as *glxgears is not a performance test*.

(It actually used to require you to run it using command *glxgears --iacknowledgethatthistoolisnotabechmark*  to show the fps reading at all. I still think they should have kept it that way. :D)

Anyway, apart from glxgears, I can't even wath HD videos or play CS 1.6. In CS 1.6 I think I got 1 or 2 fps u_u

---

