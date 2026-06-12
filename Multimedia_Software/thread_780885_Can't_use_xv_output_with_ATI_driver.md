---
title: "Can't use xv output with ATI driver?"
date: 2008-05-03
forum: Multimedia Software
---

### Post by thebordella on 2008-05-03
I'm knee-deep in customizing my new Hardy install. Thinkpad T60 w/ATI x1400 video (3GB ram).

Out of the box, desktop effects (compiz) would not work. Not sure which driver Ubuntu was using on install, but I grabbed Envy and installed the latest (8.3?) ATI proprietary driver. Worked like a charm. Installed Compiz Fusion, desktop effects all work great -- fast, smooth.

The only issue is the quality of video playback. I've got totem, mplayer/smplayer, and VLC installed. Codecs installed. Testing with all sorts of video files, including DVD VOB (mpg2). Everything plays, but the video quality at full screen looks pixelated. It reminds me of what software rendering looks like under Windows. (When I boot into Vista on this laptop and play the same files, they are sharp and silky smooth at full screen -- presumably due to hardware acceleration?)

I was toying with the video output options in SMplayer. It is set to X11 output. I tried changing this to XV, thinking maybe this would use the hardware overlay. But it doesn't work -- mplayer crashes and/or the seek timer advances but without any video. X11 output mode works, but it has that "software rendering" look to it.

Am I missing something? Is it possible to use the ATI drivers+compiz+overlay video playback? As it is now, video playback isn't exactly terrible, and at less than full screen it looks pretty good. But there is definitely a difference in full screen compared to Windows. There is a softness, pixelation, and even some frame dropping under Ubuntu and I'm not sure why.

thanks!

---

### Post by macaholic on 2008-05-03
You are right, it is a driver issue. The fat of the matter is, the ATI drivers for linux aren't that great. There are mixed reports of how the different video methods work, If I recall correctly, xv was supposed to be fixed in 8-3, but I could be wrong. Btw, the latest is 8-4, envy is often times behind.

---

### Post by mc4man on 2008-05-03
i don't have ati but this post made sense 
[http://ubuntuforums.org/showthread.php?p=4800734#post4800734](http://ubuntuforums.org/showthread.php?p=4800734#post4800734)
I'd do a little searching based on that.
Also have seen the command like this
sudo aticonfig --overlay-type=Xv

---

