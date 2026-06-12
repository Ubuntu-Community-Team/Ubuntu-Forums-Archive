---
title: "Easiest way to embed subtitles?"
date: 2011-01-08
forum: Multimedia Software
---

### Post by ULAMSS5 on 2011-01-08
Hi everyone, 

What I need done: embed, and convert 720p videos in (.mkv) format, with (.SSA) subtitles already packed into the video into 240x320 .mp4 with the subtitles embedded into the .mp4

What I tried: Googling around, my best lead so far is using mencoder and mplayer, however the installation/setup is just too tough for me. when i read through the readme and installation guides, i can't even find any place where it teaches me how to install, what to download(besides the skins, codecs and binaries). after installing with synaptic manager, i can't find it anywhere.

what alternatives do i have?(or is there a newb-friendly guide to installing mplayer/encoder?)

---

### Post by BicyclerBoy on 2011-01-08
Mencoder is part of mplayer.
I believe it is not really required as mplayer does it all.

[http://www.mplayerhq.hu/design7/documentation.html](http://www.mplayerhq.hu/design7/documentation.html)

Another app that could do what you want & better is ffmpeg.
[http://www.ffmpeg.org/documentation.html](http://www.ffmpeg.org/documentation.html)
[http://rodrigopolo.com/ffmpeg/cheats.html](http://rodrigopolo.com/ffmpeg/cheats.html)
[http://howto-pages.org/ffmpeg](http://howto-pages.org/ffmpeg)
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Are you trying to render the subtitles into the video or just copy them into the output container ?

The latter should be easy (famous last words)..

---

### Post by ULAMSS5 on 2011-01-09
Thanks for the suggestion. I am not sure what your last question means, but basically i want to merge the subtitles INTO the video permanently(y'know, like it's no longer listed as an option under the video track, but the subs are part of the video file itself), so that the subtitles will show when i convert the video into mp4. If i do not embed the subtitles, after conversions the subtitles will not show at all.

I have realised the this SVN they keep talking about is important in downloading and installing, which software should i get to use SVN?

---

### Post by BicyclerBoy on 2011-01-09
My last question was do you want to render the subtitles into the video itself.
Permanently in the video image..Internal hard subtitled.
And I think you do.

Embedded would be same as they are .. another stream in the file (video, audio, subtitles)
Internal pre-rendered separate stream.

After the transcoding the subtitles can still remain & be used so long as the media player can use them..

I'm doubting ffmpeg can hard render the subtitles from googling..but it can copy them while transcoding..

Maybe you should check out HandBrake.. I think it could be ideal.

SVN & git are both packages in the std ubuntu repos..

---

### Post by I'mGeorge on 2011-01-09
you can easily embed subtitles using avidemux. I found this you tube tutorial, check it out [http://www.youtube.com/watch?v=mNt6mEQ658s](http://www.youtube.com/watch?v=mNt6mEQ658s)  It's really easy and intuitive

---

### Post by ULAMSS5 on 2011-01-10
Wow this can be done on windows too? Thanks for the suggestion! I'll go tinker around with it.

---

### Post by I'mGeorge on 2011-01-10
> **ULAMSS5 said:**
> Wow this can be done on windows too? Thanks for the suggestion! I'll go tinker around with it.

yeah avidemux it's available for windows and linux. In windows, being multimedia oriented, I believe you could find more programs to achieve that.

---

