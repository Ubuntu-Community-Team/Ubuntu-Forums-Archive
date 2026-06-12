---
title: "XVideo not working, but it appears in xdpyinfo."
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by grendel_khan on 2006-06-10
My XVideo extension isn't working:
```
$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present
```
But it appears in my extension list:
```
$ xdpyinfo
...
number of extensions:    31
...
    XVideo
...
```
I also see it in /var/log/Xorg.0.log:
```
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
```
Any idea what might be happening? It's not really bothering me at the moment; I'm using the gl2 output driver for mplayer now instead of xv, and it's working fine, but I am curious as to why xdpyinfo and xvinfo disagree.

I'm running xserver-xorg 7.0.0-0ubuntu4, with xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-1 for my ATI video card.

---

### Post by neoflight on 2006-06-21
[QUOTE=grendel_khan]My XVideo extension isn't working:
```
$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present
```
But it appears in my extension list:
```
$ xdpyinfo
...
number of extensions:    31
...
    XVideo
...
```
I also see it in /var/log/Xorg.0.log:
```
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
```
Any idea what might be happening? It's not really bothering me at the moment; I'm using the gl2 output driver for mplayer now instead of xv, and it's working fine, but I am curious as to why xdpyinfo and xvinfo disagree.

I'm running xserver-xorg 7.0.0-0ubuntu4, with xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-1 for my ATI video card.[/QUOTE]


i had the same problem and solved it by

```
 sudo aticonfig --overlay-type=Xv
```

and restart X by **alt+ctrl+backspace**

---

