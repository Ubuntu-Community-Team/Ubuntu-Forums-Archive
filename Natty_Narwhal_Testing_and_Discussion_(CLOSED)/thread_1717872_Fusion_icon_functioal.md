---
title: "Fusion icon functioal?"
date: 2011-03-30
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by 5149.5 on 2011-03-30
I can't get fusion icon to run. Has anyone had any success with it? Does it have a dependency on a compiz setting?

---

### Post by superhick on 2011-03-31
crashes here as well:
~$ fusion-icon 
 * Detected Session: gnome
 * Searching for installed applications...
Backend     : gconf
Integration : true
Profile     : default
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "/usr/lib/python2.7/dist-packages/FusionIcon/interface.py", line 21, in <module>
    from util import env
  File "/usr/lib/python2.7/dist-packages/FusionIcon/util.py", line 419, in <module>
    decorators = CompizDecorators(_installed)
  File "/usr/lib/python2.7/dist-packages/FusionIcon/util.py", line 226, in __init__
    self.command = context.Plugins['decoration'].Display['command']
KeyError: 'decoration'

---

### Post by superhick on 2011-03-31
[https://bugs.launchpad.net/ubuntu/+source/fusion-icon/+bug/192389](https://bugs.launchpad.net/ubuntu/+source/fusion-icon/+bug/192389)

---

