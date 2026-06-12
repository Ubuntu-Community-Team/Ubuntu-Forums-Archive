---
title: "&quot;cannot open video device&quot; on Ubuntu Server Edition 11.04"
date: 2011-10-13
forum: Multimedia Software
---

### Post by Charence on 2011-10-13
I have a server running Ubuntu Server Edition 11.04 with a video capture card which outputs video on /dev/video0.

I installed gdm and vlc so that it is possible to see the video locally on the machine. However, when logging in remotely with X11 forwarding, the video cannot be opened.

Here is the output from vlc:

```

VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0xaaa120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
[0xbc5e40] signals interface error: signal 17 overriden (0x7f5fbe7b8450)
[0xbc5e40] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
[0xd93fc0] v4l2 demux error: cannot open video device '/dev/video0' (Permission denied)
[0xd93fc0] v4l2 demux error: cannot open video device '/dev/video0' (Permission denied)
[0xd41010] v4l2 access error: cannot open video device '/dev/video0' (Permission denied)
[0xd41010] v4l2 access error: cannot open video device '/dev/video0' (Permission denied)
[0x7f5fc0000bc0] main input error: open of `v4l2:///dev/video0' failed: (null)
X Error: BadValue (integer parameter out of range for operation) 2
  Extension:    144 (XInputExtension)
  Minor opcode: 46 ()
  Resource id:  0x4a002a5

```

I assume that the issue may be related to the X server somehow?

---

