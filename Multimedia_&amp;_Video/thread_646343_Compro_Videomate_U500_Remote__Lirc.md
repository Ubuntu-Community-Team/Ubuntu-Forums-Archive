---
title: "Compro Videomate U500 Remote / Lirc"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by matthewv on 2007-12-21
Hi All,

I recently bought a Compro Videomate U500 USB dvb-t tuner... while I've got most things working beautifully, I cannot work out how to get the included remote working. Would anyone have any ideas? I've tried most stuff I can think of..

---

### Post by matthewv on 2008-02-13
Here's where things are at the moment.. :

I've still been trying to get the inluded remote with my USB DVB-T Tuner working. It's a Compro Videomate U500 - it useses the dibcom 7000 chipset. After upgrading to Ubuntu 8.04 (hardy) I can now see the remote when I do a "cat /proc/bus/input/devices":

```

I: Bus=0003 Vendor=185b Product=1e78 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:00:02.1-4/ir0
S: Sysfs=/devices/pci0000:00/0000
:00:02.1/usb1/1-4/input/input7
U: Uniq=
H: Handlers=kbd event7
B: EV=3
B: KEY=10afc332 2842845 0 0 0 4 80018000 2180 40000801 9e96c0 0 800200 ffc

```

However, I get now output running irrecord:
```

matthew@matthew-desktop:~$ sudo irrecord -H dev/input -d /dev/input/event7 lircd.conf

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: initializing '/dev/input/event7'
This program will record the signals from your remote control
and create a config file for lircd.


[SNIP]

Press RETURN to continue.


Hold down an arbitrary button.
irrecord: gap not found, can't continue
irrecord: closing '/dev/input/event7'

```

Likewise, if I start lirc with the following: "sudo /usr/sbin/lircd -H dev/input -d /dev/input/event7 -n" and then run irw, it will run fine but there will be no output at all.

Just looking through /var/log/syslog and noticed that it is filled with messages such as this:
```

Feb 10 14:00:17 matthew-desktop kernel: [ 6549.313822] dib0700: Unknown remote controller key : 1E 42
Feb 10 14:00:18 matthew-desktop kernel: [ 6549.389724] dib0700: Unknown remote controller key : 1E 42
Feb 10 14:00:18 matthew-desktop kernel: [ 6549.465623] dib0700: Unknown remote controller key : 1E 42
Feb 10 14:00:18 matthew-desktop kernel: [ 6549.542087] dib0700: Unknown remote controller key : 1E 42
Feb 10 14:00:18 matthew-desktop kernel: [ 6549.617927] dib0700: Unknown remote controller key : 1E 42

```

There seems to be about 5 such messages every second, and the controller key listed at the end (1E 42 in this case) changes depending on the last button pressed on the remote. The same messages appear on dmesg. Obviously, as the code changes, the remote is being picked up by the kernel, but not being acted upon correctly. Is this normal, and does this mean something is working/not working? As stated above, I am still unable to get irrecord to show anything etc... I can't get it to work with or without lirc...

Any ideas?

---

