---
title: "Pulse?!: Applications don't show is sound settings, no sound"
date: 2011-10-26
forum: Multimedia Software
---

### Post by Gen2ly on 2011-10-26
This appears to be a problem with Pulse but I'm not entirely sure.  I've tried both Banshee and Ario (an MPD audio player) and I'm not getting sound in either.  For both, I'll push play but it's not getting recognized, the track slider isn't moving.  I've started both from terminal and this is the output I'm getting:

Banshee:

```
[Error 22:23:19.052] GStreamer resource error: NotFound
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
[Warn  22:23:20.171] Seem to be stuck loading file:///home/todd/Music/Enya/A%20Day%20Without%20Rain/06%20Flora's%20Secret.mp3, so re-trying
```

Ario:

```
    mpd decoder_thread: Unrecognized URI
```

I've watched in 'sound settings' under the Applications tab and neither will show up.  Sound with just ALSA appears to be working good though:

```
aplay /usr/share/sounds/alsa/Front_Center.wav
```

Any suggestions?

---

### Post by Gen2ly on 2011-11-18
Not sure just what did it, but some preference cause this behavior.  Ended up deleting all configurations in my Home folder, deleted everything else (i.e. not Documents, Music...) and got it working again.

---

