---
title: "sauerbraten dedicated server &amp; directFB"
date: 2009-08-24
forum: Multimedia Software
---

### Post by null-cipher on 2009-08-24
Hi Ubuntu-Forums!
I'm trying to run an Sauerbraten (Cube 2) server at home on my headless server box.
My trouble being, when I try to run the dedicated server, I get the attached error from DirectFB:
```
     =======================|  DirectFB 1.0.1  |=======================
          (c) 2001-2007  The DirectFB Organization (directfb.org)
          (c) 2000-2004  Convergence (integrated media) GmbH
        ------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2008-11-12 15:27)
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
Unable to initialize SDL: DirectFBCreate: Initialization error!

```

Now as this server is headless I am not running an Xserver, and I think this error is due to the program attempting to use graphical subsystems.

I am using the latest binaries from the sauerbraten website [http://www.sauerbraten.org/](http://www.sauerbraten.org/) as I recently installed the "sauerbraten-server" package from ubuntu and discovered they are binary-incompatible.

However, the "sauerbraten-server" ran without a hitch. (Aside from not allowing me to connect)

Is there any way for me to solve this without having to install the whole Xserver system? I would prefer to avoid this if possible.

Thanks.

---

