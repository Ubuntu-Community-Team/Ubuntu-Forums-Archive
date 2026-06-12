---
title: "How to install opengl on my x3100 intel chipset."
date: 2009-03-05
forum: Multimedia Software
---

### Post by ruado on 2009-03-05
I've recently bought a sony vaio vgn-cr320e with x3100 video chipset.Unfortunately,when i have a look at the xorg.conf,it doesn't show that OPENGL have been installed on my os.

Can anyone help me to solve this problem?
Thanks in advance.:D

---

### Post by mpsii on 2009-03-05
Install mesa-utils:

```
$ sudo apt-get install mesa-utils
```

Then:

```
$ glxinfo|grep rendering
```

The output should be:

direct rendering: Yes

If not, you need to use the Intel driver for your video card.

For further info, see:

[http://ubuntuforums.org/showthread.php?t=1075122&highlight=intel+x3100+dri](http://ubuntuforums.org/showthread.php?t=1075122&highlight=intel+x3100+dri)

---

### Post by ruado on 2009-03-05
Thanks for your reply.Can you post a sample xorg.conf file that has a configuration section for driver intel.I'm a new ubuntu user, i don't have many expriences in doing that.

Many thanks.

---

### Post by ruado on 2009-03-05
Also, when i issue the "glxinfo|grep rendering" command with LIBGL_DEBUG=verbose, i got the following message:

libGL: XF86DRIGetClientDriverName: 1.9.0 i965 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i965_dri.so
libGL error: dlopen /usr/lib/dri/i965_dri.so failed (/usr/lib/dri/i965_dri.so: undefined symbol: _glapi_Dispatch)
libGL error: unable to load driver: i965_dri.so
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

Can anyone tell me why i got this message and how to fix it?According to the message, I guesses that a wrong version has been used.:(

---

### Post by ruado on 2009-03-06
anyone?:(

---

