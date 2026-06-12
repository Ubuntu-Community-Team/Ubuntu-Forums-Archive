---
title: "mencoder pipe into ffmpeg"
date: 2012-08-04
forum: Multimedia Software
---

### Post by Valpskott on 2012-08-04
What I need is for this to be properly piped

```
mencoder *.avi | ffmpeg -f mp4 -vcodec mpeg4 -qscale 1 -s 1280x720 -pix_fmt yuv420p -qmin 1 -intra -acodec libmp3lame -ab 160k -ar 44100 -ac 2 Video-A.mov
```

Or for mencoder to output near lossless mpeg4



Backstory:
I do a lot of video rendering by scripts for my youtube channel. Due to issues with sync I have a script with a section like this.

```
mencoder -oac copy -ovc copy -o Video-A.mov *.avi

ffmpeg -i Video-A.mov -f mp4 -vcodec mpeg4 -qscale 1 -s 1280x720 -pix_fmt yuv420p -qmin 1 -intra -acodec libmp3lame -ab 160k -ar 44100 -ac 2 Video-B.mov
```

then does several of these

```
ffmpeg -ss 00:00:00 -t 00:12:05 -i Video-B.mov -vcodec copy -acodec copy "Video-1.mov"
```

With different starting (-ss) times and different names. Basically it cuts things up into episodes of 12 minutes and 5 seconds.

Now, I find it would be more efficient if mencoder could transcode the video into lossless mpeg4 from the start. Or pipe it into ffmpeg so ffmpeg takes care of the encoding. Keeping the original encoding makes things go out of sync, the later episodes gets lots of complaints.

I've googled for a solution and also gone through the man pages of mencoder.

---

