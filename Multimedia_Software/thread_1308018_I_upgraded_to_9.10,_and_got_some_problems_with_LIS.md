---
title: "I upgraded to 9.10, and got some problems with LISTEN media player"
date: 2009-10-31
forum: Multimedia Software
---

### Post by nahuel_89p on 2009-10-31
when i try to run listen, i get this:

> /home/nahuel/.themes/Dust Burnt/gtk-2.0/gtkrc:602: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/nahuel/.themes/Dust Burnt/gtk-2.0/gtkrc:603: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/lib/pymodules/python2.6/musicbrainz2/model.py:21: DeprecationWarning: the sets module is deprecated
  from sets import Set


I think that the important thing is the musicbrainz2 issue. But i already checked in synaptic, and it's installed. I even reinstalled listen, but it doesn't work.

If i try to open listen in sudo mode, i get this:

> AttributeError: 'module' object has no attribute 'Element'                                                                                     
/usr/lib/pymodules/python2.6/musicbrainz2/model.py:21: DeprecationWarning: the sets module is deprecated                                       
  from sets import Set                                                                                                                         
Traceback (most recent call last):                                                                                                             
  File "listen", line 200, in <module>                                                                                                         
    ListenApp()                                                                                                                                
  File "listen", line 141, in __init__                                                                                                         
    self.option.run_load()                                                                                                                     
  File "/usr/lib/listen/option_parser.py", line 113, in run_load
    obj = bus.get_object("org.gnome.Listen","/org/gnome/listen")
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
nahuel@nahuel-desktop:~$


Obviously, the application doesn't open.

Thanks.

---

### Post by nahuel_89p on 2009-11-01
Problem solved. Just delete the /.cache/listen and /.config/listen folders. Listen will run... but the library doesn't manage my media files properly... a lot of songs are named like "file://media/disk..." and i don't know why, any idea?

---

### Post by mine070 on 2009-11-01
When was the last time it worked and Anything you changed in Ubuntu since?

---

### Post by nahuel_89p on 2009-11-01
last time it wasn't the upgraded version of listen, since i was using it in ubuntu 9.04, and it worked perfectly... ubuntu 9.10 upgraded automatically listen (the current version is 0.6.2, and in ubuntu 9.04 i think it was listen 0.5)

by the way, it seems i have to delete the the /.cache/listen and /.config/listen folders every time i restart the computer. Otherwise it won't work.
Oh and listen process has a high cpu usage...

am i the only one with this problem? if not, i think that listen is really needing a bugfix version...

---

### Post by gaston.julia on 2009-11-05
Hi there,

I can confirm the high CPU usage (top says something about 95 - 105%). Haven't tried to delete any folders so far since the library works.

cheers,
gaston

P.S.: Just found that if I start Listen(0.6.2) and it is not resuming playback automatically CPU usage is close to 0, when playback starts everything back to ``normal'' (100% CPU) even on pause. btw notification area entry is missing as well

P.P.S: found that a bug report is filed: [https://bugs.launchpad.net/listen/+bug/385192](https://bugs.launchpad.net/listen/+bug/385192)

---

