---
title: "software for adding subtitles to Mac-made .mov video"
date: 2012-11-22
forum: Multimedia Software
---

### Post by bennypr0fane on 2012-11-22
Hello,
I have a .mov video file that was created on a Mac.
I need to subtitle this in Lubuntu or Ubuntu 12.04, as I don't have a Mac.
So, I'm looking for recommendations for which software best to use (please GUI programs only, I am a man page illiterate).
I seem to have figured out it needs to be demuxed first? Will it be  necessary to convert it, or can I do this on a Linux PC  while keeping the original format?
In the software-world of my dreams, I'd just open the file as it is, I'd have a GUI with frames from the video, and I'd just type in the subtitles right there, set them each to show from frame A to frame B, save and done. Not using Apple Quicktime. :)
thanks, Ben

---

### Post by Takanakathehacker on 2012-11-22
if you use vlc player, you can soft-sub really easily.

I know you can simply name a file the same as the video you are watching for example,

 tron.mkv (name of video file) tron.srt (name of sub-titles)

And then just add time-stamps and the subs you want.

Simple as. ;)
> 
1 
00:00:00,000 --> 00:00:03,000 
This is where... you type whatever you want 
 
2 
00:00:03,001 --> 00:00:06,000 
And boom it appears on screen 
3 
00:00:06,001 --> 00:00:09,000 
For all to see 
4 
00:00:10,000 --> 00:00:13,074 
Subtitles downloaded from [www.OpenSubtitles.org]("http://www.OpenSubtitles.org") 
 
5 
00:00:30,248 --> 00:00:31,880 
<i>Kevin Flynn: The Grid.</i> 
 
6 
00:00:33,612 --> 00:00:35,925 
<i>A digital frontier.</i> 
 
7 
00:00:37,918 --> 00:00:41,793 
<i>I tried to picture clusters of information, 
as they moved through the computer.</i>

Just make sure your .srt file is in the same folder as your .mov file.

---

### Post by bennypr0fane on 2012-11-22
Thank you.
Would I be able to make that into one file?
I completely forgot that the original file *already has subtitles* in German. This video will be submitted to a European contest (but I'm not the author, I'm doing this for them), so the Germna subtitltes need to be replaced by English ones. Just adding an .srt file would at best overlap the german subs with the english ones or whatever 
Right now, it's just that one -mov file, I think I need to open that and edit the existing subtitle stream.
The end result should be playble on a DVD player, so DVD format should be ok as well.
 Anyway, it'd be cool to avoid having to type all those time stamps, but instead to just click that frame for specifying the time.
 
> if you use vlc player, you can soft-sub really easily.

I guess storing the subtitles in the video file would be called hard-sub then?

 ...and are you sure that works with a .mov file from a Mac(!)?> 

---

### Post by bennypr0fane on 2012-11-22
please delete this post

---

### Post by AstroLlama on 2012-11-22
Try gnome subtitle, or aegisub. both great programs, though aegisub is a little more prone to errors, in my experience.

---

### Post by bennypr0fane on 2012-11-22
> **AstroLlama said:**
> Try gnome subtitle, or aegisub. both great programs, though aegisub is a little more prone to errors, in my experience.

gnome subtitle doesn't recognize the file.
aegisub is not in the ubuntu repos. On their homepage, only the source is available, I can't compile that... :confused:

---

### Post by SeijiSensei on 2012-11-23
Aegisub is available for 12.10 in the [repositories]("http://packages.ubuntu.com/quantal/video/aegisub").  For earlier versions of Ubuntu, there is a [PPA]("http://www.upubuntu.com/2012/02/how-to-install-aegisub-video-subtitle.html"), but it is out of date.

I'd give the 12.10 package a try first.

You probably should consider converting from .mov to Matroska (.mkv) before you go too far down the road, as it is well-designed for handling subtitles.  It supports multiple subtitle streams so you could add the English to the video and keep the existing German subtitle track as well. The mkvtoolnix package in the repos may also be useful.  Once you have a Matroska file you can extract the video, audio, and subtitles streams.  Then you can generate your new subtitles and remux the video.  

Aegisub is the tool of choice among anime fansubbers.  If you want to have nicely formatted subtitles, you might want to use [A-double-S subtitles]("http://matroska.org/technical/specs/subtitles/ssa.html").

---

### Post by AstroLlama on 2012-11-24
Just as a head's up, Aegisub works really well for me, but you have to be a little careful with how you use it, as it's a little buggy and sometimes can be unstable.

For example, during video play back on my system is sometimes crashes when I seek backwards. During audio playback, I get consistent crashes when I move the end of a region behind the playback point, again only DURING playback. 

I also haven't had a chance to compile the newest version yet, but maybe this week I'll have some time to tinker. Good luck to you!

---

