---
title: "ACC (also known as mp4) in ubuntu"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by robusat on 2007-11-21
Why wont rhytmbox or banshee play acc music files ripped in soundjuicer?

---

### Post by deruberhanyok on 2007-11-21
I've run into a similar problem and I've found that not only is it those programs, but ANY program. Try playing them in VLC, for example.

As near as I can tell, even if I'm using the default AAC option for ripping in Sound Juicer (no custom settings), the files come out screwed up. A 3 minute song would report a 15-minute length and not play, etc.

I also noticed that AAC files (previously ripped using iTunes) transferred to my iPod via rhythmbox come out similarly corrupted, although Banshee at least seems capable of syncing files without that problem.

I've been told that a program called Grip may be able to rip to AAC without any issues though I've not yet tried it since I'm at work.

Assuming they DO play in VLC for you (and thus are being ripped without any problems) it may be that you just need to download the proper gstreamer plugin to enable AAC playback in those apps, but I don't think you could even rip to AAC if you hadn't done that already.

---

### Post by ericesque on 2007-11-23
Yeah, I ripped a handful of cds to AAC the last few days.  I swear I listened to one of the songs after it was ripped and it sounded just fine (it MAY have been off the audio cd, but I really don't think so). 

Anyway, come this morning I go to listen to one of the albums in Rhythmbox and the audio is all choppy.  The track lengths for 3 minute songs are listed at about 5 times what they should be.

It is especially frustrating to think that it played correctly once and now things are all screwy.  I've done  a bit of searching on the forum.  It looks like the problem dates back to Hoary!  I haven't seen any threads yet where the OP has found a resolution.  That makes me nervous.

Oh! Last piece to the puzzle, an album I ripped to mp3 (night before the others, ripped by Rhythmbox) works no problem... 

Would REALLY like to figure this one out.

---

### Post by deruberhanyok on 2007-11-24
ericesque, yeah, I've tried a few things and found that ripping to any other format works just fine (I tried flac, mp3 and ogg just to make sure it wasn't the disc or something). My guess - and this is just a guess - is that it's something to do with the AAC encoder available with the version of gstreamer currently in use.

Old documentation references a gstreamer0.8-faac and gstreamer0.8-ffmpeg package that need to be installed; while I see a gstreamer0.10-ffmpeg in the repositories I don't see a matching gstreamer0.10-faac, assuming that's even still needed.

I'm running 64-bit, though. It's possible it exists in the 32-bit repositories, I just don't have another system I could run 32-bit on to check.

---

### Post by ericesque on 2007-11-27
I can confirm no gstreamer0.10-faac for 32-bit.

I have had a little success.  I found a bug filed against this issue.  I'm getting less stuttering with crossfading enabled.  Edit>Preferences  Playback tab, check the crossfade box.  Though my CPU is sittin pretty at about 95-100%  :(  I'll keep playing.

The good news is the bug seems to be fixed upstream.  Hopefully that will make it's way to us sooner than later.

---

### Post by ericesque on 2007-11-27
Bah, no love.  I guess we'll stick with mp3 for now.  Hopefully they push out that update quickly.

If anyone gets it, I'd love to hear about it.

---

### Post by langer3 on 2008-01-10
I have all the same problems.  Hope someone has  a solution.

---

### Post by ron999 on 2008-01-10
Hi
I have had good results using two other AAC encoders instead.
One by Nero and the other an AAC+ from rootkit at mp4tools.
If you're interested, this is the thread I used:-[http://ubuntuforums.org/showthread.php?t=628434]("http://ubuntuforums.org/showthread.php?t=628434")
And mp4tools is here:-[http://teknoraver.campuslife.it/software/mp4tools/]("http://teknoraver.campuslife.it/software/mp4tools/")
:cool:

---

### Post by rootkit on 2008-01-20
> **ron999 said:**
> Hi
I have had good results using two other AAC encoders instead.
One by Nero and the other an AAC+ from rootkit at mp4tools.
If you're interested, this is the thread I used:-[http://ubuntuforums.org/showthread.php?t=628434]("http://ubuntuforums.org/showthread.php?t=628434")
And mp4tools is here:-[http://teknoraver.campuslife.it/software/mp4tools/]("http://teknoraver.campuslife.it/software/mp4tools/")
:cool:
aacplusenc is in medibuntu now, while mp4tools in my PPA repository.
Have fun!

---

