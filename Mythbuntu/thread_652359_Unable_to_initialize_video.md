---
title: "Unable to initialize video"
date: 2007-12-28
forum: Mythbuntu
---

### Post by RobotAlligator on 2007-12-28
This error is extremely weird for me.  I have a Hauppauage PVR-350 and I actually had the watch tv function working on it, but I couldnt get it to display my TV.  I got fed up and left it for a month or so and didn't touch it.  Now its display is working on a new projector, but I go to watch TV on it and it gives me Unable to initialize video.  When I scan for channels, it finds all the channels though.  Everything seems set up right.

The only thing I can think of that I have changed is i tried to get the tv-out on the hauppauage card working, but I just gave up until I got a projector.  Or it doesn't like the resolution(640x480-unlikely)  Any insight on this would be appreciated.

Currently downloading updates for mythbuntu, but I don't think it will fix it. No reason for a random error that updates will fix..

One thing I noticed earlier is it said unable to access 127.0.0.1:(6478?).  I'm not sure if this has anything to do with it, but again anything would be nice.

---

### Post by RobotAlligator on 2007-12-28
fixed, i just had to turn off "use pvr350 as output"

---

### Post by superm1 on 2007-12-29
The updates for mythtv in gutsy-updates address this particular issue related to initializing video.

---

### Post by rondude on 2009-05-31
Go to  Setup - TVSettings - Playback Screen 9 of 9 UNCHECK the box ---   use the PVR-350's TV/out MPEG decoder  I also found it helpful to  Go to Setup - TVSettings - Playback Screen 3 of 9 CHANGE the box --- Current Video Playback Profile (to) Slim

---

