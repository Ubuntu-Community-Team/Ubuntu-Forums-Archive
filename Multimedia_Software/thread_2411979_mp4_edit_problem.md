---
title: "mp4 edit problem"
date: 2019-02-06
forum: Multimedia Software
---

### Post by ra7411 on 2019-02-06
I have a 13 hr mp4 that I want to delete about a 40 minute interval from, inside of it, not at the start or end.

I've used avidemux for things like this before, but when I try to open it with that program it shows a "Crash file" warning, then a "tinyPY:Exception", then it fails.

It does that even though the mp4 runs fine in vlc, smplayer, totem.

I know the exact time start-stop that I want to delete.
I don't have time to learn how to use the other vid editors I see recommened.

Any ideas?   Maybe a terminal program that uses the start-stop times to delete a section?

Thanks

---

### Post by TheFu on 2019-02-07
I'd use **mkvmerge**.
Example:
```
$ mkvmerge -o Output.mkv \
 --split parts:\
2:40-3:46,5:39-7:30,9:11-10:48,\
51:11- Input.mp4
```

This will result in Output-001.mkv ... Output-004.mkv files.  Those can quickly be merged with 
```
$ mkvmerge -o Output.mkv   Output-001.mkv + Output-002.mkv + Output-003.mkv + Output-004.mkv + 
```
Any subtitles, captions, auto tracks will be perfectly cut with this tool as well. Every other video tool that I found ignored multiple audio tracks and multiple captions.

Finer timestamps are possible (check the manpage), but video only breaks at keyframes which is determined by the video codec used.  You can trivially convert the container back to mp4, if you must.  mkvmerge does not perform any transcoding, so speed is like a file copy.

I stopped using avidemux when h.264 became a thing.  You might check out **vidcutter**. Think there is a snap or flatpak for it.  The PPA has been broken for a few months.  For simple cuts it might be sufficient.

---

### Post by ra7411 on 2019-02-09
You put me on the track to get it done.
I used Vidcutter to break out the bad section. It was easy to use. 
Apparently the latest version can merge clips (if they are compatible re. codecs, frame size, etc) by using "ADD" to put in clips to be merged, in the right order, then clicking "Save Media".

Vidcutter doesn't re-encode, so it runs relatively quickly and you shouldn't lose any resolution. 

Or,  to merge mp4 clips:  MP4Box -cat x1.mp4 -cat x2.mp4 tot.mp4    in a terminal.

Thanks

---

### Post by TheFu on 2019-02-09
Glad you found a solution.  If this is solved, please use the "Thread tools" button to let others know. This really helps out the community.

---

