---
title: "FFMPEG combining video and audeo formats"
date: 2009-12-10
forum: Multimedia Software
---

### Post by Cavsfan on 2009-12-10
Could anyone help me combine a OGV video file and an MP3 sound file via FFMPEG?
I know ffmpeg is pretty powerful and I think I combined some files once, but recently 
have not been able to get it to work.
I know how to convert ogg or ogv to avi or mpg as that is fairly straight forward.

I have a ogv video that is 6 mins and 25 seconds.
the audio is an mp3 that is  4 mins and 51 seconds long.
I want to put the video at the front and have silence after that until the 6:25 ends,

Isn't this possible? I tried to create a video with audio using jack and recordmydesktop, 
but the quality was pretty bad. So I thought I would try to do this way.

Thanks in advance to anyone who may know how to do this! :-k

---

### Post by Cavsfan on 2009-12-10
Or could it be Mencoder I am thinking of?

---

### Post by Physical Hook on 2009-12-10
```
ffmpeg -i audio.mp3 -i video.ogv output.ogv

```

Not sure whether it'll work with OGV ( haven't tried ) so let us know how it turns out.

---

### Post by FakeOutdoorsman on 2009-12-10
> **Physical Hook said:**
> ```
ffmpeg -i audio.mp3 -i video.ogv output.ogv

```

Not sure whether it'll work with OGV ( haven't tried ) so let us know how it turns out.

That will unnecessarily re-encode the video, when instead you could just copy the video stream:
```
ffmpeg -i audio.mp3 -i video.ogv -acodec libvorbis -vcodec copy output.ogv
```
or
```
ffmpeg -i audio.mp3 -i video.ogv -acodec vorbis -vcodec copy output.ogv
```
Other options of interest are audio bitrate (-ab) and number of channels (-ac).  See *ffmpeg -h* for more options.

---

### Post by Cavsfan on 2009-12-11
I really appreciate the help!

I recorded a Luther Vandross song "I'd Rather" on youtube with recordmydesktop with 
sound off and I have the same song in MP3 format. As  I mentioned above they are 
different lengths.

Here is what I got when I tried this command:

"ffmpeg -i Id_Rather.mp3 -i Luther.ogv -acodec libvorbis -vcodec copy Final.ogv"

The sound was perfect, but the video skipped the difference in the length of the 2.
The video was like it was ahead from the start by approx 1:32 (the diff).
Then at the point where the video matched the sound the video took off and they matched perfectly. 
Everything from there on matched up perfectly until the end of the video. 
There was still silence at the end, which is what i wanted.
Do you know how to fix this? I wanted them both to start at the same time (actually a
2-3 sec. delay for the sound to start after the video), have the video and audio match 
from the beginning and then have the 1:32 silence at the tail end. 
Am I making sense? It seemed to keep the bitrate and stereo sound w/o adding the 
other 2 parameters. And the output video was exactly the same length as the input 
video (Perfect!)

I tried the 2nd command "ffmpeg -i Id_Rather.mp3 -i Luther.ogv -acodec vorbis -vcodec copy Final2.ogv"
and it produced the same result except the propertied for the output file says N/A for 
the sound bitrate while the 1st command's output produced 64bit.
Thanks FakeOutdoorsman! I appreciate the help!

I tried Physical Hook's method last of course and [COLOR=Blue]it worked great[/COLOR]! It did exactly 
what I wanted to do. The sound was a tiny bit ahead at the beginning and then
it was a tiny bit behind towards the end of the song. But, not enough to make a difference! I am going to roll with it!
Thanks to both of you for your generosity in helping me do this!!!
:guitar:
I have learned a lot since I started Ubuntuing!

---

### Post by Cavsfan on 2009-12-12
When I tried to upload the OGV file to YouTube it said format was not supported.
When I try to convert it to MPG or AVI the sound and video get out of sync.
:???:

---

### Post by Cavsfan on 2009-12-13
I got this to work with this command:
ffmpeg -i video.ogv -i audio.mp3  -vcodec mpeg4 OutputFile.avi

It's not perfect, but not to bad either!
It was recorded in 1920 x 1200 so it is best viewed in HD fullscreen and it goes past the end of the song/video.
Here it is on youtube: _[My video]("http://www.youtube.com/watch?v=WU5PUTKwfP0")_

---

