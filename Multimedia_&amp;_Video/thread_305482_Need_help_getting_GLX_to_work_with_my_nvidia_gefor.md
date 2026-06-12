---
title: "Need help getting GLX to work with my nvidia geforce2 card in edgy."
date: 2006-11-23
forum: Multimedia &amp; Video
---

### Post by CJNyfalt on 2006-11-23
Hi,

I need some help getting my nvidia card working in edgy.

The facts:
- I have a geforce2, so I installed nvidia-glx-legacy.
- I changed that line in xorg.conf from nv to nvidia.
- X11 starts and the nvidia logo is shown.
- I tried to get various 3D programs to run with no success.
- glxinfo reports: Xlib:  extension "GLX" missing on display ":0.0".
- The Load "glx" line is present in xorg.conf.
- The only thing that looks like a related error in Xorg.0.log is:
(EE) GLX is not supported with the Composite extension
error opening security policy file /usr/lib/xserver/SecurityPolicy


So what is the problem and what can I do to fix it? ](*,)

---

### Post by CJNyfalt on 2006-11-23
I finally managed to get it working, I had to run the following:

```

sudo nvidia-xconfig --allow-glx-with-composite

```

---

### Post by sysdrum on 2006-11-27
hey, How did you find the command to do that. I ran it worked. I have spent the last 3 weeks trying to get a nvidia vanta to load glx... you rock..

---

### Post by CJNyfalt on 2006-11-28
> **sysdrum said:**
> hey, How did you find the command to do that. I ran it worked. I have spent the last 3 weeks trying to get a nvidia vanta to load glx... you rock..

A lot of research. I went through many different Ubuntu nvidia pages, all with a bit of different info. One of the pages (don't remember which one, didn't find it when I tried to locate it again) mentioned an option to disable composite. However, this option didn't exist, but I knew from the logs that the problem was related to composite. So, I looked for other related options and found the one above.

---

### Post by tseliot on 2006-11-28
Follow Method 1 of this guide of mine and you will find the answer:
[http://ubuntuforums.org/showthread.php?t=281823](http://ubuntuforums.org/showthread.php?t=281823)

---

### Post by CJNyfalt on 2006-11-28
> **tseliot said:**
> Follow Method 1 of this guide of mine and you will find the answer:
[http://ubuntuforums.org/showthread.php?t=281823](http://ubuntuforums.org/showthread.php?t=281823)

Yes, that was where I found it. Like I tried to tell, --no-composite is no longer an option in the nvidia-xconfig that I have.

---

