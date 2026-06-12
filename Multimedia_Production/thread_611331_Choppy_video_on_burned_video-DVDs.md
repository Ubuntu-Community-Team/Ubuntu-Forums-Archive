---
title: "Choppy video on burned video-DVDs"
date: 2007-11-12
forum: Multimedia Production
---

### Post by twolaw on 2007-11-12
The subject line pretty much says it all.  Here's what I've been doing, following the steps from [this handy guide]("https://help.ubuntu.com/community/BackupDVD"):

[LIST]
[*]split video files into m2v/ac3 with the correct bitrate
[*]re-combined them according to all the latest advice on how to do that sort of thing
[*]put together an XML file with all the pertinent info
[*]"authored" the DVD (i.e., created the VIDEO_TS directory, etc. according to the XML file)
[*]made an ISO and burned it
[/LIST]
I've burned this ISO from the command-line and from Nautilus, and no matter the burn-speed or the brand of DVD that I use, the video comes out choppy on my standalone DVD player.  (The audio is fine, incidentally.)  I've also gone the "growisofs" route straight from the directory, bypassing the ISO.  No dice.

This DVD drive is just fine for writing data DVDs; I use it regularly to back up documents.  Video, not so much.  It's almost as if there's some sort of buffer that has to play catch-up a couple of times a second or something.  I've tried this with a DVD in which there are several smaller movie files, and now one with one big movie file, with the same stuttery result.

What am I missing here?

(running Ubuntu 7.10, by the way, but this stretches back to the previous version)

---

### Post by MepisReign on 2007-11-13
At what speed r u burning the discs?. I would suggests 4X. Try that burning speed as a test and let us know

Regards,

MepisReign

---

### Post by twolaw on 2007-11-13
I first tried burning them at "maximum possible" -- I think that clocks in at 6.2X or somesuch. Then I dialed it back to 2X, with the same result.

---

### Post by twolaw on 2007-11-15
No? Nothin'?

Nobody can help me out here?

---

### Post by yabbies on 2007-11-16
What's the video you are trying to burn?
are you converting AVI to burn to disc?
if so are the avi's in two files or just one?

---

### Post by twolaw on 2007-11-21
The video I'm trying to burn is a 3.0-GB MPG file, which is up to DVD standards for bitrate (as far as I know), and plays very smoothly in VLC. It's only when I try to burn a DVD that the end result is jittery and stuttery video (the audio is fine).

---

### Post by MepisReign on 2007-11-21
Did you try to play the resulting DVD on a standard DVD player instead of  the computer's DVD player?

---

### Post by twolaw on 2007-11-21
Yes, the choppiness results from playing the DVD on my stand-alone player. I haven't bothered trying it on my DVD drive in my computer.

---

### Post by wrathkeg on 2007-12-13
anyone know of a solution to this?  I am having the same problem (authored video DVDs which come out choppy on a standalone player, but preview fine via gxine) and can't for the life of me figure out how to solve it. 
TIA
WK

---

### Post by wrathkeg on 2007-12-15
To anyone interested, see my "solution" on this thread:

[http://ubuntuforums.org/showthread.php?t=639671&page=2](http://ubuntuforums.org/showthread.php?t=639671&page=2)

WK

---

