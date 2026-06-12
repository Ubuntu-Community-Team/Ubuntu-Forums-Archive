---
title: "Bluetooth headphones do not appear."
date: 2009-12-22
forum: Multimedia Software
---

### Post by walkeraj on 2009-12-22
I recently upgraded my workstation at the office to 9.10 64-bit, and thought I'd take advantage of the supposedly-better bluetooth support and use my motorola s805 bluetooth headphones.  I put my headphones in pairing mode, and they paired no problem.  When I turn them on, the system immediately picks them up.  This is the good.

The bad is that they do not appear anywhere in the sound preferences as they are supposed to.  I cannot select them as an output, and they just sit there, unworking.

When I first turn them on and they connect, if I then right click on the sound icon in the notification area and go to "Sound Preferences", I receive a dialog that says "Waiting for the sound system to respond".  This sits there for approximately 45-60 seconds, and then the sound preferences dialog comes up, but there are no extra entries for my headphones as there should be.  Output still only lists "Internal Audio Analog Stereo"

Briefly, once, it displayed my headphones there, but they were listed as "mono" and selecting them did nothing.  I suspect this is because it was listed as being in headset mode, rather than high quality stereo mode.

Syslog entries reveal some kind of problem:

Powering on the headset:
```
bluetoothd[1225]: link_key_request (sba=00:11:67:D7:F4:42, dba=00:1A:0E:9A:CC:30)
bluetoothd[1225]: Can't open input device: No such file or directory (2)
bluetoothd[1225]: AVRCP: failed to init uinput for 00:1A:0E:9A:CC:30
```

Right click on speaker -> sound preferences:
```
bluetoothd[1225]: HUP or ERR on socket
```

Any ideas?

---

### Post by walkeraj on 2009-12-22
Tried running

```
# modprobe uinput
```

which got ridd of the AVRCP error, so when I power it on, syslog now shows:
```
bluetoothd[1225]: link_key_request (sba=00:11:67:D7:F4:42, dba=00:1A:0E:9A:CC:30)
kernel: [345638.428512] input: 00:1A:0E:9A:CC:30 as /devices/virtual/input/input9

```

However, going to the sound preferences menu still shows:

```
bluetoothd[1225]: HUP or ERR on socket
```

---

### Post by walkeraj on 2009-12-30
Bump

---

