---
title: "libva demo mpeg2vldemo failed"
date: 2015-12-22
forum: Multimedia Software
---

### Post by darrell4 on 2015-12-22
Hi,
I am using vaapi to hardware-decode h.264 streams on Ubuntu 14.04 32-bit, running on a Celeron J1800.
When I had used apt-get to install libva1 1.3.0, i965-va-driver 1.3.0, and mplayer-vaapi and the things relevant, mplayer succeeded to play H.264 videos smoothly with the following command.
```

mplayer -vo vaapi xxx.xx

```

However, after I removed all the software packages above and compiled and installed libva-1.3.0.tar.bz2 and libva-intel-driver-1.3.0.tar.bz2 from freedesktop.org, and ran the command below,
```

mpeg2vldemo 1

```
the demo failed, prompting va_put_surface() failed.
When I debugged this program, I found out va_put_surface() returned 1, VA_STATUS_ERROR_OPERATION_FAILED.

When I was compiling libva-1.3.0 I didn't get any error, well I did receive some warnings.

So which step of my verification might contain errors? Since I guess the unmodified examples directly downloaded from freedesktop.org should be correct originally.

Thanks.

---

