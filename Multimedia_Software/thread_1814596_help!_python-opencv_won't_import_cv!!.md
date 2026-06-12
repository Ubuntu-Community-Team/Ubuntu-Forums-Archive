---
title: "help! python-opencv won't import cv!!"
date: 2011-07-29
forum: Multimedia Software
---

### Post by test_tube_baby on 2011-07-29
Hi

I recently installed opencv and then installed the python support via sudo apt-get install python-opencv

HOWEVER,

when I run python then type 'import cv' i get the following error:

```
>>> import cv
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named cv
>>> 

```


Here is the full log:

```
prem@prem-laptop:~$ sudo apt-get install python-opencv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  python-opencv
0 upgraded, 1 newly installed, 0 to remove and 51 not upgraded.
Need to get 723kB of archives.
After this operation, 2,994kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/universe python-opencv 2.0.0-3ubuntu2 [723kB]
Fetched 723kB in 3s (211kB/s)         
Selecting previously deselected package python-opencv.
(Reading database ... 158668 files and directories currently installed.)
Unpacking python-opencv (from .../python-opencv_2.0.0-3ubuntu2_i386.deb) ...
Setting up python-opencv (2.0.0-3ubuntu2) ...

Processing triggers for python-support ...
prem@prem-laptop:~$ cd Dropbox/robotics/learningopencv/
prem@prem-laptop:~/Dropbox/robotics/learningopencv$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import cv
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named cv
>>> 

```


Anybody know what's wrong?

---

### Post by test_tube_baby on 2011-07-31
anybody???? can I get some help

---

### Post by arpad on 2011-08-08
In my python code I do an "import cv" rather then "import opencv". "import opencv" kicks out the following:

[I][INDENT]Traceback (most recent call last):
  File "original.py", line 4, in <module>
    capture = cv.CaptureFromCAM(0)
[/INDENT][/I]

I'm a newb on opencv and not getting much help either. Hope this helps.

---

### Post by test_tube_baby on 2011-08-08
Hello there, thanks for your reply. I tried the 'import cv' command. However, basic CV functions such as cvLoadImage(xxx). I tried CV_LoadImage because it's python, I also tried cv_LoadImage.. none of them work when I 'import cv'.

Any suggestions?

---

### Post by arpad on 2011-08-08
You might try reloading OpenCV. Beyond that here's the code I'm struggling with:

```
import cv

capture = cv.CaptureFromCAM(0)

while True:
    img = cv.QueryFrame(capture)
    gray = cv.CreateImage(cv.GetSize(img), 8, 1)
    edges = cv.CreateImage(cv.GetSize(img), 8, 1)

    cv.CvtColor(img, gray, cv.CV_BGR2GRAY)
    cv.Canny(gray, edges, 50, 200, 3)
    cv.Smooth(gray, gray, cv.CV_GAUSSIAN, 9, 9)

    storage = cv.CreateMat(gray.width, 1, cv.CV_32FC3)
    
    #cv.HoughCircles(gray, storage, cv.CV_HOUGH_GRADIENT, 2, gray.height/3)

    cv.HoughCircles(gray, storage, cv.CV_HOUGH_GRADIENT, 2, gray.height/4, 200, 100)

    print "storage.width = " + str(storage.width)
    
    for i in xrange(storage.width - 1):
      radius = storage[i, 2]
      center = (storage[i, 0], storage[i,1])

      print (radius, center)
      print "inside this loop"

      cv.Circle(img, center, radius, (0, 0, 255), 3, 8, 0)

    cv.NamedWindow('Circles')
    cv.ShowImage('Circles', gray)
    if cv.WaitKey(2) == 27:
         break
```

I'm trying to make it find circles in the visual field and getting nowhere. The code runs but won't find circles even though that looks like a pretty easy trick. The relevant function, cv.HoughCircles, seems to do nothing no matter how I tweak the parameters and there aren't any references for how to go about tweaking the parameters.

The folks at [http://tech.groups.yahoo.com/group/OpenCV/](http://tech.groups.yahoo.com/group/OpenCV/) seem spectacularly uninterested in the Python binding ignoring questions related to Python. That's got me looking for OpenCV forums with the focus on Python but without any luck so far.

---

