---
title: "Kid3 script to auto-tag MP3s?"
date: 2010-01-16
forum: Multimedia Software
---

### Post by Dbutabi on 2010-01-16
Hi all, long time ubuntu-er, first time poster :P

I have kid3 for tagging MP3s and I really like it, however I would like to be able to specify an mp3 of a song I recorded and have it tag every field except for artist and title with my personal website for promotional purposes.  I have a small amount of experience with python scripting, however I have no idea how I could get kid3 to automate this tagging.  Does anyone have any advice/help for me?

Thanks in advance :)

---

### Post by ufleisch on 2010-01-17
The D-Bus interface is described in the Kid3 handbook. You could use something like this:

```

#!/usr/bin/env python

import sys
import dbus

kid3 = dbus.SessionBus().get_object('net.sourceforge.kid3', '/Kid3')

def set_tags_in_file(filename):
    if kid3.openDirectory(filename):
        artist = kid3.getFrame(2, 'Artist')
        if not artist:
            artist = kid3.getFrame(1, 'Artist')
        title = kid3.getFrame(2, 'Title')
        if not title:
            title = kid3.getFrame(1, 'Title')
        for tagNr in (1, 2):
            kid3.removeTag(tagNr)
            kid3.setFrame(tagNr, 'Artist', artist)
            kid3.setFrame(tagNr, 'Title', title)
            for frame in  ('Album', 'Comment'):
                kid3.setFrame(tagNr, frame, 'http://my.promotional.url')
        kid3.save()

if __name__ == '__main__':
    set_tags_in_file(sys.argv[1])

```

---

### Post by Dbutabi on 2010-01-17
Thank you very much ufleisch.  Unfortunately I tried to run the script and it returned these errors: 
```
Traceback (most recent call last):
  File "tag.py", line 4, in <module>
    kid3 = dbus.SessionBus().get_object('net.sourceforge.kid3', '/Kid3')
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
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name net.sourceforge.kid3 was not provided by any .service files

```

I did some searching around, and found and downloaded a kid3 RPM file, and placed net.sourceforge.kid3.xml into /usr/share/dbus-1/interfaces/  .  At first the script seemed to be working, no errors were thrown.  Then I went in and saw that no tags had actually changed in the file, then with some debug statements I realized the script wasn't able to open the file, because I only specified file.mp3 as an argument versus /home/dbutabi/Python/file.mp3 .  So then I went and tried it again with the correct filepath and got this:
```

Traceback (most recent call last):
  File "tag.py", line 27, in <module>
    set_tags_in_file(sys.argv[1])
  File "tag.py", line 11, in set_tags_in_file
    artist = kid3.getFrame(2, 'Artist')
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

```
I realized that I had had kid3 open with file.mp3 open this whole time, so I closed it and tried to run the script again and now I keep getting that same error that I got at first.  I don't know how to fix it, any help would be greatly appreciated:confused:

---

### Post by ufleisch on 2010-01-18
First you should check if you really have a Kid3 version with dbus-support. The Kid3 version must be >= 1.0 and Kid3 must be compiled with Qt 4. You can check this for the KDE-version "kid3" in menu "Help/About Kid3", the KDE version must be >= 4, and for the version without KDE "kid3-qt" in "Help/About Qt", the Qt version must be >= 4. If you still have an old version, get a new package from [http://kid3.sourceforge.net/]("http://kid3.sourceforge.net/").

Then check if the dbus-interface works. One of the best tools for this is qdbusviewer. Start Kid3 and check if "net.sourceforge.kid3" is available in the "Session bus" tab. You can then double-click "Kid3/net.sourceforge.Kid3/Method: openDirectory" in the "Methods" tree view, then enter a path to open, "OK", and Kid3 should open that directory. Now you are ready to access Kid3 using Python.

---

