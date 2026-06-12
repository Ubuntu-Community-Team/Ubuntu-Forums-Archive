---
title: "Save part of streaming video/audio"
date: 2011-11-03
forum: Multimedia Software
---

### Post by Barney-R on 2011-11-03
Hello,

(Linux newbie as of March/April this year. Ubuntu 10.10 Maverick. Broadband connection. Fast computer.)

I don't know whether this is covered elsewhere. I've tried searching, but there are so many thousand unrelated results that it's easier to start a new thread.

I'm not interested in doing anything illegal, so please tell me if you think I could be pushing my luck. It's often difficult to be sure.

I've seen videos on YouTube that are short segments taken from an endless stream, as in the case of the (on line) BBC news channel.

I have (very) occasionally saved a YouTube video using "Easy YouTube Video Downloader" in FireFox, but my understanding is that a file cannot be saved unless it has a beginning and an end.

These continuous broadcasts never end, so how can a short segment be saved?

I can also envisage a situation where I might want to save a short segment from a film, or perhaps an audio "quote" from an internet radio broadcast.

Any advice will be appreciated, but please remember I'm no expert. I'm not afraid of using the terminal if necessary, but I don't yet fully understand what I'm doing there.

---

### Post by aeiah on 2011-11-03
it really depends on the source. to take your bbc news example, i know that in the past it was possible to view the stream with regular video players. i dont know if that's the case any more with bbc news though.

something like this would work, presuming mplayer can play the video stream in the first place:
```

mplayer streamname -dumpstream -dumpfile output.ext
```

most video streams will make things difficult though, usually as an easy-if-flawed method of DRM. sometimes you can overcome these issues with rtmpdump.

---

### Post by Barney-R on 2011-11-03
Thank for that, aeiah, but how do I stop the save when I've got the bit I want?

It IS a save (download) I want. I don't have any trouble viewing streaming video (or listening to streaming audio). I'd just like to save an occasional segment, anything from a few seconds to a few minutes. I don't have anything specific in mind. Mainly, having seen examples done by others, I want to know HOW to do it.

Would the code you've given do that?

Being somewhat inexperienced, I'm reluctant to start something that may be difficult to stop, which is why I'm asking before I try it myself.

I hope you understand my caution.

---

### Post by Barney-R on 2012-01-09
BUMP (does this work on here?).

I really would appreciate detailed (but not <b>too</b> detailed) instructions on saving a segment of streaming audio or video that I'm currently watching or listening to.

I know how to save a complete file, but when there's no beginning or end, how do I start and stop the save?

If it can be done without using the terminal, I'd prefer to do it that way because I don't really understand yet what terminal commands mean.

I'm using Ubuntu 10.10 and FireFox.

---

### Post by Barney-R on 2012-03-20
[CENTER]**HELP!**
[/CENTER]

Is there anybody "out there" who can answer my question? It may be that I'm a bit "thick", but I need to **understand** how to do this.

I'm still a comparative newbie, having been using Ubuntu (Maverick) for just under a year, and I'd rather use some kind of software than enter commands I don't really understand into the terminal.

I see short segments from live broadcasts (BBC24, RT etc) uploaded to YouTube and would like to know how it's done.

My previous understanding was that for a file to be saved, it had to have a beginning and an end, but this is clearly not the case with these segments taken from a never-ending stream.

I'd also like to be able to do the same with streaming audio.

Is that too much to ask?

---

### Post by ron999 on 2012-03-20
> **Barney-R said:**
> 

My previous understanding was that for a file to be saved, it had to have a beginning and an end, but this is clearly not the case with these segments taken from a never-ending stream.



Hi
With a live stream...
the 'beginning' is when you start to save
and the 'end' is when you stop the process.
Which stream are you trying to save part of?

---

### Post by Barney-R on 2012-03-21
Thank you for getting back to me, ron999.

I don't have any specific stream in mind. I'm just thinking generally. It's something I don't know how to do, but I'd like to know how, because I'm sure there'll be times when I **will** want to do it.

I'm thinking streaming audio as well as video, internet radio for example, and I suppose I could use the BBC news 24 and RT as examples of video streams.

I'm not afraid of the terminal, but it's easier if I can see what I'm doing (GUI) rather than have to type lines of code that I don't fully understand.

aeiah gave me a terminal command (above), but I don't know what that does, and more importantly, I don't know how to stop it once I've got the segment I want.

All help will be greatly appreciated.

---

### Post by Barney-R on 2012-03-24
Oops! Sorry aeiah. When you suggested rtmpdump, I wrongly assumed you were referring to a terminal command.

I've now installed rtmpdump, but where is it? How do I find it? How do I use it?

Sorry if I'm being a nuisance, but there's no point having something installed, however potentially useful, if I can't find out how to use it.

I'll be off-line for the next couple of days (family matters), but I'll check back early next week.

---

### Post by SeijiSensei on 2012-03-24
rtmpdump is really just a toolkit.  If you visit the [rtmpdump home page]("http://rtmpdump.mplayerhq.hu/"), you'll find a list of software that uses rtmpdump for various purposes.  I don't know how well any of these will work with continuous streams, though.  I've only used things like [get-flash-videos]("http://code.google.com/p/get-flash-videos/") which are generally intended to download a discrete file.  You could give it a try, though.

---

### Post by Barney-R on 2012-04-04
Sorry SeijiSensei. I expected to be back here last week.

From what I've seen so far (limited time), it's looking promising. Thanks for your help.

I'll mark this thread as solved. How's that for optimism?

:p

---

