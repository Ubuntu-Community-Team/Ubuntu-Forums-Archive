---
title: "How to reduce screencast file sizes?"
date: 2012-07-17
forum: Multimedia Software
---

### Post by wayover13 on 2012-07-17
I've been using Linux screencasting tools for the last year or so to record and post lectures for an on-line course I teach. It's worked fairly well after some initial fiddling I did so as to get various settings right. I've used primarily recordmydesktop from the command line for this, since I'm a command-line type-o-guy. I've also fiddled a bit with using ffmpeg's x11grab--which looks promising, except that, unlike recordmydesktop, you can't pause, then resume, the recording.

I've run into a bit of a glitch recently in that I upgraded major hardware in my system which has the effect, although just about everything's the same as far as the operating system is concerned, of doubling the final size of my screencasts. So, screencasts I make that once came in at about 2 MB per minute are now coming out to be about 4 MB per minute. This creates some problems with my course's web hosting site, which has file-size limits that are now frequently being exceeded by the size of my screencast lecture files--which can be up to one hour long.

I'm a bit mystified as to why the size of these files has doubled using the new hardware, but rather than attempting to solve that conundrum, I'd rather just try and figure out how I can make these files smaller. I'd like to ask for tips for doing that in this thread.

I've tried feeding various parameters that do things like degrade video and/or audio quality to recordmydesktop and ffmpeg in my attempts at reducing the final size of my screencast files, but I've so far been unable to reduce the size of my recordings to only about 4 MB per minute. I've also tried reencoding the files with ffmpeg, but that's resulted only in a slight reduction in file size.

For reference, here are some of the commands I've used for screencasting:

```
ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -r 15 -s 830x660 -i :0.0+227,130 -acodec libvorbis -ab 320000 -vcodec libvpx output.webm
```

```
ffmpeg -f alsa -ac 2 -ab 32k -i hw:0,0 -f x11grab -r 15 -s 830x660 -minrate 512k -i :0.0+227,130 -acodec libmp3lame -vcodec flv output.flv
```

```
recordmydesktop -x 235 -y 145 --width 810 --height 630 --device hw:0,0 --pause-shortcut Control+p --no-cursor --v_quality 12 -o out.ogv
```

If anyone has any tips for reducing the size of the output files I get using commands like these, whether that involves alternative command-line switches or ways of reencoding the finished files, please offer them. I'm hoping I can once again get my screencast files to come out at about 2 MB per minute, as that will result in files much better suited to my upload limits.

Thanks,
James

PS See [http://ubuntuforums.org/showthread.php?t=1954167](http://ubuntuforums.org/showthread.php?t=1954167) for an initial post about this topic that I made some months ago.

---

### Post by ron999 on 2012-07-17
The screencasting thread is here ---> [http://ubuntuforums.org/showthread.php?t=1392026]("http://ubuntuforums.org/showthread.php?t=1392026")

The method used in the thread is to capture '**lossless**' then convert it.

So you would modify your command to use [COLOR="Red"]libx264 crf 0[/COLOR] for video and [COLOR="Red"]pcm_16le[/COLOR] (or flac) for audio.
Like this:-
```
ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -r 15 -s 830x660 -i :0.0+227,130 [COLOR="Red"]-acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0[/COLOR] output.mkv
```

Then convert it to a smaller file with a command something like this:-
```
ffmpeg -i output.mkv -vcodec libx264 -preset medium -crf 23 -acodec libmp3lame -ab 64k final.mkv
```

---

### Post by wayover13 on 2012-07-17
Thanks for pointing out that thread, ron999--a lot of interesting information there. I really like the ffmpeg method although it does lack some of the features recordmydesktop has and which have proved pretty indispensable for my needs (pause, showing a frame around the captured area). I see from the thread that there are work-alikes for ffmpeg, so I'm in for more experimentation with it.

I should mention that the system through which my course is administered works better with flv and ogv formats (not sure about webm, but I'm anxious to try it): when any other format is used, rather than showing the video in the embedded player, the site offers a download link for the file, which I don't want. That means that, using ffmpeg as you've suggested (lossless format), the extra step of converting the file will be needed--one other strike against it versus recordmydesktop.

Anyway, the crucial factor is going to be what sorts of file sizes I get after the conversion: if they're the same as those I get using recordmydesktop (ca. 4 MB per minute), then there's no point in using ffmpeg for this. I'll post again after further experimentation.

James

---

### Post by wayover13 on 2012-07-17
There seems to be no advantage, using ffmpeg, to recording in lossless, then converting to lossy, in terms of file size. I come up with roughly the same size file whether I record it initially as an .flv or an .ogv or if I record, then transcode it. They both come in at around 4 MB per minute, which is too big for my purposes. The webm conversion worked best in terms of file size reduction: it was just under 3 MB per minute. That's pretty close to acceptable. But the test webm file I uploaded to my course site would not play through the embedded player, rather presenting itself as a download link. So it does look as though I'm stuck with .flv or .ogv formats: but how to get them down to about 2 MB per minute, as they used to come out on the older hardware I had in this computer?

I'll scrutinize that thread a bit more to see if it contains any information relevant to my aim of reducing file size.

Thanks,
James

---

### Post by wayover13 on 2012-07-17
It's kinda late now, but I did find some information in that thread that *may* help me to reduce file sizes. First, I could try the conversion-to-flv command cited in that thread: ```
ffmpeg -i output.mkv -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre slow -wpredp 0 -crf 22 -threads 0 our-final-product.flv
``` rather than the less sophisticated one I used. Doubt that'll matter but it's worth a try. Second, and more promising, use of the -qscale option in ffmpeg is discussed: > To have a constant quality (but a variable bitrate), use the option '-qscale n' when 'n' is between 1 (excellent quality) and 31 (worst quality). I'm not sure if this applies to re-encoding or not, but that looks like something worth trying. Anyway, it's late enough here that I'll have to have another go at this tomorrow.

James

---

### Post by wayover13 on 2012-07-18
Good news: the command ```
ffmpeg -i output.mkv -acodec aac -strict experimental -ab 128k -ac 2 -vcodec libx264 -vpre slow -wpredp 0 -crf 22 -threads 0 output.flv
``` re-encoded the one-minute, 14 MB, lossless test file I had recorded into an flv file that was exactly 2 MB. Looks like I now have a method for re-encoding, to a more congenial size and format, lecture files that were recorded using ffmpeg.

Thanks,
James

PS Using -acodec libfaac--one of the switches found in the linked thread--was giving me errors on this modified 12.04 system. Some internet searching revealed that one workaround is to replace that with the switch -acodec aac -strict experimental, which worked for me.

---

### Post by wayover13 on 2012-07-19
I've tested and can now confirm that the same command I used to shrink the lossless .mkv file into an .flv file also works on the .ogv files that recordmydesktop outputs. And those files, like the lossless ones, shrink to considerably smaller sizes (to about 1/3 the size of the .ogv files that recordmydesktop outputs--from about 4 MB per minute on this machine to about 1.2 MB per minute) when that's done. The command looks just like the one used on the .mkv file except that the file name is replaced by the name of the .ogv file that needs shrinking: ```
ffmpeg -i output.ogv -acodec aac -strict experimental -ab 128k -ac 2 -vcodec libx264 -vpre slow -wpredp 0 -crf 22 -threads 0 output.flv
```

This looks like the resolution to my issues, though I will need to start using the --on-the-fly-encoding switch when I record these files with recordmydesktop (so as to reduce the encoding/re-encoding time taken by the two processes to more reasonable limits).

Thanks,
James

---

### Post by FakeOutdoorsman on 2012-07-20
> **wayover13 said:**
> I've run into a bit of a glitch recently in that I upgraded major hardware in my system which has the effect [...] of doubling the final size of my screencasts.

What hardware did you change? I don't see how this would affect file size.

> **wayover13 said:**
> I should mention that the system through which my course is administered works better with flv
FLV (the container format) can contain H.264 as you've already discovered (just pointing this out for any other potential readers).

> **wayover13 said:**
> That means that, using ffmpeg as you've suggested (lossless format), the extra step of converting the file will be needed--one other strike against it versus recordmydesktop.
The reason lossless is used is because it should offer faster capturing and should allow it to reach the desired frame rate and therefore result in a smoother screencast. This helps avoid a bottleneck of capturing and performing a CPU intensive encode at the same time. Also, using the lossless step should not dictate what the output format is. You can go from the lossless output to anything ffmpeg can encode to.

> **wayover13 said:**
> Second, and more promising, use of the -qscale option in ffmpeg is discussed:  I'm not sure if this applies to re-encoding or not, but that looks like something worth trying.
*-qscale* should not be used with libx264. Use *-crf* instead.

> **wayover13 said:**
> I've tested and can now confirm that the same command I used to shrink the lossless .mkv file into an .flv file also works on the .ogv files that recordmydesktop outputs.
I'm not very familiar with recordmydesktop, but I recommend using the highest quality output that you can achieve from recordmydesktop since it appears you are going to be re-encoding its output anyway.

> **wayover13 said:**
> The command looks just like the one used on the .mkv file except that the file name is replaced by the name of the .ogv file that needs shrinking: ```
ffmpeg -i output.ogv -acodec aac -strict experimental -ab 128k -ac 2 -vcodec libx264 -vpre slow -wpredp 0 -crf 22 -threads 0 output.flv
```

You can drop the *-wpredp 0*. It was used for a bug in a version of Adobe Flash Player that I assume few people use now.

Note that if you are targeting a specific output file size then a two-pass encode using *-b:v* is often recommended. bitrate = desired output file size / duration. [Example here](http://ubuntuforums.org/showpost.php?p=10563566&postcount=8) (older syntax but you'll get the idea). *-crf* is usually used when you are targeting a specific output quality and file size is of less importance (and is what I use 99% of the time). See [this post](ubuntuforums.org/showpost.php?p=12118229&postcount=8) for an explanation on what crf and preset to use.

---

