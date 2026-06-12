---
title: "Need to run hdparm after reinsertion of DVD"
date: 2007-11-09
forum: Mythbuntu
---

### Post by ali1234 on 2007-11-09
I want to use hdparm to silence my DVD drive. I'm using this command:

hdparm -E 8 /dev/sr0

It works until I put in another disc, then the drive goes back to maximum speed and becomes very noisy once again.

Is there some way to run a command every time a new CD is inserted?

---

### Post by superm1 on 2007-11-10
> **ali1234 said:**
> I want to use hdparm to silence my DVD drive. I'm using this command:

hdparm -E 8 /dev/sr0

It works until I put in another disc, then the drive goes back to maximum speed and becomes very noisy once again.

Is there some way to run a command every time a new CD is inserted?
Perhaps in the Thunar settings, go to the area that is used to "run this command if you insert a new dvd"

---

### Post by ali1234 on 2007-11-11
Unfortunately that only works for DVD/VCDs and not data discs.

---

### Post by ali1234 on 2007-11-13
The following python script solves the problem by listening for CD drive events using DBUS. I put it in /usr/local/bin and added a line to /etc/rc.local to run it in the background.

```

#!/usr/bin/python

import gobject
import dbus
import os
from dbus.mainloop.glib import DBusGMainLoop

# The identifier of your CD/DVD drive as used by DBUS. Find it by running:
# dbus-monitor --system
# Then ejecting the CD tray. 

cd_dbus_path="/org/freedesktop/Hal/devices/storage_model_DVD_ROM_DDU1615"

def cd_tray_event_handler(x,y):
  os.system('hdparm -E 8 /dev/scd0')

# Set CD speed at startup
cd_tray_event_handler(0,0)

DBusGMainLoop(set_as_default=True)
system_bus = dbus.SystemBus()
system_bus.add_signal_receiver(cd_tray_event_handler, path=cd_dbus_path)

loop = gobject.MainLoop()
loop.run()

```

---

