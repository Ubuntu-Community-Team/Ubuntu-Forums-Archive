---
title: "MPEG 4 video and audio not synchronized"
date: 2009-03-29
forum: Multimedia Software
---

### Post by Keith_Beef on 2009-03-29
I'm trying to encode some films to MPEG4 to play either on my Nokia 5800 or on other players, and almost all the fles have a big problem: sound is out of synch by as much as 36 seconds!

I have ripped some of my DVDs to AVI files, and these play fine in Xine, MPlayer or Totem.

But when I convert these AVI files to MPEG4, the synch goes.

Here is an example of the kind of commands I used, and they all gave out-of-synch results when tested on the computer, and also on the Nokia.
```

mencoder -ovc lavc -oac lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:keyint=25:vbitrate=500:threads=4:acodec=libfaac:abitrate=64 -af lavcresample=44100 -vf harddup,scale=320:-3 -noskip -lavfopts format=mp4 mongol_1.avi -o mongol_320.mp4
```

I tried different bitrates and scale at 640; tried specifying output fames per second as 25 or 30; tried leaving out keyint... nothing brings the sound back into synch.

After searching some more, I tried slightly different arguments.
```
mencoder -oac mp3lame -lameopts cbr:br=128 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=500:vhq:autoaspect -vf scale=320:-3 -ffourcc DX50 mongol_1.avi -o mongol_DX50.mp4
```

This has the sound in synch; but the Nokia won't play the file. :(

Any clues, please?

K.

---

### Post by andrew.46 on 2009-04-01
Hi Keith_Beef,

Although a former user of MEncoder I have consistently found better results with FFmpeg. Have you ever considered using this? For Intrepid you would need:

```
sudo apt-get install ffmpeg libavcodec-unstripped-51
```

to get you started. If you are interested there is a lot of support for FFmpeg available on these forums.

All the best,

Andrew

---

### Post by Keith_Beef on 2009-04-12
> **andrew.46 said:**
> Hi Keith_Beef,

Although a former user of MEncoder I have consistently found better results with FFmpeg. Have you ever considered using this? For Intrepid you would need:

```
sudo apt-get install ffmpeg libavcodec-unstripped-51
```

to get you started. If you are interested there is a lot of support for FFmpeg available on these forums.

All the best,

Andrew

Thanks for the hint,Andrew.

I had already tried 
```
ffmpeg -i mongol_1.avi -f mp4 -vcodec h264 -acodec aac -ar 24000 -ab 64 -ac 2 mongol_h264.mp4
```
and although this plays in synch in Xine on the coputer, my Nokia will only play back the audio, with no image. :(

K.

---

### Post by andrew.46 on 2009-04-12
Hi,

Depends a lot on what the original files are of course, if they are already mpeg4 a simple '-vcodec copy' would be all that is required. Perhaps try:

```

ffmpeg -i mongol_1.avi **[COLOR="Red"]-vcodec mpeg4 -vtag XVID[/COLOR]** -acodec aac -ar 24000 -ab 64 -ac 2 mongol_mpeg4.mp4

```

and if your camera plays this have a look at some quality / bitrate settings for the video encoding.

Andrew

---

### Post by cotcot on 2009-04-13
Maybe using a compiled version of ffmpeg would allow you to play the video. The ffmpeg from the repos does not support some proprietary codecs. Therefore it is better to compile it as explained [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095").

---

### Post by Keith_Beef on 2009-05-19
Since updating to 9.04, I tried using Handbrake to rip a couple of DVDs and found that the resulting mp4 files play perfectly well on my Nokia 5800.

I had trouble with a German DVD... I could not get the subtitles, and sometimes I could not get the audio. In the end, I ripped this with AcidRip, to an avi file with subtitles and at full-size, then used HandBrake to encode this to an mp4 at a reduced size to suit the Nokia screen.

K.

---

