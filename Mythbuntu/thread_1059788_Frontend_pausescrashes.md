---
title: "Frontend pauses/crashes"
date: 2009-02-04
forum: Mythbuntu
---

### Post by nrune on 2009-02-04
I have an old crappy laptop as a frontend only, works okay but I am seeing it just freeze with playing video.  

The logs show
```
2009-02-03 07:33:42.834 VideoOutputXv Error: Could not find suitable XVideo surface.
2009-02-03 07:33:42.851 VideoOutputXv: Falling back to X11 video output over a network socket.
                              *** May be very slow ***
2009-02-03 07:33:42.851 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x934b348) visual(0x9366760)
                        XJ_depth(24) WxH(1024x768) bpl(3072)
2009-02-03 07:33:42.876 VideoOutputXv Error: Failed to create X buffers.
2009-02-03 07:33:43.078 GLVid, Error: Fatal error
mythfrontend.real: main/renderbuffer.c:2153: _mesa_reference_renderbuffer: Assertion `oldRb->Magic == 0xaabbccdd' failed.
```

I know this laptop has via hardware and is running the openchrome video driver. Also it displays video after restarting the frontend.

Ideas? 

Mike

---

### Post by scary_jeff on 2009-02-04
Have you tried different playback profiles in the frontend playback configuration?
I'm not sure about the GL error, but perhaps you are trying to use openGL sync, without a working opengl setup. Try turning off openGL sync and/or verifying in some other way that openGL is working on your system (I don't personally know how you would do this).

---

