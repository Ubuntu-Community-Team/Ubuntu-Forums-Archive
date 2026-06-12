---
title: "This is everything I see everytime I convert a video that I make..."
date: 2010-08-10
forum: Multimedia Software
---

### Post by ZequeZ on 2010-08-10
Well, everytime I convert a video (ffmpeg -i MyVideo.ogv MyVideo.avi (or flv, or anything)) the resulted video ends like this: 
[URL="http://img130.imageshack.us/img130/7204/screenshotvu.png"]
http://img130.imageshack.us/img130/7204/screenshotvu.png[/URL]

Doesn't matter what format I convert to, it everytime ends like that... And I  think it's a record problem, because if I upload it to YouTube the image that is shown on the video after it's proccesed is exactly the same if I converted....

So... Any idea of the problem? :(

PD: Sorry for my crappy english :(

---

### Post by 0004tom on 2010-08-10
I take it from the -i file, your using recordmydesktop to record?

Have you tried using another converter? I personally use mencoder, as it gives better results, and encodes faster imo then ffmpeg.

---

### Post by ron999 on 2010-08-10
There's a fix here using mencoder:-[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1501566&highlight=upload+youtube]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1501566&highlight=upload+youtube")

---

### Post by wesleybailey on 2010-08-10
Which version of ffmpeg are you using?

Are you using the one that you installed from the Ubuntu repositories or did you download ffmpeg from source and compile it yourself.

If you are using the one from the repositories, I would suggest that you download the latest ffmpeg and compile it yourself. That way you will have access to the latest bug fixes.


Latest Post: [FFmpeg Tutorial: FLV to AVI]("http://wesleybailey.com/articles/ffmpeg-flv-converter-transcode-flv-to-mpg-avi")

---

### Post by ZequeZ on 2010-08-10
Yes, I used gtk-recordmydesktop, but, a month ago I did a video with PiTiVi and when I uploaded it to YouTube there was the same image I got from converting the video...

The ffmpeg is from the repositories.

I tried to use Mencoder but it gives a lot of errors, you have to specify a lot of things just to convert a video, ffmpeg convert it automatically =/.

@ron999 I'll try that, but I have to reset the computer because I started Windows to play WoW xD.

EDIT: I tried using the Mencoder solution, it worked very well ^^. Thanks :P. Anyway the ffmpeg should work too right? =/

---

### Post by 0004tom on 2010-08-11
To use mencoder you only need a command like

mencoder output.ogv -oac mp3lame -ovc lavc -o output.avi

to use ffmpeg you need alot more options then the above mencoder command. You should really read the man pages for each. As I can't see teh command you running will actually work, as your not telling it what codec to use for audio or video.

Edit, Yes as i thought your command (ffmpeg -i out.ogv out.avi) is what is causing the issue. You need to specify more options for ffmpeg to convert the ogv properly.

Edit 2. tried several commands now with ffmpeg and still get the same effect.. This is why I use mencoder lol

---

