---
title: "I need a quick, *simple* way of installing libx264 for screencasts!"
date: 2010-09-16
forum: Multimedia Software
---

### Post by youbuntu on 2010-09-16
Hello folks. After having borked and futzed around with various commands in terminal, in order to get libx264 installed for ffmpeg, I am starting to lose my cool. Please, could someone tell me **how** I can get h.264 encoding support in ffmpeg, for my screencasts (I'm using Lucid 10.04.1), without borking my whole system, which I have almost done, it would seem.

I am not into compiling and futzing with source code at this point, I JUST WANT IT TO WORK :D

Thanks guys

---

### Post by ron999 on 2010-09-16
Hi
The tutorial is here, it's only copy and paste:-[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095")

---

### Post by youbuntu on 2010-09-16
> **ron999 said:**
> Hi
The tutorial is here, it's only copy and paste:-[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095)

Thank you, but isn't 2008 a tad dated? :-/

---

### Post by FakeOutdoorsman on 2010-09-16
2008 was when the article was created.  It was last updated *1 Week Ago at 05:53 PM* as shown on the bottom of the post.

I kind of wish the 2008 date wasn't there because it sometimes confuses people.

**Update:** Don't forget to check out [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?t=1392026).  It's the definitive FFmpeg/libx264/screencasting guide for Linux.

---

### Post by youbuntu on 2010-09-16
> **FakeOutdoorsman said:**
> 2008 was when the article was created.  It was last updated *1 Week Ago at 05:53 PM* as shown on the bottom of the post.

I kind of wish the 2008 date wasn't there because it sometimes confuses people.

**Update:** Don't forget to check out [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?t=1392026).  It's the definitive FFmpeg/libx264/screencasting guide for Linux.

Hmmmm, I appreciate all the effort, but it's all a little fragmented... and I'm *sure* I said "simple" ... :-//

---

### Post by FakeOutdoorsman on 2010-09-16
What's more simple than copying and pasting?  You can still use FFmpeg from the repository, but you'll need to manually enable libx264 as shown here:
[url=http://ubuntuforums.org/showthread.php?t=1117283]
HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg[/url]
...and now try the screencasting guide I linked to previously.

Or perhaps **gtk-recordmydesktop** is more what you're looking for.  It has a GUI and can capture your screen but does not use *libx264*.

---

