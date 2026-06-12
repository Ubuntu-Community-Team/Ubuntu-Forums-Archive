---
title: "TwinView functioning improperly when second X screen is enabled"
date: 2007-08-28
forum: Multimedia &amp; Video
---

### Post by waco616 on 2007-08-28
Hello - 

I am having an issue with a Nvidia Geforce 6800 with 2 monitors attached and a Nvidia Fx5200 with one monitor attached.

The original configuration of TwinView on the two monitors attached to the 6800 works great. The monitors are on one TwinView screen, but behave as 2 separate screens - maximized windows only maximize on one monitor and the gnome menu panel spans only 1 monitor, yet I can drag windows across both monitors.

When i enable the third monitor on the second card as a separate X screen, leaving the other two monitors as a TwinView screen (how it was), it works... except the behavior of the TwinView screen changes -  both TwinView monitors are treated as one large screen, maximizing windows across both monitors and spanning the gnome panel across both monitors.

The desired result is two monitors in a properly functioning TwinView mode attached to the 6800, and one monitor attached to the 5200 on a separate X screen.

I would use xinerama but i would like to use beryl, which currently only works with TwinView monitors, not xinerama.

If any information is needed i will gladly provide it.

---

### Post by maxsteri on 2007-08-30
I am in the same situation and have the same goal (two monitors in a properly functioning TwinView mode, and one monitor on a separate X screen).

After many hours of trial and error I have concluded that (for me at least) it is not possible, none for the three possible solutions seam to fit the bill. 

The three solutions I came across were::
- 3 separate X screens, which does not allow the dragging of windows across screens.
- Xinerama. This only allows me to run a single X screen, meaning that windows will occasionally open on the third monitor, which is a TV and not always turned on.
- TwinView and a separate X screen. This causes windows on the TwinView screens to maximize across both the screens, which is unbelievably !annoying! and kills my productivity. 

During my (extensive) Googling I came across a thread which sounds like it may help you to reach your desired result ([http://www.nvnews.net/vbulletin/showthread.php?t=85604](http://www.nvnews.net/vbulletin/showthread.php?t=85604)). This solution did not help me as this patch only supports monitors using the same resolution, and one of my monitors uses a  different resolution to the other two.

Additionally I found another thread ([http://www.nvnews.net/vbulletin/showthread.php?t=79870](http://www.nvnews.net/vbulletin/showthread.php?t=79870)) which suggests that mixing an ATI card with an Nvidia card allows triple head TwinView to work as desired. Whilst I have my doubts about this, I am going to get hold of a secondhand ATI card and give it a shot.

It would be nice to know if you get anywhere with this as it will undoubtedly help me in the future, and if anyone has any information that may help me reach the desired result it would be gratefully received!

---

### Post by waco616 on 2007-08-30
Under the same thread i see there is a [another patch ]("http://www.nvnews.net/vbulletin/showpost.php?p=1177837&postcount=10") listed, which allows spoofing of xinerama information via the xorg.conf file.  This is probably the route i will go, and i dont think you'll be limited by your differing resolutions with this patch.

Let me know if it works for you

---

