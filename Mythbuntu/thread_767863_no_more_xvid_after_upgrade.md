---
title: "no more xvid after upgrade"
date: 2008-04-25
forum: Mythbuntu
---

### Post by kameleon25 on 2008-04-25
I upgraded to 8.04 today and got mostly everything working except my userjobs that use nuvexport-xvid. This is what I get when running it manually:

```
Choose a function, or episode(s) to remove:  c
Where would you like to export the files to? [/var/lib/mythtv/videos/converted] 
Enable Myth cutlist? [Yes] 
Enable noise reduction (slower, but better results)? [No] 
Enable deinterlacing? [Yes] 
Crop broadcast overscan border (0-5%) ? [0] 
Audio bitrate? [128] 
Variable bitrate video? [Yes] 
Multi-pass (slower, but better quality)? [Yes] 
Video bitrate? [2300] 
Default resolution based on requested dimensions.
Width? [720] 
Height? [544] 

Now encoding:  30-Minute Meals:  30 Minute Deep Freeze
Encode started:  Fri Apr 25 22:47:30 2008
First pass...
2008-04-25 22:47:31.647 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-25 22:47:31.697 Empty LocalHostName.
2008-04-25 22:47:31.788 New DB connection, total: 1
2008-04-25 22:47:31.886 Closing DB connection named 'DBManager0'
2008-04-25 22:47:31.894 New DB connection, total: 2
Waiting for mythtranscode to set up the fifos.
Waiting for mythtranscode to set up the fifos.
Starting ffmpeg.
processed:  0 of -10938 frames at 0 fps (~%, eta: unknown)  

ffmpeg had critical errors:

Unknown codec 'xvid'

Cleaning up temp files.
Cleaning up child processes.
```

I have the codecs selected in mythbuntu-control-center like I did before. Any ideas what could be going on?

---

### Post by Protoss on 2008-04-26
Looks like you 'upgraded' to the new ffmpeg while upgrading to Hardy, and the standard ffmpeg isn't compiled with support for the fancy video formats.

---

### Post by kameleon25 on 2008-04-26
Any ideas of how I may get the "non-standard" ffmpeg back? I have tried multiple howto's but none for hardy and none seem to work. Might have to try mencoder for now... ewww. lol

---

