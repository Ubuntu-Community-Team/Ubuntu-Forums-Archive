---
title: "Mythbuntu control center irfrared error"
date: 2015-05-03
forum: Mythbuntu
---

### Post by donb21 on 2015-05-03
I'm trying to add an mce remote control (using Mythbuntu control center), I get this error:


org.freedesktop.DBus.Error.Spawn.ChildSignaled
Process /usr/lib/dbus-1.0/dbus-daemon-launch-helper received signal 5


It happens no matter what remote I select.  Any ideas on what to try?

PS - This is a new installation...just moved contents and hardware from previous version (12.04) over to this one.

---

### Post by donb21 on 2015-05-10
No response here, so I just re-installed mythtv and made the selections during the install.  It correctly setup lirc and now the mythbuntu control center works (maybe it needed it's initial setup).

I confirmed the lirc setup is correct.  The remote still doesn't work, but that's for another day.

---

### Post by Lester_Burnham on 2015-08-16
I'm also having the same problem with a Windows MCE remote on  Mythbuntu 14.04.2 64bit (
Bus 004 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver)

If I disable remote support by selecting "No Addittional Remote Support" in MCC, the process completes OK.
I re-enable the remote support, no problem.
I select Windows Media Centre Trancievers and apply. I get the d-bus error below
```
org.freedesktop.DBus.Error.Spawn.ChildSignaled
Process /usr/lib/dbus-1.0/dbus-daemon-launch-helper received signal 5
```
Running MCC from the command line shows the errors below, when trying to install the same remote.
```
sudo mythbuntu-control-centre 
[sudo] password for lester: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
WARNING: Failed to set from config file. Setting defaults
Traceback (most recent call last):
  File "/usr/lib/python3.4/configparser.py", line 1116, in _unify_values
    sectiondict = self._sections[section]
KeyError: 'General'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/share/mythbuntu/plugins/python/mythbuntu-bare.py", line 85, in captureState
    self.changes['serverip'] = self.config.get("General", "serverip")
  File "/usr/lib/python3.4/configparser.py", line 754, in get
    d = self._unify_values(section, vars)
  File "/usr/lib/python3.4/configparser.py", line 1119, in _unify_values
    raise NoSectionError(section)
configparser.NoSectionError: No section: 'General'
You should now have a .lircrc file generated in /home/lester/.lircrc
All application specific lircrc files are in /home/lester/.lirc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
WARNING: Failed to set from config file. Setting defaults
Traceback (most recent call last):
  File "/usr/lib/python3.4/configparser.py", line 1116, in _unify_values
    sectiondict = self._sections[section]
KeyError: 'General'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/share/mythbuntu/plugins/python/mythbuntu-bare.py", line 85, in captureState
    self.changes['serverip'] = self.config.get("General", "serverip")
  File "/usr/lib/python3.4/configparser.py", line 754, in get
    d = self._unify_values(section, vars)
  File "/usr/lib/python3.4/configparser.py", line 1119, in _unify_values
    raise NoSectionError(section)
configparser.NoSectionError: No section: 'General'
```

The remote 100% in mythbuntu 12.04 on the same hardware. When I installed the system with 14.04.2 the remote was setup during the install, but would fail after a few button clicks. (batteries are OK)
If I install it manually via dpkg the same happens.

```
dmesg | grep usb
[    3.464562] usbcore: registered new interface driver usbhid
[    3.464567] usbhid: USB HID core driver
[    3.566823] input: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.0/rc/rc0/input6
[    3.566921] rc0: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.0/rc/rc0
[    3.632212] input: MCE IR Keyboard/Mouse (mceusb) as /devices/virtual/input/input7
[    3.650270] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[    3.848374] mceusb 4-1:1.0: Registered Philips eHome Infrared Transceiver with mce emulator interface version 1
[    3.848379] mceusb 4-1:1.0: 2 tx ports (0x3 cabled) and 2 rx sensors (0x1 active)
[    3.848445] usbcore: registered new interface driver mceusb
```

Any ideas please.
Lester

---

