---
title: "RecordItNow help wanted"
date: 2011-06-05
forum: Multimedia Software
---

### Post by Zeikcied on 2011-06-05
I posted this three weeks ago on Kubuntu Forums, and I've had no luck.  So I thought I'd try here.

I've been looking for desktop recording software, and I found this Qt-based program called RecordItNow.  I guess it's a front-end for recordmydesktop and has plugin support.  But I'm not getting a very good quality on the video.

I don't know if it's like this for all Linux desktop recording, but it doesn't do a good job at catching all of what's going on.  First I tried recording a window of FCEUX running in Wine, and then the native Linux version of FCEUX, and in both cases it only caught maybe a dozen frames of video through a single Super Mario Bros. level.  It recorded the audio just fine, and it seemed to be more reliable at catching video if a screen remained static for a couple seconds (like at the level/lives screen).  The default FPS was around 16, and I tried bumping it to 30, and didn't have any better results.  What's worse is that when these recordings were played back in VLC, the player would skip ahead several seconds as if no video information existed in the first half of the file.  Reencoding it via ffmpeg didn't change the quality, and also prevented me from recording the sound.

I tried recording a window of Klickety (so happy it now has a KDE4 version) and I cranked the FPS up to 90, and it recorded about one frame of action for every second.  So essentially 90 FPS is now equaling 1 FPS.

This is all very confusing.  I'm sure that the actual output file is running at 90 FPS, but the program is only really capturing one frame per second at that setting.  I tried recording Klickety again with Desktop Effects turned off, but that didn't do any good.  I do still have a number of programs running, so that might have something to do with it, I suppose.  But I'm not even using half my system's RAM.

Is there anything I can do to get better results?

---

