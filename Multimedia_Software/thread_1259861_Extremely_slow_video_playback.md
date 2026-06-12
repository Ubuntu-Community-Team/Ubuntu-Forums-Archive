---
title: "Extremely slow video playback"
date: 2009-09-06
forum: Multimedia Software
---

### Post by mahasmb on 2009-09-06
I have extremely low video playback. Watching nearly any video in any format is annoying because it's slow and skippy. This is a problem I've been having for months and haven't been able to find a fix for it.

.mkv files seem to be the worse, but I still have problems with any other format. Because of this, I've downloaded a number of media players. They ALL give me problems some time or another:

[LIST]
[*]MPlayer (Gstreamer)
[*]MPlayer (Xine)
[*]VLC 
[*]SMPlayer
[*]Gnome MPlayer
[/LIST]

Can someone please help? Nothing I've tried works.

---

### Post by mahasmb on 2009-11-17
I've bought a new motherboard and CPU, and since then my videos play perfectly.

I guess my CPU was just old ... because I noticed that while playing videos the CPU was near or at 100% usage.

---

### Post by motonnerd on 2009-12-21
I have a similar problem...

VLC and everything else play music and videos great until some random time when it starts skipping and the assorted junk which comes with it.  I had the system monitor open and my cpu wasn't running too had, nor was RAM being eaten up -- I'm on a 2.5GHz single-core and 512MB of RAM but it would still do this a seemingly random intervals.  Windows works fine, of course, and Puppy Linux with its' player too.  I even had Puppy on a very old laptop (650Mhz processor) and it played...

I tried disabling starting GNOME and KDE services at bootup, but that hasn't helped.  I wonder if it's an issue with the hard drive -- I should see if I can improve caching in VLC, that's the idea that's made the most sense so far.... you'd think that this would be something already covered though...

---

### Post by llawwehttam on 2009-12-21
I heard a few people had this problem after upgrading. They downgraded FFMPEG and that seems to work for them.

---

