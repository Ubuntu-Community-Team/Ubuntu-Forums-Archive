---
title: "Command Line Video Editing"
date: 2017-10-27
forum: Multimedia Software
---

### Post by pneumatic2 on 2017-10-27
I'd like to be able to maintain a set of highlights from an ongoing video collection in a text file so that the latest iteration of the highlight video can be generated regularly.  To illustrate, I have a single football game video and I want to mark the beginning and end of each highlighted play in the text file and then run a command to generate a new video file using only those sections.  But then I add a new game video, demarcate the highlights and then regenerate a subsequent highlight video.

I know that Melt will do this but it is maddening to use because it requires that the beginning and end of the clips be set by frame number instead of seconds (the people selecting the highlights are not technical).  Is there a humane tool to do this or is it possible to script?

Thanks!

---

### Post by TheFu on 2017-10-27
**mkvmerge**

But it requires an mkv file as the output.  The input file can be pretty much anything - since mkv containers can hold pretty much any sort of video file with any sort of audio.

Another option is to store an EDL file with the video and use a player that recognizes edl instructions.

I use both methods for my sports highlights ... a non-trivial example:
```
$ mkvmerge -o Output-highlights.mkv   --split parts:\
1:01-1:47,4:30-5:01,8:57-9:45,15:49-16:30,17:15-17:49,\
19:33-20:16,23:17-23:50,27:01-27:34,33:50-34:29,35:14-35:49,\
36:21-36:57,39:44-40:19,42:25-43:07 \
Input-long-version.mkv
```

The .edl format is what KODI and mplayer use.  Frames or h:mm:ss.sss can be used.
[http://www.mplayerhq.hu/DOCS/HTML/en/edl.html](http://www.mplayerhq.hu/DOCS/HTML/en/edl.html) has more.  Multiple lines with 
```
{start} {end}  {action}
{start} {end}  {action}
{start} {end}  {action}
{start} {end}  {action}
```
define the EDL that mplayer, mplayer2, mpv, and about 10 others support. This would be a change at playback time only, leaving the entire file intact, should watching the full video be desired.
If you want a GUI, vidcutter has come a long way to supporting EDL files.

---

### Post by pneumatic2 on 2017-10-30
Thank you - this helps.

---

