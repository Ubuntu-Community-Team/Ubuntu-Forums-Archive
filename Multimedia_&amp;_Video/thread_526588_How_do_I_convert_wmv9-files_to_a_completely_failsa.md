---
title: "How do I convert wmv9-files to a completely failsafe format?"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by kwaanens on 2007-08-15
I have tried, time and time again to be able to convert wmv-files to a human readable format, that will play nice with every player and editor out there. Last I tried:

mencoder Trail_of_Dead__Reprise__1000_277722_20070811_000122.wmv -o trailofdead.mpg -ovc lavc -oac mp3lame -of mpeg

The file is playable in mplayer and vlc, but gxine and totem both chokes on it.

What is the magical line to convert a video to a non-proprietary format that "just works", and that plays nice with all players/editors, and maintains the quality?

I can't stress how much I hate wmv9! Grrrrr....

- Ketil

---

### Post by moore.bryan on 2007-08-15
*have you tried ```
ffmpeg -i Trail_of_Dead__Reprise__1000_277722_20070811_00012 2.wmv -o trail.avi
```?*

---

### Post by kwaanens on 2007-08-15
> **moore.bryan said:**
> *have you tried ```
ffmpeg -i Trail_of_Dead__Reprise__1000_277722_20070811_00012 2.wmv -o trail.avi
```?*

Well, that worked, sort of... It plays OK, but resolution is not as good, and the sound is muffled and somewhat distorted.

I wish video-files was as easy to understand as sound-files...

The avio-file is about 60% of the filesize of that of the wmv, so that accounts for some of the decrease in quality, I guess.

What are my options to increase quality, and not go beyond the original file size?

- Ketil

---

### Post by moore.bryan on 2007-08-15
*well, increased quality=increased size.  unfortunately, that's just how it is.  you could try "a zillion" different specifications with ffmpeg, as i just gave you the most straight-forward.  check out the ffmpeg [documentation]("http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html") for more details...*

---

### Post by kwaanens on 2007-08-15
> **moore.bryan said:**
> *well, increased quality=increased size.  unfortunately, that's just how it is.  you could try "a zillion" different specifications with ffmpeg, as i just gave you the most straight-forward.  check out the ffmpeg [documentation]("http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html") for more details...*

Just tried: $ ffmpeg -r 34 -s 768x432 -ar 48000 -i Trail_of_Dead__Reprise__1000_277722_20070811_000122.wmv trail.avi
That matches what I can tell of the original file. Man, it would be cool if e.g. ffmpeg had some sort of setting that would analyze the input file, and match the criteria.

I'll let you know how it works out.

Do you by any chance know if there exists a tool for superficial analysis of video quality? That would be good to see how different settings play out.

Thanks for your help!

- Ketil

---

### Post by moore.bryan on 2007-08-15
*i use [tovid]("http://tovid.wikia.com/") and it's tools... come to think of it, that may have some more advanced things than ffmpeg.  then you can use the "idvid" command to tell you lots of stuff about your video file.*

---

### Post by kwaanens on 2007-08-16
I checked out the log in tovid to see what arguments it uses. Very informative actually.

Now, I'm stumped by this: 
I ran idvid, to see what came up. It says:
Video bitrate: 0 bits per second

How do I determine what bitrate to set it to? On Tovid, a supreme quality encoding uses 9000, while ffmpeg's standard is 200

idvid gave the following info:

```
File: El_Caco__reprise__1000_277721_20070810_230000.wmv
              Width: 768 pixels
             Height: 432 pixels
       Aspect ratio: 1.77:1
             Frames: 0
           Duration: 00:54:58 hours/mins/secs
          Framerate: 25.000 frames per second
       Video format: WMV3
      Video bitrate: 0 bits per second
---------------------------
Audio track 1 (Stream 0.0, AID 0):
---------------------------
              Codec: wmav2
            Bitrate: 128000 bits per second
      Sampling rate: 48000 Hz
```

I've come down to trying the following:
```
ffmpeg -i "input.wmv" -vcodec xvid -acodec aac -ar 48000 -qmin 1 -qmax 31 -b 9000k -ab 128k -ac 2  -r 25.000 -s 768x432   -aspect 1.77:1  -y  "output.avi"
```

Correction: aspect ratio was wrong, should be "4:3".

But, as said, I'm wondering what bitrate to set. I'm guessing 9000 will increase the output file hugely.

- Ketil

---

### Post by kwaanens on 2007-08-16
I tried with:

ffmpeg -i "Trail_of_Dead__Reprise__1000_277722_20070811_000122.wmv" -vcodec xvid -acodec mp3 -ar 48000 -qmin 1 -qmax 31 -b 1000k -ab 128k -ac 2  -r 25.000 -s 768x432   -aspect 4:3  -y  "output.avi"

Which gave a file that is quite similar in quality, and 478 MB, compared to 421 for the input file.
Only thing is, I now used mp3 for audio. This is proprietary, and I'm unsure it maintained stereo sound. Is it likely to have done that?
What might I replace mp3 with? aac did not work in Totem, and was laggy in mplayer.

---

### Post by moore.bryan on 2007-08-16
*i think it strange your wmv has no video bitrate... is it only music?  according toi the idvid, that's what it looks like.  if it's only audio, you can easily convert between mp3, ogg, flac, etc.*

---

### Post by kwaanens on 2007-08-16
No, it's both video and audio. 

- Ketil

---

### Post by moore.bryan on 2007-08-16
*then that is REALLY weird from idvid...*

---

### Post by kwaanens on 2007-08-17
> **moore.bryan said:**
> *then that is REALLY weird from idvid...*

I know, and exiftool actually manages to get the info. Exiftool on the other hand screws up fps, so I ended up using both exiftool and idvid to get relevant info.
I ran into another problem with idvid, where it reported framerate as 1000 (!) in stead of 25. Now, that makes a big file...
Anyway, my script is done for now, check it out: [http://anotherugly.wordpress.com/wmv2avi/](http://anotherugly.wordpress.com/wmv2avi/)

Thanks for your help!

- Ketil

---

### Post by moore.bryan on 2007-08-17
[I]good work on the script... hope you find answers to all your unanswered questions!
;-)[/I]

---

