---
title: "GLX Not Working With NVidia Card"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by mmorgan27 on 2007-05-21
I'm unable to get GLX working with my NVidia GeForce 6800 Ultra running on a Fiesty Fawn install.  I've installed the nvidia-glx-new.  Everything else works fine (2D), but when I try to run glxgears, or any othe OpenGL app,  I get:
```
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  21 ()
  Serial number of failed request:  8
  Current serial number in output stream:  8
```

Any ideas?

---

### Post by renzokuken on 2007-05-21
did YOU comment out the DRI line in your xorg.conf?

may be worth uncommenting the Load "dri" line, restarting X and trying again.

may also have to add a new section to the bottom of your xorg.conf that is something like

Section "dri"
     mode  "0666"
End Section

but dont take my word for that last bit, i can remember it exaclty and i'm not at my ubuntu box so i cant check for a mo

---

### Post by mmorgan27 on 2007-05-21
Yep, that was me.  I saw it in some other thread about configuring NVidia cards.  I did it in an effort to fix the problem.

 I put the Load "dri" statement back in, as well as the permission section, to no avail.  I still get the exact same error as described above.  Interestingly the number of loaded extensions reported by xdpyinfo is the same (31).

---

### Post by mmorgan27 on 2007-05-27
After several days with no response from Ubuntu forums, I posted on NVidia forums.  They suggested installing using the official NVidia install, it worked.  GLX issues fixed.  Prior to that  I tried installing the nvidia-glx and nvidia-glx-new packages several times with no luck.
It really appears that there is something wrong with the Ubuntu GLX installation.

p.s. It looks like commenting out the "dri" section has no discernible impact; with the Ubuntu install GLX failed to work regardless and with the NVidia install GLX worked regardless.

If you are having trouble with NVidia and GLX, I would suggest that you use the official NVidia install until Ubuntu figures out what the problem is.

---

