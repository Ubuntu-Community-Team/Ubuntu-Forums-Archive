---
title: "MythTV video card question"
date: 2007-01-31
forum: Multimedia &amp; Video
---

### Post by pjman on 2007-01-31
I'm planning on setting up MythTV with my Ubuntu box. My PC has a MSI Ti-4200 128MB video card. I've read on multiple MythTV guides ([including this one]("http://www.linuxis.us/linux/media/howto/linux-htpc/video.html")) that most people recommend the FX5200 fanless series.  

I'm thinking of ordering this [one]("http://www.newegg.com/product/product.asp?item=N82E16814127181").

What would the benefits (or downsides) to installing the FX5200? Will I notice any difference with performance?

Also... I'm going to order these two Hauppauge PVR-150 cards. Does anyone see any problems that I might run into with these cards?

[http://www.newegg.com/product/product.asp?item=N82E16815116625](http://www.newegg.com/product/product.asp?item=N82E16815116625)
[http://www.newegg.com/product/product.asp?item=N82E16815116620](http://www.newegg.com/product/product.asp?item=N82E16815116620)

Thanks!

---

### Post by fenian on 2007-01-31
You shouldn't have a problem with any of those.The 5200 should reduce some of the noise from your system.I assume you are thinking of the more expensive PVR-150 for the remote control.The lower price PVR-150 that you listed is not much different (the FM tuner was the only difference I noticed),than this one which is a bit less expensive...

[http://www.newegg.com/Product/Product.asp?Item=N82E16815116633](http://www.newegg.com/Product/Product.asp?Item=N82E16815116633)

---

### Post by pjman on 2007-02-01
> **fenian said:**
> You shouldn't have a problem with any of those.The 5200 should reduce some of the noise from your system.I assume you are thinking of the more expensive PVR-150 for the remote control.The lower price PVR-150 that you listed is not much different (the FM tuner was the only difference I noticed),than this one which is a bit less expensive...

[http://www.newegg.com/Product/Product.asp?Item=N82E16815116633](http://www.newegg.com/Product/Product.asp?Item=N82E16815116633)

Nice!! I didn't see the cheaper one. Thanks!



According to [wikipedia]("http://en.wikipedia.org/wiki/Comparison_of_NVIDIA_Graphics_Processing_Units#GeForce_FX_series") The Ti-4200 supports OpenGL 1.4 and the FX5200 supports OpenGL 1.5 and limited support for 2.0. Should the level of OpenGL support be a factor with MythTV (or even Beryl/Compiz)?

---

### Post by majoridiot on 2007-02-01
> **pjman said:**
> Should the level of OpenGL support be a factor with MythTV (or even Beryl/Compiz)?

OopenGL shouldn't affect mythtv performace, unless you rely on it for timing, which i have
never gotten to work properly- so i have it disabled.  OpenGL will definitely impact beryl/compiz,
so be sure to do your research first. :D

---

### Post by heywire on 2007-02-01
I ran a "CompUSA" FX5200 with Myth -- the only problem I ran into was getting my 22" widescreen running 1680x1050 over DVI.  I had to add:

Option    "ModeValidation"    "NoMaxPClkCheck"

to my xorg.conf to get it working.

Enabling xvmc reduced my CPU usage from 100% to about 30% when playing 1080i content.  I ended up going back to my Ti4400 though, as I rarely *watch* tv on my myth backend, I usually watch it on my macbook.

---

### Post by punx45 on 2007-02-01
that first PVR-150 you linked to (the one with IR) looks like the one i bought for a mythbox, (though can't be certain i dont have exact item #s to refrence) and i have tested in both tuner and composite mode with success.   i went with a default MythDora install and the card and the remote worked, but the IR blaster needs work. (i gave up on it for the time being and am going with serial to the cable box)

---

