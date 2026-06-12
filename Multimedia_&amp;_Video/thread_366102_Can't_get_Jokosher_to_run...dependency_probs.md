---
title: "Can't get Jokosher to run...dependency probs"
date: 2007-02-20
forum: Multimedia &amp; Video
---

### Post by bodiddlie on 2007-02-20
I downloaded the Jokosher 0.2 runscript, ran it, and it gave me an error:

```
E: python-setuptools: subprocess post-installation script returned error exit status 1
E: python-zopeinterface: subprocess post-installation script returned error exit status 1
E: python-twisted-core: dependency problems - leaving unconfigured


```

then it finished the rest of the script.  If I try to run it I get this:

```
Traceback (most recent call last):
  File "/usr/bin/jokosher", line 84, in ?
    import Jokosher.JokosherApp as JokosherApp
  File "/usr/lib/python2.4/site-packages/Jokosher/JokosherApp.py", line 25, in ?
    import PreferencesDialog, ExtensionManagerDialog, RecordingView, NewProjectDialog
  File "/usr/lib/python2.4/site-packages/Jokosher/ExtensionManagerDialog.py", line 11, in ?
    import Globals, Extension
  File "/usr/lib/python2.4/site-packages/Jokosher/Extension.py", line 9, in ?
    import os, gtk, imp, pickle, pkg_resources
ImportError: No module named pkg_resources
```

After hunting around the forums I found that pkg_resources is part of python-setuptools, so I run :

```
sudo apt-get install python-setuptools
```

and get this

```
Setting up python-setuptools (0.6c3-1ubuntu4) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 861, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 195, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 120, in default_version
    _default_version = link = os.readlink('/usr/bin/python')
OSError: [Errno 22] Invalid argument: '/usr/bin/python'
dpkg: error processing python-setuptools (--configure):
 subprocess post-installation script returned error exit status 1
Setting up python-zopeinterface (3.2.2-0ubuntu1) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 861, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 195, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 120, in default_version
    _default_version = link = os.readlink('/usr/bin/python')
OSError: [Errno 22] Invalid argument: '/usr/bin/python'
dpkg: error processing python-zopeinterface (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-twisted-core:
 python-twisted-core depends on python-zopeinterface (>= 3.2.1-3); however:
  Package python-zopeinterface is not configured yet.
dpkg: error processing python-twisted-core (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-setuptools
 python-zopeinterface
 python-twisted-core
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

any ideas?  

-bodiddlie

---

### Post by eric71 on 2007-02-21
The main problem I had when using the installation script was that I did not have the source repositories enabled.  Open the settings-repositories dialogue in Synaptic and make sure you check all the deb-src options listed. Delete the .jokosher folder and repeat the installation.

---

### Post by bodiddlie on 2007-02-23
Source repos are all added.  Any other ideas?

---

### Post by DarthFlodis on 2007-07-02
I solved this problem by replacing my /usr/bin/python with an symbolic link to /usr/bin/python2.5.

It seems that os.readlink() excepts a link and when it is not, it throws the exception.

---

