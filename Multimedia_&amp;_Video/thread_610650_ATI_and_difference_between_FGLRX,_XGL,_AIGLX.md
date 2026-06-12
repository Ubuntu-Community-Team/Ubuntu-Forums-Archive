---
title: "ATI and difference between FGLRX, XGL, AIGLX"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by Rippie on 2007-11-12
Hello people...

Just installed the new ATI driver 8.42.3 on my Ubuntu Gutsy. and i followed this guide.

> [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Im quite sure that this guide here helps you to install it with fglrx right ?


Now ive heard and seen speaking about FGLRX, AIGLX and XGL. could someone please clarify this for me ? is there a bigger difference between them ??

// Rippie

---

### Post by bharadwaj on 2007-11-12
Xgl is an X server architecture designed to take advantage of modern graphics cards via their OpenGL drivers, layered on top of OpenGL via glitz. It supports hardware acceleration of all X, OpenGL and XVideo applications and graphical effects by a compositing window manager such as Compiz or Beryl. And thereis certainly another future programme of Xgl that is Xegl but the initialization of the OpenGL drawable and context management is handled by the EGL API developed by Khronos.

Aiglx was somewhat same aimed programme but has been released by Red hat and fedora. Although the AIGLX project has features similar to Xgl, it is not a competing product.

---

### Post by Rippie on 2007-11-12
Thank you so much for your reply, that helped me a bit further. so does any one know which one is best ? XGL or AIGLX ?

---

