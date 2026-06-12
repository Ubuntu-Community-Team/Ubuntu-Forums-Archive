---
title: "ATI &quot;Big Desktop&quot; (laptop + external display)"
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by Bentley on 2006-11-15
Hello all,

Many are aware of the plethora of problems using ATI's proprietary drivers with the 200m chipset (found in Compaq/HP laptops).

After much trial & error, I've managed to get it working.  I don't have 3D acceleration, but I am running ATI's driver, which allows me to make use ATI's "Big Desktop" feature (similar to Xinerama).

So now I've got and external display and my laptop display.  I'm able to drag windows between then.  There is no mouse pointer corruption (like I got with Xinerama).  I can move my panel to whichever display I want.  I can even switch between "big desktop" mode and "laptop only" mode on the fly, without restarting my X server.  I'm quite happy with it.

[I blogged about my setup, incl. my xorg.conf, here.]("http://v2670ca.blogspot.com/2006/11/ati-200m-display-driver.html")

I have only one outstanding issue, and hope to find some guidance:

My laptop lcd is 1280x768.  My external display is 1280x1024.  When use/click my mouse on the lower portion of my external display, then move the pointer over to my laptop display, the mouse pointer is *out of sync* with the mouse click area.  For example, if I click at an icon on the laptop desktop, it'll select the icon 3 positions below the one I want.

To resync the mouse, I need to move it back to the higher resolution display, and click at the very top of the screen.  I can then move it to the lower resolution display and clicks are accurate.

I'm hoping this is a configuration issue. Does anyone know what could be wrong? :confused: 

Thanks

---

### Post by molo on 2006-11-18
Hey, just wanted to say thanks for posting this, I finally got BigDesktop working after reading your config file (I have a Compaq 2610ca).

I have the same issue with the mouse.  My feeling is that it's not a configuration issue, personally, but I can't really offer any facts, sorry.

Hopefully ATI releases some updated drivers soon... the link you have in your blog ([http://www.ailis.de/%7Ek/docs/atilinux/](http://www.ailis.de/%7Ek/docs/atilinux/)) talks about a corrupt pointer bug in some earlier ATI drivers, which makes me believe that the graphics drivers can and do mess with the pointer.

---

