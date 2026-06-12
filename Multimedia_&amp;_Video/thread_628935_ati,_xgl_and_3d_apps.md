---
title: "ati, xgl and 3d apps"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by f3nol on 2007-12-01
Hi everybody,

I know there are tons of threads on similar topic and I've read a lot of them but non of them gave me straight answer to the question: will I be able to run 3d applications properly with Ati and xgl?

I want to say that I'm not linux expert and this is where I'm now:

I'm on Gutsy

I've got Radeon 9600 and fglrx driver running.

I have xgl and compiz installed and it's all working fine.

```

glxinfo | grep rendering
``` 
gives me this:
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose
```)

GoogleEarth freezes at splash screen and gives this:
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
```

Stellarium crashes my session and sends me back to login screen.

I know that my GoogleEarth worked fine on fglrx driver before I've installed xgl.

As I said I've read a lot of threads but still don't know if there is a good solution or should I just give up an idea of having smooth and fancy desktop with 3d applications running correctly on it.

Thanks in advance for all your answers
):P

---

### Post by acoustibop on 2007-12-01
Which fglrx driver are you using, f3nol, and how did you install it?  For the last couple of fglrx drivers, xgl is not needed any more; they work with AIGLX.  If you don't have direct rendering, it may be your driver is not properly installed/running - what do you get for fglrxinfo?

I have a 9800 XT, and Compiz runs beautifully with the new ATI 7.11 driver - and did with the previous 8.42.3 one, as well.  It is, of course, necessary to disable Compiz to play 3D games etc.

---

### Post by f3nol on 2007-12-02
Hi acoustibob, thanks for your reply.

I'm not very familiar with linux so I'm not quite sure which fglrx driver I'm using and I don't exactly know what xgl and aixgl is. I can tell you what I've done so far though:
On a new Gutsy installation i chose ATI accelerated graphic driver in Restricted Driver Manager. And then my googleearth worked very well but visual effects on desktop didn't. So I've installed xgl and compiz from Synaptic and that's pretty much it. Compiz works fine now but 3d applications don't. 

And that's my fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6473 (8.37.6)

```

Thanks

---

