---
title: "Clicking Addition Drivers does nothing"
date: 2012-08-25
forum: Multimedia Software
---

### Post by paichkash on 2012-08-25
hi
my system is running like crap .. its stuttering when even ;loading terminal .. there is lag b/e typing etc  in terminal and other packages like ff..
it is same behaviour like running video in xp with no drivers installed..

i thought to use old nvidia drivers .. but when i clicked "additional drivers" nothing would  happen.. i ran ```
sudo jockey-gtk and
got the following

r@rDT:~$ sudo jockey-gtk
[sudo] password for r: 
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 420, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 448, in run
    self.ui_show_main()
  File "/usr/bin/jockey-gtk", line 101, in ui_show_main
    self.update_tree_model()
  File "/usr/bin/jockey-gtk", line 277, in update_tree_model
    for h_id in self.get_displayed_handlers():
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 793, in get_displayed_handlers
    return self.backend().available(self.argv_options.mode)
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 115, in backend
    self._check_repositories()
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 826, in _check_repositories
    self._repository_progress_handler})
  File "/usr/lib/python2.6/dist-packages/jockey/backend.py", line 98, in convert_dbus_exceptions
    return fn(*args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/jockey/backend.py", line 90, in dbus_sync_call_signal_wrapper
    raise _h_exception_exc
dbus.exceptions.DBusException: org.freedesktop.DBus.Python.apt.cache.FetchFailedException: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/jockey/backend.py", line 600, in update_repository_indexes
    hasattr(self, '_locations') and self.repository_update_progress or None)
  File "/usr/lib/python2.6/dist-packages/jockey/oslib.py", line 350, in update_repository_indexes
    c.update(progress_cb and MyProgress(progress_cb) or None)
  File "/usr/lib/python2.6/dist-packages/apt/deprecation.py", line 98, in deprecated_function
    return func(*args, **kwds)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 364, in update
    raise FetchFailedException(e)
FetchFailedException: W:Failed to fetch http://deb.opera.com/opera/dists/stable/Release  Unable to find expected entry  non-free/source/Sources in Meta-index file (malformed Release file?)
, W:Failed to fetch http://deb.opera.com/opera/dists/maverick/non-free/source/Sources.gz  404  Not Found
, W:Failed to fetch http://deb.opera.com/opera/dists/maverick/non-free/binary-i386/Packages.gz  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.


```

the version of jockey-gtk currently installed is .5.10-0Ubuntu5 and jockey-common also has the same versin nstalled...  

thanks

---

### Post by 2F4U on 2012-08-25
If you are still running Ubuntu 10.10 you might notice that it is out of support

[https://lists.ubuntu.com/archives/ubuntu-security-announce/2012-March/001624.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2012-March/001624.html)

which may be the reason why you don't get additional drivers. Else you should post your Ubuntu version and your hardware specs.

---

### Post by paichkash on 2012-08-25
earlier i was able to get the additional drivers thngy .. now strangly it wont show up ..
my system specs are rather low thats y i m on old version..
cp PIII 1Ghz, RAM 512 MB, GPU Nvidia GeForce FX 5500 256MB.HDD 40 GB.
 any more ?
also when i click on additional drivers it opens a box with some progress bar saying 
downloading and updating package indexes then it vanishes..

---

