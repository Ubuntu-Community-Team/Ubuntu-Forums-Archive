---
title: "Xserver crashes randomly since 32bit ubuntu 12.04 LTS upgrade (NVidia 8500GT)"
date: 2012-05-09
forum: Multimedia Software
---

### Post by helix_r on 2012-05-09
My desktop has been crashing randomly since I've upgraded to ubuntu 12.04 LTS. There is no strong pattern to the crashes (I can't repeat them at will) but they seem to occur most often during media playback (eg Youtube or VLC).

What happens is that the screen goes black for a couple of seconds and then I am presented with a GUI login prompt. After logging back in, all apps have been shut down. I see the following segmentation fault in /var/logs/Xorg.0.log.old

```

[ 54766.300] 3: /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so (0xcad8000+0x63d38) [0xcb3bd38]
[ 54766.301] Segmentation fault at address (nil)
[ 54766.301] 
Caught signal 11 (Segmentation fault). Server aborting
[ 54766.301] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
```

This appears to be a known bug ([Bug #980519]("https://bugs.launchpad.net/ubuntu/+bug/980519")). The comments in the bug report indicate some promising work-around, but I am not confident about applying it.

[One of the comments talks about applying a "PPA"]("https://bugs.launchpad.net/ubuntu/+bug/980519/comments/47"). I don't know how to do that. Can someone explain what is a PPA and how do I apply it (without scewing up future updates related to nVidia drivers)? I have a feeling it will take forever to get this problem fixed, otherwise.

I wish I had waited to update to 12.04 LTS!

Thanks!

---

