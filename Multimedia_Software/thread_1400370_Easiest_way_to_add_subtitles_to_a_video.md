---
title: "Easiest way to add subtitles to a video?"
date: 2010-02-06
forum: Multimedia Software
---

### Post by Replicon on 2010-02-06
Hi all,

I'm sure this is easy to do. I want to create one of those "Hitler" internet meme things for a presentation I'm doing at work, which of course, involves adding custom subtitles to a video.

Now, I've found the tutorial that says how to use the right filter with avidemux, but I was wondering what the easiest way is to create the file for that filter to read. Is it just a matter of manually writing it up in my fav text editor, or is there a simpler way to do it? I figure if the syntax is really, really simple... something that looks like

startTime,duration,text

(one per line)

then I'd rather just textedit it manually, but if it's something ugly and complicated, then I should use some software to do it... Any advice?

---

### Post by LightB on 2010-02-06
What are you going to play it back with? If it's with a player that supports ÁSS. (ridiculous censor), you could use subtitleeditor or aegisub to add them. These are softsubs and don't get encoded to the video. If you need hard encoded subs, you could do the previous, then use mplayer to output to yuv with the -áss (without accent) tag and 'vo yuv4mpeg'. Then you encode that again into a playable format and mux the audio track in.

---

### Post by lovinglinux on 2010-02-06
First you wil need to create the subtitles with a subtitle editor, like [subtitleeditor](apt:subtitleeditor), [aegisub](http://www.aegisub.org/), [gaupol](apt:gaupol), [jubler](http://www.jubler.org/) or [gnome-subtitles](apt:gnome-subtitles). I recommend subtitleeditor. Aegisub looks very powerful, but I never was able to make it work properly, specially the video feature. I use jubler for subtitle conversion, but never tried to create subtitles with it. Gaupol is not as good as subtitleeditor IMO.

After you create the subtitle, you will need to save it somewhere. I recommend saving it as srt then converting to ssa format (which includes text formatting like color and position) with Jubler. I do this way because I never was able to aplly the same formatting style to all subtitles in a file using subtitleeditor, but Jubler can do that in a few steps.

After saving the subtitle file you will have to hardcode it into your video. I don't recommend avidemux, since it's subtitle support is a hack and doesn't work well on all players. Instead use mencoder. Here is an example of mencoder command:

```
mencoder source_video.avi -sub source_subtitles.ssa -a\s\s -a\s\s-color FFFF0000 &#8722;\a\s\s&#8722;font&#8722;scale 3 -o output_video.mp4 -oac lavc -lavcopts acodec=libfaac:abitrate=128 -ovc lavc -lavcopts vcodec=libx264:vbitrate=1500
```

The encoder options above are probably compatible with YouTube and will render excellent quality results.

BTW, I'm a fan of those Hitler parodies. There are some really funny, specially when they involve Windows or DRM.

---

### Post by Replicon on 2010-02-09
Thanks for the tips! I'll give all those a try!

---

### Post by Mariane on 2011-05-16
Additional question: How long does it take to add subtitles per hour of video talk? (Provided you know both languages reasonably well and the sound is clear enough so you don't have to listen several times to the same sentence to make sure of what was said)? 

Mariane

---

### Post by lovinglinux on 2011-05-16
> **Mariane said:**
> Additional question: How long does it take to add subtitles per hour of video talk? (Provided you know both languages reasonably well and the sound is clear enough so you don't have to listen several times to the same sentence to make sure of what was said)? 

Mariane

A lot. But depends on your experience. The most complicated issue I think is setting the correct timeline. That takes time to do it.

---

### Post by Mariane on 2011-05-18
Timeline? Do you mean coordinating the text with the video? Can't I just select two points in the video scroll bar and say "this piece of text should be visible from then to then"? 

Which is the easiest program to use, please? 

Mariane - total beginner in video editing

---

### Post by lovinglinux on 2011-05-18
> **Mariane said:**
> Timeline? Do you mean coordinating the text with the video? 

Yes, that is what I mean.

> **Mariane said:**
> Can't I just select two points in the video scroll bar and say "this piece of text should be visible from then to then"? 

Yes, but that takes time anyway.

> **Mariane said:**
> Which is the easiest program to use, please?

Try Subtitle Editor:

```
sudo apt-get install subtitleeditor
```

---

### Post by Mariane on 2011-05-19
I will. Thank you very much for your explanations. 

Mariane

---

### Post by Mariane on 2011-05-24
I does not want to open my video. (avi with Xvid and mp3) 
I open subtitleeditor then do "video - open" and it crashes. 
Once it said "segmentation fault" and once it said "Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0. 

The video can be seen [http://www.lapf.eu/ritual_cmp_mp3_320.avi](http://www.lapf.eu/ritual_cmp_mp3_320.avi) 

Another program called subtitlecomposer opens the video but does not display it, I can only hear the sound. This is good enough for writing the subtitles I guess. 

Mariane

---

### Post by lovinglinux on 2011-05-24
> **Mariane said:**
> I does not want to open my video. (avi with Xvid and mp3) 
I open subtitleeditor then do "video - open" and it crashes. 
Once it said "segmentation fault" and once it said "Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0. 

The video can be seen [http://www.lapf.eu/ritual_cmp_mp3_320.avi](http://www.lapf.eu/ritual_cmp_mp3_320.avi) 

Another program called subtitlecomposer opens the video but does not display it, I can only hear the sound. This is good enough for writing the subtitles I guess. 

Mariane

I never create my own subtitles, but I use [Jubler]("http://www.jubler.org/") to convert them from .srt to .a\s\s. I don't think it has an embedded player, but you can test subtitles with a selected video.

---

