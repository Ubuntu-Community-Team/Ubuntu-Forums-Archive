---
title: "OpenShot problem"
date: 2011-05-05
forum: Multimedia Software
---

### Post by beew on 2011-05-05
Hi,

Openshot appears to be dead, clicked the launcher nothing happened. Starting it in the terminal produced the following error messages

> $ openshot

------------------------- ERROR 1 ------------------------------
Failed to import 'from openshot import main'
Error Message: cannot import name main
----------------------------------------------------------------
--------------------------------
   OpenShot (version 1.3.1)
--------------------------------
Process no longer exists: 10436.  Creating new pid lock file.
*** ERROR: MLT Python bindings failed to import ***
*** ERROR: MLT Python bindings failed to import ***
*** ERROR: MLT Python bindings failed to import ***
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 532, in __bootstrap_inner
    self.run()
  File "/usr/lib/pymodules/python2.6/openshot/classes/thumbnail.py", line 170, in run
    mlt.Factory().init()
NameError: global name 'mlt' is not defined

*** ERROR: MLT Python bindings failed to import ***

------------------------- ERROR 2 ------------------------------
Failed to import 'from openshot.openshot import main'
Error Message: No module named mlt
----------------------------------------------------------------

OpenShot has failed to import some of the Python files or libraries 
required for our application to run.  Here are some trouble shooting
tips:

Tip 1) Check if MLT can be successfully imported in Python.  Run the 
 following commands, and see if any errors are displayed.  If you get 
 an error, you need to investigate the correct way to install MLT.
 NOTE:  Do not type the $ or >> characters in the examples below.

       $ python
       >> import mlt
       >> mlt.Factory().init()

Tip 2) If MLT is working from the first example, then the next tip is 
 to look at the above error messages very closely, and google for more 
 help.  It's likely the problem is already reported, and maybe there is
 a simple work-around.  Also, you can search for bugs or report a new 
 bug at [https://bugs.launchpad.net/openshot](https://bugs.launchpad.net/openshot).  Good luck!


Following Tip 1) produced the following

> 
$ python
Python 2.6.6 (r266:84292, Sep 15 2010, 15:52:39) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import mlt
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named mlt
>>> mlt.Factory().init()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'mlt' is not defined
>>> 




Appreciate any help, thanks.

---

### Post by beew on 2011-05-06
Bump!

---

