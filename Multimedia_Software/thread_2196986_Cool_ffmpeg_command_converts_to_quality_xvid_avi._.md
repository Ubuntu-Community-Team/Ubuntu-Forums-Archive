---
title: "Cool ffmpeg command converts to quality xvid avi. Help me automate with bash script."
date: 2014-01-01
forum: Multimedia Software
---

### Post by Terry of Astoria on 2014-01-01
Some time ago, I found this really cool command made by someone. I don't even remember where I found it. I tried it and it converts mkv files and mp4 files very reliably to xvid-mp3 avi files that to my eyes, rival the originals in quality and are WAY SMALLER, and they play on my standalone divx player! SO COOL! See here:

```
mencoder -mc 0 -noskip -vf expand=:::::16/9,scale=720:480,hqdn3d,harddup -ovc xvid -oac mp3lame -xvidencopts fixed_quant=3.8:me_quality=6:noqpel:nogmc:trellis:chroma_me:chroma_opt:hq_ac:vhq=4:lumi_mask:max_key_interval=300:quant_type=mpeg:max_bframes=2:closed_gop:nopacked:profile=asp5:autoaspect:bvhq=1 -lameopts vbr=2:q=6:aq=2 -o "NEW_FILENAME" "FILE_TO_CONVERT"
```

Just replace FILE_TO_CONVERT with the actual filename of the file you want to convert. Replace NEW_FILENAME with the new filename you want. Put .avi at the end of the filename, of course. I like to add "xvid.mp3" like this - Robin_Hood.xvid.mp3.avi 

I want to share that command that works so well for me on my Ubuntu 12.04 installation. Note that I do have a few extras installed, such as ffmpeg, lame, and, I think, ubuntu-restricted-extras among others. 

QUESTION: 
Can you guys help me write a script that will simply do this to all *mkv or *.mp4 files in a directory? This will help me learn how to make my own bash scripts, a skill I have been lacking, but always wanted to learn!

Technically I suppose there's another subforum for this question, but I wanted to share the command itself here, and I know that this is a very trivial type of task which any skilled admin ought to be able to do, so . . .

---

### Post by andrew.46 on 2014-01-02
You might be better to use FFmpeg rather than MEncoder, I have personally found better quality encodes with FFmpeg...

---

### Post by Terry of Astoria on 2014-01-02
Why did I say ffmpeg? It's mencoder. I'm going to go do one, and watch the output.
Anyway, thanks for the pointer, andrew.46. I'll go look up how to use ffmpeg.
By the way, it was here on ubuntuforums where I found the mencoder command.
[It was recommended here]("http://ubuntuforums.org/showthread.php?t=1011091") by user eye208. Some other interesting suggestions are also given in that thread, including a couple of possible solutions for my current question.

However, I am still open to suggestions for a good method of batch-processing high-bitrate mp4 files into nice xvids. These days I use my computer to play the videos usually, but a few friends still use their DVP642 or other standalone divx players, so there's another reason why I want to to this.

 Thanks, all.

---

### Post by FakeOutdoorsman on 2014-01-02
[size=4]1. Get ffmpeg[/size]
[Get a recent build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds) from FFmpeg (or [compile ffmpeg](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)). The repository contains [old, buggy junk](http://stackoverflow.com/a/9477756/1109017) that you don't need to waste your time using.

[size=4]2. Encode[/size]

Note the ./ since we're using the downloaded ffmpeg binary):

```
ffmpeg -i input.mkv -vcodec mpeg4 -acodec libmp3lame -qscale:v 2 -qscale:a 5 output.avi
```

[list]
[*]Control video quality with "-qscale:v". 2-5 is a good range and a lower value is a higher quality. 2 is often considered roughly visually lossless.
[*]Control audio quality with "-qscale:a". Range is 0-9. 0-3 will produce transparent results and 4 should be close to perceptual transparency.  See [Recommended LAME Encoder Settings](http://wiki.hydrogenaudio.org/index.php?title=LAME#Recommended_encoder_settings) for more info.
[/list]

[size=4]3. "Batch" process[/size]
You can use a bash for loop:
```
mkdir newvids
for f in *.mkv; do ffmpeg -i "$f" -vcodec mpeg4 -acodec libmp3lame -qscale:v 2 -qscale:a 5 newvids/"${f%.mkv}.avi"; done
```

See some additional options at [What are good parameters for encoding high quality MPEG-4?](http://ffmpeg.org/faq.html#Which-are-good-parameters-for-encoding-high-quality-MPEG_002d4_003f) (I'm unsure if this is up to date).

---

### Post by Terry of Astoria on 2014-01-02
Wow! Thanks, FakeOutdoorsman! I'm gonna try it.
I see what you did there! That's just exactly the kind of help I was looking for!
OK! w00t!

---

### Post by monkeybrain20122 on 2014-01-02
> **FakeOutdoorsman said:**
> The repository contains [old, buggy junk]("http://stackoverflow.com/a/9477756/1109017") that you don't need to waste your time using.

.

For those interested.

Check out [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=729203](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=729203)
and
[https://bugs.launchpad.net/ubuntu/+source/libav/+bug/1263278](https://bugs.launchpad.net/ubuntu/+source/libav/+bug/1263278)

There is a ppa which provides up to date real ffmpeg (no, not Jon Severinsson's, which is old)

[https://launchpad.net/~samrog131/+archive/ppa](https://launchpad.net/~samrog131/+archive/ppa)

This can be made the default ffmpeg (for compiling media players e.g) with update-alternatives.
[http://askubuntu.com/questions/361299/ffmpeg2-on-ubuntu-12-10-quantal-server](http://askubuntu.com/questions/361299/ffmpeg2-on-ubuntu-12-10-quantal-server)

---

### Post by andrew.46 on 2014-01-02
A few explanatory notes here if you wish to use xvidcore:

[http://ffmpeg.org/ffmpeg-codecs.html#libxvid](http://ffmpeg.org/ffmpeg-codecs.html#libxvid)

I see my old frien 'theads' is in there too. Also the global options:

[http://ffmpeg.org/ffmpeg-codecs.html#codec_002doptions](http://ffmpeg.org/ffmpeg-codecs.html#codec_002doptions)

---

### Post by andrew.46 on 2014-01-04
My brain finally clicked: there is a very nice shell script that has been around a long time that uses MEncoder to produce quality xvid files:

[http://xvidenc.sourceforge.net/](http://xvidenc.sourceforge.net/)

It is in the Ubuntu repositories...

---

