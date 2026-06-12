---
title: "Intel 915 - Slow scrolling in firefox/gedit/etc when compiz/desktop effects enabled"
date: 2008-09-14
forum: Multimedia Software
---

### Post by speaker219 on 2008-09-14
Hello, i'm running ubuntu 8.04.1, with an Integrated intel graphics card: the intel 915.

I found a couple of problems. With any kind of desktop effects enabled, scrolling in firefox/gedit/pretty much anything is very slow. It is the most noticable in firefox.

I've read other reports of users with intel/other cards with slow scrolling and stuff, i've seen a few solutions including: 
removing the xserver-xgl package. I checked, and don't have this installed.
I also found out that i **do** have direct rendering enabled:
```
~$ glxinfo | grep direct
direct rendering: Yes
```

If I turn off compiz, the scrolling problems go away.
I *could* turn it off, but the desktop effects work fine and i'd love to keep them, the only problem is scrolling.

Does anyone have a working/proposed solution? I'd really appreciate it, this is the only thing that's keeping me from the perfect desktop.

EDIT: Also wanted to tell you that this seems strange, because i've used previous versions of ubuntu with this same laptop, with compiz, and firefox/etc had no scrolling problems, it was as smooth as butter.

---

### Post by BlairKatu on 2008-10-03
Actually I had that problem, I installed the xserver-xgl package and things worked smoothly. Give it a try.

~Blair

---

### Post by SteveMcQwark on 2008-10-12
I've got intel 950, and just recently, scrolling in some applications (most notably firefox) became slower, as well as rotating the desktop cube to and from the a desktop with firefox on it. I think the problem was created by an update, and I hope it is fixed soon, because it is annoying. Also, installing xserver-xgl only made things slower...

---

### Post by simao on 2008-10-14
Is there a solution for this?

Thank you,
SM

---

### Post by SteveMcQwark on 2008-10-20
This thread solved it for me, however this is regarding 945 and I'm using 950, whereas the thread owner is using 915. You could try it anyways, but remember: ctrl alt F1 gets you into a terminal screen to fix any problems. :D (and ctrl alt F7  gets you back)

[http://forum.compiz-fusion.org/showthread.php?t=8119&highlight=slow+firefox+scrolling]("http://forum.compiz-fusion.org/showthread.php?t=8119&highlight=slow+firefox+scrolling")

---

