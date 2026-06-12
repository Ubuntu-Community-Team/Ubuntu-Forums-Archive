---
title: "Need help with hand gestures (webcam)"
date: 2010-11-09
forum: Multimedia Software
---

### Post by JBud on 2010-11-09
I found this neat program in python that allows you to control your mouse with hand gestures, however after spending a while getting all the required libraries, and compiling them, I have run into an error, here is what the terminal shows me when I run the program:

```
OpenCV Python version of lkdemo
Xlib.protocol.request.QueryExtension
Hot keys: 
	ESC - quit the program
	r - auto-initialize tracking
	c - delete all the points
	n - switch the "night" mode on/off
To add/remove a feature point click it

/usr/share/themes/MurrinaChrome/gtk-2.0/gtkrc:83: Murrine configuration option "gradients" is no longer supported and will be ignored.
Traceback (most recent call last):
  File "/home/jbud/Downloads/cam-mouse-ctrl.py", line 161, in <module>
    image.origin = frame.origin
  File "/usr/lib/pymodules/python2.6/opencv/cv.py", line 2095, in <lambda>
    __setattr__ = lambda self, name, value: _swig_setattr(self, CvMat, name, value)
  File "/usr/lib/pymodules/python2.6/opencv/cv.py", line 48, in _swig_setattr
    return _swig_setattr_nondynamic(self,class_type,name,value,0)
  File "/usr/lib/pymodules/python2.6/opencv/cv.py", line 41, in _swig_setattr_nondynamic
    if method: return method(self,value)
RuntimeError:  openCV Error:
        Status=The function/feature is not implemented
        function name=CvMat_origin_get
        error message=IplImage is replaced by CvMat in Python, so its fields are read-only
        file_name=/build/buildd-opencv_2.1.0-2-i386-59WXeK/opencv-2.1.0/obj-i486-linux-gnu/interfaces/swig/python/cvPYTHON_wrap.cxx
        line=6060

```

I do not know how to debug python stuff, so maybe some wizz out there can help :)

I have attached the python script to this post

Thanks in advance!
-JBud

---

