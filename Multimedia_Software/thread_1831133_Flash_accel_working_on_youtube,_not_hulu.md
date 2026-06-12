---
title: "Flash accel working on youtube, not hulu"
date: 2011-08-22
forum: Multimedia Software
---

### Post by pulpinator on 2011-08-22
Any time I've searched, I can't find a thread with this problem, sorry! So, I have Lucid, flash 10.3, and whether I'm running Chrome or Firefox, I can get full-screen HD video to play perfectly on youtube using hardware acceleration. I right-click, view video information, and sure enough, it's using hardware decoding.

So what's the problem? Well, full screen on hulu or espn3 is just as choppy as with no hardware video acceleration (and the right-click "view video information" menu option is not there!).

Anybody have any ideas what's going on?

---

### Post by pulpinator on 2011-08-23
An update. I ran flash-aid, and it made it worse. It installed flash 11.x beta, and now I can't even get youtube to have video rendering be hardware accelerated.

So anyway, I went into Chrome and disabled the firefox plugin (which is now 11.x), and it went back to using Chrome's built-in flash player, which is 10.3.

Again, youtube in full screen looks GREAT, but hulu is choppy in full screen. And of course Firefox is now choppy on both.

---

### Post by beew on 2011-08-23
> **pulpinator said:**
> An update. I ran flash-aid, and it made it worse. It installed flash 11.x beta, and now I can't even get youtube to have video rendering be hardware accelerated.

So anyway, I went into Chrome and disabled the firefox plugin (which is now 11.x), and it went back to using Chrome's built-in flash player, which is 10.3.

Again, youtube in full screen looks GREAT, but hulu is choppy in full screen. And of course Firefox is now choppy on both.

Flash-aid asks you whether you want to install the latest beta version of flash or the stable version. Just re-run it and choose the stable version, it will remove the beta version and reinstall the stable one.

I can confirm that the beta version doesn't work with VDPAU. I have now reverted to the stable version and Youtube works fine in Firefox.

It seems that Flash only uses vdpau on some sites but not others.

---

### Post by pulpinator on 2011-08-23
> **beew said:**
> Flash-aid asks you whether you want to install the latest beta version of flash or the stable version. Just re-run it and choose the stable version, it will remove the beta version and reinstall the stable one.

I can confirm that the beta version doesn't work with VDPAU. I have now reverted to the stable version and Youtube works fine in Firefox.

It seems that Flash only uses vdpau on some sites but not others.

Thanks! You're correct, after choosing the stable version I now have VDPAU acceleration working in Youtube again. However, I still don't have it on hulu or espn3.

Do you know why vdpau works on some sites but not others?

---

