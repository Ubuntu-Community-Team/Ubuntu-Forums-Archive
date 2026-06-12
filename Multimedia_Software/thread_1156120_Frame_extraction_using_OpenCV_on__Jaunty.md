---
title: "Frame extraction using OpenCV on  Jaunty"
date: 2009-05-11
forum: Multimedia Software
---

### Post by bogdan_negru on 2009-05-11
First of all I should say that I`m relatively new to the Linux world.
I am writing an application in which I have to extract frames by index from .avi files. I have implemented a function that does this using OpenCv. My code is:

```

...
CvCapture *capture = cvCreateFileCapture("path/to/avi/file");
cvSetCaptureProperty(capture, CV_CAP_PROP_POS_FRAMES, frameIndex);
cvGrabFrame(capture);
IplImage *frame = cvRetrieveFrame(capture);
...

```

Everything worked fine until last week when I upgraded to Ubuntu 9.04. First I had problems with simply running OpenCV - FFMPEG related. I solved those using [http://ubuntuforums.org/showthread.php?t=1076793&highlight=opencv]("http://ubuntuforums.org/showthread.php?t=1076793&highlight=opencv")

Now, I have problems with cvSetCaptureProperty, it does nothing. The call in my code should jump to the specified frame. The documentation at [http://opencv.willowgarage.com/wiki/HighGui#cvSetCaptureProperty]("http://opencv.willowgarage.com/wiki/HighGui#cvSetCaptureProperty") says this: 
> ...
NB This function currently does nothing when using the latest CVS download on Linux with FFMPEG (the function contents are hidden using #if 0 and it returns 0)

Judging by this, it is normal that my code does not work. I have tried to configure OpenCV to use gstreamer:

Using the "latest tested snapshot": svn co [https://opencvlibrary.svn.sourceforge.net/svnroot/opencvlibrary/tags/latest_tested_snapshot](https://opencvlibrary.svn.sourceforge.net/svnroot/opencvlibrary/tags/latest_tested_snapshot)

[HTML]$> autoreconf --force
$> ./configure --with-gstreamer
$> make
$> sudo make install
$> sudo ldconfig[/HTML]

I get the following errors on make:

[HTML]make[2]: *** No rule to make target `cv/cvoptflowbbw.cpp', needed by `cvoptflowbbw.lo'.  Stop.
make[2]: Leaving directory `/home/opencv/latest_tested_snapshot/opencv/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/opencv/latest_tested_snapshot/opencv'
make: *** [all] Error 2[/HTML]

Can anyone help me with this?

---

