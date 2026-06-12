---
title: "xv output Purple screen? - reinstall XV?"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by ikkefc3 on 2007-10-21
I have compiled Mplayer from source (see [http://smspillaz.wordpress.com/2007/10/18/unlocking-the-full-video-potential-of-your-video-card]("http://smspillaz.wordpress.com/2007/10/18/unlocking-the-full-video-potential-of-your-video-card") tutorial).
The screen is purple in all mediaplayers when I use Compiz Fusion, so is there a way to revert back to the "old" xv / reinstall xv?
I have tried reinstall all packages with xv in synaptic, but that still doesn't help.

---

### Post by jimmi3987 on 2008-02-25
I _did_ get xv  to work on Ubuntu 7.10 but I had to follow the steps in

[http://blog.trivadis.com/blogs/yannneuhaus/archive/2007/09/19/xv-an-image-viewer-quot-on-ubuntu-7-04.aspx](http://blog.trivadis.com/blogs/yannneuhaus/archive/2007/09/19/xv-an-image-viewer-quot-on-ubuntu-7-04.aspx)

Many of the apt-get actions did not do anything: some libraries simply did not exist and some were already there on my machine and in upgraded form - I don't know why my machine is any different to the ones referred to above. Sorry, I just can't remember which ones did something and which were irrelevant - most were irrelevant - but do them all to be sure.

Even that didn't quite work because when tried to make it, it had syntax errors. so I edited the file xv.h adding:

   #define FALSE 0
   #define TRUE  1

near the top somewhere. Then (still in xv.h) I had to delete the existing line:
 
  #include <X11/Intrinsic.h>

and replace it with:

    #include <X11/Xresource.h> 

Then I had to edit the file xvgrab.c, changing line number 527:

    Pixel red, green, blue, red1, green1, blue1;

to:

    int red, green, blue, red1, green1, blue1;

then it compiled and I could finally do a 

   make install

and it ran.

Notes about my system: my version of 7.10 is so recently created that it has to be very standard. I have kept it updated it. It surprises me a bit that the file `X11/Intrinsic.h' is not there. but it just isn't any more. Apparently the world moves on, even just since last October.

Jim

---

