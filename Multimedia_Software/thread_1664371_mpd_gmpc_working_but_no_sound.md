---
title: "mpd gmpc working but no sound"
date: 2011-01-10
forum: Multimedia Software
---

### Post by snapback77 on 2011-01-10
mpd gmpc working but no sound
I got mpd and gmpc to work (finally). When I open gmpc and connect to mpd it shows files, even shows file playing but no sound.
I installed Sonata; same thing. (but, Sonata connect is auto)

I open sound preferences, applications; I read: no application is currently playing or recording audio. (does that help?)

I Got two errors when openning gmpc:
1."could not grab the following multikeys: playpause FX86audioplay,next,previous,stop.
2. error code 52: ACK [52@0] {setvol} problem setting volume

When I open Sonata: it just starts playing without error message, just no sound.
I am almost there. But, not yet. Help please.
Operating System: Ubuntu 9.10 Karmic on HP AMD 64 computer.

---

### Post by snapback77 on 2011-01-10
Solved, I got the sound and oh is it wonderful.  How you ask?
It seems it was a pulse problem. Found this site.
[http://ubuntuforums.org/showthread.php?t=1298789](http://ubuntuforums.org/showthread.php?t=1298789)

It was closed but I followed the directions exactly and that was it.
When he says add these lines to the audio section he means just that.  Do not touch anything else just copy and paste at the end of the section, follow the last direction and that is it.  
Great sound.

My problem now is that my choice of music is limited to what was in my Music folder at the time of the mpd configuration. I followed the advice of MCDuck and made a symbolic link (whatever that is) based on his and that is where it ended but I got a chance to listen to it!  I have only about of 6 hours of music to enjoy but it is worth the trouble of installing the MPD and Sonata.  I hope someone with more knowledge can help me add more songs to my Sonata library.

For those who want MPD the following sites provided the answer for me with Ubuntu 9.10.  (and I have been trying for months!)
1.[http://crunchbanglinux.org/forums/topic/4686/howto-mpd/](http://crunchbanglinux.org/forums/topic/4686/howto-mpd/)
2.[http://ubuntuforums.org/archive/index.php/t-1141190.html](http://ubuntuforums.org/archive/index.php/t-1141190.html) (This is where I learned about symbolic links)
3.  [http://ubuntuforums.org/showthread.php?t=1298789](http://ubuntuforums.org/showthread.php?t=1298789) 
Follow all directions carefully and you will have MPD.
Add your favorite frontend, like Sonata and enjoy your files like you never have before.
Sincerely, Kenneth

---

