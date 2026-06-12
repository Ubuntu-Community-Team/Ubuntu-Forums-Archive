---
title: "Video formats"
date: 2011-10-10
forum: Multimedia Software
---

### Post by JoshuaMiller0 on 2011-10-10
I am running Ubuntu 10.04 on my laptop and I have recently been using gtk-recordMyDesktop.

I have been recording some Minecraft videos (recording as I am playing and speaking) and I have found recordMyDesktop automatically saves its files as ".ogv"s. I have not been able to find any way of saving these videos as anyhting different.

When I have tried uploading these videos onto [COLOR="blue"][[COLOR="Blue"]YouTube[/COLOR]](http://www.youtube.com)[/COLOR] I have spent 30-60 minutes uploading them before playing them and finding a completely blank green screen like [COLOR="Blue"][[COLOR="blue"]this[/COLOR]](http://www.youtube.com/watch?v=3UGvy70XFCU)[/COLOR].

So basically I am asking; How do I convert ".ogv"s into something that I can upload onto YouTube???


[CENTER]
**> **FakeOutdoorsman said:**
> **[COLOR="Navy"]recordMyDesktop creates an output that YouTube and some older versions of FFmpeg can not process. Some options:
[list]
[*][[COLOR="red"]re-encode the ogv using mencoder[/COLOR]](http://ubuntuforums.org/showthread.php?t=1501566) from the repository
[*]re-encode the ogv using a [[COLOR="red"]compiled ffmpeg[/COLOR]](http://ubuntuforums.org/showthread.php?t=786095)
[*]use [[COLOR="red"]ffmpeg to record your desktop[/COLOR]](http://ubuntuforums.org/showthread.php?t=1392026)
[*]use something else other than YouTube
[/list][/COLOR][/CENTER]

---

### Post by papibe on 2011-10-10
Take a look at [this]("http://www.omgubuntu.co.uk/2011/09/how-to-convert-ogv-avi-ubuntu").

Regards.

---

### Post by thatguruguy on 2011-10-10
Assuming you have a file named "minecraft1.ogv", you can try the following.  Open a terminal, and navigate to wherever you have the file stored.  Then type:

```
ffmpeg -i minecraft1.ogv minecraft1.mpg
```

---

### Post by FakeOutdoorsman on 2011-10-11
recordMyDesktop creates an output that YouTube and some older versions of FFmpeg can not process. Some options:
[list]
[*][re-encode the ogv using mencoder](http://ubuntuforums.org/showthread.php?t=1501566) from the repository
[*]re-encode the ogv using a [compiled ffmpeg](http://ubuntuforums.org/showthread.php?t=786095)
[*]use [ffmpeg to record your desktop](http://ubuntuforums.org/showthread.php?t=1392026)
[*]use something else other than YouTube
[/list]

---

### Post by JoshuaMiller0 on 2011-10-11
Thanks!

> **FakeOutdoorsman said:**
> 
1. [re-encode the ogv using mencoder](http://ubuntuforums.org/showthread.php?t=1501566) from the repository


That is what the first person suggested and I am currently using that.

> **FakeOutdoorsman said:**
> 
3. use [ffmpeg to record your desktop](http://ubuntuforums.org/showthread.php?t=1392026)


I will give that a go!

Now to mark the thread as solved :)

---

