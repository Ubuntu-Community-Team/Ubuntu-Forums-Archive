---
title: "Best free video editing software for my criteria."
date: 2016-02-18
forum: Multimedia Software
---

### Post by arthur24 on 2016-02-18
I use Ubuntu 14.04.3
I have a GTX 750 ti videocard.

I want video editing software (free) which can cut, paste, delete video fragments and I would also like to put audio from a audio file under the video playback. If it is possible I would also like to be able to add simple effects.
Audio formats are (WMA)
I bet I need to convert them to something else before I can work with it in Linux video editing software, is that correct?
 
The videoformats of the videos I will be using are mpeg4 (avi) and .mov. Again the question, do these filetypes need to be converted before handling? If yes, what program would I need?

I'm not completely new to video editing, but it is a long time ago, it's the first time on Ubuntu though. 
I have already found names of several video editing software programs like kdenlive, openshot and others. They seem to have the options I need, but I wanted to check out which one would be best, just to be sure.
If you think about anything necessary for a Ubuntu video editing newb to know on the subject, please don't hesitate to inform me.
The final video should be in a .avi / mpeg format. The reason for this is because it's a project for my job, and the video should be able to be played with both mac and windows mediaplayer software.

---

### Post by goofprog on 2016-02-18
Hit and miss.  You can use ffmpeg for most of it.  You just have to know the right commands to get what you want.

---

### Post by FakeOutdoorsman on 2016-02-19
> I bet I need to convert them to something else before I can work with it in Linux video editing software, is that correct?
You probably won't need to convert those, but there may be some WMA variants that can't be decoded by FFmpeg 'n friends yet.

> The videoformats of the videos I will be using are mpeg4 (avi) and .mov. Again the question, do these filetypes need to be converted before handling? If yes, what program would I need?
They will probably work fine, but AVI and MOV are just containers that can utilize many different video and audio formats, so without more specifics we won't know until you try it. It also depends on what you mean exactly by "using". Are these what you're going to import into the editor?

> The final video should be in a .avi / mpeg format. The reason for this is because it's a project for my job, and the video should be able to be played with both mac and windows mediaplayer software.
Using the stock players for each OS? Or is something like VLC an option? Again, "avi/mpeg" is vague, and these days I'd be surprised of these players can't handle  more modern formats.

I've only really used Kdenlive in Linux (with FFmpeg, not the junk from Libav). It's never had an issue for me.

---

### Post by Linuxisfast on 2016-02-20
Try the new Openshot 2.0 from their ppa @ [https://launchpad.net/~openshot.developers/+archive/ubuntu/ppa](https://launchpad.net/~openshot.developers/+archive/ubuntu/ppa) runs very good on my i7 Haswell powered desktop. I did some heavy file editing of over 4GB and the program never crashed. You can also try KDENLIVE, another program thats actively developed and well worth it.

---

### Post by Bucky Ball on 2016-02-21
If you're game you can go for Blender. It edits video very nicely (am using it to edit and render fieldwork a/v at the moment) but there is a steep learning curve. You'll find it in the software centre and tons of 'how tos' online.

Kino, Openshot, Kdenlive, Cinelerra. The 'best' is what suits your workflow and purpose best. We can't tell you which is going to work best for you. Advise you install and try them then ask more specific technical support questions in a new thread(s) when you have them. This one tends toward discussion/opinion  rather than support ('what's the best' threads often find themselves in 'Recurring Discussions' because, well, they can become cyclic, repetitive and sometimes argumentative as the question can't be answered). 

Asking what's the 'best' will get you a raft of posts about what is best for specific users. Their best may be your worst. 

Good luck. :)

---

### Post by montag dp on 2016-02-21
I've used kdenlive before, and it can do everything you are asking. I don't know too much about which formats are supported, but I assume that depends on the codecs installed on your system. The one gotcha for me was that the version I was using was a bit buggy and crashed/locked up when doing certain operations.

---

### Post by shantiq on 2016-02-21
[kdenlive]("https://kdenlive.org/features") for GUI and ffmpeg for CLI [but a serious learning curve]  for this I would personally choose GUI

---

### Post by gordintoronto on 2016-02-21
My choice: cinelerra

Mostly because of this web site: [http://www.g-raffa.eu/Cinelerra/HOWTO/](http://www.g-raffa.eu/Cinelerra/HOWTO/)

There are also many tutorials on youtube.

---

### Post by yoshii on 2016-02-22
@arthur, 
I think most of the video editors should be able to do what you are asking.  
Ubuntu Studio comes with an older version of KDEnlive and also a few other video editors such as Pitivi (which is rather simple).  
So you could download and burn the LiveDVD and test it out.

---

