---
title: "Missing Xlib extension on display 0 ? ATI/fglrx"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by WalmartSniperLX on 2007-03-18
fglrxinfo :

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6334 (8.34.8)

```

```

patrick@patrick-desktop:~$ glxinfo | grep direct
direct rendering: Yes

```

I ran Americas Army 2.5 (linux) and after exiting, I get this in the terminal 

```

WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Defaulting to false

```

I get these kind of errors when running other games such as Doom 3. I dont remember what it said for Doom 3 but I know it had to do with missing extensions. What does this mean? Is there a way to add new ones?

---

### Post by skalsky on 2007-11-23
Hi, I'm having the exact same error on Gutsy while running America's Army 2.5. I Have an ATI 9600 and other 3d apps work great, including compiz and glxgears gives a result of ~1600 fps. I used to run the game just fine on Ubuntu 5.10.. anyway, the game runs but the frame rate is horrible. I tried lowering the video settings to minimum, but there seems to be no change whatsoever in performance.

Any ideas?

Thanks a bunch. Skalsky

---

