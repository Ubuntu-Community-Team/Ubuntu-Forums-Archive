---
title: "Monitor &amp; display settings"
date: 2009-06-10
forum: Multimedia Software
---

### Post by mattblack11 on 2009-06-10
having some probs with my system settings monitor & display wont open and when i play a dvd all i get is blue screen

here is the kcmshell output

  	 	 	 	 	 	  matt@NEC:~$ sudo kcmshell displayconfig
 [sudo] password for matt:
 Error: "/var/tmp/kdecache-matt" is owned by uid 1000 instead of uid 0.
 

 

 Pythonize constructor -- pid = 6724
 Python interpreter initialized!
 

 

 

 Pythonize constructor -- pid = 6724
 []
 Traceback (most recent call last):
   File "<string>", line 8, in kcontrol_bridge_create_displayconfig
   File "/var/lib/python-support/python2.5/displayconfig.py", line 1733, in create_displayconfig
     return DisplayApp(parent, name)
   File "/var/lib/python-support/python2.5/displayconfig.py", line 441, in __init__
     self.xsetup = XSetup(self.xconfigpath)
   File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 394, in __init__
     self._finalizeInit()
   File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 404, in _finalizeInit
     gfxcard._finalizeInit()
   File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1125, in _finalizeInit
     screen._resyncResolution()
   File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1861, in _resyncResolution
     self.gfx_card.setup.getPrimaryScreen()._resyncResolution()
   File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1817, in _resyncResolution
     (preferred_width,preferred_height) = self.getAvailableResolutions()[-1]
 IndexError: list index out of range
 error: *** runFunction failure


any ideas ??
cheers

 ;

---

