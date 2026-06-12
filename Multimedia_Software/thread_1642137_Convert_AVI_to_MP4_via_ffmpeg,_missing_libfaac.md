---
title: "Convert AVI to MP4 via ffmpeg, missing libfaac"
date: 2010-12-10
forum: Multimedia Software
---

### Post by Andreas Riedel on 2010-12-10
Hello Forum.

I tried to convert an AVI-video to a MP4-video for my ipod. Therefore I used ffmpeg as I can read in the FAQ
```
ffmpeg -i in.avi -acodec libfaac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 -flags +mv4 -trellis 2 -cmp 2 -subcmp 2 -s 320x180 -metadata title=X out.mp4
```The problem is, that the given encoder libfaac is not installed and I can't get it through the pack-adminstration
```
Unknown encoder 'libfaac'
```What I can get there is libfaac0. But put this in command-line
```
ffmpeg -i in.avi -acodec libfaac0 -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 -flags +mv4 -trellis 2 -cmp 2 -subcmp 2 -s 320x180 -metadata title=X out.mp4
```ended up with
```
Unknown encoder 'libfaac0'
```even if it is installed.

```
apt-cache show libfaac0
```return some result.

What going wrong.

TIA
  Andreas

---

### Post by FakeOutdoorsman on 2010-12-10
See Option A or Option C in:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

If you decide to compile FFmpeg see my example iPod command here (I haven't actually tested it because I don't own an iPod):
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Handbrake might be worth investigating if you don't like command-line although I'm not familiar with it.

---

### Post by Andreas Riedel on 2010-12-10
Thanks for your quick answer. I will try this at weekend.

Greeting to Alaska.

Andreas

---

### Post by Andreas Riedel on 2010-12-10
Hi FakeOutdoorsman.

I tried your option C, because it seams to the solution with the fewest impact.

It works great. Good job.

Many, many thanks.

Greeting from Germany
Andreas

---

### Post by marjonz on 2012-09-06
> **FakeOutdoorsman said:**
> See Option A or Option C in:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg]("http://ubuntuforums.org/showthread.php?t=1117283")

If you decide to compile FFmpeg see my example iPod command here (I haven't actually tested it because I don't own an iPod):
[HOWTO: Install and use the latest FFmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095")

Handbrake might be worth investigating if you don't like command-line although I'm not familiar with it.

Hi! beginner here. Trying to open the link but it says I am less than 50 posts or something and won't allow me. Is there some other way to view the link? Thanks.

---

### Post by FakeOutdoorsman on 2012-09-06
I removed the link because a recent forum policy change required me to request editing privileges from a forum moderator each time I wanted to edit/update the page. Also, Ubuntu no longer uses FFmpeg and I do not use the fork that they (the sole maintainer) decided to use instead. I did not want the guide to moulder and present outdated or wrong information and thought it better to remove it.

The link basically said to install the **libavcodec-extra-5*** package to enable some additional encoders in "ffmpeg" from the repository. If you get **libavcodec-extra-5*** from Medibuntu then it will supply at least one additional encoder (libfaac, an AAC encoder). However, this may be outdated information because I no longer keep up with the repository.

---

### Post by ElecTrOXP on 2012-10-23
> **FakeOutdoorsman said:**
> See Option A or Option C in:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

If you decide to compile FFmpeg see my example iPod command here (I haven't actually tested it because I don't own an iPod):
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Handbrake might be worth investigating if you don't like command-line although I'm not familiar with it.

I do not have permission to access since I just registered anyway if viewing the option C as your indicated so I can fix my faac on my server. 

Thank you in advance.

---

### Post by FakeOutdoorsman on 2012-10-23
> **ElecTrOXP said:**
> I do not have permission to access since I just registered anyway if viewing the option C as your indicated so I can fix my faac on my server.

I requested that guide to be deleted, which apparently means that a moderator moves it to "The Jail" which gives the permission message to most users.

Option C basically said to install the **libavcodec-extra-53** package from Medibuntu to enable the AAC encoder called libfaac, but since I do not use libav I am not sure if this is accurate information anymore or what other AAC encoders are available. See [Who can tell me the difference and relation between ffmpeg, libav, and avconv](http://stackoverflow.com/a/9477756/1109017) for clarification on that topic.

---

