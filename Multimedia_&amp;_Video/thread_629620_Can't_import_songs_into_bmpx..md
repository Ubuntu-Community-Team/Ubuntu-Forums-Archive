---
title: "Can't import songs into bmpx."
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by qiemem on 2007-12-02
I recently switched to fluxbuntu and wanted a music player with library capabilities, so I tried bmpx.  Upon running "beep-media-player-2", I receive the following error message (popup, not in terminal):
> 
BMP/DBus Error

BMP can not be started trough DBus activation.
The following error occured trying to start up BMP:

'Failed to connect to socket /tmp/dbus-2qQuoPiOiW: Connection refused'

DBus might not be running at all or have even crashed, please consult further help with this problem from DBus or BMP support.


So I run "dbus-launch beep-media-player-2" and it works fine.  But when I try to import music, for every file (all mp3s) I get a message saying "No Metadata for this File: Unable to determine File Type".  When trying to import individual files, they are simply greyed out and I am unable to select them.  When I try to stream any music, either from Jamendo or from radio, it seems like it starts to play but no sound comes out.

Anyone know whats going on?  Or anyone know of a lightweight (no gnome/kde/xfce dependencies) music player with a library browser?

Thanks!

---

