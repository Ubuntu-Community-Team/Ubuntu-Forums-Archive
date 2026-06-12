---
title: "Karmic - No Audio in Media Players"
date: 2009-12-10
forum: Multimedia Software
---

### Post by ashlayne on 2009-12-10
I can't get either Rhythmbox or Banshee to play any audio. When I try to play, the counter and progress bar both move as if a song is playing, but no sound comes out of my speakers. These are audio files I tested on my fiance's computer, then transferred to my own. I have audio from other applications, such as Firefox (yay Youtube!!), Pidgin, and XChat... but no media players. (I even tried to download and install Amarok on the off chance it would work, but no.)

Upon loading Rhythmbox through terminal:

```
blank@blank:~$ rhythmbox

** (rhythmbox:26331): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:26331): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

** (rhythmbox-metadata:26354): WARNING **: Side info bad: block_type == 0 in split block.
```

Upon loading Banshee through terminal:

```
blank@blank:~$ banshee
[Info  15:33:38.612] Running Banshee 1.5.1: [Ubuntu karmic (development branch) (linux-gnu, i486) @ 2009-10-19 14:46:07 UTC]
[Info  15:33:47.448] All services are started 7.149637s
[Info  15:33:51.325] nereid Client Started
```

So it appears that Banshee loads without errors, but Rhythmbox doesn't. I have uninstalled, purged, and reinstalled both apps, I have gstreamer plugins (good/bad/ugly) installed... I don't know what else is going on!!

Help?

---

### Post by spiderbatdad on 2009-12-10
I can tell you those errors have nothing to do with lack of sound or rhythmbox's ability to play the files. You could try running in debug mode.
```
rhythmbox -d path/to/file.mp3
``` It is strange that you have sound playing other files type like flash.

---

### Post by ashlayne on 2009-12-11
(Link to Pastebin as the forum wouldn't allow me to put that much text in a post. >.<) [http://paste.ubuntu.com/339085/](http://paste.ubuntu.com/339085/)

That's what I got. I scanned over it and couldn't find any errors, but maybe I'm missing something...?

---

### Post by ashlayne on 2009-12-11
How strange. I rebooted my computer after installing some updates that had absolutely nothing to do with Rhythmbox... and Rhythmbox is now using my speakers again! o_O And yes, I had rebooted my computer several times in the course of trying to fix this myself with no luck. Weird...

Also, thank you, spiderbatdad. Still wonder what caused it to begin with...

---

