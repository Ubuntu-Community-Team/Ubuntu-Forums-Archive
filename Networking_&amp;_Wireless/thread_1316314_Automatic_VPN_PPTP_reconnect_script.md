---
title: "Automatic VPN PPTP reconnect script"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by liamria.z01 on 2009-11-05
I would like to share what I learnt with regards to reconnecting VPN connections. I am using 9.04 and I had the problem that my VPN connection dropped now and then, and I did not want to manually reconnect it all the time again. Obviously the Ubuntu network manager (applet) does not provide such an automatic VPN reconnect functionality, so I started searching for a solution on the internet. Several bugs have been filed with regards to that and I am surprised that nobody has taken care of this yet. This issue seems to have been ignored for quite a while.

Nevertheless, a couple of guys tried to find a solution using scripts. I found [this thread]("http://www.gingedas.net/node/269"), but it did not work for me, but [this one]("http://www.mail-archive.com/networkmanager-list@gnome.org/msg12947.html") had the right solution. Thanks to Daniel Akerud who was so kind as to resend me his modified script I could work out a solution for me. It is the following python script to reconnect the VPN connection previously configured via network manager:

First the original script from Daniel Akerud:

nm-vpn-restart.py

```

#!/usr/bin/python

import sys
import os
import dbus
import gobject
from  dbus.mainloop.glib import DBusGMainLoop

# The uuid of the VPN connection to activate
VPN_CONNECTION_UUID = "FILL IN YOUR OWN"

# The uuid of the connection that needs to be active to start the VPN connection
ACTIVE_CONNECTION_UUID = "FILL IN YOUR OWN"

# some service, path and interface constants
NM_DBUS_SERVICE                   = "org.freedesktop.NetworkManager"
NM_DBUS_PATH                      = "/org/freedesktop/NetworkManager"
NM_DBUS_INTERFACE                 = "org.freedesktop.NetworkManager"
NM_DBUS_IFACE_CONNECTION_ACTIVE   = "org.freedesktop.NetworkManager.Connection.Active"
NM_DBUS_SERVICE_SYSTEM_SETTINGS   = "org.freedesktop.NetworkManagerSystemSettings"
NM_DBUS_SERVICE_USER_SETTINGS     = "org.freedesktop.NetworkManagerUserSettings"
NM_DBUS_IFACE_SETTINGS            = "org.freedesktop.NetworkManagerSettings"
NM_DBUS_PATH_SETTINGS             = "/org/freedesktop/NetworkManagerSettings"
NM_DBUS_IFACE_SETTINGS_CONNECTION = "org.freedesktop.NetworkManagerSettings.Connection"

DBusGMainLoop(set_as_default=True)

nm_dbus_settings_services = (NM_DBUS_SERVICE_SYSTEM_SETTINGS, NM_DBUS_SERVICE_USER_SETTINGS)

def get_connections(bus, service):
  proxy = bus.get_object(service, NM_DBUS_PATH_SETTINGS)
  iface = dbus.Interface(proxy, dbus_interface=NM_DBUS_IFACE_SETTINGS)
  return iface.ListConnections()

def get_connection_by_uuid(bus, uuid):
  for service in nm_dbus_settings_services:
    for c in get_connections(bus, service):
      proxy = bus.get_object(service, c)
      iface = dbus.Interface(proxy, dbus_interface = NM_DBUS_IFACE_SETTINGS_CONNECTION)
      settings = iface.GetSettings()
      if settings['connection']['uuid'] == uuid:
        return (c, service)
  return None

def list_uuids(bus):
  for service in nm_dbus_settings_services:
    for c in get_connections(bus, service):
      proxy = bus.get_object(service, c)
      iface = dbus.Interface(proxy, dbus_interface=NM_DBUS_IFACE_SETTINGS_CONNECTION)
      settings = iface.GetSettings()
      conn = settings['connection']
      print " %s: %s - %s (%s)" % (service, conn['uuid'], conn['id'], conn['type'])

def get_active_connection_path(bus, uuid):
  proxy = bus.get_object(NM_DBUS_SERVICE, NM_DBUS_PATH)
  iface = dbus.Interface(proxy, dbus_interface='org.freedesktop.DBus.Properties')
  active_connections = iface.Get(NM_DBUS_INTERFACE, 'ActiveConnections')
  connection_and_service = get_connection_by_uuid(bus, uuid)
  if connection_and_service == None:
    return None
  for a in active_connections:
    proxy = bus.get_object(NM_DBUS_SERVICE, a)
    iface = dbus.Interface(proxy, dbus_interface='org.freedesktop.DBus.Properties')
    path = iface.Get(NM_DBUS_IFACE_CONNECTION_ACTIVE, 'Connection')
    service = iface.Get(NM_DBUS_IFACE_CONNECTION_ACTIVE, 'ServiceName')
    if service != connection_and_service[1]:
      continue
    proxy = bus.get_object(connection_and_service[1], path)
    iface = dbus.Interface(proxy, dbus_interface=NM_DBUS_IFACE_SETTINGS_CONNECTION)
    settings = iface.GetSettings()
    if settings['connection']['uuid'] == uuid:
      return a
  return None

def activate_connection(bus, vpn_connection, active_connection):
  def reply_handler(opath):
    print "<<SUCCESS>>"
    sys.exit(0)
  def error_handler(*args):
    print "<<FAILURE>>"
    sys.exit(1)
  proxy = bus.get_object(NM_DBUS_SERVICE, NM_DBUS_PATH)
  iface = dbus.Interface(proxy, dbus_interface=NM_DBUS_INTERFACE)
  iface.ActivateConnection(NM_DBUS_SERVICE_USER_SETTINGS,
                           vpn_connection[0],
                           dbus.ObjectPath("/"), 
                           active_connection,
                           reply_handler=reply_handler,
                           error_handler=error_handler)

bus = dbus.SystemBus()

print "connections:"
list_uuids(bus)

if len(VPN_CONNECTION_UUID) < 1 or len(ACTIVE_CONNECTION_UUID) < 1:
    print "you need to set the uuids"
    sys.exit(0)

vpn_connection = get_connection_by_uuid(bus, VPN_CONNECTION_UUID)
if not vpn_connection:
    print "Configured VPN connection is not known to NM, check VPN_CONNECTION_UUID."
    sys.exit(1)

active_connection = get_connection_by_uuid(bus, ACTIVE_CONNECTION_UUID)
if not active_connection:
  print "Configured active connection is not known to NM, check ACTIVE_CONNECTION_UUID."
  sys.exit(1)

if get_active_connection_path(bus, VPN_CONNECTION_UUID) != None:
  print "VPN connection already activated"
  sys.exit(0)

active_connection_path = get_active_connection_path(bus, ACTIVE_CONNECTION_UUID)
if not active_connection_path:
  print "The required connection isn't active at the moment"
  sys.exit(0)

print "connecting to:\n  '%s'\nwith active connection:\n  '%s'" % (vpn_connection, active_connection)

activate_connection(bus, vpn_connection, active_connection_path)

loop = gobject.MainLoop()
loop.run()


```**DO NOT FORGET to fill in your UUID on the top section of the script after you have run it for the first time....**


I modified it a bit for my purposes:

nm-vpn-restart2.py

```

#!/usr/bin/python

import sys
import os
import dbus
import gobject
from  dbus.mainloop.glib import DBusGMainLoop

# The uuid of the VPN connection to activate
VPN_CONNECTION_UUID = "FILL IN YOUR OWN"

# The uuid of the connection that needs to be active to start the VPN connection
ACTIVE_CONNECTION_UUID = "FILL IN YOUR OWN"

# some service, path and interface constants
NM_DBUS_SERVICE                   = "org.freedesktop.NetworkManager"
NM_DBUS_PATH                      = "/org/freedesktop/NetworkManager"
NM_DBUS_INTERFACE                 = "org.freedesktop.NetworkManager"
NM_DBUS_IFACE_CONNECTION_ACTIVE   = "org.freedesktop.NetworkManager.Connection.Active"
NM_DBUS_SERVICE_SYSTEM_SETTINGS   = "org.freedesktop.NetworkManagerSystemSettings"
NM_DBUS_SERVICE_USER_SETTINGS     = "org.freedesktop.NetworkManagerUserSettings"
NM_DBUS_IFACE_SETTINGS            = "org.freedesktop.NetworkManagerSettings"
NM_DBUS_PATH_SETTINGS             = "/org/freedesktop/NetworkManagerSettings"
NM_DBUS_IFACE_SETTINGS_CONNECTION = "org.freedesktop.NetworkManagerSettings.Connection"

DBusGMainLoop(set_as_default=True)

nm_dbus_settings_services = (NM_DBUS_SERVICE_SYSTEM_SETTINGS, NM_DBUS_SERVICE_USER_SETTINGS)

def get_connections(bus, service):
  proxy = bus.get_object(service, NM_DBUS_PATH_SETTINGS)
  iface = dbus.Interface(proxy, dbus_interface=NM_DBUS_IFACE_SETTINGS)
  return iface.ListConnections()

def get_connection_by_uuid(bus, uuid):
  for service in nm_dbus_settings_services:
    for c in get_connections(bus, service):
      proxy = bus.get_object(service, c)
      iface = dbus.Interface(proxy, dbus_interface = NM_DBUS_IFACE_SETTINGS_CONNECTION)
      settings = iface.GetSettings()
      if settings['connection']['uuid'] == uuid:
        return (c, service)
  return None

def list_uuids(bus):
  for service in nm_dbus_settings_services:
    for c in get_connections(bus, service):
      proxy = bus.get_object(service, c)
      iface = dbus.Interface(proxy, dbus_interface=NM_DBUS_IFACE_SETTINGS_CONNECTION)
      settings = iface.GetSettings()
      conn = settings['connection']
      print " %s: %s - %s (%s)" % (service, conn['uuid'], conn['id'], conn['type'])

def get_active_connection_path(bus, uuid):
  proxy = bus.get_object(NM_DBUS_SERVICE, NM_DBUS_PATH)
  iface = dbus.Interface(proxy, dbus_interface='org.freedesktop.DBus.Properties')
  active_connections = iface.Get(NM_DBUS_INTERFACE, 'ActiveConnections')
  connection_and_service = get_connection_by_uuid(bus, uuid)
  if connection_and_service == None:
    return None
  for a in active_connections:
    proxy = bus.get_object(NM_DBUS_SERVICE, a)
    iface = dbus.Interface(proxy, dbus_interface='org.freedesktop.DBus.Properties')
    path = iface.Get(NM_DBUS_IFACE_CONNECTION_ACTIVE, 'Connection')
    service = iface.Get(NM_DBUS_IFACE_CONNECTION_ACTIVE, 'ServiceName')
    if service != connection_and_service[1]:
      continue
    proxy = bus.get_object(connection_and_service[1], path)
    iface = dbus.Interface(proxy, dbus_interface=NM_DBUS_IFACE_SETTINGS_CONNECTION)
    settings = iface.GetSettings()
    if settings['connection']['uuid'] == uuid:
      return a
  return None

def activate_connection(bus, vpn_connection, active_connection):
  def reply_handler(opath):
    print "<<SUCCESS>>"
    sys.exit(0)
  def error_handler(*args):
    print "<<FAILURE>>"
    sys.exit(1)
  proxy = bus.get_object(NM_DBUS_SERVICE, NM_DBUS_PATH)
  iface = dbus.Interface(proxy, dbus_interface=NM_DBUS_INTERFACE)
  iface.ActivateConnection(NM_DBUS_SERVICE_USER_SETTINGS,
                           vpn_connection[0],
                           dbus.ObjectPath("/"), 
                           active_connection,
                           reply_handler=reply_handler,
                           error_handler=error_handler)

bus = dbus.SystemBus()

#print "connections:"
#list_uuids(bus)

if len(VPN_CONNECTION_UUID) < 1 or len(ACTIVE_CONNECTION_UUID) < 1:
    print "you need to set the uuids"
    sys.exit(0)

vpn_connection = get_connection_by_uuid(bus, VPN_CONNECTION_UUID)
if not vpn_connection:
    print "Configured VPN connection is not known to NM, check VPN_CONNECTION_UUID."
    sys.exit(1)

active_connection = get_connection_by_uuid(bus, ACTIVE_CONNECTION_UUID)
if not active_connection:
  print "Configured active connection is not known to NM, check ACTIVE_CONNECTION_UUID."
  sys.exit(1)

if get_active_connection_path(bus, VPN_CONNECTION_UUID) != None:
  print "VPN connection already activated"
  sys.exit(0)

active_connection_path = get_active_connection_path(bus, ACTIVE_CONNECTION_UUID)
if not active_connection_path:
  print "The required connection isn't active at the moment"
  sys.exit(0)

print "connecting...." # to:\n  '%s'\nwith active connection:\n  '%s'" % (vpn_connection, active_connection)

activate_connection(bus, vpn_connection, active_connection_path)

loop = gobject.MainLoop()
loop.run()

```and I created a bash script that takes care of the reconnection every 20 seconds which I run in a terminal

```

#!/bin/bash

while [ 1 ]; do
   echo -n $(date) "##  "
   sudo /home/USER/Install/VPN-Control/nm-vpn-restart2.py #wherever you have installed the script
   sleep 20
done

```I know that I will not win a programming price for that but for me it works and I am very happy with it....:D

---

### Post by TidyBhoy on 2010-01-17
sorry to sound a bit silly here... but what do i do with that script exactly... how do i implement it? where does it go?

---

### Post by agkbill on 2010-01-17
Tried this out today and it works great.

For me the first script worked but not the second one you modified.

What is the difference?


Really happy for getting this to work, thank you!

---

### Post by TidyBhoy on 2010-01-17
any chance you could tell me how you done it? I couldnt open python to add that code..

---

### Post by agkbill on 2010-01-19
I am running Ubuntu 9.10 and python must have been installed by default. I just made the textile with the script executional and then run it in a terminal.

The first time without any changes whatever. That gives the UUID. Then I copied thous into the script.

That process you need to do every time you restart the computer, looks like you get new UUID every time.

Best regards,
/Christer

---

### Post by TidyBhoy on 2010-01-19
well that sucks :(

---

### Post by KhaaL on 2010-04-30
I think its silly that such a basic functionality is sorely missing from ubuntu for so long, with no reliable solution!

---

### Post by Sandiep on 2010-04-30
[COLOR=Magenta]**Does the rm command work in bash scripts?**[/COLOR]

---

### Post by Eldis on 2010-05-12
Really nice script thanks for posting and sharing.

Would be really nice to get the UUIDs somehow automagically into the script on boot. I don't boot often but still I dislike the idea of having to manually fiddle with this. I'm sure it's possible but just beyond my scripting abilities.

couldn't we somehow grep and echo it into the script ?

---

### Post by Eldis on 2010-05-14
Nevermind my previous post, the UUIDs don't seem to change on reboot I assumed they would.

My only problem now is that it still requires a keyring password for the vpn connection on reboot. Any way I could get rid of that keyring password asking for the VPN connection ?

If I check the available for all users checkbox the VPN connection will no longer start.

---

### Post by deanfox on 2010-06-03
WOW!  Thanks!  This works prefect.  I've needed this for quite a while.  It's difficult to understand why this issue has been ignored for so long year(s).  VPN is by definition supposed to be secure.  When disconnected, for what ever reason, packets should not then start to be sent out over a non-secure connection.  This has been a real problem until now.  I wish there was a way to "up-vote" you :)  Well done!

---

### Post by KhaaL on 2010-06-05
TRying to get this work in Lucid, but there's no /etc/network/interfaces/ /NetworkManager/system-connections/Auto eth1

---

### Post by mastergb on 2010-06-23
You can use this software:
[http://sourceforge.net/projects/vpnautoconnect/](http://sourceforge.net/projects/vpnautoconnect/)
it does the job perfectly for you, is very small and can be seen as an addon has NetworkManager. It's very easy to install and it's automatically launch at startup ;)

---

### Post by apoapo on 2010-10-27
Please complain here to raise importance:

[B][https://bugs.launchpad.net/network-manager/+bug/280571](https://bugs.launchpad.net/network-manager/+bug/280571)
[/B]

Show them, that small showstoppers are  important bugs also.
It's a main problem of linux. Developers stop when things "work".

Like: Just get that little script, copy it there, configure itwith vi, give some access rights, make it autostart,  works! 

Hell no!!!

Probably 90% of all Ubuntuusers have no idea how to do only 1 step of that. And it shouldn't be necessary to know such technical stuff.

---

### Post by sreeslinux on 2010-10-29
Works a treat. Thanks

[http://sourceforge.net/projects/vpnautoconnect/](http://sourceforge.net/projects/vpnautoconnect/)

---

### Post by myrison on 2011-02-03
I realize this is a late reply to this thread, but I wanted to send a thank you to the OP for the script.  The original script is tested and working well in Lucid (I didn't test the second since the first one worked fine).  Thank you for posting them.

To others with the same question as Khaal, the way you find your UUIDs is by running gconf-editor in a terminal and then navigating to system-> networking -> connections -> <connection number> -> connection -> UUID.  Then make sure you input two separate UUIDs into the script, one for the LAN connection (i.e. eth0) and one for the VPN you want to autoreconnect.

---

### Post by buntu504 on 2011-11-12
Script still works for 10.10 Maverick.  To find your UUID just use the command "nmcli con status" and input the UUID's into the python script.

vpnautoconnect works just as well

[https://we.riseup.net/riseuphelp+en/vpnautoconnect](https://we.riseup.net/riseuphelp+en/vpnautoconnect)

---

### Post by j.daniel on 2012-04-05
Just my $0.02; I had a similar problem a while ago and found an in my opinion better solution: nmcli.

To establish a connection: 
```
nmcli con up id <VPN NAME>
```

To see which connections are up:
```
nmcli con status
```

These can be put in a script fairly easy
```

#! /bin/bash

VPN="<YOUR VPN NAME>"

while true; do
  UP=$(nmcli con status | grep "$VPN")
  if [ -z "$UP" ]; then
    nmcli con up id "$VPN"
  fi
  sleep 20
done

```

With reservations for bad memory; I write this well away from my linux box.

Cheers!
/ Daniel

---

### Post by ziphem on 2012-04-13
I know also a super late reply to this thread, but how do I modify this script so that, instead of my system connecting to the VPN when I connect to the defined UUID Wifi network, I connect to the VPN wen I'm *not* connected to the defined UUID Wifi network?  I tried changing the == to != in the blind hope it would just work, and of course it didn't.  Any help would be greatly appreciated!!!


Thanks!!

---

