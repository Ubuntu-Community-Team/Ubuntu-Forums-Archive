---
title: "mencoder -&gt; pipe to mplayer"
date: 2016-06-16
forum: Multimedia Software
---

### Post by peter253 on 2016-06-16
[COLOR=#000000][FONT=Verdana]Hello,[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I would like to encode with [/FONT][/COLOR][mencoder]("http://www.videohelp.com/software/MPlayer")[COLOR=#000000][FONT=Verdana] stream from my /dev/video0 camera and[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]send it directly to [/FONT][/COLOR][mplayer]("http://www.videohelp.com/software/MPlayer")[COLOR=#000000][FONT=Verdana] for immediate watching (or to any[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]other player => this is why I need to encode it with mencoder first)[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I tried something like this:[/FONT][/COLOR]
[HTML]$ mkfifo output.avi
$ mencoder tv:// -tv driver=v4l2:width=720:height=576:device=/dev/video0
-ovc lavc -lavcopts vcodec=mpeg4:vbitrate=900 -o output.avi -v -nosound
BUT this does not work
$ mplayer output.avi (this is how I wanted to play it)[/HTML]

[COLOR=#000000][FONT=Verdana]When I save stream to normal file first, mencoder works ok - but file[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]is getting bigger and bigger, so this is not way to go for me (I need[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]to save it to something like fifo and then play it in realtime).[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Any idea please how to put strem into fifo or pipe and then play it?[/FONT][/COLOR]

---

### Post by gordintoronto on 2016-06-17
If you just want to watch video from the camera, use cheese.

---

### Post by mc4man on 2016-06-17
named pipes (fifo) should be done in 2 terminals at same dir. prompt

---

### Post by TheFu on 2016-06-18
Optimal transcode settings for files and streaming are different.  Streaming needs chunks put together since jumping around the file and pre-loading audio/subtitles/captions aren't known at the start.  Which is more important to you?  Optimize for that.

I haven't tried this, but perhaps '**tee**' can be useful?  This will send output both to a file and stdout.

I have used screen capture tools to save recordings (simpleScreenRecorder or OBS) then used other players to playback the output file from disk. Don't do it too often, but it has worked.

---

