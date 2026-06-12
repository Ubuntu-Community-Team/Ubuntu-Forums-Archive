---
title: "How to append .avi? Standard tips to join .avi files not working"
date: 2009-05-23
forum: Multimedia Software
---

### Post by wmgcf on 2009-05-23
Wow, video is tough to work with!

I have about 10 .avi files recoded on a flip video camera. I need to join them into one file.

The video information I can see is:

640x480
xvid mpeg4
30 frames per second
bitrate N/A
ADPCM Audio
Mono
44100 HZ
64kbs

(I am using xubuntu 9.04 on an intel machine if that makes any difference)

The most common solution I see on the forum (and the web) is to use AVIDEMUX. I already tried that many times. Using the append feature of the first video plays, and when the second video starts it repeats the audio from the first segment, over and over until the end. 

So then I tried another suggestion to cat the files into one and reencode them with mencoder. That made a video that didn't play, but I could scroll through it and see the images.

There has got to be an easy way to do this, preferably at the command line. And somebody else must have already gone through this. Please help.

---

### Post by benerivo on 2009-05-23
I would keep trying mencoder.```
mencoder -oac copy -ovc copy -o '/home/ben/newvideo.avi' '/home/ben/test1.avi' '/home/ben/test/2.avi'
```
where the first file is the output and test 1 and 2 are the input files, and the commands before the file names are telling it to make a direct copy of the video and audio. I think this only works when the two input files have the same codec, resolution etc.. When they differ, then you have to specify what format/codec you want the resulting file to be in. This command might work```
mencoder -oac mp3lame -ovc raw -o '/home/ben/1.mpg' '/home/ben/test/1.avi' '/home/ben/test/2.avi'
```

---

### Post by wmgcf on 2009-05-24
benerivo, thank you. With your example I realized that the reason mencoder hadn't worked for me is because I was using quotes (") instead of apostrophe (') around the filenames. I get mixed up becasue I have to use microsoft scripts at work.

And when I used your first example the video worked but there was no audio. so I used your second example to explicitly encode mp3. here is the exact command that worked for me: 

mencoder -oac mp3lame -ovc copy -o '../combined.avi' `find -name '*.avi'`

For another person with a level of experience like mine I will explain each part.

**mencoder** is the encoder library for mplayer. There is also a womencoder library.

**-oac mp3lame** tells mencoder to convert the audio to mp3

**-ovc copy** tells mencoder copy the video codec of each clip. works as long as all clips are the same size, bitrate, etc. 

**-o '../combined.avi'** tells mencoder the outfile will be up one directory named combined.

**`find -name '*.avi'`** tells mencoder to grab every audio file in the present working directory and merge it. The (`) tells the bash shell to execute the find command and return it the list of files to the mencoder command statement.

Result I had a single video made from about 14 FlipVideo clips. No loss of video or audio quality. For the next run I will spell out the files in a specific order, this was just a test.

---

### Post by andrew.46 on 2009-05-24
Hi wmgcf,

I note that you would prefer to use the commandline to join these files so can I suggest FFmpeg? There is a section of the FFmpeg FAQs that considers exactly your situation:

3.18 How can I join video files?
[http://ffmpeg.mplayerhq.hu/faq.html#SEC30](http://ffmpeg.mplayerhq.hu/faq.html#SEC30)

Perhaps this might be worth a look?

Andrew

---

### Post by wmgcf on 2009-05-24
> **andrew.46 said:**
> Hi wmgcf,

I note that you would prefer to use the commandline to join these files so can I suggest FFmpeg? There is a section of the FFmpeg FAQs that considers exactly your situation:

3.18 How can I join video files?
[http://ffmpeg.mplayerhq.hu/faq.html#SEC30](http://ffmpeg.mplayerhq.hu/faq.html#SEC30)

Perhaps this might be worth a look?

Andrew

yes andrew.46, thanks. I will try ffmpeg. I was originally trying ffmpeg. but gave up because I couldn't find documentation that works for me. And I kept finding other examples of people doing the same thing with mencoder.

command line always seems easier and more reliable - probably in part because my PC is a little older. Maybe some people just like it better.

---

