---
title: "Horizontal lines when playing video"
date: 2012-02-10
forum: Multimedia Software
---

### Post by kniwor on 2012-02-10
Ok, I am on a mission to get perfect video playback on my desktop, as Ubuntu is now my primary OS and so far things have been good, but not upto the standards.

So, I install vlc, and playback isn't too good. So, I decide to then compile smplayer from source, using [this]("http://ubuntuforums.org/showthread.php?t=1024592") and the latest codecs and the source from mplayer website. As a result, the mplayer playback is not impressive by relative standards.

However, it isn't quite as perfect as vlc works in Windows 7 (mplayer in linux though is smoother than in windows for heavy files, let me point it out). So, what's the problem? Well, there are these horizontal lines that I see while playback. Video tearing at it seems it is called out there. They are barely noticable but they are there. Now, i messed around a lot with mplayer and maybe I did not compile it properly, and that's the reason. I'd like to sort this out.


Config:
Intel i5 2500K
ASUS P8Z8V-LX
2 x 4Gb G.Skill

basically, the graphics I am using is the integrated Intel HD 3000 in the Sandy Bridge. I'd like to work this one out for my satisfaction and that of the community. For once, I would like a "perfect" playbak on ubuntu. It would feel nice.

---

### Post by Rodney9 on 2012-02-10
This post thanks to TrakerJon shows how to add every codec ever needed - 

[http://ubuntuforums.org/showthread.php?t=1884105&highlight=lmms](http://ubuntuforums.org/showthread.php?t=1884105&highlight=lmms)

Rodney

---

### Post by kniwor on 2012-02-10
Thanks,

However, my problem isn't a missing codec, or the playback. It is the quality that I want to improve. I have all the codecs doing their job just well. And the little problem I mention isn't codec specific, or file specific for that matter. 1080p movies play without the hitch, however, those lines are present in videos no matter if I'm playing a 1080 or a much lower resolution video.

---

### Post by mörgæs on 2012-02-10
Changed the thread title to a more informative one.

---

### Post by Johnny Buffalkill on 2012-02-10
What you're describing sounds like "tearing".  Do the lines happen most often during fast motion, and look a little like the picture has been cut horizontally, and then the pieces slightly offset?

Something that might help is changing the video output module in your playback software.  In VLC its Tools/Preferences/Video.  There should be an "Output" dropdown.  Try switching between  Opengl,  Glx, or X11 and test it out.  You might have to restart VLC after each switch.  Smplayer should have similar options for changing the video output.

I don't have any experience with Intel integrated graphics, but tearing is a common issue with ATI graphics cards using proprietary drivers.  I've succeeded in getting good video playback with proprietary ATI drivers by changing the video output.  I have no idea if it will work with your GPU, but its pretty easy to do and risk free.

---

### Post by kniwor on 2012-02-10
@Johnny 
Thanks, but that did not help.


After searching around, I found that with Sandy Bridge processors in x64 with can be fixed with changing the compiz settings and ticking the following options in "Workarounds"

- Force full screen redraws on repaint
- Don't wait for video sync.

Although I'm using ubuntu 32bit, I think this could fix it for me. I've changed the settings and I'll find out the next time I watch a video (it wasn't very noticable to begin with, so I can't just play something and find out if it has worked). I will mark the thread as solved if it works. 

Thanks everyone.

---

### Post by mörgæs on 2012-02-10
Good. Marking the thread 'solved' is done with 'thread tools'.

---

### Post by kniwor on 2012-02-12
That did it, everything seems to be working well. Thanks everyone.

---

