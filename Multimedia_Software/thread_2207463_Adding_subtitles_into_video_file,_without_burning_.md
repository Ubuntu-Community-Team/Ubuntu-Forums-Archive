---
title: "Adding subtitles into video file, without burning it on the frames."
date: 2014-02-23
forum: Multimedia Software
---

### Post by xp15 on 2014-02-23
Sometime when you download a movie, like with utorrent/Transmission (Torrent), it will play it with subtitles and you can choose another one like another language, or disable them. The subtitles are not in a seperated file, they are like inside the video.

How can I do it linux? Addind subtitles to a video, without changing the video itself, but still making them a one file.

Thanks!

---

### Post by TheFu on 2014-02-23
```
mkvmerge -o output.mkv input-video.file input.srt
```

Input-video.file can be pretty much any video file type you like - mp2, mp4, h.264, ogv, flv, mpg, ... with pretty much any sort of audio like - ac3, aac, mp3, mp2, dts, flac, ogg ... there must be 20 other formats too. Of course, having audio and video that is supported by the player is important.

MKV is a fantastic container format, provided the players can handled it.

---

### Post by andrew.46 on 2014-02-23
Perhaps mp4box (a part of gpac) might meet your needs?

---

### Post by xp15 on 2014-02-24
Thank you both! I think the command will be better as It's very simple  and GUI is slmost not needed, but if it wont work I wil try the mp4box  (:

> **TheFu said:**
> ```
mkvmerge -o output.mkv input-video.file input.srt
```

Input-video.file can be pretty much any video file type you like - mp2, mp4, h.264, ogv, flv, mpg, ... with pretty much any sort of audio like - ac3, aac, mp3, mp2, dts, flac, ogg ... there must be 20 other formats too. Of course, having audio and video that is supported by the player is important.

MKV is a fantastic container format, provided the players can handled it.

Can you just tell me what every word in the command do? like -o ? Well I think I got the rest ^^
1) the program
2) ?
3) new file I want (Video)
4) The file I use (Video)
5) The subs.

Are there more options like giving a name to the subs? like "English" "Hebrew"

Thanks!

---

### Post by TheFu on 2014-02-24
> **xp15 said:**
> Thank you both! I think the command will be better as It's very simple  and GUI is slmost not needed, but if it wont work I wil try the mp4box  (:
Can you just tell me what every word in the command do? like -o ? Well I think I got the rest ^^
1) the program
2) ?
3) new file I want (Video)
4) The file I use (Video)
5) The subs.

Are there more options like giving a name to the subs? like "English" "Hebrew"

Thanks!

I hope you didn't wait for a response. Sorry that I didn't use the --long-options-method. Didn't feel like typing.  All that specific data is in the manpage ... just like for every other command on the system.  Including the way to spell out which language any subtitle or audio track might be.
```
man mkvmerge
```
to see it.

I'm trying to teach you to fish, not just hand you 1 fish for today.

---

### Post by xp15 on 2014-02-25
OK, Ill try it (:

---

