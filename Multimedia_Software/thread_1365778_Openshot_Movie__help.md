---
title: "Openshot Movie  help"
date: 2009-12-27
forum: Multimedia Software
---

### Post by Foxfire on 2009-12-27
trying to get it to run I get this


-------------------------------
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

noname@noname-desktop:~$ sudo python setup.py install
[sudo] password for jreynolds: 
python: can't open file 'setup.py': [Errno 2] No such file or directory
noname@noname-desktop:~$

---

