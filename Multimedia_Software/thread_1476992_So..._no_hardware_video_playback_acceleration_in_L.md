---
title: "So... no hardware video playback acceleration in Lucid?"
date: 2010-05-08
forum: Multimedia Software
---

### Post by stelekpl on 2010-05-08
A month ago I've made this post:
[http://ubuntuforums.org/showthread.php?t=1447595](http://ubuntuforums.org/showthread.php?t=1447595)
hoping that it would change something with the respect to video playback acceleration in Ubuntu for the 10.04 release.

Today I installed the latest Ubuntu, added VLC and... the acceleration is not there. When I compiled VLC myself on 9.04 I had a checkbox to enable hardware acceleration in the FFMPEG codec settings but this checkbox is not present in the VLC that was downloaded to my 10.04 by default.

So... am I doing something wrong or is the hardware acceleration simply not there? And what do I have to do to enable it?

Is FFmpeg in 10.04 compiled with VAAPI support?
Is VLC in 10.04 compiled with VAAPI support?

Do I need to recompile both or just on of them?

Please help, because I have just updated my system and now I'm not able to watch the family movies from my HD camcorder.

References:
[http://wiki.videolan.org/VLC_VAAPI](http://wiki.videolan.org/VLC_VAAPI)

---

### Post by xzero1 on 2010-05-08
If you have the right hardware....
[http://ubuntuforums.org/showthread.php?t=1385896]("http://ubuntuforums.org/showthread.php?t=1385896")

---

### Post by stelekpl on 2010-05-08
Seems my solution is here:
[https://edge.launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia](https://edge.launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia)

Installed and it works. It's just a pity that I had to spend half a day looking for it. Really wish it was included in the default packages...

---

