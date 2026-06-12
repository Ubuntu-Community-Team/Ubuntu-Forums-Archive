---
title: "Yiff-server installation problems"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by utkjamie on 2007-10-30
When attempting to install/setup YIFF-SERVER I get the following error message:
```

Setting up yiff-server (2.14.5-2.2) ...
Starting Y Sound Server: ERROR.
invoke-rc.d: initscript yiff-server, action "start" failed.
dpkg: error processing yiff-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 yiff-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```If I attempt to run *yiff --configure* from the terminal, I get the following error:
```

/dev/dsp: Cannot open for playing.

```

I haven't been able to find any useful information on how to get yiff-server running properly.

---

### Post by Wirshlitza on 2008-04-16
I get the exact same error message... I even tried downloading from YIFF homepage, but the Debian package seems corrupt or something, since dpkg -i returns an error that it is not a proper Debian package...

Anyone knows what's up with YIFF installation on Ubuntu? I'm using version 7.10

---

