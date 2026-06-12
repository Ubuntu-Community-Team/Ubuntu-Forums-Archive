---
title: "WinFF issue"
date: 2013-06-03
forum: Multimedia Software
---

### Post by Toxic Tom on 2013-06-03
I have been trying to use WinFF to convert some video files (MTS) to something that will work in PiTiVi but I'm not having much luck. I have avconv installed and everything seems to work correctly but when I go to the directory where I set the video to convert to, It is empty. Every time. Also I get a text file (with the same name as the video I try to convert) in /home/tom that contains this: CRC=0xa3a40090 or similar (the CRC bit is always the same but the code at the end differs). So what is going on here?

---

### Post by Merrattic on 2013-06-03
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=1572473&highlight=MTS](http://ubuntuforums.org/showthread.php?t=1572473&highlight=MTS)

You may need to compile "proper" ffmpeg (or use a binary download ) to get the commands to work.

---

### Post by Toxic Tom on 2013-06-04
So by proper ffmpeg you mean not avconv? It's weird because the readouts saying how much has been converted comes up, but there is no file outputted.

Thanks for the link too!

---

### Post by Toxic Tom on 2013-06-04
Okay so I followed the instructions in the link you gave me and the file is converted correctly BUT there is a very choppy/stuttering picture, what can I do about that?

---

### Post by Toxic Tom on 2013-06-08
Help?

---

### Post by FakeOutdoorsman on 2013-06-09
You can use ffmpeg to make a temporary intermediate file for editing:
```
ffmpeg -i input -vcodec huffyuv -acodec pcm_s16le -ac 2 output.mkv
```
Yes, this file will be huge because it is using a lossless format, but it will be editor friendly. Once you're done you can delete these if you like.

---

### Post by Toxic Tom on 2013-06-09
Thanks! I'll try that!

---

### Post by Toxic Tom on 2013-06-10
Thanks a lot for that syntax, is there a way that I could batch process a folder of MTS files into another folder of MKV files?

---

### Post by FakeOutdoorsman on 2013-06-10
Sure, with a bash "for loop":

```
mkdir output
for f in *.MTS; do ffmpeg -i "$f" -vcodec huffyuv -acodec pcm_s16le -ac 2 output/"${f%.MTS}.mkv"; done
```

Although you may want to see if the original audio works fine instead of re-encoding and possibly changing the number of channels:
```
ffmpeg -i input -vcodec huffyuv -acodec copy output.mkv
```

---

### Post by Toxic Tom on 2013-06-11
Thanks for that! Where do I put the input and output directory paths if I don't want to cd or mkdir to them first?

---

### Post by FakeOutdoorsman on 2013-06-11
I forgot about the directory in the example. I updated it.

---

### Post by Toxic Tom on 2013-06-11
Also why does a 1.7GB file turn into a 40.1GB file after the convert? What makes the file so big? Surely lossless just means that the file quality is not reduced in any way, not that it is HUGE?


Another thing, the files I am trying to convert are MTS, H264 video and stereo AC3 audio. Can I just copy the encoding setting from the MTS and put them in the mkv? For example: ```
ffmpeg -i input -vcodec copy -acodec copy output.mkv
```

or is this the same as just changing the file extension?

Would doing something like that reduce the file size?

I really don't know much about digital video.

Thank you!

---

### Post by Toxic Tom on 2013-06-11
> **FakeOutdoorsman said:**
> I forgot about the directory in the example. I updated it.
Thanks, is the input directory where you wrote "in"?

---

### Post by FakeOutdoorsman on 2013-06-11
> **Toxic Tom said:**
> Also why does a 1.7GB file turn into a 40.1GB file after the convert? What makes the file so big? Surely lossless just means that the file quality is not reduced in any way, not that it is HUGE?

Lossless is generally huge. I suggested a lossless format because you said the video was choppy. I assumed you meant it was playing choppy in your editor. Although the lossless file is obese it should be easier for the editor to decode, so hopefully resulting in something easier to edit. The lossless files are meant to be temporary just so you have a format that is editor friendly in addition to not losing any quality due to the extra step of converting.

> **Toxic Tom said:**
> Another thing, the files I am trying to convert are MTS, H264 video and stereo AC3 audio. Can I just copy the encoding setting from the MTS and put them in the mkv?
That is [stream copying](https://ffmpeg.org/ffmpeg.html#Stream-copy), or re-muxing. You can try it, but I doubt it will help because the H.264 video is probably the culprit.

> **Toxic Tom said:**
> or is this the same as just changing the file extension?
It is different since you are copying the video and audio from one container format to another. See [What is a Codec? What is a Container? What is the difference?](http://slhck.wordpress.com/2011/06/23/what-is-a-codec-what-is-a-container-what-is-the-difference/)

> **Toxic Tom said:**
> Would doing something like that reduce the file size?
No, unless the input file contains multiple video and audio streams. By default these additional streams will be ignored by ffmpeg unless you tell it not to with the "-map" option (see [stream selection](https://ffmpeg.org/ffmpeg.html#Stream-selection)).

> **Toxic Tom said:**
> Thanks, is the input directory where you wrote "in"?
You mean in the "for loop"? No, the example assumes you are in the directory containing the videos you want to convert.

At this point the first step is to see if the lossless version is an actual improvement over the original. Is it choppy too?

---

### Post by Toxic Tom on 2013-06-11
The (losslessly converted) files convert fine and work okay when editing, certainly much better than the MTS files. The only thing is they are huge and I feel they are slowing down editing as they are having to be streamed from the disk constantly (and that is slow with files that big!). The origional files were not choppy when played back, it was when they were converted by using the instructions in the link the other guy posted that they were choppy.

How can I modify that batch convert code so the input directory can be specified? The only reason I ask is because I am writing a simple GUI python script so that I can achieve this quicker (and learn python).

---

### Post by FakeOutdoorsman on 2013-06-11
> **Toxic Tom said:**
> How can I modify that batch convert code so the input directory can be specified?

What have you tried? Some basic experimentation and research may prove to be faster than my replies. Here's a lazy method:

```
cd /path/to/directory && for f in *.MTS; do ...
```

---

### Post by Toxic Tom on 2013-06-12
Awesome thanks! Sorry if I'm being a pain.

---

### Post by Toxic Tom on 2013-06-12
Okay so if I write ```
for f in INPUT_DIRECTORY/*.MTS; do ffmpeg -i "$f" -vcodec huffyuv -acodec pcm_s16le -ac 2 OUTPUT_DIRECTORY/"${f%.MTS}.mkv"; done
```

  The files end up being outputted to OUTPUT_DIRECTORY//INPUT_DIRECTORY/*.mkv which of course does not exist. How can I stop this from happening?

---

### Post by Merrattic on 2013-06-12
Give a full path e.g

```

for f in /home/merrattic/input/*.MTS; do ffmpeg -i "$f" -vcodec huffyuv -acodec pcm_s16le -ac 2 /home/merrattic/output/"${f%.MTS}.mkv"; done

```

---

### Post by Toxic Tom on 2013-06-12
> **Merrattic said:**
> Give a full path e.g

```

for f in /home/merrattic/input/*.MTS; do ffmpeg -i "$f" -vcodec huffyuv -acodec pcm_s16le -ac 2 /home/merrattic/output/"${f%.MTS}.mkv"; done

```
Yes that's what I did

---

### Post by FakeOutdoorsman on 2013-06-12
I forgot that the bash parameter expression in my example will include everything after "in" to the semicolon. I updated my example using a less elegant solution. See [How can I use parameter expansion?](http://mywiki.wooledge.org/BashFAQ/073) if you want to experiment with a better method.

---

### Post by Toxic Tom on 2013-06-12
Okay I'll try it...

 Just to be sure, the code you are now suggesting is this?:

```
cd input && for f in *.MTS; do ffmpeg -i "$f" -vcodec huffyuv -acodec pcm_s16le -ac 2 output/"${f%.MTS}.mkv"; done
```

---

### Post by Toxic Tom on 2013-06-13
> **FakeOutdoorsman said:**
> I forgot that the bash parameter expression in my example will include everything after "in" to the semicolon. I updated my example using a less elegant solution. See [How can I use parameter expansion?]("http://mywiki.wooledge.org/BashFAQ/073") if you want to experiment with a better method.


OK, that works perfectly. Thank you for your time!

---

