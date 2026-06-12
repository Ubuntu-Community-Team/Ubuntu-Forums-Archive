---
title: "fglrx installed, but Oneiric still using vesa"
date: 2011-10-17
forum: Multimedia Software
---

### Post by osarusan on 2011-10-17
I did a fresh install of Oneiric 64bit today, and set up the FGLRX drivers from the repositories. They seemed to install just fine, and running fglrx and fgl_glxgears seems to work fine... however System Info tells me I am still using Vesa drivers.

Any idea what is happening here and why it's not using fglrx?

```
osarusan@GLaDOS:~$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4770 
OpenGL version string: 3.3.11005 Compatibility Profile Context
```

---

### Post by Fallballa on 2011-10-17
Having the same Problem, maybe reporting a bug on this tomorrow...didnt have that problem while using oneiric beta.

---

### Post by osarusan on 2011-10-17
The weird thing is that it did use fglrx for a while for me too. Then at some point it went to vesa without me realizing it.

---

### Post by Fallballa on 2011-10-18
Same here, maybe just a bug in gnome-settings-daemon or something like that. Tested it and fglrx is definitly in use.

---

### Post by osarusan on 2011-10-18
Are you sure? I'm having mixed results. I can run some 3d programs like fgl_glxgears and minecraft, but I noticed that on the other hand windows shadows are failing to render... not sure which to trust.

---

### Post by orkineric on 2011-10-18
I'm having the same issue. I can run fglx_gears, but Savage 2 fails to render the sky, and I can't run Google MapsGL. Any ideas how to disable vesa and just use fglrx?

---

### Post by osarusan on 2011-10-19
No idea! This is frustrating.

If it's loading vesa, that means fglrx is not loading. It's not an issue of disabling vesa, it's an issue of getting fglrx to work properly. It appears to be working in all aspects, considering that fglrxinfo returns the correct result. However glxinfo shows that the 3D rendering is not happening, and clearly compiz is not working properly.

I can't find anything else about this on Google either. It was working only a few days ago and now it's not. I have no idea why.

---

### Post by osarusan on 2011-10-20
Did you file a bug report yet? If you do, please post the link here.

Are all of you using the fglrx package in the repositories? Or fglrx-updates? Or are any of you using the driver from the AMD website?

---

### Post by Fallballa on 2011-10-21
I did: [https://bugs.launchpad.net/ubuntu/+bug/879522](https://bugs.launchpad.net/ubuntu/+bug/879522)

---

### Post by Linuxisfast on 2011-10-21
Its a bug in reporting, I have the same issue here on my Oneiric x64, however video acceleration works fine and so does vaapi with vlc.

---

