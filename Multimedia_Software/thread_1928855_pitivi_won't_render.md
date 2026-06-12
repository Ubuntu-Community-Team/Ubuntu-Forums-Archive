---
title: "pitivi won't render"
date: 2012-02-20
forum: Multimedia Software
---

### Post by gdgilda on 2012-02-20
Hello,

I'm trying to use pitivi to do some fairly basic rendering (i.e. a couple of AVI files cross-faded together in the middle).  Whenever I try to render, pitivi seems to run through the rendering process and gets to 100% rendered in the dialog box, with "about 1 second remaining" displayed.  At this point progress stops.  Eventually I cancel out of the dialog, exit pitivi and find the rendered file, but it's 0 bytes.  I've tried this with a variety of formats but the results are always the same.

I tried running pitivi from a term and it didn't output any warning messages except the following when I started the application:
$ pitivi
/usr/lib/pitivi/python/pitivi/application.py:255: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.mainloop.run()

I've installed ubuntu-restricted-extras and am not aware of anything else I need.  I'm running ubuntu 11.10 on a system76 pangolin performance laptop.

Does anyone have any ideas on how to fix this?

Thanks,
Glenn

---

### Post by ricardisimo on 2012-03-18
I'm having difficulty getting pitivi to render .mxf files, which are necessary if I am to use opendcp. Pitivi appears to be my only option, sadly. Rendering proceeds smoothly (or so it seems) until progress hits 100% and one second remains. Then it just hangs (doesn't freeze, mind you). I can cancel the process, but the resulting mxf file is 0 bytes in size.

I may have another option, which is to produce .m2v files, which opendcp can transform into .mxf. Anyone know how to do that, either with pitivi or another editor?

P.S. - This is a duplicate post, but I think this one is in the correct forum.

---

### Post by IGetMad on 2012-07-13
I can not save any video, too. It will always show "100 %" and stall.

Pretty useless if you cannot export the video. What is wrong there?

---

### Post by gdgilda on 2012-07-13
FWIW, I switched to using openshot which exported fine and never looked back.

Glenn

---

### Post by cotcot on 2012-07-14
Not sure if it will help but it might be worth to try.
Pitivi uses Gstreamer. Check if you have gstreamer0.10-plugins-bad and gstreamer0.10-plugins-ugly installed.

---

