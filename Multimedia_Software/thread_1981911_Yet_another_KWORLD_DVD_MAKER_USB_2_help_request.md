---
title: "Yet another KWORLD DVD MAKER USB 2 help request"
date: 2012-05-17
forum: Multimedia Software
---

### Post by powermeep on 2012-05-17
I've been scanning the Internet for ages over the past two or three years now, and have yet to find a solution for this.

I picked up a Kworld DVD Maker USB 2 sometime in 2010, and I'm trying to use it to capture some old VHS's to my media pc before they go kaput.

I'm using Ubuntu 10.04 64bit, I've installed cheese, and the device is recognized under the name em28xx, which is correct, but the output cheese produces is a black screen with a green bar at the bottom.

I've installed Kino, but I hit the fabled roadblock of "/dev/raw1394 module not loaded or cannot read/write /dev/raw1394", and none of the solutions I've tried have made that work (yes, the file is there, with crw-rw-rw- permission, and the driver IS loaded, so I don't have any clue).

Any attempts I've made to display the video from the device in either mplayer or the v4l2 config i found in the repository have only shown my webcam, regardless of what was selected for input device.

And any forum I've found on this topic for anything after 9.10 has just been ignored. Seriously, we need one solution that actually works, and then make it known so that others can just read that.

---

