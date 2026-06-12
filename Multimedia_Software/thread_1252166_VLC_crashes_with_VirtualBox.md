---
title: "VLC crashes with VirtualBox"
date: 2009-08-28
forum: Multimedia Software
---

### Post by shiva.n on 2009-08-28
Wierd. On Jaunty, when I am using VirtualBox 3.0.4, or after I use it, VLC 1.0.1 will crash if I try to play any video.

Here is the error I get

[COLOR=Navy]shiva@rastafarI:~/Downloads$ vlc
VLC media player 1.0.1 Goldeneye
[0x8d0c3e8] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode: 2 (X_ChangeWindowAttributes)
  Resource id:  0x2e0004e[/COLOR]

After I try to open any video file
[COLOR=Navy]
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 132.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  101
  Current serial number in output stream:  102[/COLOR]

Anyone else see this, or have any clues? Glad I didnt remove MoviePlayer...

---

### Post by agent-s on 2009-09-07
I'm having the same problem, but even if I haven't used Virtualbox yet it just won't start.  Interestingly enough I get the X11 BadMatch error if I try to play Enemy Territory Return to Castle Wolfenstein.

```
~ $ vlc
VLC media player 1.0.1 Goldeneye
[0x983f140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x9e175f0] oss audio output error: cannot open audio device (/dev/dsp1)
[0x9e175f0] main audio output error: couldn't find a filter for the conversion
[0x9e175f0] main audio output error: couldn't create audio output pipeline
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 132.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  106
  Current serial number in output stream:  107

```

edit:
Switching video output to OpenGL seems to fix it.

---

### Post by agent-s on 2009-09-07
Ok, so I just looked at this page:

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/281743](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/281743)

and right now I'm using the workaround of using Xvideo (OpenGL does not play nice with rendering of the desktop) and not embed the video in the interface.

---

