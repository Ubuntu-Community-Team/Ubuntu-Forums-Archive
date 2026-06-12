---
title: "Mplayer option &quot;-stop-xscreensaver&quot; not working?"
date: 2009-02-17
forum: Multimedia Software
---

### Post by nicoloks on 2009-02-17
I'm using Mplayer as my default player in MythTV, however when watching movies the screen keeps on going dark and I have to push a key to restore it. I assume this was the screen saver, so I added this to my Mplayer command line;

-stop-xscreensaver 

The full command looks like this;

mplayer -vc ffvc1vdpau,ffh264vdpau,ffwmvvdpau,ffmpeg12vdpau -vo vdpau -ac hwdts,hwac3 -ao alsa:device=spdif -fs -zoom -quiet -stop-xscreensaver %S

This doesn't seem to have worked though as the screen is still going dark. Any ideas what is causing it?

P.S 

I should add that I am using a VDPAU enabled version of Mplayer that I compiled, and that using the default MythTV command line for  Mplayer seemed to work without an issue.

---

### Post by mikewu on 2009-02-17
Supposedly this doesn't work because xscreensaver doesn't support XSuspendScreensaver or XResetScreensaver.

One way to get around it is to put
```
heartbeat-cmd="xscreensaver-command -deactivate"
``` in your ~/.mplayer/config file

It should simulate user activity every 30 seconds.

Hopeful this works. Good luck!

---

