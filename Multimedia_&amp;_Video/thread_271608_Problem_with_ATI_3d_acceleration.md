---
title: "Problem with ATI 3d acceleration"
date: 2006-10-04
forum: Multimedia &amp; Video
---

### Post by l0c0dantes on 2006-10-04
Hello there. I have recently installed my ati driver, and installed cedega. It passed all the system tests, except for the 3d acceleration one. So I check to make sure that the driver is installed right, and it says it is, so I test it with glxgears, and it is only giving me ~150 fps. Any idea what the problem is, and how I could go about fixing it?

---

### Post by pay on 2006-10-05
run ```
fglrxinfo
```

---

### Post by boskone on 2006-10-05
I'm having the same problem.

glxinfo reports:
* direct rendering: Yes

fglrxingo reports:
* display :0.0 screen: 0
* OpenGL vendor string: ATI Technologies Inc.
* OpenGL renderer string: ATI Mobility Radeon X1400 Generic
* OpenGL version string: 2.0.6065 (8.29.6)

However, Cedega fails the 3D acceleration test, and glxgears -printfps reports ~125fps.  I've tried the wiki.cchtml.info methods, and replacing libGL.so.1.2 with an older version; none had any effect.

dmesg | grep fglrx gives a bunch of normal shit, plus one line about kernel taint.

Any thoughts?  Please?  Pretty please?  :D

---

### Post by l0c0dantes on 2006-10-05
loco@loco-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 2.0.6065 (8.29.6)

---

### Post by ThaRabbit on 2006-10-07
Could you provide your xorg.conf file ?

```
/etc/X11/xorg.conf
```

---

### Post by PosTi85 on 2006-11-21
I have the same problem, I'm talking about the same in the following thread:
[http://www.ubuntuforums.org/showthread.php?t=302333&highlight=ati+9550](http://www.ubuntuforums.org/showthread.php?t=302333&highlight=ati+9550)
I hope that someday ATI cards will work fine on ubuntu...:(

---

