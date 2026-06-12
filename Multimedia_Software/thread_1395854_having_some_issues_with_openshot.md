---
title: "having some issues with openshot"
date: 2010-02-01
forum: Multimedia Software
---

### Post by nerdy_kid on 2010-02-01
hello everyone, when i run openshot it spits out this:
```

Added /usr/share/openshot to system path
--------------------------------
   OpenShot (version 1.0.0)
--------------------------------
*** ERROR: MLT Python bindings failed to import ***
*** ERROR: MLT Python bindings failed to import ***
-------------------------------------------------------
Error:  OpenShot has not been installed in the Python path.
(Both the site-packages and /usr/share/openshot folders were checked)

Use the following command to install OpenShot:
  $ sudo python setup.py install

Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
    self.run()
  File "/usr/share/openshot/classes/thumbnail.py", line 174, in run
    mlt.Factory().init()
NameError: global name 'mlt' is not defined

```
i cant fix it, i think i did it by installing a package (might have been a kdenlive "upgrade" (cough downgrade lol) ) but im not sure.  thanks a zillion to anyone who helps, as this is the ONLY awesome video editor for linux and its broke on my system :S

---

### Post by nerdy_kid on 2010-02-02
did some purging and autoremoving and more purging and now it works! to be exact, purged python mlt, autoremoved with --purge, then installed openshot again.  Hope this helps anyone who has this issue.

---

