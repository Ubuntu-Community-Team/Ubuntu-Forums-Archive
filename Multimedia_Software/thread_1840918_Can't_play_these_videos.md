---
title: "Can't play these videos"
date: 2011-09-08
forum: Multimedia Software
---

### Post by Nisal on 2011-09-08
HI,

I can't play some video's, it says my VGA Is not compatible , but i can play same videos on windows with this graphic cards,

Is there any way to solve this matter ? and my ubuntu version is 10.10

---

### Post by papibe on 2011-09-08
It looks like the message refers to the accelerations capabilities of your graphic card. If you have a a fast enough processor may be the video can be played using just the CPU (disabling acceleration on VLC).

What is your graphic card and CPU?

Regards.

---

### Post by .... on 2011-09-08
Note that VLC only supports VA-API for video acceleration. If you have an nvidia card, and you're using the nvidia driver, then you need this: [http://www.splitted-desktop.com/~gbeauchesne/vdpau-video/pkgs/](http://www.splitted-desktop.com/~gbeauchesne/vdpau-video/pkgs/)

To make sure video accel is working, look at vainfo:
```
sudo apt-get install vainfo
vainfo
```

---

### Post by Nisal on 2011-09-09
@papibe well the problem is why this same video play one windows but not in ubuntu ?

@.... no its not nvidia 

Anyway M player did solve the problem with some configurations but still cant play on vlc

---

### Post by papibe on 2011-09-09
> **Nisal said:**
> @papibe well the problem is why this same video play one windows but not in ubuntu ?
I'm afraid HD playback in Lunux is somehow limited, and not as available as in Windows.

For some time the combo Nvidia cards, proprietary driver, vdpau and mplayer (or XBMC) has been the most stable and functional way to reproduce HD videos.

Lately thanks to vaapi, ATI/AMD cards are being also able to reproduce HD videos using VLC, or a special version of mplayer. However you either have to use 11.04 or (maybe and) ppa's  (check ....'s post).

Regards.

---

### Post by Nisal on 2011-09-09
> **papibe said:**
> I'm afraid HD playback in Lunux is somehow limited, and not as available as in Windows.

For some time the combo Nvidia cards, proprietary driver, vdpau and mplayer (or XBMC) has been the most stable and functional way to reproduce HD videos.

Lately thanks to vaapi, ATI/AMD cards are being also able to reproduce HD videos using VLC, or a special version of mplayer. However you either have to use 11.04 or (maybe and) ppa's  (check ....'s post).

Regards.

yes i should upgrade i think, i miss the ship it programme because it is kind of hard to download with this limited internet connections :(

---

