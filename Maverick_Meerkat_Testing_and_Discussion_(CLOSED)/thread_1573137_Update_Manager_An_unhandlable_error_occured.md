---
title: "Update Manager: An unhandlable error occured"
date: 2010-09-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by rps63ifid on 2010-09-12
I have been running 10.10 and updating on pretty much a daily basis since the beta was released. This morning when I ran the update manager, it responds with a dialog titled "An unhandlable error occured", with the following information: There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry. 

In the "Details" portion of the window, it shows:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 163, in _process_transaction
    self.update_cache(**self.trans.kwargs)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 589, in update_cache
    self._cache.update(progress, sources_list=sources_list)
  File "/usr/lib/python2.6/dist-packages/apt/deprecation.py", line 98, in deprecated_function
    return func(*args, **kwds)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 343, in update
    raise LockFailedException("Failed to lock %s" % lockfile)
LockFailedException: Failed to lock /var/lib/apt/lists/lock

If the update manager is busted, where does that leave us?

---

### Post by ronacc on 2010-09-12
try from the terminal and see if that works . open a terminal and 
```
sudo apt-get update 
``` and then ```
  sudo apt-get upgrade 
``` 

look at what it wants to do after the 2nd cmd to make sure it won't remove anything vital before telling it to go ahead .

---

