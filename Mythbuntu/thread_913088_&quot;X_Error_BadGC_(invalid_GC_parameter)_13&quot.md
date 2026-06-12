---
title: "&quot;X Error: BadGC (invalid GC parameter) 13&quot; in 0.21.0+fixes18228"
date: 2008-09-07
forum: Mythbuntu
---

### Post by rts on 2008-09-07
Since updating to 0.21.0+fixes18228-0ubuntu0+mythbuntu1 MythVideo will occasionally stop playing video (audio still plays; just a black screen) and in /var/log/mythtv/mythfrontend.log I get lots and lots of:

X Error: BadGC (invalid GC parameter) 13
  Major opcode:  60
  Minor opcode:  0
  Resource id:  0x2e00001

TV and all other display unaffected; only video files played by MythVideo hit this.

The only way to get video playback again is to shut down mythfrontend and re-start it.

Details on my setup are here: [http://ubuntuforums.org/showpost.php?p=5375949&postcount=127](http://ubuntuforums.org/showpost.php?p=5375949&postcount=127)


Any suggestions?

---

### Post by laga on 2008-09-07
Can you post the full log?

---

### Post by rts on 2008-09-07
One example:

2008-09-07 14:53:00.799 TV: Changing from None to WatchingPreRecorded
2008-09-07 14:53:00.800 Realtime priority would require SUID as root.
Initialize Yadif Deinterlacer. In-Pixformat = 1 Out-Pixformat=1
yadifdeint: size changed from 0 x 0 -> 1280 x 688
2008-09-07 14:53:00.909 OpenGLVideoSync()
2008-09-07 14:53:01.023 Video timing method: SGI OpenGL
X Error: BadGC (invalid GC parameter) 13
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x3200001
... (millions of these) ...
2008-09-07 14:53:20.225 TV: Changing from WatchingPreRecorded to None
2008-09-07 14:53:21.311 DPMS Reactivated.


Another example:


2008-09-07 17:39:21.412 TV: Attempting to change from None to WatchingPreRecorde
d
2008-09-07 17:39:21.589 AFD: Opened codec 0x8a434b0, id(MPEG2VIDEO) type(Video)
2008-09-07 17:39:21.589 AFD: codec MP2 has 2 channels
2008-09-07 17:39:21.589 AFD: Opened codec 0x831b530, id(MP2) type(Audio)
2008-09-07 17:39:21.594 Opening audio device 'default'. ch 2(2) sr 44100
2008-09-07 17:39:21.595 Opening ALSA audio device 'default'.
2008-09-07 17:39:21.631 mixer unable to find control Master 1
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode:  55
  Minor opcode:  0
  Resource id:  0x240339b
2008-09-07 17:39:21.960 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-09-07 17:39:21.978 OSD Theme Dimensions W: 640 H: 480
2008-09-07 17:39:22.287 TV: Changing from None to WatchingPreRecorded
Initialize Yadif Deinterlacer. In-Pixformat = 1 Out-Pixformat=1
yadifdeint: size changed from 0 x 0 -> 352 x 240
2008-09-07 17:39:22.291 Realtime priority would require SUID as root.
2008-09-07 17:39:22.393 OpenGLVideoSync()
2008-09-07 17:39:22.411 Video sync method can't support double framerate (refres
h rate too low for bob deint)
Initialize Yadif Deinterlacer. In-Pixformat = 1 Out-Pixformat=1
yadifdeint: size changed from 0 x 0 -> 352 x 240
2008-09-07 17:39:22.414 Video timing method: SGI OpenGL
X Error: BadGC (invalid GC parameter) 13
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x2e00001
... (2x of these) ...
X Error: BadGC (invalid GC parameter) 13
  Major opcode:  141
  Minor opcode:  19
  Resource id:  0x2e00001
... (millions of these) ...
2008-09-07 17:39:28.737 Marking recording as watched using offset 4 minutes
2008-09-07 17:39:28.737 TV: Attempting to change from WatchingPreRecorded to Non
e
X Error: BadGC (invalid GC parameter) 13
  Major opcode:  141
  Minor opcode:  19
  Resource id:  0x2e00001
X Error: BadGC (invalid GC parameter) 13
  Major opcode:  141
  Minor opcode:  19
  Resource id:  0x2e00001
X Error: BadGC (invalid GC parameter) 13
  Major opcode:  141
  Minor opcode:  19
  Resource id:  0x2e00001
2008-09-07 17:39:28.805 ~OpenGLVideoSync() -- begin
2008-09-07 17:39:28.805 ~OpenGLVideoSync() -- middle
2008-09-07 17:39:28.805 ~OpenGLVideoSync() -- end
X Error: BadGC (invalid GC parameter) 13
  Major opcode:  70
  Minor opcode:  0
  Resource id:  0x2e00001
X Error: BadGC (invalid GC parameter) 13
  Major opcode:  60
  Minor opcode:  0
  Resource id:  0x2e00001
2008-09-07 17:39:28.849 TV: Changing from WatchingPreRecorded to None
2008-09-07 17:39:39.310 TV: Attempting to change from None to WatchingLiveTV


Full log for the last ~12 hours attached.

---

### Post by Blairboy on 2008-09-08
I'm having the same issue.  Although, on my main machine (which runs compiz) it happens all the time.  On my other frontend (that just runs metacity) it never happens.  It's still absurd and I'd love to figure out why its screwy.

---

### Post by rts on 2008-09-08
> **Blairboy said:**
> I'm having the same issue.  Although, on my main machine (which runs compiz) it happens all the time.  On my other frontend (that just runs metacity) it never happens.  It's still absurd and I'd love to figure out why its screwy.

I don't have compiz on my myth machine, just xfce4/xfwm4.

---

### Post by rts on 2008-10-09
Problem persists with 0.21.0+fixes18528.

---

### Post by rts on 2008-12-26
Problem persists with 0.21.0+fixes18961-0ubuntu0+mythbuntu1, and after having upgraded  to Intrepid.

---

