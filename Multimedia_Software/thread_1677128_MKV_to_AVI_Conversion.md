---
title: "MKV to AVI Conversion"
date: 2011-01-28
forum: Multimedia Software
---

### Post by chome4 on 2011-01-28
Got some TV progs in MKV format which are jumpy when played through VLC. Other shows in the series AVI format play OK.

Are there any open source programs out there that can convert MKV to AVI?

Thank you.

---

### Post by howefield on 2011-01-28
Try Winff, it's a GUI for ffmpeg which will do the job.

You'll can install it from the Ubuntu Software Centre.

---

### Post by 0N3 on 2011-01-28
WinFF

---

### Post by chome4 on 2011-01-28
Thanks for that.

I'm looking at presets and when I scroll through, I can't see the extension .avi

Is there a way to import a file to make .avi appear?

---

### Post by vanadium on 2011-01-28
Winff aithout more is not an excellent suggestion. If you do not configure it, it will copy and recode your mkv file. That will take a (very) long time and result in quality loss.

You should not transcode audio and video, but directly copy the audio and video streams from the mkv to an avi (in as far as avi supports the format, that is).

avidemux is a graphical tool for that.

winff is usefull if you create a dedicated preset for it. The ffmpeg command is probably as simple as:
```

ffmpeg -acodec copy -vcodec copy -i infile.mkv outfile.avi

```

Conversion in minutes, no quality loss.

---

### Post by lukeiamyourfather on 2011-01-28
> **chome4 said:**
> Got some TV progs in MKV format which are jumpy when played through VLC. Other shows in the series AVI format play OK.

Are there any open source programs out there that can convert MKV to AVI?

Thank you.

MKV is just a muxer/container that stores multimedia streams. Converting it to AVI won't inherently make it run better because AVI is just another muxer. What matters is the video codec, bit rate, and resolution of the video stream stored within the muxer.

Chances are the video stream in that MKV is higher resolution than your computer can playback in real-time or using a codec that requires a lot of power to decode (AVC/H.264). So the issue is the performance of your machine, not the muxer of the video. If you watch a lot of videos on your computer it might be time for an upgrade.

If upgrading the hardware is not in the cards anytime soon you might consider transcoding the video stream to a different codec but keep the MKV muxer rather than going to an AVI since the muxer is not the problem here. AVI is both obsolete (circa 1992) and proprietary.

[http://en.wikipedia.org/wiki/Audio_Video_Interleave#Continued_use](http://en.wikipedia.org/wiki/Audio_Video_Interleave#Continued_use)

MKV or Matroska is neither obsolete nor proprietary.

[http://en.wikipedia.org/wiki/Matroska](http://en.wikipedia.org/wiki/Matroska)

---

### Post by vanadium on 2011-01-28
It would to be investigated in more detail or be tested: I sometimes have the impression that different containers do make a difference in cases where the hardware indeed is rather minimal to play the content.

---

### Post by FakeOutdoorsman on 2011-01-28
> **vanadium said:**
> The ffmpeg command is probably as simple as:```
ffmpeg -acodec copy -vcodec copy -i infile.mkv outfile.avi
```

You're applying "-acodec copy -vcodec copy" to the input file instead of the output. Output options come after "-i input.foo". It will probably create a working file, but a more "correct" command would follow the FFmpeg usage convention:
```
ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...
```

---

### Post by shantiq on 2011-01-28
since you want to convert more than one file may i suggest you do this in **bulk**


First go into the directory where your files are then run



```

for f in *.mkv; do ffmpeg -i "$f" -acodec copy -vcodec copy "${f%.mkv}.avi"; done
```


**and** if you want to delete the original file add

```
&& rm "$f"
```   just before ```
; done 
``` in the line above

---

### Post by Malkhut on 2011-01-29
If you're looking for an easy-to-use programme instead of terminal commands, DeVeDe works pretty well.  Choose the option to convert to DivX and it will convert all .mkv files to the .avi container, using a DivX codec.

Warning: if the .mkv file has multiple tracks for audio, subtitles, etc, it will just take the defaults and mash them all together.  You can use MKV Files Creater to easily separate out the unwanted tracks.

Both programmes are readily available in the standard repository.

---

### Post by chome4 on 2011-01-30
> **Malkhut said:**
> If you're looking for an easy-to-use programme instead of terminal commands, DeVeDe works pretty well.  Choose the option to convert to DivX and it will convert all .mkv files to the .avi container, using a DivX codec.

Warning: if the .mkv file has multiple tracks for audio, subtitles, etc, it will just take the defaults and mash them all together.  You can use MKV Files Creater to easily separate out the unwanted tracks.

Both programmes are readily available in the standard repository.

DeVeDe did the trick with no fuss and gave a perfect copy!

Thank you very, very much.

---

### Post by Mars-x on 2011-11-24
Hi

I try to convert a file from *.mkv to *.avi using console:
```
ffmpeg -i infile.mkv -acodec copy -vcodec copy outfile.avi
``` 
but i get this:
```

  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Sep 16 2011 17:04:18, gcc: 4.4.3
[matroska @ 0x9432a60]Unknown entry 0x4484

Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
    Last message repeated 4 times
Input #0, matroska, from 'infile.mkv':
  Duration: 04:09:07.44, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264, yuv420p, 1280x720, PAR 1:1 DAR 16:9, 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: vorbis, 48000 Hz, stereo, s16
Output #0, avi, to 'outfile.avi':
    Stream #0.0: Video: libx264, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], q=2-31, 90k tbn, 25 tbc
    Stream #0.1: Audio: vorbis, 48000 Hz, stereo, s16
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
[NULL @ 0x9452430]error, non monotone timestamps 3 >= 2
av_interleaved_write_frame(): Error while opening file

```

can anyone help?

PS. I've tried WinFF but the quality is auwful.

---

### Post by sammiev on 2011-11-24
Just use VLC to convert MKV to AVI. :)

---

### Post by FakeOutdoorsman on 2011-11-24
> **Mars-x said:**
> can anyone help?
You are attempting to stuff H.264 video and Vorbis audio into the AVI container. AVI does not support H.264 video if it contains "b-frames" which is often the case, and I doubt Vorbis does well in this moth-eaten, aging multimedia container.

If you must use AVI, then re-encode to formats that it can support. Example:
```
ffmpeg -i input -vcodec mpeg4 -qscale 4 -acodec libmp3lame -aq 4 output.avi
```
Make sure to [enable the mp3 encoder](http://ubuntuforums.org/showthread.php?t=1117283) (see option B) if you decide to try this command. Adjust qscale to change video quality (3-5 is a good range, lower is higher quality) and aq for audio quality (when using libmp3lame aq is mapped to the "lame -V" option, lower is higher quality).

---

### Post by Mars-x on 2011-11-26
@FakeOutdoorsman thank You for this command and explanation.

---

