---
title: "FFMPEG  with libfaac - says libfaac is unknown encoder"
date: 2010-03-04
forum: Multimedia Software
---

### Post by play_ on 2010-03-04
Hi.

I am trying to convert some mp3's into m4r format.

I got to step 4 on this page:
[http://blog.forret.com/tag/ffmpeg/]("http://blog.forret.com/tag/ffmpeg/") and do as the guy does:

```
ffmpeg.exe -i ringtone.mp3 -ac 1 -ab 128000 -f mp4 -acodec libfaac -y ringtone.m4r
```

minus the .exe part. here's what i use:

```
ffmpeg -i test.mp3 -ac 1 -ab 128000 -f mp4 -acodec libfaac -y test.m4r
```

but ffmpeg throws me this error:
```
Unknown encoder 'libfaac'
```

even though i have libfaac0 and libfaac-dev installed

any thoughts?

---

### Post by andrew.46 on 2010-03-05
Hi play,

> **play_ said:**
> any thoughts?

aac encoding has become a problem with Karmic, I presume that is what you are using? Have a look here for the solution:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

All the best,

Andrew

---

### Post by play_ on 2010-03-05
thank you!

---

### Post by stoian on 2013-05-02
that thread won't show today...

---

### Post by stoian on 2013-05-02
and still... wtf? need 25 posts to READ a thread?

---

### Post by FakeOutdoorsman on 2013-05-02
This is an old thread, and that thread you are referring to has since been "deleted"* because:

[list=1]
[*]Forum rules did not allow me to update it without contacting a forum moderator
[*][Ubuntu no longer uses FFmpeg](http://stackoverflow.com/a/9477756/1109017)
[/list]
I did not want to deal with the forum bureaucracy each time I wanted to edit my own post, and I did not want users to follow a moldering, outdated guide.
[size=1]
* Unfortunately, instead of being deleted, the post was moved to "The Jail" and is still available at least to me and the forum overlords.[/size]

---

