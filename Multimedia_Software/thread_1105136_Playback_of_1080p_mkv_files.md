---
title: "Playback of 1080p mkv files"
date: 2009-03-24
forum: Multimedia Software
---

### Post by colo505 on 2009-03-24
Opteron 165/ 2 GB DDR400/ NVIDIA 8600GT
Ubuntu Intrepid AMD64/ NVIDIA Driver 180.35


I am using Intrepid with the latest kernel and NVIDIA driver. Playback of 1080p mkv files is choppy in mplayer/ vlc/ totem-xine, totem-gstreamer, while Media player classic plays them smoothly in Vista 64-bit.

Shall appreciate any help.

Thanks

---

### Post by Bachstelze on 2009-03-24
[CoreAVC]("http://ubuntuforums.org/showthread.php?t=1034075") might (read: will) help.

---

### Post by sloggerkhan on 2009-03-24
I have a similar setup. NVIDIA's new video accel API helps a lot. There are patches for mplayer, ffmpeg, myth, etc. Also, you can try can using multithreaded ffmpeg. A lot of apps don't multithread by default even if it's an option.

 Unless you're outputing to a larger than 32" TV or monitor, 1080P is probably unecessary, though.

---

### Post by colo505 on 2009-03-24
I have already tried CoreAVC.

I have a Dell 24" full HD monitor, and direct rendering is enabled for the NVIDIA 7300GT card, using 180.35 driver.

---

