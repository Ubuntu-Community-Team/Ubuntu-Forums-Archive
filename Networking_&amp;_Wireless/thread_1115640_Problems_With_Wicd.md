---
title: "Problems With Wicd"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by Kenny_C on 2009-04-04
Hi.
I am trying to connect to my wireless network with Wicd, after many attempts with network manager failed. Wicd installed fine, but I cannot get it to run. When i run *sudo wicd*, it seems to be ok, and then i try running *sudo wicd-client* like it says in the readme, but this is what I get:
[CENTER][I]pc@pc-desktop:~$ sudo wicd-client
Traceback (most recent call last):
  File "/usr/lib/wicd/wicd-client.py", line 50, in <module>
    import wicd.gui as gui
  File "/usr/lib/python2.5/site-packages/wicd/gui.py", line 2005, in <module>
    setup_dbus()
  File "/usr/lib/python2.5/site-packages/wicd/gui.py", line 177, in setup_dbus
    proxy_obj = bus.get_object("org.wicd.daemon", '/org/wicd/daemon')
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 240, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 236, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 179, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 277, in start_service_by_name
    'su', (bus_name, flags)))
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 603, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.wicd.daemon was not provided by any .service files
[/I][/CENTER]

Can anybody help?

---

### Post by Cotopaxi on 2009-04-04
I am using wicd under kubuntu intrepid. In my case, I have an icon (two computer screens with black screen colour) in the lower right corner of the task bar. When I click on this icon, it the wicd window opens and shows me the available networks. Then I just choose a network and click on &#8220;connect&#8221;. When this clicked icon changes to &#8220;disconnect&#8221;, I know that I am connected.

I would eventually dis-install wicd and re-install it.

I hope I helped a bit. Good luck

---

### Post by Kenny_C on 2009-04-06
No luck. Ive reinstalled it a number of times, and still get the same problem. I can get Wicd running on my laptop running Zenwalk, but i still cannot get access to my network.](*,)

---

### Post by imdano on 2009-04-06
> **Kenny_C said:**
> Hi.
I am trying to connect to my wireless network with Wicd, after many attempts with network manager failed. Wicd installed fine, but I cannot get it to run. When i run *sudo wicd*, it seems to be ok, and then i try running *sudo wicd-client* like it says in the readme, but this is what I get:
[CENTER][I]pc@pc-desktop:~$ sudo wicd-client
Traceback (most recent call last):
  File "/usr/lib/wicd/wicd-client.py", line 50, in <module>
    import wicd.gui as gui
  File "/usr/lib/python2.5/site-packages/wicd/gui.py", line 2005, in <module>
    setup_dbus()
  File "/usr/lib/python2.5/site-packages/wicd/gui.py", line 177, in setup_dbus
    proxy_obj = bus.get_object("org.wicd.daemon", '/org/wicd/daemon')
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 240, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 236, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 179, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 277, in start_service_by_name
    'su', (bus_name, flags)))
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 603, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.wicd.daemon was not provided by any .service files
[/I][/CENTER]

Can anybody help?You have to start the daemon before you can run the client```
sudo /etc/init.d/wicd start
```If you still get the same error, run this:```
sudo wicd -foe
```and post the error you get here.

---

