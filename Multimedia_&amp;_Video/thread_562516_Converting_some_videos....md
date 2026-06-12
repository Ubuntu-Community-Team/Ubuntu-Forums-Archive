---
title: "Converting some videos..."
date: 2007-09-28
forum: Multimedia &amp; Video
---

### Post by ZeldaFan on 2007-09-28
I want to get some videos ready to be playable on my newly purchased Archos 605. However, while some of my videos, in the .avi format, work fine, other .avi and .mp4 files don't work because they use a codec that requires me to purchase an additional plugin for. They either use H.264 vid or ac3 audio codecs. How can I convert these videos to codecs viewable in my archos. Also, a problem is that with ffmpeg, I followed some random guide to compile it or something, and I thing I messed it up. It doesn't work with WinFF (the gui frontend for it) and if I uninstall it, I'm forcent to uninstall stuff as well that I dont want to uninstall.

---

### Post by rsambuca on 2007-09-28
I use avidemux to convert my videos for use in my Archos504.  I can't remember off hand what settings I used, but I think it was mpeg4 for video with lame (mp3) audio and avi container.  If mpeg4 doesn't work, then it may have been xvid for video.

Avidemux is in the repos and very easy to use.

---

### Post by ZeldaFan on 2007-09-29
thanks so much, this has made converting much easier. I'm in the midst of converting my videos right now, hopefully they'll all work fine as they should anyway on my archos.

---

### Post by rsambuca on 2007-09-29
Good luck.  Let me know what settings you used.  As I said it has been a while since I have converted any, and I have a bunch more I want to put on there!

---

### Post by ZeldaFan on 2007-09-30
Ok, well originally I was going to complain in the post that none of the conversion were working, neither the .mp4 nor the xVid formats would be recognized in my player, despite the fact that they had used exactly the same codecs as my working video files. Then I noticed, that all my working files had extensions of .avi afterwards, and my converted files did not. After appending those files with .avi by simply renaming, they showed and played in my player. I, by the way, used the .mp4 (lavc) codec for video encoding and lame for audio encoding. Thanks for all your help.

---

### Post by ZeldaFan on 2007-09-30
Just a question though. Is there a limit on the length of the videos that the archos can play, because I have a video thats 3 hours long and another thats 2 hrs 59 min, and both open and then immediately close after I attempt to open them on my archos. Are they too long? All my other videos work fine though.

---

### Post by rsambuca on 2007-09-30
No limit that I am aware of.  What is the size of these files?

---

### Post by ZeldaFan on 2007-09-30
2 GB and 2.4 GB, and they happen to be my largest vids too. Should I compress them? and how?

---

### Post by rsambuca on 2007-10-01
Are you going to be watching these on your Archos, or are you plugging it into a tv to view them.  If you are just going to be viewing them on your Archos, then you can compress them way down.

---

### Post by stlouis1 on 2007-10-01
i use avidemux as well right now. not for an archos, but for a zen vision.

though im not sure what the archos is capable of. i use xvid for video on my zen and mp3 for audio. not that it helps you. but in reference to you're question on how to compress you're videos, assuming the archos uses 320x240 resolution like my zen, all you have to do is add a resize filter on whatever video codec you have set, and then put whatever the native resolution is for your archos

you might also want to limit the video bitrate to 600 at most if the resolution is higher than what my zen supports. i personally use 450kbps bitrate on my zen and find the video quality just fine and it keeps the file size down. i think even the longest movie i have, 12 monkeys, roughly 129 minutes is only about 500mb

---

### Post by ZeldaFan on 2007-10-01
Well the archos 605 resolution is 800 by 480. The resolution on my vids are closer to 720 by 480, so I dont think they are too high. However, I guess I'll try and compress them. Can I reset the size filters through avidemux?

---

### Post by rsambuca on 2007-10-01
Under the video "Configure" button, you can select "Encoding Type" as Two pass.  Then you can select a final target size.  You should be able to crunch a 2hour movie down to about 700MB without really having any noticeable effect on a screen that small.

---

### Post by ZeldaFan on 2007-10-02
Thanks that helped a lot, I got all my videos working now. By the way, what does 2-pass do?

---

### Post by rsambuca on 2007-10-02
> **ZeldaFan said:**
> Thanks that helped a lot, I got all my videos working now. By the way, what does 2-pass do?

That is great you got it working.  Maybe there is a size limit on the Archos afterall?  Anyways, the 2-pass transcoding is exactly what it says:  it runs through the video twice so that it only has to do so much with each pass.  If you are doing significant compression it seems to make quite a big difference.  The obvious downside is that it takes twice as long.

---

### Post by ZeldaFan on 2007-10-03
Apparently, after looking on the archos forums, there isn't an archos video size limit, there's a size limit of 2 GB for the .avi format. At least that's what the posters said. Of course, I'm not sure if that makes sense, because I can play .avi files larger than 2 GB on my computer.

---

### Post by little_penguin on 2007-10-05
Iriverter is a nice little program that will convert your videos. I use it for my Archos 504 and it works great. I think I got it off Sourceforge.net.

---

