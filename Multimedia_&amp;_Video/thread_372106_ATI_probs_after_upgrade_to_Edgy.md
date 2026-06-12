---
title: "ATI probs after upgrade to Edgy"
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by tsantos on 2007-02-27
I have an ATI x1900xt and was running successfully with Xgl and Compiz before my upgrade to Edgy.  Before I switched to Edgy, I went back to screen 0 and no Xgl (as far as I could tell).  After I switched to Edgy, my fglrxinfo command returns:

> ERROR: DDX driver fingerprint mismatch: got 0x84220BA7, but expected 0x32C4A39B
libGL error: InitDriver failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

(glxinfo | grep vendor) returns:

> ERROR: DDX driver fingerprint mismatch: got 0x84220BA7, but expected 0x32C4A39B
libGL error: InitDriver failed
server glx vendor string: SGI
client glx vendor string: ATI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)

I was hoping to get Xgl back up and running on Edgy but I can't figure out what's wrong with my basic fglrx setup.  Is it old mesa stuff from my compiz days?  If so, how can I get my system back to a simple video setup?

Thanks for any help,

-Tom-

---

### Post by doobydave on 2007-02-28
Check your /etc/X11/xorg.conf for this :-

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Add it if is not there.

---

### Post by tsantos on 2007-03-01
Yup I have that block in my xorg.conf.  

-Tom-

---

### Post by doobydave on 2007-03-03
Have you tried to use Envy over at
[http://albertomilone.com](http://albertomilone.com)

Its a script that automates install/unintall of ATI/Nvidia drivers.

---

### Post by derrekito on 2007-04-21
Please refer to this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

else please provide more information.

---

