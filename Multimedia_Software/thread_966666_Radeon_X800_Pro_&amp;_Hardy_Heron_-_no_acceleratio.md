---
title: "Radeon X800 Pro &amp; Hardy Heron - no acceleration :("
date: 2008-11-01
forum: Multimedia Software
---

### Post by masani3llo on 2008-11-01
I just put an ATI Radeon X800 Pro chipset R420 

```

lspci
01:00.0 VGA compatible controller: ATI Technologies Inc R420 JI [Radeon X800PRO]
01:00.1 Display controller: ATI Technologies Inc R420 [Radeon X800 PRO/GTO] (Secondary)

```

No way to make opensource drivers work? I followed [](https://help.ubuntu.com/community/RadeonDriver) this guide by letter but the result is:

```
masani3llo@masani3llo-desktop:~$ glxinfo | grep vendor
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
masani3llo@masani3llo-desktop:~$ glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

Should I try the official drivers? Opensource should work looking at the wiki...

thanks

---

### Post by masani3llo on 2008-11-01
up!

---

