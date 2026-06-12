---
title: "Can't change settings in monitor &amp; display"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by TremerePuck on 2007-06-25
When I try to active the second screen or anything like that I get an error. I get it doing anything in "Size, Orientation & Positioning" and "Hardware"

```
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/displayconfig.py", line 1474, in slotSecondMonitorToggled
    self.xsetup.setLayout(self.secondary_options[pressed_id])
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 960, in setLayout
    gfxcard.setLayout(XSetup.LAYOUT_SINGLE_XINERAMA)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1164, in setLayout
    screen._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1769, in _resyncResolution
    (preferred_width,preferred_height) = self.getAvailableResolutions()[-1]
IndexError: list index out of range
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 44, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
AttributeError: 'module' object has no attribute 'argv'

Original exception was:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/displayconfig.py", line 1474, in slotSecondMonitorToggled
    self.xsetup.setLayout(self.secondary_options[pressed_id])
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 960, in setLayout
    gfxcard.setLayout(XSetup.LAYOUT_SINGLE_XINERAMA)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1164, in setLayout
    screen._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1769, in _resyncResolution
    (preferred_width,preferred_height) = self.getAvailableResolutions()[-1]
IndexError: list index out of range

```


Any and all help is appreciated.

---

