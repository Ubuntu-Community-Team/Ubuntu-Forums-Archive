---
title: "Removing silence from m4a files using ffmpeg"
date: 2015-06-27
forum: Multimedia Software
---

### Post by tejasanilshah on 2015-06-27
[SIZE=2][FONT=arial]I have an audio file which has both leading and trailing silence and with the following specifics:

Codec: MPEG AAC Audio (mp4a) Channels: Stereo Sample rate: 44100 Hz Bitrate: 253 kbps
[B]
I want to remove the silences AND keep the quality intact.[/B]
```
ffmpeg -i 1.m4a -af silenceremove=1:0.5:0:1:0.5:0 2.m4a
``` 
This is supposed to remove both the leading and trailing silences. But for some reason it doesn't remove the trailing silence. This seems to be a recurring problem. Found the following on another forum.
[http://ffmpeg-users.933282.n4.nabble.com/How-to-delete-digital-silence-tp4667256p4667356.html](http://ffmpeg-users.933282.n4.nabble.com/How-to-delete-digital-silence-tp4667256p4667356.html)

Also, ffmpeg reduces the bitrate to 128kbps. This I could fix by adding **-ab 253k** and making the command:
```
ffmpeg -i 1.m4a -af silenceremove=1:0.5:0:1:0.5:0 -ab 253k 3.m4a 
```
Now the problem is that the trailing silence isn't removed and when I want to process a batch of files I can't use the same bitrate (like 253kbps ) for every file. I'd like to know how VBR could be used for this case.

I know I can use sox and use the silence and reverse features to trim the silences.
[http://digitalcardboard.com/blog/2009/08/25/the-sox-of-silence](http://digitalcardboard.com/blog/2009/08/25/the-sox-of-silence)  -- Example 3 in this post
But sox has the following problems:
[/FONT][/SIZE]
[LIST=1]
[*][SIZE=2][FONT=arial]It can't handle m4a files, I had to convert all files to mp3.[/FONT][/SIZE]
[*][SIZE=2][FONT=arial]When using the silence filter in sox it caps the bitrate at 128kbps.
```
sox 1.mp3 2.mp3 silence 1 0.5 1% reverse silence 1 0.5 1% reverse
```[/FONT][/SIZE]
[/LIST]

---

### Post by TheFu on 2015-06-28
Don't know anything about silence, but a few months ago I found that ffmpeg and avconv cut routines didn't do everything I needed (it didn't leave extra tracks) - don't really remember the details now.  But if I put the media into mkv containers, then used mkvmerge --split ... it would cut the at the desired places.
An example: 
$ mkvmerge -o $IN-new.mkv  --split parts:-43:05.0,43:09.0-1:26:16.0,1:26:20.0-2:09:10.0,2:09:13.0- $IN

If you just want to cut some beginning and end off - that would be the easiest way ... or you might find avidemux handy if you need a GUI.

---

### Post by FakeOutdoorsman on 2015-06-28
> I want to remove the silences AND keep the quality intact.
Try silencedetect filter. Then use -ss and -t using the info from the filter. You can stream copy this way by using -c copy. The disadvantage of silenceremove (other than it not working for you at the moment) is that filtering requires re-encoding.

---

### Post by mc4man on 2015-06-28
> **FakeOutdoorsman said:**
> Try silencedetect filter. Then use -ss and -t using the info from the filter. You can stream copy this way by using -c copy. The disadvantage of silenceremove (other than it not working for you at the moment) is that filtering requires re-encoding.

I've found the :d= parameter a little easier to understand & in a test file it finds silence both at the beginning & end vs the noise= parameter which only found at beginning (& had to raise the value from ex. given
.  The [ex. given for d=]("https://ffmpeg.org/ffmpeg-filters.html#Examples-13") though was a bit confusing (to me) as it doesn't show full & took a minute or two to realize it could use the -f null - to produce a 'report'

---

