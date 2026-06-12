---
title: "Creative Webcam Live! Pro not working?"
date: 2007-09-24
forum: Multimedia &amp; Video
---

### Post by onlineapps on 2007-09-24
I followed all the threads, enabled v4l, modprobed videodev and gspca, all without errors.  But Camorama produces this error:

Could not connect to video device (/dev/video0).  Please check connection.

Here's the terminal output:

andrew@ANDREWSCOMPUTER:~$ camorama
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  150
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  150
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found

FYI, there's a green light on the cam that goes on when plugged into Windows (where it works).  That light is not on.

---

### Post by onlineapps on 2007-09-24
Oh yeah, I'm on Kubuntu Feisty

---

### Post by onlineapps on 2007-11-07
Now I'm on a clean Gutsy install.  The green light is on, and there are no esd errors, but Camorama still can't connect to /dev/video0 (it doesn't exist as far as Konqueror is concerned).  /dev/video doesn't exist either.

---

