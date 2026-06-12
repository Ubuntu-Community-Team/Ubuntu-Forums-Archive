---
title: "VLC no sound captured from stream but plays directly!"
date: 2014-01-01
forum: Multimedia Software
---

### Post by axe87 on 2014-01-01
I have a Hauppage Live-USB2 video grabber.

When using VLC I can play the stream back directly and get sound. However, if I try and save the stream to a file as a raw dump I don't get any sound when I play back the file.

I've also tried mencoder with similar results.

The fact that I get sound on playback makes me think this may be a configuration problem, but I have "keep original audio track" enabled in VLC.

I see from other posts others have used Live-USB2 successfully so hopefully I'm right...

---

### Post by axe87 on 2014-01-02
Possibly also related to this, with the Live-USB2 plugged in I am also having hibernate problems. When I hibernate the screen goes black but the PC doesn't fully hibernate. The only way to resume is to restart the PC.

On resuming I get a crash report with a Pulse error, as follows:

Error: command ['pacmd', 'list'] failed with exit code 1: No PulseAudio daemon running, or not running as session daemon.

So may be this is a problem between the Live-USB2 driver and pulse. Any pointers for how to debug further appreciated.

---

### Post by axe87 on 2014-01-12
Capturing the raw stream with audio now works with mencoder by specifying alsa, as per the following link

[http://linux.goeszen.com/digitising-vhs-tapes-on-linux.html](http://linux.goeszen.com/digitising-vhs-tapes-on-linux.html)

Therefore I'm assuming this was / is a pulse audio problem.

---

