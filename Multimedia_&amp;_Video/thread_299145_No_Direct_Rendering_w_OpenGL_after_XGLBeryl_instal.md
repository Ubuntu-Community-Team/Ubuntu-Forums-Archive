---
title: "No Direct Rendering w/ OpenGL after XGL/Beryl install"
date: 2006-11-13
forum: Multimedia &amp; Video
---

### Post by JDillio12 on 2006-11-13
Ack..........I've been trying to fix this issue for days now and still no solution.  I am using Kubuntu Dapper Drake 6.06 on my HP MX7515 Laptop and after installing the fglrx drivers using 
 [THIS GUIDE]("http://wiki.cchtml.com/index.php/Ubu...allation_Guide") I had 3d Direct rendering say "Yes" when I ran fglrxinfo.  However, after going through  [THIS GUIDE]("http://www.smorgasbord.net/ati_beryl_kde_dapper_my_guide"), even though Beryl loaded and ran correctly, if I run fglrxinfo now I get this output:
----------------------------------------------------
[I]Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X600 Generic
OpenGL version string: 2.0.5814 (8.25.18)[/I]
-----------------------------------------------------

Now if I try to run the OpenGL screensavers, my PC locks up and I'm sent back to the KDE/Ubuntu login screen.  Also, direct rendering says no when I run fglrxinfo | grep rendering, as the output is still just this:

Xlib:  extension "XFree86-DRI" missing on display ":1.0".

I don't understand why it is giving me this error because I believe the guide I used installed Xorg 7, not XFree-86.  In fact, I have no Xfree86 files on my system at all (figured out by doing a file search).  

Does anyone know of a fix for this??  Or perhaps a guide that actually works on an X600 mobility ati card with XGL+fglrx+Beryl installed??

---

### Post by whatever on 2006-11-14
well, it's quite simple: if you want DRI you must not use Xgl.

---

### Post by JDillio12 on 2006-11-14
But don't Beryl and Compiz both require XGL to run?

---

### Post by whatever on 2006-11-14
if you want to use the proprietary fglrx drivers then Xgl is the only way to run Beryl at the moment. with the open source radeon drivers Beryl can use the AIGLX extension of Xorg instead.

---

### Post by JDillio12 on 2006-11-15
Nevermind I went with something else and it works beautifully!!!

I switched over to Debian Testing (Netinstall Etch) that comes with Xorg 7.1 and the ATI drivers already installed.  However, Xorg 7.1 is defaulted to AIGLX, which some said wouldn't work with ATI cards.  Well, it does, and I now have Compiz + Direct 3D rendering enabled.  You were right though, flgrx and XGL do not allow direct 3d rendering at the same time.

Note: I'm using an ATI X600 Mobility Card and this easy Tutorial worked for me: [http://wizah.blogspot.com/2006/10/debian-how-to-aiglx-compiz.html]("http://wizah.blogspot.com/2006/10/debian-how-to-aiglx-compiz.html")

---

### Post by antidrugue on 2006-11-15
> **JDillio12 said:**
> 
Note: I'm using an ATI X600 Mobility Card and this easy Tutorial worked for me: [http://wizah.blogspot.com/2006/10/debian-how-to-aiglx-compiz.html]("http://wizah.blogspot.com/2006/10/debian-how-to-aiglx-compiz.html")

I'm glad you liked my tutorial. Thanks for reading it ! Feel free to post any comment you may have regarding that tutorial here or directly on my blog.

---

