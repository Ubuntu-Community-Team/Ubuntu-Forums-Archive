---
title: "ZTE MF112 - SMS and data simultaneously ?"
date: 2011-05-20
forum: Networking &amp; Wireless
---

### Post by adsb on 2011-05-20
Just wondering if anyone has solved the problem of having an SMS listener (e.g. gnome-phone-manager) running whilst the MF112 is active for data.
The MF112 presents itself as 3 device nodes - /dev/ttyUSB{0,2}.  ttyUSB1 and ttyUSB2 both respond to AT commands, ttyUSB0 doesn't.  gnome-phone-manager, wammu, and others will talk to the MF112 with AT commands - until modem-manager comes along and grabs both /dev/ttyUSB1 and 2:

# fuser /dev/ttyUSB1
/dev/ttyUSB1:          919
# fuser /dev/ttyUSB2
/dev/ttyUSB2:          919
# ps -ef | grep 919
root       919     1  0 16:28 ?        00:00:00 /usr/sbin/modem-manager

Now the SMS tools can't connect to the MF112 on /dev/ttyUSB{1,2}.

My service provider sends SMS messages to warn me when I'm running low on credit.  At the moment I can't receive these whilst using the dongle for data.
It's like a car in which the fuel gauge can only be read when the engine is turned off...

---

### Post by alexfish on 2011-05-20
hi

try using sakis3g for the network connection,
**[*Sakis3G* - All-in-one script]("http://www.google.co.uk/url?sa=t&source=web&cd=1&sqi=2&ved=0CBgQFjAA&url=http%3A%2F%2Fwww.sakis3g.org%2F&rct=j&q=sakis3g&ei=FavWTcSkNoywhAfl8NTCBg&usg=AFQjCNFR0OA7GJQY3djYswddHkMjARyyDw&cad=rja")**

---

### Post by adsb on 2011-05-31
> **alexfish said:**
> hi

try using sakis3g for the network connection,

 
I think you're right.  I've written a little script to use the ModemManager API to retrieve SMSes, and that throws DBUS errors.  From what I gather, ModemManager is not complete yet.
 I've also managed to get gnome-phone-manager to connect to /dev/ttyUSB1, and then brought the 3G connection up.  However this doesn't show me received SMSes, it just loses them.
 sakis3g seems to work OK, haven't tried it with gnome-phone-manager yet.  I just need a big flashing red icon to remind me that my network connection is expensive when I'm using the dongle!

---

### Post by alexfish on 2011-06-01
hi

modem manager via dbus is the only way to communicate , but best done with python script. but do know certain developers do there own replacement for modem-manger but often limited to the type of devices they access.

whilst the modem-manager may on top of, seem to have decent api I think there is a lot to be desired at the Network Manager end as regards these devices.

if your interested in taking this further as regards scripting can have a look at
                         [Natty, known bugs, fixes and work arounds]("http://ubuntuforums.org/showthread.php?t=1749312")  Look at post #30 . there is a download script call mm-test . it gives most of what you need as mm and using the dbus, it is written in python. to get access to the script best to sudo to the downloads then wget, don't for get to chmod 666 <file> for user access.

other than that as far as a desktop user is concerned have always found sakis3g in combination with gammu or (wammu)the best option.
[B]
Added:
ModemManager,rest of info where to look

[/B]do file search "modemmanager" then look at 
/user/share/dbus-1/interfaces/org.freedesktop.ModemManager.Modem.*.xml files
**doc files look in folder** (ref to API ,functions ,etc)
user/share/doc/modemmanager/spec.html[B]
also forgot there is also python gammu (should be in the repo's)
[/B] 
regards

alexfish

---

### Post by adsb on 2011-06-05
> **alexfish said:**
> hi

modem manager via dbus is the only way to communicate , but best done with python script. but do know certain developers do there own replacement for modem-manger but often limited to the type of devices they access.

whilst the modem-manager may on top of, seem to have decent api I think there is a lot to be desired at the Network Manager end as regards these devices.

if your interested in taking this further as regards scripting can have a look at
                         [Natty, known bugs, fixes and work arounds]("http://ubuntuforums.org/showthread.php?t=1749312")  Look at post #30 . there is a download script call mm-test . it gives most of what you need as mm and using the dbus, it is written in python. to get access to the script best to sudo to the downloads then wget, don't for get to chmod 666 <file> for user access.

other than that as far as a desktop user is concerned have always found sakis3g in combination with gammu or (wammu)the best option.
[B]
Added:
ModemManager,rest of info where to look

[/B]do file search "modemmanager" then look at 
/user/share/dbus-1/interfaces/org.freedesktop.ModemManager.Modem.*.xml files
**doc files look in folder** (ref to API ,functions ,etc)
user/share/doc/modemmanager/spec.html[B]
also forgot there is also python gammu (should be in the repo's)
[/B] 
regards

alexfish

Thanks, I'd previously downloaded a couple of the examples from the git repository and wrote a little Python script to poll for SMSes:

```
#!/usr/bin/python

# An example on how to receive an SMS message using ModemManager

import sys
import dbus

bus = dbus.SystemBus()

manager_proxy = bus.get_object('org.freedesktop.ModemManager', '/org/freedesktop/ModemManager')
manager_iface = dbus.Interface(manager_proxy, dbus_interface='org.freedesktop.ModemManager')
modems = manager_iface.EnumerateDevices()
if len(modems) == 0:
    print "No modems found"
    sys.exit(1)
proxy = bus.get_object('org.freedesktop.ModemManager', modems[0])
modem = dbus.Interface(proxy, dbus_interface='org.freedesktop.ModemManager.Modem')
sms_iface = dbus.Interface(proxy, dbus_interface='org.freedesktop.ModemManager.Modem.Gsm.SMS')
try:
    msg_dict = sms_iface.Get(0)
    print msg_dict.number
    print msg_dict.text
except:
    print "Receiving message failed"
    print sys.exc_info()[0]
```
All it does is tell me there's a DBUS error:
$ ./mm-check-sms.py 
Receiving message failed
<class 'dbus.exceptions.DBusException'>

so I guess this is part of the ModemManager API that's not finished yet.

---

