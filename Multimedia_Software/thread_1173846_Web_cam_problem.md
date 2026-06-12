---
title: "Web cam problem"
date: 2009-05-30
forum: Multimedia Software
---

### Post by robert_ugo on 2009-05-30
I'm using Kubuntu 9.04 and i have problem with my camera.
My webcam is Creative Vista Plus.
via [http://mxhaard.free.fr/spca5xx.html:](http://mxhaard.free.fr/spca5xx.html:)
Creative 191 0x041e 0x4028 Vista Plus Pac207 Pac207 Yes gbrg spca5xx ****
output from v4lctl -c /dev/video0 list:
```
attribute  | type   | current | default | comment
-----------+--------+---------+---------+-------------------------------------
norm       | choice | (null)  | (null)  |
input      | choice | pac207  | pac207  | pac207
bright     | int    |       4 |       4 | range is 0 => 255
exposure   | int    |      26 |       5 | range is 5 => 26
Auto Gain  | bool   | on      | on      |
gain       | int    |      31 |       9 | range is 0 => 31
```
output from v4l-conf:
```
v4l-conf: using X11 display :0.0
dga: version 2.0
WARNING: No DGA direct video mode for this display.
mode: 1680x1050, depth=24, bpp=32, bpl=6720, base=unknown
/dev/video0 [v4l2]: no overlay support
```

and probles is skype works correctly with adding "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so" but software created with using OpenCV don't work (without adding LD_PRELOAD my webcam is not visible for opencv and with using it i have craped image).

Is there any solution for that? :(

---

### Post by robert_ugo on 2009-05-31
I made a screenshot with sample program using opencv with "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so". You can see there my hand and part of my face.
Maybe it will help in solve this problem.

source code (to get a frame)
```

#include <opencv/cv.h>
#include <opencv/highgui.h>
...
CvCapture* m_capture;
IplImage* m_image;
...
m_capture = cvCaptureFromCAM(-1);
cvGrabFrame(m_capture);
m_image = cvRetrieveFrame(m_capture);
...

```

---

### Post by libra1780 on 2009-07-02
v4l1compat.so is only a compatibility interface from v4l2 to v4l. if you pleoad it, you just tell the app that you have v4l instead of v4l2. the supported functions depend from the libv4l projekt. you'll find it at linuxtv.org

it's up to them

---

