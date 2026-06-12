---
title: "Bluetooth Tethering Problems"
date: 2013-06-14
forum: Networking &amp; Wireless
---

### Post by loafkin on 2013-06-14
Hello all, I'm having some issues setting up tethering on my android smartphone to work with ubuntu 13.04. Having tried unsuccessfully to connect to anything at all using the standard bluetooth-applet, I installed Blueman, and am having better luck, but I'm still having problems. With blueman installed I can connect to bluetooth audio devices, I can see and pair to my phone, and I can browse the files on my phone using bluetooth. When I try to connect to the phone as a network adapter, I get the following errors out of Blueman:

Connection Failed: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
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


I've done a lot of searching around online and found a few bug reports including these:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=658572](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=658572)
I installed the patch on that site and it didn't help. I've tried with two different android phones and the same results. USB tethering works, Wi-fi tethering works, and bluetooth file browsing works, just no bluetooth tethering. Please help, I would like to make this work without going to a different or an older distro.

---

