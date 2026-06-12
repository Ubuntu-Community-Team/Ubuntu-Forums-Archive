---
title: "Change aspect ratio during video playback?"
date: 2009-03-04
forum: Mythbuntu
---

### Post by Lido on 2009-03-04
When I'm watching a video (not a recording), sometimes the video is 4:3 but it shows up stretched to 16:9 on my screen. The video player I'm using is mplayer and I can't figure out if it's possible to change the aspect ratio during playback. Seems like a crucial feature so I'd hope that it's possible. I used to use the internal player but I'm now using mplayer with the nvidia vdpau because of excessive cpu usage otherwise. Thanks.

---

### Post by orethrius on 2009-03-04
If you're using gmplayer, it's right in the right-click menu, under "Aspect Ratio".

If you're using mplayer from the Terminal, throw the flag -aspect 4:3 in there so it looks something like this:
```
mplayer -aspect 4:3 somefile.avi
```

Hope this helps.  :)

---

### Post by Lido on 2009-03-07
I'm running it with MythTV. Right clicking doesn't bring up anything and when I tried to put "-aspect 4:3" into the playback setup for that file, the file wouldn't play anymore.

---

### Post by itlarson on 2009-03-07
Not sure if this is too easy, but here goes: 
You can change the aspect with the "w" key in the default setup.  It works with dvd and recording playback anyway.

---

### Post by oobe-feisty on 2009-03-07
nope that wont help he is using mplayer w is a binding for Internal player

> **itlarson said:**
> Not sure if this is too easy, but here goes: 
You can change the aspect with the "w" key in the default setup.  It works with dvd and recording playback anyway.

my suggestion is to start using Internal player or get used to editing the default player commands you can do this in setup / utilities / media settings / video settings / player settings 

then edit mplayer command to play using 16:9 or 4:3

e.g  

this is my default player in myth when im not using Internal 

mplayer -vf pp=fd -fs -zoom  -aspect 16:9 -quiet -vo gl2 %s


the part you are interested in is -aspect 


you can also create a unique player command for each video file in video manager which is a tad tedious and unecesary if the files you are playing are supported by Internal player

---

### Post by Lido on 2009-03-08
Thanks. Yeah, I'm using the Avenard repo 0.21 vdpau fixes so I thought I needed to use mplayer. I changed to "Internal" and it seems to be working fine now. Not sure I'm getting all the speedeup I can, but I prefer the internal player for a number of reasons (primarily aspect ratios seem to work automatically and the player remembers where you were if you stop watching).

---

