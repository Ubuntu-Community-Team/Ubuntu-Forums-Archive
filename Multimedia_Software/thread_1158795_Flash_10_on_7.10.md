---
title: "Flash 10 on 7.10?"
date: 2009-05-14
forum: Multimedia Software
---

### Post by Jiawen on 2009-05-14
I've got long-term problems watching YouTube videos in Firefox 3. When I click the FlashBlock icon to let YouTube play the video, the player screen is just a black rectangle. Nothing to click, nothing plays. Reloading doesn't help. Downloading the videos with DownloadHelper allows me to play them with VLC, but that's far from ideal. I can do things with a lot of other Flash sites. Desktop Tower Defense works fine, for example.

On the theory that it was because YouTube had updated to Flash 10 (I had been running Flash 9), I upgraded to 10. But I still have the same problem. YouTube videos don't work. (I can still download them, and DTD and other flash content works fine.)

Please help! Thanks.

---

### Post by Bigneil on 2009-05-14
I had some similar issues with youtube videos. make sure you have all the right updates and codecs. also if you remove all the flashplayer or players from you pc and download the one from the repositories instead of the one from the adobe website it could make all the difference.   here is a link to another simelar thead that helped me.  >[http://ubuntuforums.org/showthread.php?t=1074523]("http://ubuntuforums.org/showthread.php?t=1074523")


Good luck and remember to have a good read of the the sticky about video amd media

---

### Post by gandaran on 2009-05-14
> **Jiawen said:**
> I've got long-term problems watching YouTube videos in Firefox 3. When I click the FlashBlock icon to let YouTube play the video, the player screen is just a black rectangle. Nothing to click, nothing plays. Reloading doesn't help. Downloading the videos with DownloadHelper allows me to play them with VLC, but that's far from ideal. I can do things with a lot of other Flash sites. Desktop Tower Defense works fine, for example.

On the theory that it was because YouTube had updated to Flash 10 (I had been running Flash 9), I upgraded to 10. But I still have the same problem. YouTube videos don't work. (I can still download them, and DTD and other flash content works fine.)

Please help! Thanks.
how did you install the flashblock addon? from the repos or mozillas addon website? the one from repositories is outdated, if this is the one you have remove it.
and try the flash videos without flashblock installed just to ensure it's not a adobe flash problem.

---

### Post by _Purple_ on 2009-05-14
7.10 has reached end of life and the repositories might not work anymore. Why don't you upgrade?

---

### Post by Jiawen on 2009-05-14
> **Bigneil said:**
> I had some similar issues with youtube videos. make sure you have all the right updates and codecs. also if you remove all the flashplayer or players from you pc and download the one from the repositories instead of the one from the adobe website it could make all the difference.   here is a link to another simelar thead that helped me.  >[http://ubuntuforums.org/showthread.php?t=1074523]("http://ubuntuforums.org/showthread.php?t=1074523")I didn't see a solution there other than what I've already tried. Thanks for pointing me to it, though. 

The player in the repositories for 7.10 doesn't work for Flash 10. The .deb for Flash 10 doesn't work with 7.10 (requires libcairo2, which7.10 apparently doesn't have).
> **gandaran said:**
> how did you install the flashblock addon? from the repos or mozillas addon website? the one from repositories is outdated, if this is the one you have remove it.
and try the flash videos without flashblock installed just to ensure it's not a adobe flash problem.As I mentioned, a lot of Flash content works just fine, and Flashblock works just as it should. Even with Youtube, Flashblock works as it should; it's just that, after I click the "play" button to allow Flash content, there's nothing there in YouTube.

I've tried installing both from the repositories and from the Adobe website. The package in the repositories, as I mentioned above, only goes up to Flash 9. The Flash 10 .deb package on Adobe's site has dependencies that 7.10 can't support.
> **_Purple_ said:**
> 7.10 has reached end of life and the repositories might not work anymore. Why don't you upgrade?Because 7.10 is working well enough as it is, and every time I upgrade, a dozen packages are broken, and bloat increases, and my system slows down.

---

### Post by gandaran on 2009-05-14
> As I mentioned, a lot of Flash content works just fine, and Flashblock works just as it should. Even with Youtube, Flashblock works as it should; it's just that, after I click the "play" button to allow Flash content, there's nothing there in YouTube.
youtube should work fine with flash 9, are you sure firefox is using adobe flash and not some open source flash like swfdec or gnash?

---

### Post by Jiawen on 2009-05-14
About: plugins gives me:```
    File name: libflashplayer.so
    Shockwave Flash 10.0 r22
```So yes, it's using the actual Flash player.

---

