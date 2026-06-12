---
title: "mp3 to ogg, benefits or dangers?"
date: 2011-09-20
forum: Multimedia Software
---

### Post by Bryant.GhostInTheMachine on 2011-09-20
Alrighty, so here's the problem:

I have a decent size collection of .mp3 files in my music folder, all of which were originally AAC which I then converted after transferring them to my ubuntu comp. They were converted using sound converter (it's in the repos) using the VBR and 'Insanely High Quality' settings. Recently, however, I have been contemplating converting these mp3s into .ogg format, based on some tidbits I found online. Apparently, if I convert these to .ogg files with the same quality settings it will produce a smaller files size while retaining the quality of the original mp3. My other reason for converting them is that the Ogg format is open-source, and I like open source stuff :D.

My main concern is whether this could cause a decrease in quality or create hiccups in the audio file after its been converted. Also, is the claim of a smaller file size accurate? I know that mp3 is a decent format and that it would be less of an issue if I just left them alone, but I'd like to convert them to .ogg anyway for the aforementioned reasons.

---

### Post by dniMretsaM on 2011-09-20
> **Bryant.GhostInTheMachine said:**
> Alrighty, so here's the problem:

I have a decent size collection of .mp3 files in my music folder, all of which were originally AAC which I then converted after transferring them to my ubuntu comp. They were converted using sound converter (it's in the repos) using the VBR and 'Insanely High Quality' settings. Recently, however, I have been contemplating converting these mp3s into .ogg format, based on some tidbits I found online. Apparently, if I convert these to .ogg files with the same quality settings it will produce a smaller files size while retaining the quality of the original mp3. My other reason for converting them is that the Ogg format is open-source, and I like open source stuff :D.

My main concern is whether this could cause a decrease in quality or create hiccups in the audio file after its been converted. Also, is the claim of a smaller file size accurate? I know that mp3 is a decent format and that it would be less of an issue if I just left them alone, but I'd like to convert them to .ogg anyway for the aforementioned reasons.

Would it decrease the quality? Yes, slightly. But since The MP3 tracks are such high quality, the affects would be barely noticeable. I have converted files with much lower quality (medium/high) and still find it barely noticeable, if at all. And yes, filesizez will be smaller. Ogg Vorbis is also more computationally efficient, so your computer will use less power playing them.

---

### Post by andrew.46 on 2011-09-21
If you were interested in putting 'icing on the cake' you could consider using the AoTuV version of libvorbis, there is a guide on these Forums that would be worth hunting out...

---

### Post by dniMretsaM on 2011-09-21
[LEFT]__[Here's a link.](http://ubuntuforums.org/showthread.php?t=1137670)
__[/LEFT]

---

### Post by andrew.46 on 2011-09-21
> **dniMretsaM said:**
> [LEFT]__[Here's a link.](http://ubuntuforums.org/showthread.php?t=1137670)
__[/LEFT]

And that AoTuv patch that I put together is still available, as detailed in that particular thread :)

---

### Post by jmate24 on 2011-09-21
it does create some hickups unless you convert down to a smaller bitrate. the smaller the bitrate the smaller the filesize and try a test .mp3 to convert to .ogg i like to use soundconverter and i shrink my .mp3s down to 64Kbps and it takes up only 1/5th the space of those massive 320Kbps .mp3s.
i also heard that a famous singer commented that you should not convert or compress your audio files but leave them lossless for better sound quality but if you rip to .flac then you are looking at 250-900MB or/so of cd size.

also if you want a great website for free .mp3s then check out [http://www.jamendo.com/en/]("http://www.jamendo.com/en/")

---

### Post by dniMretsaM on 2011-09-21
> **jmate24 said:**
> it does create some hickups unless you convert down to a smaller bitrate.

Really? I have never noticed this.

---

### Post by Bryant.GhostInTheMachine on 2011-11-03
I've been on Jamendo before, and it is awesome in the extreme. :)
And thank you all for the excellent answers.

Just a secondary question, but I was considering doing this with my video files too. I have a large collection of movies and two seasons of House MD ripped to my computer and I was wondering if there's a more efficient format to convert them to besides .avi It would take geological ages to convert all that video in one go, but I figured I might as well if it will save disk space and processor time in the long run.

---

### Post by FakeOutdoorsman on 2011-11-04
> **Bryant.GhostInTheMachine said:**
> Just a secondary question, but I was considering doing this with my video files too...but I figured I might as well if it will save disk space and processor time in the long run.

Deciding to do this depends on what your input files are, the encoder you decide to use, and the encoder settings you use. Note that lossy encoders always decrease the output quality. However, it may do such a good job that you may not notice. You can use FFmpeg to show us detailed information about one of your inputs:
```
ffmpeg -i input.avi
```
If the inputs are from some old, inefficient encoder then you may consider re-encoding them if disc space is a priority. I'm not sure what you mean by "processor time", but video encoding is very processor intensive, and not all formats decode with equal processing power (this can also depend on your encoding settings).

---

### Post by sanderd17 on 2011-11-04
If you are into FOSS formats, there are two main options for lossy video encoding: ogv (the video variant of ogg) and webm (bought by google and released as FOSS). 

WebM is making great progress (since google also uses it for Youtube and Chrome), so it's definitely worth to take a look at.

---

### Post by Lars Noodén on 2011-11-04
Don't transcode from lossy to lossy.  To get the first lossy format some of the file is discarded.  To go to the second lossy format, you lose further data, the effect is multiplied.  If you're going to rip to MP3, leave it as MP3.  If you're going to rip to ogg, leave it as ogg.  But you can't go between them.  Try it with one file and hear the difference.

---

