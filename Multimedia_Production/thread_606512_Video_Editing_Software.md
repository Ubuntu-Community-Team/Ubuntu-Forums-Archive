---
title: "Video Editing Software"
date: 2007-11-08
forum: Multimedia Production
---

### Post by Qwerty_ on 2007-11-08
G'day, I have done abit of googling but I would like some advice on what is the best video editing software for Ubuntu, if in deed there is any.

I would like to beable to add subtitles etc to some video I have shot.

Would be awesome if it could edit 1280X720 resolution footage.

Thanks in advance for any help, much appreciated.

---

### Post by cotcot on 2007-11-08
I am using Kdenlive, Kino (for capturing to edit in Cinelerra) and Cinelerra.  Kino is nice, but only single track.
You also have Pitivi, Lives, Avidemux. Any of these have there fans and their objectors. So best is to try them out. 

Cinelerra is able to deal the footage you want. The other I do not know. Please check the features on the home pages of the programs.

Subtitling is possible in almost all of them, but not always to the same extent and font quality. Banners and moving titles are possible in Kino and Cinelerra, maybe also some others. Best is to experiment it.

Cinelerra is clearly more powerful than the others.  The backside is a longer learning curve. But IMHO it is worth to learn it if you want more than putting scenes together with titles, transition effects and other effects. I appreciate Cinelerra for(zooming, panning, multiple tracks on the output, keyframes, sound adding, .... Cinelerra gets critics on its layout and user interface. If you take your time to learn it I do not see the reason for the critics.

---

### Post by UbuWu on 2007-11-08
I find Kdenlive the easiest to use. ([instal)]("apt:kdenlive")

---

### Post by wlc3069 on 2007-11-08
I use cinelerra, its a little harder to use than kino, and some others but it has many more features that are comparable to what i was using in windows xp (avid liquid)

---

### Post by netyire on 2007-11-09
Kdenlive will do what you want - plus its really easy to use. Give it a 10 minute learning curve :D you can get it in the repositories.

---

### Post by eye208 on 2007-11-09
I use Blender. It's probably the most versatile one because you can use its 3D render engine and compositing system to manipulate video footage in various ways, but it also has a steep learning curve. However, once you have mastered it you probably won't want to use anything else.

---

### Post by MepisReign on 2007-11-09
I would suggest Avidemux, its available on the repos. I  use it to process AVI files into DVD compatible mpgs, also there is a filter to add subtitles hard coded into the final video file. U should give it a try:popcorn:

Greetz

MepisReign

---

### Post by Qwerty_ on 2007-11-09
The problem I have with Kino is I cant seem to use AVI's in it it wants some kind of DV file and I have no idea what that is.

---

### Post by eye208 on 2007-11-12
Most video editing programs can't edit AVI directly. They may be able to import them, but editing is done in a different format anyway.

The reason for this is the way MPEG (and similar) compressed stream formats work. In compressed video, there's usually a keyframe, followed by a sequence of delta frames. Delta frames do not encode the entire screen content but only the differences from the previous frame. So in order to decode a given frame of the video you often have to go back in the stream to the previous keyframe and process all the intermittent delta frames, i.e. seeking a specific frame may be difficult and time-consuming. In order to cut video at a non-keyframe position, a new keyframe has to be inserted at the position of the cut. These things make delta-frame compressed video unsuitable for editing.

DV is a keyframe-only format, similar to MJPEG or HuffYUV. Many video editors can also work on sequences of individual images in PNG or JPEG format. For maximum quality you might even want to use a format that encodes color channels in 16bit instead of 8bit.

The bottom line is, you'll have to convert most AVI files into an editing-friendly format anyway. Some video editors may be able to do it for you, but you can always use FFMPEG or MEncoder to do it yourself.

---

### Post by Qwerty_ on 2007-11-12
Thanks for the explanation there eye208 I appreciate it.

---

### Post by morgan_greywolf on 2007-11-12
> **eye208 said:**
> I use Blender. It's probably the most versatile one because you can use its 3D render engine and compositing system to manipulate video footage in various ways, but it also has a steep learning curve. However, once you have mastered it you probably won't want to use anything else.

I currently use Blender for 3D modelling and rendering.  I knew it could do animation and video composition, but didn't know it could be used for general video editing.  Are there any tutorials you would recommend for using Blender as a general video editing tool?

---

### Post by carusoswi on 2007-11-12
> **eye208 said:**
> Most video editing programs can't edit AVI directly. They may be able to import them, but editing is done in a different format anyway.


Not certain where you got your information.  AVI is a digital video format.  Capture DV from a DV cam and .avi is what you will get - and it is much more editable than MPEG which is a compressed format used by DVD.  Shoot original footage onto a DVD cam, and you may find that you are limited in your ability to make frame accurate edits.

Caruso

---

### Post by MepisReign on 2007-11-12
OK, why we just point the person that asked for a video editing software in the right direction?. Again, I would suggest Avidemux since is very powerful and WILL handle avi files without major hassles. Give it a try and if you have further questions we will try to stick to point.

Regards,

MepisReign

---

### Post by eye208 on 2007-11-12
> **morgan_greywolf said:**
> Are there any tutorials you would recommend for using Blender as a general video editing tool?
[http://wiki.blender.org/index.php/Manual#Video_Sequence_Editing](http://wiki.blender.org/index.php/Manual#Video_Sequence_Editing)

Blender uses SDL for audio. To make audio work in Blender, you have to point SDL at the audio driver you are using. "export SDL_AUDIODRIVER=alsa" worked well for me, but there are other options such as "dma" or "esd" you may want to try depending on your setup.

> **carusoswi said:**
> Not certain where you got your information.  AVI is a digital video format.  Capture DV from a DV cam and .avi is what you will get - and it is much more editable than MPEG which is a compressed format used by DVD.
AVI is a container format that can handle almost anything, including MPEG. But it has a 2 GB file size limit which makes it unsuitable for professional purposes. I have not used Kino yet, but I guess it will handle the same formats as any other non-linear editing tool: Raw DV, Quicktime DV and OpenDML AVI.

However, it makes perfect sense to get rid of containers altogether and work on sequences of bitmap files instead. Most video editors support this method just fine, and there are some retouching tools that only work this way (e.g. CinePaint).

> Shoot original footage onto a DVD cam, and you may find that you are limited in your ability to make frame accurate edits.
It depends. MPEG-2 and MPEG-4 can be used in a keyframe-only ("intraframe") way which makes them just as editable as DV.

> **MepisReign said:**
> I would suggest Avidemux since is very powerful and WILL handle avi files without major hassles.
Avidemux is a nice transcoding tool, but I would not call it a video editor.

---

### Post by kayosiii on 2007-11-13
From the size you posted I am assuming you are using a HD Camera. It would be helpful to know what format that data captured is in (AFAIK HD is not standardised the way that miniDV was).

Cinelerra is designed as a HD Editing Program. You can use it with a renderfarm if you need more grunt. I generally find that it behaves best when working with uncompressed footage - but that takes up a LOT of disc space. H624 I think is the favoured codec for distributing HD content and one of the few that cinelerra does reliably.
I think you will find Cinelerra cabable if not as refined as the top commercial editors and a little bit tricky if you are not used to 3 point editing.

I also use open movie editior to convert files to uncompressed Quicktime which is what Cinelerra seems happiest with.

---

### Post by Qwerty_ on 2007-11-14
How do I install cinelerra sudo apt-get install did not work for me.

---

### Post by dad311 on 2007-11-14
This is how I installed Cinelerra last time.

[http://cvs.cinelerra.org/getting_cinelerra.php](http://cvs.cinelerra.org/getting_cinelerra.php)

---

### Post by bobbybobington on 2007-11-14
Kdenlive

Tried it, seemed like a reasonable interface, but it was so buggy I couldn't 

Pitivi

very promising, but currently you can't really do anything

Avidemux 
Can add effects etc... but when it comes to linking clips into a video with a sane interface it fails completely

---

### Post by Qwerty_ on 2007-11-15
Ta dad311 ill try that later this evening.

---

### Post by Qwerty_ on 2007-11-15
Excellent Cinelerra looks to be the exact program I was looking for. Thanks very much for your help.

Just a case of learning everything now.

---

### Post by dad311 on 2007-11-16
Make sure to read this while you are leaning....

[http://heroinewarrior.com/cinelerra/cinelerra.html](http://heroinewarrior.com/cinelerra/cinelerra.html)

Good luck!

---

