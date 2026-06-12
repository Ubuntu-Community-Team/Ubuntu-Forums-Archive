---
title: "syncropated! - installed but nothing happens"
date: 2009-09-05
forum: Multimedia Software
---

### Post by sidestrand on 2009-09-05
I'm running Hardy LTS.  I've installed Syncropated! but when I select it from the menu nothing loads.  When I initiate it from the command line I get the following result:

richard@richard-desktop:~$ syncropated
16:39:29 environ              No en_GB translation found for domain kiwi
16:39:29 environ              No en_GB translation found for domain gazpacho
/usr/share/syncropated/data/
/usr/share/syncropated/data/ui/syncropated-ui.glade
Traceback (most recent call last):
  File "/usr/bin/syncropated", line 24, in <module>
    from syncropated.Syncropated import init_app; init_app()
  File "/var/lib/python-support/python2.5/syncropated/Syncropated.py", line 536, in init_app
    model.handle_device()
  File "/var/lib/python-support/python2.5/syncropated/Syncropated.py", line 486, in handle_device
    devices = DeviceDetection.get_compatible_devices()
  File "/var/lib/python-support/python2.5/syncropated/DeviceDetection.py", line 35, in get_compatible_devices
    fstype = volume.GetProperty ('volume.fstype')
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking


Can anyone advise what the problem is?

Thank you

---

