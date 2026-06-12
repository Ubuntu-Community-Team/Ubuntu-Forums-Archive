---
title: "gksudo displayconfig-gtk"
date: 2008-06-19
forum: Multimedia Software
---

### Post by John.Barner on 2008-06-19
I have an ATi Radeon card, and it was set to a widescreen resolution when I installed Ubuntu (I have a CRT). I tired running gksudo displayconfig-gtk, but all I can get is the following error:

```
  File "/usr/bin/displayconfig-gtk", line 75, in <module>
    app = DisplayConfig(options)
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 189, in __init__
    debug_scan_pci_filename=self.options.pcitable)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 394, in __init__
    self._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 404, in _finalizeInit
    gfxcard._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1123, in _finalizeInit
    screen._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1588, in _finalizeInit
    (cw,ch,x,x) = self.x_live_screen.getSize()
  File "/var/lib/python-support/python2.5/xf86misc.py", line 77, in getSize
    return self.sizes[self.currentsizeid]
IndexError: list index out of range

```

---

