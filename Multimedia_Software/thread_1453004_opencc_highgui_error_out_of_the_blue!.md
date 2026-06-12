---
title: "opencc highgui error out of the blue!"
date: 2010-04-12
forum: Multimedia Software
---

### Post by iochinome on 2010-04-12
Hey guys, so i am developing an application with opencv and i suddenly got this error out of the blue-

HIGHGUI ERROR: V4L2: Pixel format of incoming image is unsupported by OpenCV
Unable to stop the stream.: Device or resource busy
Unable to stop the stream.: Bad file descriptor
HIGHGUI ERROR: V4L: Pixel format of incoming image is unsupported by OpenCV


everything was working, then it reverted to giving off this error. the webcameras that i am using both work with guvcview. (but, another error that somebody might be able to instruct me on, they cannot both stream at 640 by 480p at 30 fps whereas they previously could... the error it gives is 
VIDIOC_STREAMON - Unable to start capture: No space left on device
VIDIOC_STREAMON - Unable to start capture: Device or resource busy
)

any advice?? anybody know what is up?? thanks!

---

### Post by vlad75 on 2010-08-08
I have the same problem.

---

### Post by giancarlocp on 2010-12-23
I was trying install **touchlib** follow instruction from [http://karuppuswamy.com/wordpress/2010/07/27/diy-installing-touchlib-based-cheaper-touch-pad-on-ubuntu-10-04/](http://karuppuswamy.com/wordpress/2010/07/27/diy-installing-touchlib-based-cheaper-touch-pad-on-ubuntu-10-04/)

execute ```
~/touchlib/src$ ./configapp
``` do the same error.

---

### Post by giancarlocp on 2010-12-23
I install **openvc** following [http://www.brue.org/2010/02/compilando-opencv-2-en-debian/](http://www.brue.org/2010/02/compilando-opencv-2-en-debian/)

and recompile **TouchLib** and it's "working", but now:
```

mmap: Invalid argument
munmap: Invalid argument
munmap: Invalid argument
munmap: Invalid argument
munmap: Invalid argument
Unable to stop the stream.: Bad file descriptor
munmap: Invalid argument
munmap: Invalid argument
munmap: Invalid argument
munmap: Invalid argument

```

---

