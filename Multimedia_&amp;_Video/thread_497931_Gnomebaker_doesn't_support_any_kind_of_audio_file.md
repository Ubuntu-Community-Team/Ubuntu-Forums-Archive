---
title: "Gnomebaker doesn't support any kind of audio file"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by PatrickMay16 on 2007-07-10
Hello there. When I try to add a wav file to gnomebaker, to burn an audio cd, it says "a plugin to handle a file of type audio/x-wav is not installed.". It doesn't work with mp3 file either. The thing is, the last time I tried it, it worked with these files with no problems at all. I don't know what's suddenly caused this to happen. Googling and forum searches turned up nothing.
I also tried uninstalling and reinstalling gnomebaker, but that didn't change anything.

Does anyone know what the problem is?

At the same time, I have a problem with serpentine. It won't burn an audio CD with more than 22 tracks; it just doesn't do anything when I click the 'write to disc' button. But it does output this at the terminal when I click the button:
> 
(serpentine:20793): GStreamer-CRITICAL **: 
Trying to dispose element capsfilter34, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


I'm using ubuntu dapper 6.06.

---

### Post by stchman on 2007-07-10
> **PatrickMay16 said:**
> Hello there. When I try to add a wav file to gnomebaker, to burn an audio cd, it says "a plugin to handle a file of type audio/x-wav is not installed.". It doesn't work with mp3 file either. The thing is, the last time I tried it, it worked with these files with no problems at all. I don't know what's suddenly caused this to happen. Googling and forum searches turned up nothing.
I also tried uninstalling and reinstalling gnomebaker, but that didn't change anything.

Does anyone know what the problem is?

K3B does what you want, use the following to get K3B up and running:

sudo apt-get install k3b libk3b2-mp3


This will install K3B and the mp3 plugin.

---

### Post by PatrickMay16 on 2007-07-10
Thanks, but I would rather fix this problem than move to another program.

---

### Post by stchman on 2007-07-11
> **PatrickMay16 said:**
> Thanks, but I would rather fix this problem than move to another program.

I don't believe Gnomebaker does what you want it to.  Also Gnomebaker does not do video DVD as well.  K3B is a better program so I suggest use it.

---

### Post by Topfs on 2007-07-11
Well Gnomebaker is mostly Data CD there is a really good program that resize and fits almost every audio file, don't know if you need it supported in Gstreamer first.
It's called serpentine and is pre-installed on any ubuntu version. It easily beats most of it's simplicity :)

---

### Post by PatrickMay16 on 2007-07-11
> **stchman said:**
> I don't believe Gnomebaker does what you want it to.  Also Gnomebaker does not do video DVD as well.  K3B is a better program so I suggest use it.

But it does. All I want to do is burn an audio cd out of wav and mp3 files, and just a few months ago it did this fine. For some reason now, it won't work.

>  Well Gnomebaker is mostly Data CD there is a really good program that resize and fits almost every audio file, don't know if you need it supported in Gstreamer first.
It's called serpentine and is pre-installed on any ubuntu version. It easily beats most of it's simplicity 
Thanks. I'm also having a problem with serpentine. It seems like it can't burn an audio cd with more than 22 tracks. It might be a problem specific to the version included in Ubuntu 6.06, though, because I tried burning the CD on my laptop (which has 7.04) and it worked alright there.

But if anyone knows how to fix this problem with gnomebaker, I'd really like to know.

---

### Post by stchman on 2007-07-11
> **PatrickMay16 said:**
> But it does. All I want to do is burn an audio cd out of wav and mp3 files, and just a few months ago it did this fine. For some reason now, it won't work.


Thanks. I'm also having a problem with serpentine. It seems like it can't burn an audio cd with more than 22 tracks. It might be a problem specific to the version included in Ubuntu 6.06, though, because I tried burning the CD on my laptop (which has 7.04) and it worked alright there.

But if anyone knows how to fix this problem with gnomebaker, I'd really like to know.

I have never used Gnomebaker for CD or DVD burning.  When I was a Windows user I used to use Nero.  I find K3B to have a similar functionality to Nero.

---

### Post by mcduck on 2007-07-12
If I remember right, GnomeBaker still uses Gstreamer0.8. So if you haven't got all needed Gstreamer0.8-plugins installed that could be the reason why burning audio CD's doesn't work for you.

---

