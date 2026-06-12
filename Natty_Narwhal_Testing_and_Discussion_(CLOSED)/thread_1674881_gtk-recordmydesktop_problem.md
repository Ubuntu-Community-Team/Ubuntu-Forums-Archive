---
title: "gtk-recordmydesktop problem"
date: 2011-01-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by w3rt on 2011-01-24
Just upgraded to natty and since the upgrade I cannot launch gtk-recordmydesktop at all, anyone else experienced this?

---

### Post by w3rt on 2011-01-24
Here is the error I get from the command line


[HTML][/HTML]Traceback (most recent call last):
  File "/usr/bin/gtk-recordMyDesktop", line 43, in <module>
    main()
  File "/usr/bin/gtk-recordMyDesktop", line 40, in main
    tr=rmdSimple.simpleWidget()
  File "/usr/lib/pymodules/python2.7/recordMyDesktop/rmdSimple.py", line 515, in __init__
    self.trayIcon=trayIcon(self)
  File "/usr/lib/pymodules/python2.7/recordMyDesktop/rmdTrayIcon.py", line 394, in __init__
    self.tray_popup=iTP.TrayPopupMenu(self.parent,self.parent.values,self.optionsOpen)
  File "/usr/lib/pymodules/python2.7/recordMyDesktop/rmdTrayPopup.py", line 51, in __init__
    self.popupmenu_continueitem.hide()
AttributeError: TrayPopupMenu instance has no attribute 'popupmenu_continueitem'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 105, in apport_excepthook
    os.O_WRONLY|os.O_CREAT|os.O_EXCL, 0600), 'w')
OSError: [Errno 2] No such file or directory: '/var/crash/_usr_bin_gtk-recordMyDesktop.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/gtk-recordMyDesktop", line 43, in <module>
    main()
  File "/usr/bin/gtk-recordMyDesktop", line 40, in main
    tr=rmdSimple.simpleWidget()
  File "/usr/lib/pymodules/python2.7/recordMyDesktop/rmdSimple.py", line 515, in __init__
    self.trayIcon=trayIcon(self)
  File "/usr/lib/pymodules/python2.7/recordMyDesktop/rmdTrayIcon.py", line 394, in __init__
    self.tray_popup=iTP.TrayPopupMenu(self.parent,self.parent.values,self.optionsOpen)
  File "/usr/lib/pymodules/python2.7/recordMyDesktop/rmdTrayPopup.py", line 51, in __init__
    self.popupmenu_continueitem.hide()
AttributeError: TrayPopupMenu instance has no attribute 'popupmenu_continueitem'

---

