---
title: "Watching TV while its recording"
date: 2010-10-18
forum: Multimedia Software
---

### Post by grock215 on 2010-10-18
I have a PVR-150 for recording TV shows.  

I can record shows using this command:
```
cat /dev/video0 > /mnt/raid/show.mpg
```

I can watch the show.mpg file while its recoding using VLC, Xine, Mplayer... pretty much any video player.

This is nice because i can pause, rewind, and fast-forward live TV, just like all the commercial DVRs out there.

The problem with this method is returning to "Live TV" mode.  When using a commercial DVR, when you are fast-forwarding and reach "Live TV", the player stops fast-forwarding and begins playing the live TV in real-time.  When doing the same thing with Xine or VLC, the player simply stops when you reach the EOF.

Is there a player that mimics this?  When it get close to the EOF, it switches from Fast-Forward to play?

I used to have MythTV, but it way too bloated for what I want to do. 

Any Ideas?

---

### Post by Jonie on 2010-10-18
Use tee to split the output. Just as simple as

```
cat /dev/video0 >( tee /mnt/raid/show.mpg | mplayer -)
```

Don't close mplayer first. Press Ctrl-c in terminal to terminate.

This way you'll be able to watch live tv. But EOF is EOF, file playing is just file playing, unless you're very close to EOF it will be almost "live".

---

### Post by grock215 on 2010-10-18
Thanks for the response

It looks like you solution separates the recording and "live tv" into 2 separate processes.

Say i start watching a show 10 minutes after it started.  I start from the beginning by watching the recording file (/mnt/raid/show.mpg).  During the commercials, i fast-forward (except for the shake-weight commercials... those are awesome).  After a few commercial breaks, i catch up to the live stream.  I want the player to recognize that it is approaching the EOF and disable fast-forwarding and continue playing in "Almost Live" TV mode.

---

### Post by grock215 on 2010-10-19
Any more ideas???

---

