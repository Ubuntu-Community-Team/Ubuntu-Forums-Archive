---
title: "How do I install a webcam on a server?"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by Mortuis on 2007-05-29
I have a box with ubuntu server installed, it has no xwindows, I get into it with ssh.  I plugged a  Intel Pro PC Camera into it. lsusb returns:

> $ lsusb
Bus 001 Device 003: ID 8086:0431 Intel Corp. Intel Pro Video PC Camera
Bus 001 Device 001: ID 0000:0000

So I know it sees it, but I didn't see anything that looked like it'd be the camera in /dev.   So I figured maybe I needed drivers,  I installed easyspca, but when I run it I get:
> $ sudo easyspca
This option is not available. Please see --help for all possible usages.

Trying it with the argument '--help' doesn't do anything, there are no man pages.  I'm not sure where to go from here.

What I'd like to do is have the camera running on the server, and link to it to get the streams or image captures or whatever the next step ends up being.  Am I wasting my time?  Should I hunt down a monitor for this thing and just install a GUI to run the thing?

---

