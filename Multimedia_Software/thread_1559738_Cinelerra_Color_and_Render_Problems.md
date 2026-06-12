---
title: "Cinelerra Color and Render Problems"
date: 2010-08-23
forum: Multimedia Software
---

### Post by trunkmonkeytoo on 2010-08-23
I have recently been doing video editing in Ubuntu Studio using Cinelerra. But I have had some problems rendering.

When I render a video, with the Linux Quicktime (.mov) option, it comes out with dramatically wrong colors (turns screen blue, etc.). And a 30 second HD 720p video shot way up to 2.3 GB, which was massively larger than the original file. And a video that was about 480 MB went up to 22GB when rendered, with only a title (.png) that I made with Gimp in the beginning of the video for five seconds.

I have tried rendering my videos as other options given, such as Microsoft AVI, but when rendered, I still have the color problem, and it is saved as a .avi01, and cannot be played in Windows 7 or Ubuntu. And why is it that all of the videos saved with .01 after them? (e.g. .mov01, etc.)

All of my effects, etc., play back wonderfully in the compositor, and there is no problem with the color, so I am very confused about what is wrong with the rendering. 

So how would I go about fixing these problems? And what formats would be good for playing these videos back on a DVD, Windows PC, and Mac? 

Thanks for your help!

---

### Post by no2498 on 2010-08-24
? if you are playing them back in totem click edit preferences movie. move some of the sliders to suit your needs

---

### Post by trunkmonkeytoo on 2010-08-24
I tried your advice, but it didn't work. Should I post some screenshots or a video, to find out what I'm doing wrong?

---

### Post by no2498 on 2010-08-25
you may after you go back to totem an reset to default
i see i did not say that my bad sorry

---

### Post by trunkmonkeytoo on 2010-08-26
I've been watching and reading tutorials on how to render video in Cinelerra, to try and figure out what the problem is. I've now been rendering the audio separate from the video, and it no longer has the 01 after it (ex. .mp301) and plays back normally. However, when I go to render the video portion, guides say to leave the interlacing as unknown, but when I go to render, it says "Not Interlaced" and I think this may be causing me to not be able to render the video, because I get error messages when I try to render the video. How would I change interlacing to unknown, because I don't see anything that let's me change that setting. 

[IMG]http://ubuntuforums.org/picture.php?albumid=1992&pictureid=6680[/IMG]

---

### Post by trunkmonkeytoo on 2010-08-26
I managed to get the video rendered without the audio as a .avi. I will need to go into Windows to see if the color is correct. But when I rendered just the video with formats that Linux accepts, it still came out with the incorrect color. I have tried other color options in the format menu, but nothing changes it. I'll post some screenshots, with some of the problems I have been having. 

I also stopped using the YUVStream, because I could not get it to render with that. But with Quicktime for Linux and Microsoft Avi, the video rendered, but with color problem. 

With the video I have here, I didn't use any effects or transitions, and it looked perfect in the compositor, so I don't know why it keeps rendering this way. 

[IMG]http://ubuntuforums.org/picture.php?albumid=1992&pictureid=6683[/IMG]

[IMG]http://ubuntuforums.org/picture.php?albumid=1992&pictureid=6682[/IMG]

[IMG]http://ubuntuforums.org/picture.php?albumid=1992&pictureid=6681[/IMG]

---

### Post by wildhostile on 2010-08-27
Hi trunkmonkeytoo,

What association (format-videocodec-audiocodec) did you do to get these results?
Depend on what you want to do with your video, you could try jpegphoto or mjpeg (=motionjpeg) with mp3 or pcm in a mov container. But that will still give you huge files. It's the problem with HD content. You could try mpeg4 too.

YUV4MPEG Stream uses a commandline of mpeg2enc or ffmpeg. Two commands are given for each for DVD and VCD. Maybe it can be use to render hd video with an appropriate command.

If you are using progressive video (720p), no need to worry about interlacing.

---

### Post by trunkmonkeytoo on 2010-08-27
> **wildhostile said:**
> Hi trunkmonkeytoo,

What association (format-videocodec-audiocodec) did you do to get these results?
Depend on what you want to do with your video, you could try jpegphoto or mjpeg (=motionjpeg) with mp3 or pcm in a mov container. But that will still give you huge files. It's the problem with HD content. You could try mpeg4 too.

YUV4MPEG Stream uses a commandline of mpeg2enc or ffmpeg. Two commands are given for each for DVD and VCD. Maybe it can be use to render hd video with an appropriate command.

If you are using progressive video (720p), no need to worry about interlacing.

Thanks! I tried rendering a video a just now, with no interlacing, YUVA 8Bit color model, as a .mov. I'm not sure why, but when I clicked the wrench in the render options for video, it gave me a completely different screen, and compression options, so I chose MPEG4 Video. When I rendered, it came out with all the correct coloring! I thank you all for helping out!:p

---

