---
title: "Ati Raedon Mobility x1400 Rendering Issues - glxgears working, dir rendering no..."
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by Romanovzky on 2008-02-02
Hi there,

I've an ATI mobility x1400 graphic card on my laptop and I'm having what I assume to be texture related rendering issues.

I've the restricted module activated, the glxgears command is working and it draws the gears at ~1800 FPS. Although, doing glxinfo | grep rendering returns this:

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

Which is weird...

My compiz works just fine (I only have a slight boot delay when it's activated), and never had problems with 3d graphics, but this week I installed Diablo 2 pc game (via wine) and the graphics were terrible.
In the beginning I thought it ought to be a wine problem, so I downloaded and installed Urban Terror  and Open Arena and I got this:

[IMG]http://porthos.ist.utl.pt/~mcromao/files/images/ss1.jpg[/IMG]
[IMG]http://porthos.ist.utl.pt/~mcromao/files/images/ss2.jpg[/IMG]

I've already reinstalled the drivers, but nothing changed.

---

### Post by Romanovzky on 2008-02-03
Nobody?...

I've search in many sites and I can't find an answer...

---

### Post by Romanovzky on 2008-02-03
Since nobody says a thing I will just update with a new symptom:

If I turn on the Desktop Effects, glxgears returns ~6000 fps, instead of the ~1300 I get with DE turned off...

---

### Post by Chris Morin on 2008-03-12
i have the exat same problem. have u found a fix?

---

