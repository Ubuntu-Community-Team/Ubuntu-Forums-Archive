---
title: "Problems with using DV camera as webcam (with dv4l)"
date: 2009-01-28
forum: Multimedia Software
---

### Post by andersgb on 2009-01-28
Hi

ref. this post: [http://ubuntuforums.org/showthread.php?t=664596](http://ubuntuforums.org/showthread.php?t=664596)

I want to use my DV camera as a webcam in internet applications (like skype).

It can capture video perfectly well in kino, but I can't get it to work with dv4l. When I fire up dv4l and start vlc or camorama, I can see the first frame, but that's it. In skype I can't see anything when I test the camera.

If I start dv4l with debugging: dv4l -v 2
```
use /dev/video1 in your webcam application
dv4l.c +757: mmap_mode
dv4l.c +247: VIDIOCGCAP
dv4l.c +251: VIDIOCGCHAN
dv4l.c +255: VIDIOCSCHAN
dv4l.c +267: VIDIOCGWIN
dv4l.c +259: VIDIOCGPICT
dv4l.c +272: VIDIOCSPICT depth 24 palette 4
dv4l.c +259: VIDIOCGPICT
dv4l.c +272: VIDIOCSPICT depth 24 palette 15
dv4l.c +263: VIDIOCGMBUF
dv4l.c +354: unsupported ioctl 0xffffffff
dv4l.c +354: unsupported ioctl 0xffffffff
dv4l.c +354: unsupported ioctl 0xffffffff
dv4l.c +354: unsupported ioctl 0xffffffff
dv4l.c +354: unsupported ioctl 0xffffffff
dv4l.c +354: unsupported ioctl 0xffffffff
dv4l.c +354: unsupported ioctl 0xffffffff
dv4l.c +354: unsupported ioctl 0xffffffff
dv4l.c +354: unsupported ioctl 0xffffffff
dv4l.c +354: unsupported ioctl 0xffffffff
dv4l.c +354: unsupported ioctl 0xffffffff
dv4l.c +354: unsupported ioctl 0xffffffff
dv4l.c +354: unsupported ioctl 0xffffffff
dv4l.c +354: unsupported ioctl 0xffffffff
dv4l.c +354: unsupported ioctl 0xffffffff
dv4l.c +354: unsupported ioctl 0xffffffff
dv4l.c +354: unsupported ioctl 0xffffffff

```

and then start vlc and open /dev/video1:
```
VLC media player 0.8.6e Janus
[00000289] logger interface: using logger...
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed syncing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed syncing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed syncing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed syncing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed syncing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame
[00000296] v4l demuxer error: failed capturing new frame

```

both this errors continues until I stop vlc. 

I saw other people with the same problem in the post i referred to, but not an answer to the problem. Can anyone help?

---

