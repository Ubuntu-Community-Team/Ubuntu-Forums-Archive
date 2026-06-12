---
title: "(simple) program for *cutting* video"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by Finch75 on 2007-06-03
Hi everybody,

sorry if this seems like a stupid question, but I've really done quite some searching without success...

I have a PVR card that records as MP2 (hardware encoder!).

Now I'm looking for a very simple program to "cut" those files, i.e. just remove something at the beginning and the end, sometimes remove commercial breaks.
Most importantly, 
1) I do NOT want the program to "re-encode" the entire stream, it's a perfect (?) MP2 stream.
2) I don't want to do a multi-step process like demux, create cut list, remux, create, whatever...

I DO have a program like this for Windows (came with the card!) and it works fine, but the user interface is really bad and of course, I am now looking for a Linux solution :-)

Why I don't want to re-encode? Well, simple: For one thing, I don't think the quality gets any better by doing this and at least as important: it takes a long time. I have a fast computer, but a two hour file still takes a long time. The Windows program I have is limited only by hard disk speed - that means it can write a two hour movie in less than a minute (source file on one hard disk, target file on a different disk).

I've already taken a look at KDEnlive - looked quite promising at first, but I haven't found a way to avoid the re-encode and also, it stopped working the next day :-( :-(

Thanks for any hints - this is one of currently "only" two or three "major problems" I have in my move to Linux...

Finch

---

### Post by AnRa on 2007-06-03
I think you mean MPEG-2, you may use gopchop, it is in the repositories.

---

### Post by Finch75 on 2007-06-06
> **AnRa said:**
> I think you mean MPEG-2, 
Yep. For me, mp2 was just a shorter way of writing mpeg2. But it's actually audio, isn't it? Oh well...

> **AnRa said:**
> you may use gopchop, it is in the repositories.

Thanks for the hint - yes, gopchop *looks* exactly like what I was looking for ...

Unfortunately, the following things happened:
1) I installed gopchop from the repositories. I started it, opened a short movie... it took a long time to scan the movie for GOPs, then did something else... then crashed. I tried again, same problem. Tried 3 other movies. This seems to be a 64 bit problem? (did I mention I work in 64 bits?) I installed it from the 64-bit repositories!
2) I looked at the GOPchop page and found a link to GOPdit (derived program) - same problem! (downloaded and compiled the source - still no luck in 64 bit)

:-(

3) I installed GOPchop on a 32 bit machine just to see it if works there. Still a long time for scanning, then it worked :-). For every "redraw" of the window, it seems to play the last GOP. When I resized the window, it redrew a couple of dozen times and that crashed it :-(
4) GOPdit seems to work better and uses no time for scanning the video first. I am not sure any more (did this right after your posting...), but I think it also crashed on me ;-( There was something wrong with it...

Both of these programs look "promising", but still "very beta" and unfortunately, "very dead" :-(. The latest version of GOPchop is more than two years old and there is no current status on the web page. Even worse: The last thing it says is "version 1.20 is expected soon" (dated May 2005).

All of this in combination with the unsuccessful attempts on a 64 bit platform makes it look like a "potential temporary solution" - but I'll have to keep looking...

Any other suggestions?

---

### Post by AnRa on 2007-06-06
You may try Avidemux but I'm not sure if it does what you need ;)

---

### Post by srt4play on 2007-06-06
[This]("http://www.linuxalt.com/") site lists some equivalents to some Windows software, including windows movie maker.  

Among them, [lives]("http://lives.sourceforge.net/") looks particularly interesting.

---

