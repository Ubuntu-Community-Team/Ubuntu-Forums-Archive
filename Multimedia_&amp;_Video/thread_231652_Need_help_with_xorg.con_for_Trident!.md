---
title: "Need help with xorg.con for Trident!"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by mojoman on 2006-08-07
Hi everyone!

I've been having problems with my Trident CyberBlade graphic card and after an earlier post on it I got help to pinpoint the problem and made some headway but as some problems remain I thought I'd give it an other try. ](*,) Sorry if it is a bit long but I might as well give as much info as possible so here it is.

Xorg.0.log states DDC-rates are not within their ranges so I gather that the refreshment rate is not correct.

In xorg.conf it is set to 28-51 for horizontal and 43-60 for vertical. The manual states that for 1024x768 SVGA the vertical rate is 60/75/85 Hz and the horizontal rate is 48,3/60/68,7 kHz (no other resolution is set in xorg.conf though 1024x768 is just fine by me). I did try to change xorg.conf to the values given in the manual but x-session wouldn't start due to unexpected values. I think xorg.conf wants the values either as a range with a "-" or as discrete values separated with "," or "/" and that the combination made it crash but I don't know how to state them correctly (if this is in fact the problem)

Xorg.0.log also shows error /usr/share/X11/fonts/cyrillic doesn't exist but I don't know if that has any impact.

Finally, Xorg.0.log states:

> (EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument

Direct rendering is not on.

Also, when I run glxgears the cogs that show up hardly moves and I get the following error message.

```
X connection to :0.0 broken (explicit kill or server shutdown).
```

At first I thought my problems were due to the 3D-driver that wasn't enabled. However, it may not even exist a 3D driver and the accelerated driver might only work in 2D. For me, the 3D driver really isn't that important (though it would be a nice bonus) but I would really like to be able to play movies with the DVD and use the TV-Out. When I try to play video or DVD it gets out of sync and it's playing jerky. 

I got some really good help last time I posted which got me this far and if anyone could help me out to make it the last stretch I sure would appreciate it. :D 

Best regards
/Mojoman

ps: I'm posting the xorg.conf and the Xorg.0.log here as well. ds

---

