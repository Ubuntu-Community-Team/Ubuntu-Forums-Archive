---
title: "Streaming mp3s ?"
date: 2009-09-25
forum: Multimedia Software
---

### Post by dargaud on 2009-09-25
Hello all,
I'm looking for a way to stream mp3 files from my home ubuntu machine so I can listen to them at work (win or lin), or possibly from my Linux/Android phone. "*aptitude search stream cast*" gives tons of hits and I've tried some, but they are overly complicated (one I tried, which I can't remember the name [poc-streamer maybe], seems more oriented towards making a net radio than a single user server).

In particular I'd like to have the possibility to control the stream (at least a skip button on a random selection). A web interface maybe ?


A similar question: is there a movie streamer that can show my .avi collection and convert/stream on the fly so movies can be seen on a cell phone with only flash, mp4 or 3gp. Without having to run the whole list in ffmpeg before, obviously.

Thanks a bunch for the tips.

---

### Post by dargaud on 2009-10-18
I'll just post a partial solution I've found that works well from one ubuntu box to another: use sshfs to mount the remote and then play it in amarok as usual (without adding the files to the collection which would take forever). I'm still looking for a streaming solution that works with Windows and/or mobile...

---

### Post by Visko on 2009-10-26
I'd also like to see a solution to this.

Sshfs mounts take ages to load in any player.

---

