---
title: "encoding video with only one long frame"
date: 2011-01-27
forum: Multimedia Software
---

### Post by tdy on 2011-01-27
Hi, everyone!

I'm sorry but I feel kind of incompetent, cause I'm trying to encode a video using only one image during a complete audio file, but a can't find the way to do it.
What I need to do is to extend the duration of the frame up to the duration of the audio file. How do I do that with mencoder?
Thanks
tdy

---

### Post by ron999 on 2011-01-27
> **tdy said:**
>  How do I do that with mencoder?

tdy
Hi
I don't know how to do that with mencoder, but it's very easy using ffmpeg instead.

---

### Post by tdy on 2011-01-27
Sorry Ron999 but I'm having the same isue with ffmpeg as with ffmpeg.

I get just a 1s video.

what i need would be like:

mycommandline:# ffmpeg -i audiofile.wav -i img.jpg mymovie.avi

the thing is that ffmpeg or mencoder use as preority for the video duration the image file. Or better the fps option and that gives me a 1s of video with sound but not the actual 3.30 minutes the audio file have.

how can I can tell to mencoder or ffmpeg that the frame lasted instead of 1s, 3.30 min?
Enyone knows?

Thanks again!

tdy.

---

### Post by ron999 on 2011-01-27
Hi
It's easiest to use a jpg or png image together with an mp3 or aac/m4a audio file to make an mp4 video. 
Like this:-
```
ffmpeg -loop_input -i img.jpg -i audiofile.mp3 -shortest -b 1000k -acodec copy mymovie.mp4

```
This will give you a movie same duration as the audiofile.

If you want to specify a certain duration hh:mm:ss use this instead (example 90 seconds):-
```
ffmpeg -loop_input -i img.jpg -i audiofile.mp3 -t 00:01:30 -b 1000k -acodec copy movie90.mp4

```

---

### Post by tdy on 2011-01-28
Thanks Ron999!!! that realy works :)
Definitly I've pass over the -loop_input parameter in the man page.

Great help!!!

tdy.

---

