---
title: "openshot error message"
date: 2009-12-31
forum: Multimedia Software
---

### Post by zachthejones on 2009-12-31
I've been editing up a family video for the last couple of weeks and have been nearing completion. but today when I try to open up OpenShot, I get this error message: 

```
my-laptop:~$ openshot
Added /usr/share/openshot to system path
--------------------------------
   OpenShot (version 0.9.54)
--------------------------------
*** ERROR: MLT Python bindings failed to import ***
*** ERROR: MLT Python bindings failed to import ***
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
    self.run()
  File "/usr/share/openshot/classes/thumbnail.py", line 174, in run
    mlt.Factory().init()
NameError: global name 'mlt' is not defined

-------------------------------------------------------
Error:  OpenShot has not been installed in the Python path.
(Both the site-packages and /usr/share/openshot folders were checked)

Use the following command to install OpenShot:
  $ sudo python setup.py install

my-laptop:~$
```

I tried running the command suggested at the end, but no juice. I get this message:

```
python: can't open file 'setup.py': [Errno 2] No such file or directory

```

Any help would be greatly appreciated...I have no idea what is going on here. I did do the latest update this morning, which i believe included an upgrade of sorts (I think to the linux kernal, but I'm not %100 sure)

---

### Post by zachthejones on 2010-01-01
ok...just in case anyone else out there has this problem, I finally fixed it by going to OpenShot's [website]("http://www.openshotvideo.com/") and downloading their dependecies package. After I installed the dependencies the program worked fine again.

I'm not really sure what happened, but it seems that when I did an update somehow something got messed up between python and OpenShot. Whatever it was, installing the dependencies fixed it

---

### Post by JC Cheloven on 2010-01-01
Thanks for the info. I'm using openshot, and I think it is awesome.

---

### Post by fazzuk on 2010-01-04
Thanks very much for the information.

I was getting the same error after installing from the ppa.

I only needed to install the openshot-mlt_0.4.3-1_amd64.deb from the dependencies package to get it working.

---

