---
title: "FFMPEG Calculating Aspect Ratio"
date: 2011-03-15
forum: Multimedia Software
---

### Post by Alan James on 2011-03-15
I have several videos (around 50) of varying resolutions aspect and varying aspect ratios that all need to be down converted to be playable on iOS and Android. Some videos are 4x3 some are 16x9 and some are 2.35x1. I want to write a script to convert all of these to a 360P version in one go. That means the 4x3 will be 480x360 the 16x9 will be 640x360 and the 2.35 will be 640x272.

Is there a feature in FFMPEG that will automatically do the calculations for me?

---

### Post by FakeOutdoorsman on 2011-03-15
You could use the scale filter. Unfortunately you would have to compile FFmpeg because the repository version currently does not have any filter support. Fortunately compiling is fairly easy:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

(Note that there is some turmoil in FFmpeg-land right now and the Git repository in the guide may not be up to date)

Example:
```
ffmpeg -i input -vcodec libx264 -vpre medium -vpre ipod640 -vf scale=640:-1 -threads 0 -acodec libfaac -aq 100 output.mp4
```

The scale filter, with the *-1* value, can automatically determine the correct width or height and keep the aspect ratio. It doesn't always work however (with libx264) if the value interpolated by *-1* is not an even number.

You'll probably have to do some bash scripting to automatically determine what the output width should be depending on the input. Or you could manually sort the sizes by directory and then run a for loop with the FFmpeg command:
```
for f in *.avi; do ffmpeg -i "$f" -vcodec libx264 -vpre medium -vpre ipod640 -vf scale=640:-1 -threads 0 -acodec libfaac -aq 100 "${f%.avi}.mp4"; done
```

I would make a fancy bash script if I knew I would be doing this often and if my levels of nerd cred were getting low.

---

### Post by Alan James on 2011-03-15
Thanks. After posting this I found another thread where this question was asked and you had answered it. That is exactly what I needed.

---

### Post by Alan James on 2011-03-15
Looks like I am getting that problem you mentioned. The height of some of my videos isn't divisible by 2. How can I correct for this?

---

### Post by FakeOutdoorsman on 2011-03-15
You can manually set it, as in *-vf scale=640:360*, or your script can get the width from the input and a conditional statement could be used to apply the proper FFmpeg command. Another option is to use an encoder (other than libx264) than can handle odd output sizes.

---

### Post by Alan James on 2011-03-16
Is there a way of getting FFMPEG to round to the nearest even number? I know how to write a script to calculate the height but, that seems a little convoluted.

---

### Post by FakeOutdoorsman on 2011-03-16
Not yet. I wanted to submit this as a feature request (since this comes up once in a while and would be useful to me too), but the bug tracker appears to be in limbo right now.  I did talk to Stefano, the main filter developer, and he likes the idea of an option in the scale filter to auto-round to an even number. He added it to his todo list.

---

### Post by Alan James on 2011-03-16
I just e-mailed Michael Niedermayer with this idea as well. I'm not sure if he is the best person to ask, but the e-mail is already sent.

It would be a very useful feature. I might even start using FFMPEG as a large part of my workflow if this feature were to be added. Thanks for the help.

---

### Post by FakeOutdoorsman on 2011-03-16
If you really wanted to get this feature implemented you could [hire a FFmpeg developer](http://ffmpeg.org/consulting.html) to complete it. It's a good way to support the project especially if you are using it for your business and need this for your workflow.

---

### Post by Alan James on 2011-03-16
I would need to approve that through my boss and higher ups. They currently believe Apple software is the only software that should ever be used for video work, so I am fighting an uphill battle with them. I am going to take a look at the source code myself and figure out if I can impliment the code over this weekend. I doubt I can, but it will be a learning experience.

---

### Post by FakeOutdoorsman on 2011-03-16
They sound like Apple's type of customer. Seems like you'll be doing a lot of point and click encoding. Good luck.

You might be interested in:
[[FFmpeg-devel] [Patch] Scale filter should use multiples of 2](http://lists.mplayerhq.hu/pipermail/ffmpeg-devel/2010-June/091764.html)

---

### Post by Alan James on 2011-03-17
Yes, I do very little command line work. But I can't blame them, they are just being drawn in by marketing. And I can't even blame that because I am a video editor who works at a marketing company. I understand the thought but its still frustrating.

Anyway, I had actually just posted that link in this message and now I am editing this post because you beat me to it. I will try to get that code to work.

---

### Post by Alan James on 2011-03-17
Over lunch I added that patch, recompiled and ran it. It works great! I'm getting some audio errors but I have fixed most of those by using the experimental aac codec included with FFMPEG instead of libfaac.

Thank you for the help.

---

### Post by FakeOutdoorsman on 2011-03-17
Glad it's working for you. What were the audio errors?

I never tested the patch and it was never committed to FFmpeg. If I remember I'll post to this thread if this feature officially gets added anytime soon.

---

### Post by Alan James on 2011-03-17
The audio errors weren't caused by the patch. They were there before.

There were blips in the audio at random spots. Sometimes it would drop the audio completely.

The problems I'm still having are only when converting a video that contains one audio track, aka mono sound. FFMPEG just stops and won't do anything. The render has to be cancelled and rendered using different settings. I'm thinking of starting a thread for that, because we would we getting off topic if we discuss it in this one.

---

### Post by SeijiSensei on 2011-03-17
> **Alan James said:**
> Is there a way of getting FFMPEG to round to the nearest even number? I know how to write a script to calculate the height but, that seems a little convoluted.

As I recall, [H.264 prefers that the dimensions be divisible by 16]("http://forums.animesuki.com/showthread.php?t=48116").  That's why you see a lot of H.264 16:9 files that are 704x400 rather than 704x396 which is the mathematically correct resolution for 16:9.

---

### Post by FakeOutdoorsman on 2011-03-17
The warning was removed from x264 because it caused unnecessary confusion. It wasn't as important as the message made people believe.

---

### Post by Alan James on 2011-03-17
> As I recall, H.264 prefers that the dimensions be divisible by 16. That's why you see a lot of H.264 16:9 files that are 704x400 rather than 704x396 which is the mathematically correct resolution for 16:9.

I have found no problems with rounding to 2.

I have another question that is in line with Calculating Aspect Ratio. Within a bash script how can I get the width and height of the video for use in manually calculating the aspect ratio instead of adding this patch? I'm interested because it might help me with other code in the future and users that don't want to patch and compile might be interested because they could use it instead of the patch.

---

### Post by FakeOutdoorsman on 2011-03-17
You could adapt this:
```
ffmpeg -i input 2>&1 | awk '/Video/{print $7}' | sed 's/,//'
```

---

### Post by Alan James on 2011-03-20
This doesn't seem to work for all the videos I am working with. FFMPEG prints out different information for different codecs.

It works here

```
Stream #0.1(eng): Video: h264 (Main), yuv420p, 1920x816, 9914 kb/s, 23.98 fps, 23.98 tbr, 2997 tbn, 5994 tbc
```

But not here

```
Stream #0.0(eng): Video: dvvideo, yuv411p, 720x480 [PAR 8:9 DAR 4:3], 23016 kb/s, PAR 10:11 DAR 15:11, 23.98 fps, 23.98 tbr, 23976 tbn, 29.97 tbc
```

Any ideas how to get this working?

---

### Post by hatsch on 2011-03-21
i use this in a script to get the height and the width of the different videos.

```
WIDTH=$(ffprobe -show_streams $1 2>/dev/null | grep "width=" | cut -d'=' -f2)
HEIGHT=$(ffprobe -show_streams $1 2>/dev/null | grep "height=" | cut -d'=' -f2)
```

the rest of my script isn't really working for all szenarios, so i am searching for a better solution.

i found that piece of pseudo code that should do the math for calculating the correct width and height. but i haven't integrated that into my script yet.

> aspect_ratio_of_display = width_of_display / height_of_display
aspect_ratio_of_video = width_of_video / height_of_video
if aspect_ratio_of_video > aspect_ratio_of_display
then height = (height_of_video / aspect_ratio_of_video) and width = width_of_display
else width = (height_of_display x aspect_ratio_of_video) and height = height_of_display
[http://www.frasq.org/en/transcoding-an-audio-or-a-video-file](http://www.frasq.org/en/transcoding-an-audio-or-a-video-file)

---

### Post by Alan James on 2011-03-21
Awesome that worked. I'm trying to now use that information to determine multiple resolution outputs, 360P 480P, 720P etc. I can't seem to get that perfect, but this is a start.

What part of your script do you need help with?

---

### Post by hatsch on 2011-03-21
**UPDATE**
i improved the resolution detection. i assumed that no video will have a smaller aspect ratio than 4:3 (1.3333)
and i use [melt]("http://mltframework.org") for encoding, because i want more advanced things like logo overlay, timer,.. on the video
ffmpeg, x264 and melt are compiled with the melted [installer script]("http://www.mltframework.org/twiki/bin/view/MLT/BuildScripts").

```

#!/bin/bash
#$1 input file
#$2 output file
#


WIDTH=640
HEIGHT=480

P_WIDTH=$(ffprobe -show_streams $1 2>/dev/null | grep "width=" | cut -d'=' -f2)
P_HEIGHT=$(ffprobe -show_streams $1 2>/dev/null | grep "height=" | cut -d'=' -f2)

P_ASPECT=$(echo "$P_WIDTH / $P_HEIGHT" |bc -l)
echo "PIXEL:   $P_WIDTH / $P_HEIGHT = $P_ASPECT"
DAR=$(ffmpeg -i $1 / 2>&1 | sed -e '/DAR/!d; s/^.*DAR \([0-9]*:[0-9]*\).*/\1/' | sed 's/\:/\//')
DR=$(echo "aspect=@$DAR")
if [ $DAR ]
 then
        D_WIDTH=$(echo $DAR |cut -d'/' -f1)
        D_HEIGHT=$(echo $DAR |cut -d'/' -f2)
        D_ASPECT=$(echo "$D_WIDTH / $D_HEIGHT" |bc -l)
        echo "DISPLAY: $D_WIDTH / $D_HEIGHT = $D_ASPECT"

        HEIGHT=$(echo "$WIDTH / $D_WIDTH" | bc -l)
        HEIGHT=$(echo "$HEIGHT * $D_HEIGHT" |bc -l)
        HEIGHT=${HEIGHT/\.*}
        echo "$WIDTH x $HEIGHT"

 else
        HEIGHT=$(echo "$WIDTH/$P_ASPECT" |bc -l)
        HEIGHT=${HEIGHT/\.*}
        echo $HEIGHT
fi



/home/hatsch/melted/current/bin/melt $1  -consumer avformat:$2.mp4 s=640x$HEIGHT progressive=1 acodec=aac ab=128k vcodec=libx264 b=800k flags=+loop cmp=+chroma partitions=+parti8x8+parti4x4+partp8x8+partb8x8 me_method=umh subq=7 me_range=16 g=250 keyint_min=25 sc_threshold=40 i_qfactor=0.71 qcomp=0.6 qmin=10 qmax=51 qdiff=4 directpred=1 trellis=1 coder=0 bf=0 refs=3 flags2=-wpred-dct8x8 level=30 maxrate=10000k bufsize=10000k wpredp=0 $DR

#indexing for pseudo streaming
qt-faststart $2.mp4 $2
rm $2.mp4


```

---

