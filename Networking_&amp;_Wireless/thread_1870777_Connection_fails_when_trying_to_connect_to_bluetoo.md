---
title: "Connection fails when trying to connect to bluetooth PAN network with Blueman"
date: 2011-10-27
forum: Networking &amp; Wireless
---

### Post by BinaryMn on 2011-10-27
See below for traceback. I've tried reinstalling blueman and python2.7. I never experienced this problem in 11.04.

```
Connection Failed: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "<string>", line 2, in ServiceProxy
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/applet/DBusService.py", line 121, in ServiceProxy
    self.Applet.Plugins.RunEx("service_connect_handler", cb, interface, object_path, _method, args, ok, err)
  File "/usr/lib/python2.7/dist-packages/blueman/main/PluginManager.py", line 231, in RunEx
    ret = getattr(inst, function)(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/applet/NMPANSupport.py", line 333, in service_connect_handler
    conn = self.find_active_connection(d.Address, "panu")
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/applet/NMPANSupport.py", line 290, in find_active_connection
    nma_connection = self.find_connection(address, type)
  File "/usr/lib/python2.7/dist-packages/blueman/plugins/applet/NMPANSupport.py", line 278, in find_connection
    conns = self.nma.ListConnections()
AttributeError: 'NoneType' object has no attribute 'ListConnections'
```

---

### Post by BinaryMn on 2011-10-31
Bump.

---

