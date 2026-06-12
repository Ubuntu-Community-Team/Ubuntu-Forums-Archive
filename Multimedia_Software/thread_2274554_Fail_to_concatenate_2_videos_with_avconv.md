---
title: "Fail to concatenate 2 videos with avconv"
date: 2015-04-20
forum: Multimedia Software
---

### Post by damien20 on 2015-04-20
Hi,
 
I'm trying to concatenate 2 different files.
 
The first is a title image i generate with those commands:
[FONT=courier new]# I generate a 2 sec mute video
avconv -y -loop 1 -r 27.75 -i blank.png -vcodec h264 -t 00:00:02 -an output.avi
# And I had a blank sound
avconv -y -ar 44000 -b 320 -ac 2 -f  s16le -i /dev/zero  -i output.avi -shortest -c:v copy -c:a mp3 -b:a 320k output-2.avi[/FONT]
 
So finnally I have this file (avconv -i)
[FONT=courier new]    Stream #0.0: Video: h264 (High), yuv420p, 1920x1080, 27.75 fps, 27.75 tbr, 27.75 tbn, 55.50 tbc
    Stream #0.1: Audio: mp3, 44100 Hz, stereo, s16p, 320 kb/s[/FONT]
 
The second file is generated from a digital recorder. Here is all the detail on that file. I don't want to transform this file because, I will have to process many files
[FONT=courier new]    Stream #0.0: Video: h264 (High), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 27.75 fps, 30 tbr, 30 tbn, 60 tbc
    Stream #0.1: Audio: mp3, 44100 Hz, stereo, s16p, 320 kb/s

[/FONT]So it's not exactly the same setting. Tbr, tbn and tbc differ...
 
When I try to concatenate with :
[FONT=courier new]avconv -y -i "concat:output-2.avi|Recorder_2_Apr20_19-55-28.avi" -c copy final.avi[/FONT]
 
But I have some audio troubles.
When avconv is processing I have this error message :
[FONT=courier new]Non-monotonous DTS in output stream 0:0; previous: 392, current: 361; changing to 393. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:1; previous: 467, current: 424; changing to 468. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:1; previous: 468, current: 425; changing to 469. This may result in incorrect timestamps in the output file.[/FONT]
 
And the sound is destroyed and unsynchronised
 
Do you have an idea to solve this issue ?
 
Thanks in advance for your help
Best
Damien

---

### Post by Merrattic on 2015-04-20
Your answer is probably in the different settings for each video. As you have control over the creation of the first file, create it the same as the second.

To concat files you normally need to have files of the same type with the same settings

---

### Post by damien20 on 2015-04-21
Hi Merratic, 

Thanks for your reply
Sure, it's the problem... but the question is how to adjust it!

I've been googling about it
First the meaning:

[LIST]
[*][FONT=courier new]**tbn** = the time base in AVStream that has come from the container[/FONT]
[*][FONT=courier new]**tbc** = the time base in AVCodecContext for the codec used for a particular stream[/FONT]
[*][FONT=courier new]**tbr** = tbr is guessed from the video stream and is the value users want to see when they look for the video frame rate[/FONT]
[/LIST]
[FONT=courier new][FONT=arial]After, how to adjust it for the first video, is a good question. 
[/FONT][/FONT]
I have found this website with H264 options, but nothing about tbn, tbr and tbc...
[http://h264.code-shop.com/trac/wiki/Encoding](http://h264.code-shop.com/trac/wiki/Encoding)

[FONT=arial]I have also tried to reprocess the second video file. And I can concatenate. But it's a bad solution because I will have to process 8h of video a day...

[/FONT]So if you have any idea, it's welcome
Best
Damien

---

### Post by FakeOutdoorsman on 2015-04-22
You're not going to be able to use avconv to do this (at least in a sane way). Compared to ffmpeg it lacks the specific features for your requirements.

What is the content of blank.png? It it really just a blank, single color image?

Your post is kind of hard to read. Please use the code tag/button to format your commands and console outputs.

---

