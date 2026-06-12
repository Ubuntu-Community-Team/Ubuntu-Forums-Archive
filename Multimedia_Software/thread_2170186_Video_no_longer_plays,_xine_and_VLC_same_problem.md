---
title: "Video no longer plays, xine and VLC: same problem"
date: 2013-08-25
forum: Multimedia Software
---

### Post by Keith_Beef on 2013-08-25
Until recently, I was able to play all my video files (AVI, h264, FLV, MPG, etc) through VLC. Xine stopped working a couple of years ago, and I had become more fond of VLC's features and interface, so that wasn't a problem.

But a few days ago, VLC stopped working, and I don't understand why. VLC media player 1.0.6 Goldeneye running on Ubuntu 10.04. I know, it's old, but I don't want to change on this laptop until I have got my main system up and running (it just came out of the storage warehouse after moving house).

I know that it happened sometime after I had installed gst-tools in order to fix a problem with Rhythmbox, so I removed gst-tools, but that has not fixed the problem.

Here's what happens now with VLC: the video display window appears, and stays black, there is audio (so the computer is not completely hung), but no response to keyboard or mouse. If I start VLC from a terminal window with a video file as an argument, I see a short message of VLC starting up and I see a message about the file being opened, no obvious problems or error messages, other than this that appears even if I start without pointing VLC at a file.
```
[0x8a6d390] main stream error: cannot pre fill buffer
```

Is there a logfile somewhere that might contain some useful info, or does anybody here have any ideas how I might fix this problem?

---

### Post by Merrattic on 2013-08-25
Do you get a different result if you try from terminal:

```
cvlc <file>
```

This launches vlc cli mode so cuts out the gui stuff....

---

### Post by Yellow Pasque on 2013-08-25
I would try different video output methods (in VLC's video options).

You can also reset to default configuration (you lose your preferences):
```
vlc --reset-config
```

As for logfile
```
vlc --file-logging
```

---

### Post by Keith_Beef on 2013-08-26
> **Temüjin said:**
> I would try different video output methods (in VLC's video options).

You can also reset to default configuration (you lose your preferences):
```
vlc --reset-config
```

As for logfile
```
vlc --file-logging
```

Thanks for the ideas, Temüjin.

I reset the config, unchecked acceleration, tried "GNU/Linux framebuffer", "XVideo", "X11"… no difference.

I started vlc with logging turned on, and:

```
 -- logger module started --
main: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
pulse: No. of Audio Channels: 2
-- logger module started --
main: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
pulse: No. of Audio Channels: 2
```

I'm going to keep trying with vlc, but suspect that the problem with xine has the same root cause.

---

### Post by SeijiSensei on 2013-08-26
Try installing mplayer and using "mplayer /path/to/video/file" to display it from the command line.  Mplayer will spit out a bunch of information about the container and codecs it found as well as any errors.  If that works, install smplayer to get a nice graphical interface for mplayer.

---

