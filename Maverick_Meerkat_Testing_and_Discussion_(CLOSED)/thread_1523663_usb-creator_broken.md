---
title: "usb-creator broken"
date: 2010-07-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jppr on 2010-07-04
sudo usb-creator-gtk
** Message:  pygobject_register_sinkfunc is deprecated (GtkWindow)
** Message:  pygobject_register_sinkfunc is deprecated (GtkInvisible)
** Message:  pygobject_register_sinkfunc is deprecated (GtkObject)
Traceback (most  recent call last):
  File "/usr/bin/usb-creator-gtk", line 26, in  <module>
    from usbcreator.frontends.gtk import GtkFrontend
  File   "/usr/lib/python2.6/dist-packages/usbcreator/frontends/gtk/__init__.py",  line 1, in <module>
    from frontend import GtkFrontend
  File   "/usr/lib/python2.6/dist-packages/usbcreator/frontends/gtk/frontend.py",  line 30, in <module>
    from usbcreator.misc import *
  File  "/usr/lib/python2.6/dist-packages/usbcreator/misc.py", line 36, in  <module>
    from IN import INT_MAX
ImportError: cannot  import name INT_MAX

 ------

 sudo usb-creator-kde
Traceback  (most recent call last):
  File "/usr/bin/usb-creator-kde", line 32,  in <module>
    from usbcreator.frontends.kde.translate import  translate
  File  "/usr/lib/python2.6/dist-packages/usbcreator/frontends/kde/__init__.py",  line 1, in <module>
    from frontend import KdeFrontend
   File  "/usr/lib/python2.6/dist-packages/usbcreator/frontends/kde/frontend.py",  line 37, in <module>
    from usbcreator.misc import *
   File "/usr/lib/python2.6/dist-packages/usbcreator/misc.py", line 36, in  <module>
    from IN import INT_MAX
ImportError: cannot  import name INT_MAX

I have 2 HD system, /dev/sda1 is Ubuntu 10.10 and /dev/sdb1 is Kubuntu 10.10
I did fresh installation 2 days ago.

---

### Post by rogeliodelarosa97 on 2010-07-04
dude im sorry but your usb is messed up i really recommend you get the pc or usb creator checked

---

### Post by xeizo on 2010-07-04
Ehem, this is the testing forum for the next release, things are supposed to be broken from time to time at this stage ...

---

### Post by dino99 on 2010-07-04
these are complaints against python

---

### Post by VMC on 2010-07-09
I have the exact same error message, as of todays  (07/08/10) install, using amd64.

Here's the [bug report]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/601560"). If it effects you, please "me too" it.

I get this pop up dialog when I try to report it using the crash report dialog.

Edit: After seeing the attached dialog pop-up, I updated python2.6-minimal, it now works. Odd, but that pop-up doesn't always show up when the crash dialog pop-up does. Hopefully this gets updated into daily-live soon. The creator of the bug report also fixed it yesterday by updating python.

---

### Post by jppr on 2010-07-09
Just did todays fresh Kubuntu live-cd installation and usb-creator works fine both ubuntu and kubuntu.

---

