---
title: "ffmpeg: Extract images from a video, but exclude duplicated frames"
date: 2024-08-28
forum: Multimedia Software
---

### Post by Paddy Landau on 2024-08-28
I have an interesting problem. I want to extract all of the images from a video, but omit all duplicated frames. As the video is a screencast, the vast majority of the images are duplicates, so eliminating duplicates is a major bonus.

The easiest way that I've found, but definitely not the most efficient, is:
```
ffmpeg -i video.webm images/image-%05d.jpg  # Extract all of the images
fdupes --delete --noprompt images/          # Delete all of the duplicates
```
In my test video file, ffmpeg produces 4,221 images, and fdupes reduces this to a mere 120 images, which is great!

A better way would be for ffmpeg not to save the duplicated images in the first place. Searching for an answer, I keep finding that I should use mpdecimate.
```
ffmpeg -i video.webm -vf mpdecimate image-%05d.jpg
```
mpdecimate comes with several options. I've tried an assortment of options, including none, but all of them produce output over 4,000 images! So, this option simply doesn't do what I want it to do.

I've read the description of mpdecimate in "man ffmpeg-filters", and I confess that I don't fully understand what it means.

Could you help me to figure this out, please?

*Side question:*

For greatest processing efficiency, should I be extracting into jpg or png (I've been using jpg)? I'm not worried about space used; only about speed of processing.

Thank you

---

### Post by TheFu on 2024-08-28
Why not just record at a lower frame rate?  There's no need for 30 or 25 fps when 5 will do just fine.  That would be my first change.  Then any processing would certainly be faster.  Heck, 1fps for a slide presentation is probably sufficient.

---

### Post by Paddy Landau on 2024-08-28
> **TheFu said:**
> Why not just record at a lower frame rate?
In this instance, I needed to catch something that briefly flashed on the screen, less than a second.

But in any case, I wouldn't know how to change the frame rate for a screencast. I'm using Gnome's built-in screen recorder (Ubuntu 22.04).
> **TheFu said:**
> 1fps for a slide presentation is probably sufficient.
Sure, but this isn't for a slide presentation.

---

### Post by TheFu on 2024-08-28
There's an fps filter or a -r (frame-rate) option for transcoding in ffmpeg. [https://trac.ffmpeg.org/wiki/ChangingFrameRate](https://trac.ffmpeg.org/wiki/ChangingFrameRate)
 Pick whatever frame rate is needed to get what you want.  Anything less than 25 fps would save space, right? 15, 10, 5, 2, 1, whatever.  

I use SSR [https://www.maartenbaert.be/simplescreenrecorder/](https://www.maartenbaert.be/simplescreenrecorder/) to capture stuff on the screen if I can't capture it with a hardware video recorder.  It's in the repos.  That's just me.  I don't think it works with Wayland, but IDK.

---

### Post by Paddy Landau on 2024-08-28
> **TheFu said:**
> Anything less than 25 fps would save space, right?
As mentioned in my original post, I'm not worried about space used.

What I'm really after is searching for a specific frame within the video, which is hard to find because the flash is so quick, and I want to keep that one frame as an image. Cutting the extracted images down to unique frames will make it massively easier to find.

I don't want to change the original video at all; I want to keep it as is.

However, this also intrigues me as to how to go about extracting unique images efficiently. I already have a solution, just horribly inefficient. This has become not about just fixing one specific problem that I have right now, but also trying to learn more about ffmpeg (in this case, mpdecimate). ffmpeg is an awesome utility, so learning more about it is always interesting and potentially useful.

---

### Post by TheFu on 2024-08-28
If you just want 1 frame, why not use frame accurate video editing software after using mpdecimate to remove extra frames?
Interesting problem.  While I don't have any use for it today, I can see where it would have made life easier in the past and perhaps in the next few months I'll have a use.  I mux 2 video sources together for some sports. 1 has all the stats and an overview of the different plays, while the other has the expected game play.  The sources are different for each.

---

### Post by Paddy Landau on 2024-08-28
> **TheFu said:**
> If you just want 1 frame, why not use frame accurate video editing software after using mpdecimate to remove extra frames?
I get the unique frames, and then quickly scroll through them (using Gnome Image Viewer, i.e. eog). That's going to be easier than learning a new video-editing package.

Still, the original question remains: I'd like to know how to use mpdecimate properly. I haven't managed to get my head around it.

---

### Post by qyot27 on 2024-08-28
Duplicate frame detection and removal have been fairly well established in the AviSynth and VapourSynth side of things for a long time, because it's a core component of creating variable framerate content (it matters in some cases).  Glancing at the ffmpeg-filters documentation, it doesn't look too dissimilar from the parameters used by DeDup ([http://avisynth.nl/index.php/DeDup](http://avisynth.nl/index.php/DeDup)).  It took me less than an hour to get DeDup to run natively with the local AviSynth+ install.  It can then be piped into FFmpeg or (if you've built FFmpeg with --enable-avisynth) opened directly in FFmpeg and output to whatever your choice is - png, jpg, ffv1, etc.  Merging the timecodes back in to achieve real VFR content would be optional and hinge mostly on whether you actually care to watch the output with the duplicates removed.  mkvtoolnix can add the timecodes back in, and I wouldn't be surprised if there's some way FFmpeg might also be able to while encoding, I just haven't looked that deeply into it.

On a test video that I grabbed, an ~22-minute animated TV episode was reduced from 39329 frames, to 35221 frames using the example provided on the Wiki page I linked to:
```
DeDup(threshold=0.3, maxcopies=10, maxdrops=3, log="dups.txt", times="times.txt")
```

If, however, I tweak the parameters a bit to
```
DeDup(threshold=3, maxcopies=20, maxdrops=20, log="dups.txt", times="times.txt")
```

The result is 15909 frames.  In-script, you could maximize the duplicate detection by smoothing or warpsharpening the footage before using DeDup, to minimize or eliminate artifacts that could cause the detection to leave too many frames behind.  On simple content, this may or may not be as necessary as it would be for things like live action or animation.


As before when I've mentioned AviSynth, though, it's not in the repositories, so it'd require building it yourself.  It's not difficult, but there are several parts involved.

---

### Post by Paddy Landau on 2024-08-29
> **qyot27 said:**
> Duplicate frame detection and removal have been fairly well established in the AviSynth and VapourSynth side of things for a long time…
Thank you; that's interesting, and certainly something to note for future.

The thing is that I don't want to change the video itself; I only want to extract the non-duplicated images, for separate use as images not as video.

---

### Post by qyot27 on 2024-08-29
> **Paddy Landau said:**
> Thank you; that's interesting, and certainly something to note for future.

The thing is that I don't want to change the video itself; I only want to extract the non-duplicated images, for separate use as images not as video.
That's what I was explaining.  AviSynth is a frameserver; you write a text file with the operations to perform, and the frameserver performs those operations in memory without touching the original file or creating large intermediate videos/images.  The client program (FFmpeg, mpv, x264, etc.) treats the text file as if it were a video with those changes already applied.  So AviSynth would present the video to FFmpeg with the duplicates removed, and FFmpeg could then output the image sequence of only the non-dupes.

---

### Post by Paddy Landau on 2024-08-29
> **qyot27 said:**
> So AviSynth would present the video to FFmpeg with the duplicates removed, and FFmpeg could then output the image sequence of only the non-dupes.
Oh, I see! I didn't get that. Thank you.

---

