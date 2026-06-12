---
title: "ffmpeg - convert .ogv to .avi"
date: 2010-11-04
forum: Multimedia Software
---

### Post by Segofam on 2010-11-04
Recently I installed gtk-recordMyDesktop, so that I could record my movements and send the Media File to my dad, so he could learn how to use Ubuntu too :) [plug]

My problem is converting the .ogv file to .avi - I have tried ffmpeg but it loses quality dramatically.

Can anyone tell me how to get better quality video out of ffmpeg, or let me know another way to convert the .ogv file to .avi or something that is widely used?

Sincerely,

Scott

---

### Post by ron999 on 2010-11-04
Hi
If you have an up-to-date version of ffmpeg then this command is good for YouTube:-
```
ffmpeg -i out.ogv -vcodec libx264 -vpre medium -crf 24 -threads 0 -acodec copy foo.mkv
```

And this command is OK, but might not work for YouTube:-
```
ffmpeg -i out.ogv -vcodec libx264 -vpre medium -crf 24 -threads 0 -acodec libfaac foo.mp4
```

If you need to update your ffmpeg there's a smart tutorial here:-
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095&highlight=Upgrading+FFmpeg+x264]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095&highlight=Upgrading+FFmpeg+x264")
There are also some example commands.

If you want to use mencoder instead to make an avi file there's a tutorial here:-
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1501566&highlight=upload+youtube]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1501566&highlight=upload+youtube")

:)

---

### Post by Segofam on 2010-11-09
Thanks ron999,
I will give it a go soon.
Kind regards,
Scott

---

### Post by Segofam on 2010-11-09
> **ron999 said:**
> Hi
  ```
ffmpeg -i out.ogv -vcodec libx264 -vpre medium -crf 24 -threads 0 -acodec copy foo.mkv
```And this command is OK, but might not work for YouTube:-
```
ffmpeg -i out.ogv -vcodec libx264 -vpre medium -crf 24 -threads 0 -acodec libfaac foo.mp4
```
:)

Hey ron999,
This worked really well for me!
Thanks,
Sincerely,
Scott

---

