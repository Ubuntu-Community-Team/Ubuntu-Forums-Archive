---
title: "glxgears giving me this error"
date: 2005-11-18
forum: Multimedia &amp; Video
---

### Post by nallelcm on 2005-11-18
Umm I have a GeForce2 Ti, I'm not sure what other information to give.  Yes, I know I'm useless.
```
$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
```

---

### Post by Teroedni on 2005-11-18
Go into synaptic and completely remove nvidia glx.
Then Reebot Install the Nvidia glx legacy 
Open terminal
Write sudo nvidia-glx-config enable
and restar

Then all should work fine

---

