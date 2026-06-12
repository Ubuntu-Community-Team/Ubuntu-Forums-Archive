---
title: "ATI can't set color depth to 32-bit"
date: 2006-09-04
forum: Multimedia &amp; Video
---

### Post by jlapier on 2006-09-04
I tried to modify my xorg.conf file to set to 32 bit instead of 24 bit and I get this error starting X:

```

(**) fglrx(0): Depth 32, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 32 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(EE) fglrx(0): Weight given (000) is inconsistent with the depth (32)
(EE) fglrx(0): PreInitWeight failed

```

Using Ubuntu Dapper AMD 64-bit release, ATI Radeon 9550 with proprietary drivers, ver: 8.28.8

Anyone know how to switch to 32-bit color depth with ATI drivers? I can post my whole xorg.conf if needed. I just basically went into and changed the default depth from 24 to 32 and added a 'SubSection "Display"' entry for depth 32.

---

### Post by whatever on 2006-09-04
24bit is what you want

---

### Post by BJones on 2006-09-05
24-bit is the maximum supported under Ubuntu.  They claim the quality is the same as 32-bit.  

I'd have to agree, it looks as good as 32-bit in Windows.

---

### Post by whatever on 2006-09-05
if you set windows to 32bit colors you will in fact "only" get 24bit output.

you have to distinguish between rendering and output. a current graphics card will never output more than 24bit colors. however, the rendering (the process of creating this 24bit image) will usually be done in 32bit, where the additional 8bits are used for transparency information.
if you set xorg.conf to 24bit you just select the output format. in most cases the driver will decide to do the actual calculation in 32bit. therefore the result does not only look as good as 32bit in windows, it really **is** the same result.

---

### Post by jlapier on 2006-09-06
Ah. Well, that explains it. I personally agree - anyone who can spot the difference between 24 and 32 bit is lying ;)

I was trying to test out the SecondLife linux client (which is in alpha) and in the output of the error messages it gave me was:

```

2006-09-07T00:41:32Z INFO: Initializing window...
2006-09-07T00:41:32Z INFO: createContext, fullscreen=0 size=800x600
2006-09-07T00:41:33Z INFO: createContext: creating window 800x600x32
2006-09-07T00:41:33Z INFO: createContext: window creation failure. SDL: Couldn't find matching GLX visual
2006-09-07T00:41:33Z INFO: destroyContext begins
2006-09-07T00:41:33Z INFO: shutdownGL begins
--snip--
2006-09-07T00:41:33Z WARNING: Unable to create window, be sure screen is set at 32-bit color in Control Panels->Display->Settings

```

Obviously the defaults it's set for is an 800x600 screen at 32-bit color. Being an alpha client, the documentation is nil, so I'll have to post on their boards and see if there's a way to set the default to 24-bit. 

Thanks again for the info guys.

---

