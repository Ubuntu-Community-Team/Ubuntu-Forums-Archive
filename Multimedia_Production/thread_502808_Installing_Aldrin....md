---
title: "Installing Aldrin..."
date: 2007-07-17
forum: Multimedia Production
---

### Post by hseiken on 2007-07-17
I'm having trouble installing Aldrin.  Could someone install it and run it and if successful, let me know what steps you took?  I've installed all dependencies and aldrin itself and I get the message from terminal:

```

Traceback (most recent call last):
  File "/usr/bin/aldrin", line 10, in <module>
    aldrin.run(sys.argv)
  File "/usr/bin/../share/aldrin/__init__.py", line 28, in run
    import main
  File "/usr/bin/../share/aldrin/main.py", line 32, in <module>
    from utils import format_time, ticks_to_time, prepstr, linear2db, filepath, \
  File "/usr/bin/../share/aldrin/utils.py", line 26, in <module>
    import time, sys, math, os, zzub, imp
ImportError: No module named zzub

```

Aldrin is available at:
[http://trac.zeitherrschaft.org/aldrin/](http://trac.zeitherrschaft.org/aldrin/)


Thanks for any and all help.

---

### Post by renzokuken on 2007-07-17
it would appear you either havent installed the pyzzub package, or you did but it ddnt install correctly.

how are you trying to install it? following the guide on their site?

---

### Post by dhiester on 2007-07-20
I ran into the same problem. The Aldrin site says that libzzub is currently compiled for Python 2.4 instead of 2.5. So what I did was went into /usr/lib/python2.5/site-packages/ and created a symlink to /usr/lib/python2.4/site-packages/zzub, and that seems to work as a temporary solution.

However, I imagine that once the next version of libzzub is released, you'll probably want to delete that symlink.

---

### Post by hseiken on 2007-07-21
I'm not sure what you said, dhiester, but I talked with some of the guys on #aldrin.  Basically, I added 3 characters to the aldrin launch script and fixed it...for those interested, this is the steps:

1.)  Open Terminal and type sudo gedit /usr/bin/aldrin
2.)  When it opens, on the first line, with no spaces, add 2.4 (so that at the end it says ../python2.4
3.)  Save
4.)  Exit terminal, close gedit
5.)  Run aldrin.

You must have 2.4 installed (obviously) for this fix to work, but it's listed in the synaptic package manager and both 2.4 and 2.5 can be installed simultaneously. Anyway, if you're into music making, this is a very nice program and I've been having lots of fun with it.  :)

---

### Post by phetre on 2007-08-04
hseiken, thank you!!! I had planned to wait for the next version, but after months of waiting I just gave up. But this fix works on my Gutsy machine. Hooray! I've missed Buzz.

---

