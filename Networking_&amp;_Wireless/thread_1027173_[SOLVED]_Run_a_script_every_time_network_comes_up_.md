---
title: "[SOLVED] Run a script every time network comes up after boot"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by Cheesehead on 2009-01-01
I want to run a script after networking comes up at boot, just like ntp does.

The script is simple, it just refreshes my desktop. But how do I get it to work at startup? If I put it in /etc/network/if-up.d, nothing happens. Do I need to add a link somewhere?

I'm running Xubuntu 8.04, with Network Manager, and all networking works just great.

---

### Post by kevdog on 2009-01-01
Not sure if Network Manager is setup to run scrips after a connection is made unless manually configured.  That would require manual configuration of the /etc/network/interfaces file and would be an entry similar to post-up ....etc.  I know WICD has the ability to run scripts after making a connection, however to the best of my knowledge it also makes use of the post-up

---

### Post by mpokrywka on 2009-01-01
There is a way to start script after Network Manager gets a connection, but it requires some python scripting.
Not very elegant: separate process that waits for network connection to be established to run some scripts.
This functionality should be built-in in NM - but I had something like this working:
```

#!/usr/bin/env python
# -*- coding: utf-8 -*-

import gobject, dbus
from dbus.mainloop.glib import DBusGMainLoop
import os

# what to do on network device activation
def on_device_now_active(*args):
        obj_path = args[0]
        net_name = args[1]
        #print "obj_path", obj_path
        #print "net_name", net_name
        if obj_path.endswith("eth1") and (net_name == "home_network"):
                #print "Connected to:", net_name
                #print
                os.system("pon myvpn")
                #os.system("skype &") # run skype in background

# dbus events will be part of glib message loop
DBusGMainLoop(set_as_default=True)
# attach to D-BUS system bus and wait for DeviceNowActive event
bus = dbus.SystemBus()
proxy = bus.get_object('org.freedesktop.NetworkManager',
        '/org/freedesktop/NetworkManager')
proxy.connect_to_signal("DeviceNowActive", on_device_now_active)
# program main loop - waits for events and dispatches handlers
loop = gobject.MainLoop()
loop.run()

```
but I actually didn't put it in desktop startup. Nevertheless, from console it works as expected.
This code needs validating parameters for handler (I dunno if f.e. net_name is available for wired network).

---

### Post by Cheesehead on 2009-01-02
Thanks. I may try it.
ntp seems to work upon network startup. Anyone have an idea how it does that?

---

### Post by blueridgedog on 2009-01-02
I assume you mean that your network goes up and down in the course of a session (however long), otherwise you could put your command at the end of the run level start up.  For example, when the commands in /etc/init.d/rc.local are run, the the network start phase has finished (S28NetworkManager).

---

### Post by blueridgedog on 2009-01-02
> **Cheesehead said:**
> I want to run a script after networking comes up at boot, just like ntp does.


Looking at the man page:

> There exists for each of the above mentioned options a directory
/etc/network/if-<option>.d/ the scripts in which are run (with no argu
ments) using run-parts( after the option itself has been processed.

So, if you put your script in /etc/network/if-up.d (the directory) it will run with ntp and the rest.

However, Kevdog implies that there may be another process of starting and stopping interfaces, which may negate this.

---

### Post by Favux on 2009-01-03
Hi,

This may be somewhat of assistance:

[http://www.arachnoid.com/linux/Netwo...ger/index.html]("http://www.arachnoid.com/linux/Netwo...ger/index.html")

---

### Post by Cheesehead on 2009-01-03
Placed the script in /etc/dhcp3/dhclient-enter-hooks.d
Works perfectly upon network startup.

---

### Post by kevdog on 2009-01-03
Glad you got this solved however this would only be applicable if you were running dhcp :)

---

### Post by Cheesehead on 2011-01-20
I found another method that is easier to maintain - use Upstart events.

When connecting to a network, if-up emits a 'network-device-up' upstart signal.

I wrote an upstart listener to that simply runs my script(s) when it hears the signal. Since there are all kinds up upstart events, and I can add my own events, it's a convenient place to keep a lot of my event-based customizations.

---

