---
title: "Download and convert to mp4 videos from youtube?"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by RAFAMP on 2007-11-01
Hello

 how can i download videos from youtube and convert them to mp4? so i can view them on my cell phone?

---

### Post by netyire on 2007-11-01
You can use QTTube ([http://www.getdeb.net/app.php?name=QTTube](http://www.getdeb.net/app.php?name=QTTube)) to download the videos and then convert them with ffmpeg (in the repos) try typing the following in a terminal in the same directory where you downloaded the file with QTTube to:

ffmpeg -i <input.flv> -r 12.5 -s <your phone's screen size in pixels like 100x80 or something> -vcodec h264 -ar 22050 -ab 32 -acodec ac3 <output.avi>

---

### Post by RAFAMP on 2007-11-02
thx for the reply netyire

 but i think my Samsung D900i does not support the codec h264

-r 12.5 it's 12.5 FPS? i cant adjust it to the original video rates? same on audio?

EDIT

 I'm using [WinFF]("http://biggmatt.com/winff/downloads/winff-version-0.31.html") to convert the videos, but when i click convert nothing happens, just ablank console screen quickly opens and closes after a few ms...

---

### Post by netyire on 2007-11-05
Sorry for the long reply time. I wrote a python program which I think may do what you want it to. I don't own a Samsung D900i so I can't test this in advance but from what I've read online the screen resolution is 240 x 320 and the player supports mpeg4 asp and aac + mp3. I added the Samsung D900i profile to the program, simply pick the input and output directories, choose the Samsung D900i profile and hit enque for all the files you want to convert. Then click start to process the files.

Tell me how it works out for you, and I'll try refining the profile. The current profile is as follows:

320x240, video mpeg4 asp 400kbits/s 20 fps with high quality filters applied, audio mp3 highest quality and 64 kbits/s joint-stereo.

Make sure you install mencoder though, it does all the hardwork behind the scenes.

---

