---
title: "Problems with opencv and ffmpeg installation"
date: 2017-06-16
forum: Multimedia Software
---

### Post by jlb222 on 2017-06-16
I am porting an application from IOS to Ubuntu and I am having problems reading MP4 files from a GOPRO in the Ubuntu environment:

[FONT=courier new]    >>> import cv2
    >>> cap = cv2.VideoCapture("test.avi")
    >>> cap.isOpened()
    True
    >>> cap = cv2.VideoCapture("GOPR0050.MP4")
    >>> cap.isOpened()
    False
    >>> [/FONT]

I have tried several times to install and compile OpenCV and FFMPEG without luck. It may be the case that I have ended with inconsistencies in the sytem. OpenCV is apparently compiled with FFMPEG, this is the output from the compilation:
 
   [FONT=courier new] --   Video I/O:
    --     DC1394 1.x:                  NO
    --     DC1394 2.x:                  NO
    --     FFMPEG:                      YES
    --       codec:                     YES (ver 56.60.100)
    --       format:                    YES (ver 56.40.101)
    --       util:                      YES (ver 54.31.100)
    --       swscale:                   YES (ver 3.1.101)
    --       resample:                  NO
    --       gentoo-style:              YES[/FONT]

However FFMPEG is not working because it complains about opencv:
[FONT=courier new]
    $ ffmpeg
    ffmpeg: error while loading shared libraries: libopencv_core.so.2.4: cannot open shared object file: No such file or directory[/FONT]

Thanks in advance

---

### Post by deadflowr on 2017-06-16
Moved to *Multimedia Software*

---

### Post by SeijiSensei on 2017-06-16
Does this help?  [https://ubuntuforums.org/showthread.php?t=2109967](https://ubuntuforums.org/showthread.php?t=2109967)  

I did a search for "libopencv_core.so.2.4" and found that.

---

### Post by monkeybrain20122 on 2017-06-16
I have compiled the latest opencv-3.2 successfully on Ubuntu 16.04. I installed ffmpeg and the libav-dev packages from this[ ppa]("https://launchpad.net/~mc3man/+archive/ubuntu/xerus-media"). You may need to update your protobuf  (remove libprotobuf-dev with apt and then compile protobuf from source, protobuf-3.2.0 worked for me) Also you need vtk version >= 7.1. I compiled vtk 7.2 from source as well.

---

### Post by jlb222 on 2017-06-23
Thanks SeijiSensei and monkeybrain, but my problem was somewhere else.

In the end, I had several problems in my project. FFMPEG did not work because I had deleted the references to opencv_core that are required; this was not fixed by uninstalling and reinstalling FFMPEG and was solved after Ubuntu was reinstalled.

However, my problem was that I was pip installing the opencv-python package on top pf the OpenCV installation from source and this blocked acces to the real libraries.
When I uninstalled it from my system, I was finally able to handle video files.

Here is an example, this is my test.py file:
[FONT=courier new] 
import cv2
cap = cv2.VideoCapture("/home/envac/Documentos/GOPR0043.MP4")
p = cap.isOpened()
print "GOPR0043.MP4 is opened:%s"%p
TOTAL_FRAMES_FLAG = cv2.CAP_PROP_FRAME_COUNT
num_frames = cap.get(TOTAL_FRAMES_FLAG)
print "num_frames:%s"%num_frames 
 [/FONT]
And this is what happens in my ubuntu environment:
[FONT=courier new] 
$ python test.py
GOPR0043.MP4 is opened:True
num_frames:165.0
$ sudo pip install opencv-python
[sudo] password for envac: 
...
Installing collected packages: opencv-python
Successfully installed opencv-python-3.2.0.7
$ python test.py
GOPR0043.MP4 is opened:False
num_frames:0.0
$ sudo -H pip uninstall opencv-python
Uninstalling opencv-python-3.2.0.7:
...
Proceed (y/n)? y
  Successfully uninstalled opencv-python-3.2.0.7
$ python test.py
GOPR0043.MP4 is opened:True
num_frames:165.0
 [/FONT]
As you probably know (but I didn&#8217;t) opencv-python is a lightweight package with a partial opencv functionality that can be used INSTEAD of the original libraries; as stated in the documentation ([https://pypi.python.org/pypi/opencv-python):](https://pypi.python.org/pypi/opencv-python):)
[B]
IMPORTANT NOTE[/B]
MacOS and Linux wheels have currently some limitations:

[LIST]
[*]video related functionality is not supported (not compiled with FFmpeg) 
[*]for example cv2.imshow() will not work (not compiled with GTK+ 2.x or Carbon support) 
[/LIST]

Hope this is of help

---

