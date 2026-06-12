---
title: "natty 32 bits: Firefox 4 b12 stop running"
date: 2011-03-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by meanpt on 2011-03-16
This happened after this (my) morning system upddate and a restart in unity 2D. After powering it down and restarting with the classic no effects desktop, again it didn't run. Did a reinstall through the software center and it still refuses running. On the other hand, it runs fine on the natty 64 bits.

---

### Post by dino99 on 2011-03-16
you might have rc1 now ( since a week or so), so be sure you get the latest updates applied.

sudo dpkg-reconfigure firefox

---

### Post by meanpt on 2011-03-16
Did as suggested and getting on terminal:

please restart all running instances of firefox, or you will experience problems.

But when trying to run firefox from terminal:


:~$ firefox
Could not stat private per-user gnome configuration directory `/home/meanpt/.gnome2_private/': Not a directory

 
And it seems does also affects other applications.

When trying to run cellwriter from terminal:

:~$ cellwriter
Could not stat private per-user gnome configuration directory `/home/meanpt/.gnome2_private/': Not a directory

When tried to run onboard from the terminal:


:~$ onboard
WARNING:Config:Can't load Default loading default layout instead
Traceback (most recent call last):
  File "/usr/bin/onboard", line 14, in <module>
    from Onboard.OnboardGtk import OnboardGtk as Onboard
  File "/usr/lib/python2.7/dist-packages/Onboard/OnboardGtk.py", line 26, in <module>
    from Onboard.KeyboardSVG import KeyboardSVG
  File "/usr/lib/python2.7/dist-packages/Onboard/KeyboardSVG.py", line 22, in <module>
    from Onboard.KeyboardGTK import KeyboardGTK
  File "/usr/lib/python2.7/dist-packages/Onboard/KeyboardGTK.py", line 13, in <module>
    import Onboard.X11 as X11
  File "/usr/lib/python2.7/dist-packages/Onboard/X11.py", line 27, in <module>
    XOpenDisplay = libX11.XOpenDisplay
  File "/usr/lib/python2.7/ctypes/__init__.py", line 366, in __getattr__
    func = self.__getitem__(name)
  File "/usr/lib/python2.7/ctypes/__init__.py", line 371, in __getitem__
    func = self._FuncPtr((name_or_ordinal, self))
AttributeError: /usr/bin/python: undefined symbol: XOpenDisplay

---

### Post by dino99 on 2011-03-16
.gnome2_private is probably corrupted, rename it then reboot

---

