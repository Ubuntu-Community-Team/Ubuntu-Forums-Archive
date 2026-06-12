---
title: "Ubuntu 11.10 Bluetooth Iphone tethering broken, worked in 11.04"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by regiss on 2011-10-20
Hi guys,

everything was working fine with bleutooth iPhone tethering under 11.04 however after upgrade to 11.10 I am getting these error messages from blueman.

Connection Failed: Traceback (most recent call last):...

I can successfully pair device, but when trying to create Network Access Point I get: 

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
```Can anybody help? 

Thank you Ondrej

---

### Post by regiss on 2011-10-26
Good news everyone, there is new version of blueman 1.23
[http://blueman-project.org/download.html](http://blueman-project.org/download.html)

This version fixed my problem. :)

---

