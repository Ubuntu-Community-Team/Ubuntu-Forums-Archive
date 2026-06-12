---
title: "Determine audio codec required for a stream?"
date: 2011-05-15
forum: Multimedia Software
---

### Post by Parsa86 on 2011-05-15
When I play [this]("http://live.irib.ir/tv3.asx") stream on my VideoLan, video plays fine but there is no audio. I am pretty sure that this means that I do not have the audio codec. But how can I determine which codec I require so I can download/install it? :confused:

Many thanks

---

### Post by cotcot on 2011-05-15
Have you tried [[COLOR="Red"]this[/COLOR]]("http://vntutor.blogspot.com/2008/01/how-to-play-asx-files-under-firefox.html")?

---

### Post by Parsa86 on 2011-05-15
Thanks for that plugin seems to be 3 years old and no longer in the repository. I would rather just be able to play it in Videolan or movie player using the right codec..

/edit - Ok I found out that the ASX is just a media container and holds the video at mms://62.220.122.4/tv3. This stream uses WMV3 and WMA2. Video seems to play 100% fine but audio/WMA2 not. Any ideas anyone..?! thanks

---

### Post by andrew.46 on 2011-05-17
Admittedly I compile my own vlc but it plays audio *and* video fine here, I attach a screenshot showing codec details. Can anybody else test the stream with a repository vlc?

---

### Post by nothingspecial on 2011-05-17
Video and audio work fine with vlc 1.1.9 from the natty repos for me.

---

### Post by ron999 on 2011-05-17
The other day, when the OP asked the question, there was something wrong with the stream.
There was a WMA audio stream, but it was silent.
It's fixed, the audio works fine now.

---

### Post by Parsa86 on 2011-05-17
Ron you are correct sir. I wonder if it was because they were streaming a football match and the audio was DRM-ed or something for a silly reason?!

Many thanks everyone

---

