---
title: "Videos Full Screen to the Wrong Monitor"
date: 2013-10-29
forum: Multimedia Software
---

### Post by Michael_Peterson on 2013-10-29
When I use Google Chrome to watch a video and go to full screen, it will full screen on my secondary monitor no matter where the window is. With Firefox it works correctly, but I would prefer to use Chrome if I can get this fixed.

I have a dual monitor setup with a Samsung P2370 main display and a laptop screen as a secondary display.

If my specs would help,
Here is a link to my monitor: [http://www.newegg.com/Product/Product.aspx?Item=N82E16824001330](http://www.newegg.com/Product/Product.aspx?Item=N82E16824001330)
Here is a link to my laptop: [http://www.msi.com/product/nb/GT70-0NC.html#/?div=Overview](http://www.msi.com/product/nb/GT70-0NC.html#/?div=Overview)
I am using Ubuntu Gnome.

Any ideas?

---

### Post by Michael_Peterson on 2013-10-31
Bump as it's been a while.

Also I somehow put this in the wrong section. I meant to put it in the Multimedia & Video section. If anyone could move this, I would appreciate that.

---

### Post by bapoumba on 2013-10-31
> **Michael_Peterson said:**
> ..
Also I somehow put this in the wrong section. I meant to put it in the Multimedia & Video section. If anyone could move this, I would appreciate that.

Done :)

---

### Post by warp99 on 2013-10-31
This looks like it may be a bug in Chrome:

[https://code.google.com/p/chromium/issues/detail?id=153172&q=second%20monitor&colspec=ID%20Pri%20M%20Iteration%20ReleaseBlock%20Cr%20Status%20Owner%20Summary%20OS%20Modified](https://code.google.com/p/chromium/issues/detail?id=153172&q=second%20monitor&colspec=ID%20Pri%20M%20Iteration%20ReleaseBlock%20Cr%20Status%20Owner%20Summary%20OS%20Modified)

---

### Post by Michael_Peterson on 2013-11-01
> **warp99 said:**
> This looks like it may be a bug in Chrome:

[https://code.google.com/p/chromium/issues/detail?id=153172&q=second%20monitor&colspec=ID%20Pri%20M%20Iteration%20ReleaseBlock%20Cr%20Status%20Owner%20Summary%20OS%20Modified](https://code.google.com/p/chromium/issues/detail?id=153172&q=second%20monitor&colspec=ID%20Pri%20M%20Iteration%20ReleaseBlock%20Cr%20Status%20Owner%20Summary%20OS%20Modified)

That doesn't seem like the same issue. My issue is when I'm watching videos, and full screen the video, it full screens to my secondary monitor only no matter where my chrome window is.

---

### Post by Michael_Peterson on 2013-11-03
I found this google groups post with a kind of related issue - [http://productforums.google.com/forum/#!topic/chrome/NdiPhjFmbUc](http://productforums.google.com/forum/#!topic/chrome/NdiPhjFmbUc)

Their solution was to turn the secondary monitors resolution down, which worked. I also tried rotating the secondary monitor, and that worked as well. This workaround isn't very ideal, but at least it's better than having to disable my secondary monitor.

Anyone have any thoughts on this yet?

---

### Post by Michael_Peterson on 2013-11-04
I finally solved this issue by typing "[chrome://plugins/](chrome://plugins/)" in the omnibox, clicking "Details" on the top right, finding the "Adobe Flash Player" plugin, and disabling the first file which was in the location "/opt/google/chrome/PepperFlash/libpepflashplayer.so", and keeping the "/usr/lib/flashplugin-installer/libflashplayer.so" file enabled.

I'm not 100% sure, but I believe that this is disabling the default chrome flash player and using my system flash player instead. If anyone wants to confirm/correct me there, that would be appreciated.

---

### Post by bapoumba on 2013-11-04
> **Michael_Peterson said:**
> I finally solved this issue by typing "[chrome://plugins/](chrome://plugins/)" in the omnibox, clicking "Details" on the top right, finding the "Adobe Flash Player" plugin, and disabling the first file which was in the location "/opt/google/chrome/PepperFlash/libpepflashplayer.so", and keeping the "/usr/lib/flashplugin-installer/libflashplayer.so" file enabled.

I'm not 100% sure, but I believe that this is disabling the default chrome flash player and using my system flash player instead. If anyone wants to confirm/correct me there, that would be appreciated.

Yes, this is correct. Sorry I did not think of it, I've already recommended this on other circumstances..

---

### Post by Michael_Peterson on 2013-11-17
So this problem isn't as fixed as I thought. It does work for youtube videos, but a lot of other flash players are still having issues. Some of them do not full screen at all and the player just freezes. Others will full screen on the correct monitor, but it will start in the middle and cut off at the edge of the screen (It looks like it's trying to place it in the middle of both my monitors, but it doesn't get on the second one).

The same thing happens with Chromium and Firefox, so I don't have any alternatives.

The only other workaround (other than the one posted above) I have found to work is to disable one of my monitors every time I watch a video in full screen, which is obviously not very ideal.

I'm really not sure what to do at this point and I doubt I'll get much help here as I haven't gotten any yet, but I thought it was at least worth posting.

---

### Post by movielovers112 on 2013-11-17
I have this problem

---

### Post by Michael_Peterson on 2013-11-17
Well I'm glad I am not the only one with this problem. Have you been able to find any information about this besides what's here?

---

