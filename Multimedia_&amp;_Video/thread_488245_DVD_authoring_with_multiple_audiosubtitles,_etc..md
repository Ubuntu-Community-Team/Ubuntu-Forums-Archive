---
title: "DVD authoring with multiple audio/subtitles, etc."
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by michaelzap on 2007-06-29
Is there a linux program capable of this? So far I haven't found one. In Windows I used to use dvd-lab pro, which let me add all the audio tracks and subtitles I wanted, but I can't get that to work using CrossOver Office and I'd really rather use a native application.

Oh and while I'm asking, do any of the Linux DVD rippers have the sort of error-checking/recovery that DVD Decrypter has? I currently still use that for problematic rips because I haven't found anything in Linux that will keep trying until it is able to read a dirty disc.

And lastly, I personally don't see any relation between the DVD Shrink in Windows (which is a great program with a very straightforward GUI) and xDVDShrink in Linux. Anyone else as disappointed as I am in that program? I'm perfectly willing to use the Gimp instead of Photoshop whenever possible, but I'd really like to have some better ripping tools...

---

### Post by michaelzap on 2007-07-06
nobody?

---

### Post by michaelzap on 2007-07-15
*bump!*

I can't believe that no one using Ubuntu hasn't figured out a way to author multi-subtitle DVDs. I've been using ManDVD lately to make single-subtitle DVDs (after processing my source files through AviDemux), but I've only just realized that it's superimposing the subs over the video instead of creating a separate subtitle track. That's definitely not what I want, so now I don't even have a decent method for single-subtitle DVDs.

What do you Ubuntu users do to make multi-subtitle DVDs?!?

---

### Post by rojanu on 2007-08-31
Have you found anything or is there anyone else using a such app.

---

### Post by michaelzap on 2007-08-31
> **rojanu said:**
> Have you found anything or is there anyone else using a such app.

No, I haven't found anything yet :(

---

### Post by bogolisk on 2007-08-31
> **michaelzap said:**
> No, I haven't found anything yet :(

There is (actually a combination of tools). But the whole process has a very error-prone so no-one dare to guide you step by step using the forum. Hand-holding using the forum for easy problems is already hard. Hand-holding using forum for hard problems is just ... not worth it.

Sorry.

---

### Post by michaelzap on 2007-08-31
I don't need hand-holding. If someone would just say "I use tovid for x and whatever for y and then burn with z" that would be helpful. Although if you think about your answer for a second you'll realize that there really ought to be an authoring program in Ubuntu that does this without being so complex or obtuse that you feel that you can't even explain it to anyone...

---

### Post by bogolisk on 2007-08-31
> **michaelzap said:**
> I don't need hand-holding. If someone would just say "I use tovid for x and whatever for y and then burn with z" that would be helpful. Although if you think about your answer for a second you'll realize that there really ought to be an authoring program in Ubuntu that does this without being so complex or obtuse that you feel that you can't even explain it to anyone...

Well the problem with with ppl who are not making money with their software is that they do it for fun, first and foremost. Therefore they like to add powerful features more than to reduce the learning curve.

Now to answer your question: if you'd become an expert of transcode/mencoder/ffmpeg (for transcoding), mjpeg (for multiplexing) and dvdauthor (for authoring) then you would know how to accomplish your task.

---

### Post by michaelzap on 2007-08-31
> **bogolisk said:**
> Well the problem with with ppl who are not making money with their software is that they do it for fun, first and foremost. Therefore they like to add powerful features more than to reduce the learning curve.

Now to answer your question: if you'd become an expert of transcode/mencoder/ffmpeg (for transcoding), mjpeg (for multiplexing) and dvdauthor (for authoring) then you would know how to accomplish your task.

I am enough of an "expert" to know that your answer is to tell me that if I were as smart as you are I'd have figured it out by now, and I also don't agree that free software needs to be less user-friendly than commercial software, nor does that seem to be the case in my experience (and frankly, adding multiple subs and audio tracks to a DVD is a basic feature, not something new and amazing only available on Linux).

My limited investigation into this before now led me to conclude that the command line version of dvdauthor was capable of creating a multi-subtitle DVD, but the GUI version (in my case qDvdAuthor) was still not quite working. Apparently they did add this feature to it around the beginning of this year, but there are a number of posts in their forums from people having trouble using it. I'm going to update to the latest version of qDvdAuthor and see if I can get it to work now.

I would certainly prefer a GUI app for authoring DVDs, since creating menus and whatnot is intrinsically a GUI task, and I will happily report back here the good news that I've found a way to do this in Ubuntu as soon as I find one (and I'll try to give specific and useful instructions so that others can do it as well).

---

### Post by bogolisk on 2007-08-31
> **michaelzap said:**
> I am enough of an "expert" to know that your answer is to tell me that if I were as smart as you are I'd have figured it out by now,

I'm sorry that you took it that way. The truth is:
[list]
[*] I've managed to do it **once**!
[*] I'm not sure what were the required steps because it was a long trial-error session
[*] I don't want (and have no need) to do it again.
[/list]

>  and I also don't agree that free software needs to be less user-friendly than commercial software, nor does that seem to be the case in my experience (and frankly, adding multiple subs and audio tracks to a DVD is a basic feature, not something new and amazing only available on Linux).

As I said, with transcode, mplex and dvdauthor, you can do it if you use the **right** incantation.

---

### Post by Amazona aestiva on 2007-09-02
See the first link in my signature.

You might try Tovid.

---

