---
title: "DVD Burning Audio Question"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by radioraheem on 2008-01-27
I finally got a DVD to burn and play in our dvd player after several failed attempts.  K9copy and k3b both failed at everything I asked them do (even while using the more up to date copies from getdeb) but DeVeDe and GnomeBaker seemed to be able to get the job done.

Problem is, though the video finally plays the audio does not, even though the audio plays fine on the computer.

Here's the mplayer audio output from one of the files that is getting burned to the DVD:
> 
====================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
====================================================


All I get out of the audio when burned to a DVD is a series of short pops and clicks that happen occasionally throughout the entire video.

I'm a total newb to DVD burning but I've already learned a fair amount and want to learn more. 

Well, I obviously would like a working DVD burn too :)

Anyone have any ideas how I can fix this?  Thanks!

---

### Post by ron999 on 2008-01-27
Hi
I think that the sound problems might be caused by DeVeDe.
There's information on their website. Here:-[http://www.rastersoft.com/programas/devede.html]("http://www.rastersoft.com/programas/devede.html")
Also, there have been several threads on this forum about it.:cool::cool:

---

### Post by radioraheem on 2008-01-27
I updated mplayer/mencoder to the 1.0rc2-4.1.3 version as recommended at the DeVeDe site but that did not fix this issue.

At this point I've gone through almost half a box of blank DVD-R's trying to figure out how to just copy a simple avi file to a playable video DVD.  I have a lot of new coasters now :)

What software combinations is everyone else using to do this?  I've tried k9copy and k3b, but k3b crashes right before it finishes a burn.  The latest combo I'm trying is acidrip to create the avi's, DeVeDe to create the disc image, and GnomeBaker to burn it.  I tried ManDVD also to create the disc image but I really don't like it's interface and the iso's it created didn't seem to want to burn correctly.

When I open one of these avi files using mplayer at the terminal I get the following info about it:

> [aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  512x384  12bpp  23.976 fps  952.6 kbps (116.3 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.2 (build 2540/release)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)


All of the avi's I'm attempting to burn should have the exact same type of setup and encoding.

I've done plenty of forum searching and all the tutorials and tips I'm finding seem to be old/out of date so I'm hoping to get some current information from someone who is successfully doing this now.

Thanks!

---

### Post by mc4man on 2008-01-27
Your problems non withstanding what is the reason for putting your xvids on dvd vs.  on cd(s)
> the latest combo I'm trying is acidrip to create the avi's
What was the format of original source?

---

### Post by radioraheem on 2008-01-27
I'm trying to creative an archive of family videos, both digitally (on an external hard drive) and on burned DVD's.  

I've been collecting them from various family members by having them upload them to my web server, so they're in a variety of sources and formats.  The ones I'm trying these test burns with are more recent and were encoded with previously mentioned settings by another family member off of their DV camera who then uploaded them to me.

I know that for backup DVD archives you can just make them data DVDs, but more importantly I'm trying to learn how to make them playable on a regular DVD player because I want to burn videos of our 7 month old son so we can mail them to family members who we don't get to see very often.

I also have a DV camera that I use to take video, and said family is getting a little impatient with me for not sending them new videos of the baby on DVD because the camera was a baby shower present :)

Anyway, thanks for the help.  If you need more detail besides what I tried to provide here just let me know.

---

### Post by mc4man on 2008-01-27
I don't know much about avi's and dv so i can't really venture a guess other than possibly your orig. audio format(s) are not being converted to a dvd-video compliant format.
Hopefully someone who knows this stuff will come along or doing a search on mandvd, avidemux, or convert avi to dvd should give you some useful reading

---

### Post by ve3rpm on 2008-02-08
I trust I'm not out of line here, but after making a few coasters of my own, I finally tried the trial version of NERO for linux, and it worked so well, for the first time I actually bought some software as it solved a myriad of problems that I ran into.  As well, I found that buying a few RW disks saved me a whole lot of grief as you can always erase them should things not work out.

---

### Post by ubuntu-freak on 2008-02-10
Anyone tried WinFF? Would a combination of dvd::rip, WinFF and Gnomebaker work well? Never tried to rip and burn DVDs, and can't right now, so I'd appreciate some info regarding this combination.
 
Nathan

---

### Post by ron999 on 2008-02-10
Hi
I use WinFF.
It's OK.
But it's just a front end for ffmpeg.
It has options such as 'PAL DVD' etc.
But that just converts your file to DVD compliant format.
You need to author it afterwards with tovid (for example) before you can burn it with Gnomebaker.
WinFF is a free download from Bigg Matt's website here:-[http://biggmatt.com/]("http://biggmatt.com/")
8)8)

---

### Post by ubuntu-freak on 2008-02-10
> **ron999 said:**
> Hi
I use WinFF.
It's OK.
But it's just a front end for ffmpeg.
It has options such as 'PAL DVD' etc.
But that just converts your file to DVD compliant format.
You need to author it afterwards with tovid (for example) before you can burn it with Gnomebaker.
WinFF is a free download from Bigg Matt's website here:-[http://biggmatt.com/]("http://biggmatt.com/")
8)8)

 
Yeah I've used WinFF to make mp4 vids for phone (renamed .3g2 to .mp4). I realised later after posting that it can't generate the DVD image itself. I've read avidemux is good for that, tried it?
 
Nathan

---

### Post by ron999 on 2008-02-10
> **reassuringlyoffensive said:**
> it can't generate the DVD image itself. I've read avidemux is good for that

Hi Nathan
You've got your wires crossed mate :)
I've used Avidemux, it's a video **editor**.
It will also convert a file into DVD compliant format (like WinFF) but it won't **author** a DVD.
For authoring a DVD from a video file look at tovid, there may be a GUI for it.
When you've done that your result is a video_ts folder. That's what has to be burnt to disc.
This is where to read about tovid:-[http://tovid.wikia.com/wiki/Main_Page]("http://tovid.wikia.com/wiki/Main_Page")

Keep on truckin'

:cool::guitar::cool:

---

### Post by ubuntu-freak on 2008-02-10
duplicate post

---

### Post by ubuntu-freak on 2008-02-10
> **ron999 said:**
> Hi Nathan
You've got your wires crossed mate :)
I've used Avidemux, it's a video **editor**.
It will also convert a file into DVD compliant format (like WinFF) but it won't **author** a DVD.
For authoring a DVD from a video file look at tovid, there may be a GUI for it.
When you've done that your result is a video_ts folder. That's what has to be burnt to disc.
This is where to read about tovid:-[http://tovid.wikia.com/wiki/Main_Page]("http://tovid.wikia.com/wiki/Main_Page")

Keep on truckin'

:cool::guitar::cool:

 
Seriously? Geez. Is there a GUI authoring app for Gnome? qdvdauthor is KDE, dvdstyler isn't packaged for Ubuntu anymore so isn't in the repo, as far as I know. There's a new gtk frontend for dvdauthor but it's alpha at the mo. Does K3b author? It's odd that we lack GUI authoring apps. What about mandvd?
 
Nathan

---

### Post by ron999 on 2008-02-11
> **reassuringlyoffensive said:**
> Does K3b author? 
No

](*,)

---

### Post by ubuntu-freak on 2008-02-11
It's okay I'm up to speed now. Hate not knowing about certain subjects so read up on it. Tovid seems to be the best bet, authors, burns and works well in Ubuntu.
 
Thanks for the info.
 
Nathan

---

