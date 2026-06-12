---
title: "If VPN fails, stop all traffic."
date: 2012-02-06
forum: Networking &amp; Wireless
---

### Post by Seeked on 2012-02-06
Hello all,

As it stands, I can connect to my VPN without issues.  Every once and a while the connection is dropped, which is no big deal.  Much of the time whichever application was passing traffic over the VPN will start to put it over the regular network connection after the VPN fails.

Is there a way I can stop all internet traffic after the VPN fails?

Thank You

---

### Post by Vinkus on 2012-03-12
Why do not first disabling the regular network connection?

---

### Post by Seeked on 2012-04-20
If I disable the regular network connection, how will I connect to the VPN?

---

### Post by Seeked on 2012-06-03
Hello everybody here is a solution I found and modified. I am using it on Debian however, I don't see why it wouldn't work on Ubuntu.  I suspect that most recent versions of Ubuntu are running python 3 so you may have to use input() instead of raw_input().

I found it at [http://forums.fedoraforum.org/showthread.php?t=228773](http://forums.fedoraforum.org/showthread.php?t=228773) and made some modifications.

When  the VPN connection is lost or manually disconnected it will disable the  network adapter.  Just change "eth0" to your network adapter.

Cheers

```

#!/usr/bin/env python

#
# licensed under GNU General Public License version 2
#

import sys
import traceback

import gobject

import dbus
import dbus.decorators
import dbus.mainloop.glib

import os

def catchall_signal_handler(*args, **kwargs):
    print ("Caught signal: "
           + kwargs['member'])
    if args[0] >= 6: #vpn disconnect (6) or failure (7)
        print ("Killing internet connection...")
    #set eth0 to your network adapter
        os.system('ifconfig eth0 down')
    #if you are using python 3 no raw_input() exists so use input()
    raw_input("Press Enter to enable your network adapter...")
    #set eth0 to your network adapter
    os.system('ifconfig eth0 up')
    print ("Your network adapter has been enabled.")    

if __name__ == '__main__':
    dbus.mainloop.glib.DBusGMainLoop(set_as_default=True)
    print ("Monitoring your VPN connection...")
    bus = dbus.SystemBus()

    #lets make a catchall
    bus.add_signal_receiver(catchall_signal_handler, signal_name='VpnStateChanged', interface_keyword='dbus_interface', member_keyword='member')
    
    loop = gobject.MainLoop()
    loop.run()

```

---

