---
title: "Video playback freezes when playing sound over network"
date: 2011-01-02
forum: Multimedia Software
---

### Post by zzarko on 2011-01-02
I have three computers in my home network and I wanted to play all audio on one computer. On the audio-server machine, pulseaudio is configured to accept connections from other computers. On the client computers I did something like this:
```
pacmd load-module module-tunnel-sink server=192.168.2.100
```and I can choose this sink for playback. And it all works just fine if I play ONLY AUDIO (Rhythmbox ,mpd, DeadBeef, Audacious,...).

The problem begins if I try to play video file: the sound goes to sound server, but video on client is frozen (it plays through approximately first 1-5 frames and then stops). This is happening with ALL video, and ALL players I tried (Totem, MPlayer, SMPlayer, VLC, Youtube with Firefox/Chrome), no matter what output I choose (xv, gl, ...). I can move video slider to any position in all players, and the sound changes accordingly, but the video remains frozen. If I move other window over the player, video frame is not corrupted. Same thing is happening on both clients (one laptop, one desktop).  If I change pulseaudio sink to local soundcard (Internal Audio), everything works fine.

All three computers are running fully updated Ubuntu 10.10. There are no errors in logs that I colud find regarding pulseaudio/X/players, no error output when I start players from command line, there is no high CPU usage during video playback, and I don't even know where to start...

And now the big question: did anybody had probelm like this? Does someone maybe have a solution for this, or maybe just a hint where to start looking?

---

### Post by Tito1337 on 2011-06-04
I have exactly the same problem, this is very annoying.

---

### Post by SliMM322 on 2011-12-17
I have the same problem with my Arch systems. Seems to be a PulseAudio thing... Also, the slider progress doesn't seem to be working either when playing stuff over the network.

---

### Post by Miggles on 2012-03-15
Did you ever find a solution for this? I was having it back in November and I'm still getting it now.

---

### Post by load.runner on 2012-11-20
Does this thing even work? (video playback using pulseaudio over network)
In my experience, it never worked properly.
Always laggy and unstable.
It's basically usable only for audio.

---

### Post by wildmanne39 on 2012-11-20
Old thread with no answers so it has been closed.

---

