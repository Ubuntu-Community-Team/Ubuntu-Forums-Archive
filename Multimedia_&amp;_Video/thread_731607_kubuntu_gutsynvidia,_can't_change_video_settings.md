---
title: "kubuntu gutsy/nvidia, can't change video settings"
date: 2008-03-22
forum: Multimedia &amp; Video
---

### Post by code-breaker on 2008-03-22
I hava a fresh install of kubuntu gutsy, with all updates applied. I have an nvidia chipset card with both a vga and a dvi port, and I have the restricted driver installed. The vga monitor is working fine, but the dvi monitor only displays something during boot. Once the login screen appears, the dvi screen goes blank. I had previously had a two monitor setup working great (also kubuntu gutsy, and on the same machine/same hardware), and I'm trying to get it set up again. But when I run systemsettings, none of the changes I make get saved. I can change the resolution of the primary monitor and that will get saved, but if I check the 'second screen' check box for example, the apply button is not accessible (it is grayed out as though no settings had been changed). Here is the console output.

This first snip is what I see when I first run systemsettings, then click 'Monitor & Display':
```

code-breaker@code-breaker:~$ systemsettings
adding Monitor & Display /usr/share/applications/kde/displayconfig.desktop


Pythonize constructor -- pid = 5902
Python interpreter initialized!



Pythonize constructor -- pid = 5902
open /dev/mem: Permission denied
VESA BIOS Extensions not detected.

```

Then, if I click on the adminstrator button to gain root access:

```

X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  6
  Minor opcode:  0
  Resource id:  0x2e00bbf
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  12
  Minor opcode:  0
  Resource id:  0x2e00bbf
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  12
  Minor opcode:  0
  Resource id:  0x2e00bbf
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  8
  Minor opcode:  0
  Resource id:  0x2e00bbf
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  12
  Minor opcode:  0
  Resource id:  0x2e00bbf
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  12
  Minor opcode:  0
  Resource id:  0x2e00bbf
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  25
  Minor opcode:  0
  Resource id:  0x2e00bbf
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  25
  Minor opcode:  0
  Resource id:  0x2e00bbf
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  25
  Minor opcode:  0
  Resource id:  0x2e00bbf

```

And when I click the 'second screen' checkbox:

```

Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/displayconfig.py", line 1474, in slotSecondMonitorToggled
    self.xsetup.setLayout(self.secondary_options[pressed_id])
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 965, in setLayout
    gfxcard.setLayout(XSetup.LAYOUT_CLONE)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1177, in setLayout
    screen._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1854, in _resyncResolution
    self.gfx_card.setup.getPrimaryScreen()._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1810, in _resyncResolution
    (preferred_width,preferred_height) = self.getAvailableResolutions()[-1]
IndexError: list index out of range
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 42, in apport_excepthook
    binary = os.path.re


Pythonize constructor -- pid = 6361
Python interpreter initialized!



Pythonize constructor -- pid = 6361
[]

alpath(os.path.join(os.getcwdu(), sys.argv[0]))
AttributeError: 'module' object has no attribute 'argv'

Original exception was:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/displayconfig.py", line 1474, in slotSecondMonitorToggled
    self.xsetup.setLayout(self.secondary_options[pressed_id])
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 965, in setLayout
    gfxcard.setLayout(XSetup.LAYOUT_CLONE)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1177, in setLayout
    screen._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1854, in _resyncResolution
    self.gfx_card.setup.getPrimaryScreen()._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1810, in _resyncResolution
    (preferred_width,preferred_height) = self.getAvailableResolutions()[-1]
IndexError: list index out of range

```

Does anyone have any ideas? Is there more information I can post that could be helpful?

---

### Post by code-breaker on 2008-03-22
I uninstalled the restricted driver, and then I installed [envy]("http://www.albertomilone.com/nvidia_scripts1.html"). Then, I used the nvidia settings program to setup twinview, which absolutely works like a champ. 

This is better than my previous setup, which was done using 'monitor & display' in KDE's 'system settings'. With that one, the login window always showed up on the vga monitor, even though that was not the primary monitor. With twinview, everything works perfectly.

---

