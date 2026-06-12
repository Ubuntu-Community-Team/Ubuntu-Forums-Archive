---
title: "Video Conversion for the Nintendo Wii"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by thunderstorm on 2006-12-03
I just moved over to Kubuntu a couple of months ago, leaving Windows completely behind.  I love Linux and have no desire to re-install Windows XP... but.

We got a Wii, and it can play video files.  AVI and MOV format, with some restrictions.  There's a converter for Windows that converts the video files into a workable format, but I haven't found a video converter for Linux yet.

Does anyone know of any type of video converter that would let me convert a file to AVI, scale down the size and stuff like that?  Doesn't have to be fancy really, but I'm not a video expert either.  

Any help would be appreciated.

---

### Post by Mike'sHardLinux on 2006-12-03
If you can find out what exactly the Wii can handle or wants to get, you can probably use any typical converter that will convert to that format. In other words, find out what codec, bitrate and resolution that is best for the Wii, and use any converter to convert to that format. It should work with any good converter. You shouldn't need a special converter software just for the Wii.

---

### Post by thunderstorm on 2006-12-03
> **Mike'sHardLinux said:**
> If you can find out what exactly the Wii can handle or wants to get, you can probably use any typical converter that will convert to that format. In other words, find out what codec, bitrate and resolution that is best for the Wii, and use any converter to convert to that format. It should work with any good converter. You shouldn't need a special converter software just for the Wii.

I know I don't need one special for the Wii, but I can't seem to find a converter...

---

### Post by Mike'sHardLinux on 2006-12-04
There are several video converters for Linux. Have you looked in the Synaptic Package Manager? Have you searched the forums for avi converter.

I don't know the names right off hand, but they are there.

---

### Post by n2j3 on 2006-12-04
AFAIK, mplayer [http://www.mplayerhq.hu/](http://www.mplayerhq.hu/) comes bundled with mencoder, which converts from/to quite a few different formats. Check this link for more info : [http://en.wikipedia.org/wiki/MEncoder](http://en.wikipedia.org/wiki/MEncoder) or just *man mencoder* in your terminal

---

### Post by n2j3 on 2006-12-04
.

---

### Post by dolson on 2006-12-06
This should work...

mencoder ORIGINALMOVIEHERE.avi -fps 29.97 -ovc lavc -lavcopts vcodec=mjpeg -oac pcm -vf scale -zoom -xy 512 -o OUTPUTVIDEOFORWII.avi

I haven't tried it yet, but I will tonight when I get home from work. If you want to adjust the framerate or video width, go ahead. These are just values I will probably use.

I have put up a webpage with my info here, so some day it might hit the google search engine results:

[http://icculus.org/~dolson/wii-video-conversion.html](http://icculus.org/~dolson/wii-video-conversion.html)

I am scaling it down to 512px wide just because the Wii isn't hi-res, so there's no real need for anything much bigger (512 might not be optimal, I don't know) and so I scale down to save space on my SD card.

---

### Post by jlynaugh on 2007-02-04
I tried this and the movie plays great on the wii but the sound is way out
of sync - the sound is late by alot. Any ideas on what i should change? Thanks in advance for any help.

---

### Post by jlynaugh on 2007-02-04
figured out what was wrong-there is a typo in the code-changed -fps 29.97 to -fps 23.97
that fixed it

---

### Post by jlynaugh on 2007-02-05
I know I am talking to myself but I should not have used the word typo in the previous post-
I realise now that the frame rate varies depending on the file. I am pretty ignorant about this stuff. But maybe my ignorance will help someone else out.

---

### Post by kjvanmierlo on 2008-02-07
You should be able to set a fixed frame rate in mencoder. Sometimes the audio in the original avi file is not in mp3 format so you should use mencoder to convert the audio as well. (since Wii only plays mp3) It is probably best to set the audio encoding to constant bitrate mp3 to avoid sync problems. I'll have a look at this during the weekend and see if I can come up with an improved script.

---

### Post by kjvanmierlo on 2008-02-07
from the website

[http://www.redkawa.com/videoconverters/wiivideo9/](http://www.redkawa.com/videoconverters/wiivideo9/)

you can download a video converter for Windows. The installer is just an archive which can be extracted with 7z. When you look at the extracted files there is a xml file which contains the settings for ffmpeg. So you should be able to convert video files with ffmpeg and the same settings to get avi files which will play on the wii.

---

