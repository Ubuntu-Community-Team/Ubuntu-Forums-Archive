---
title: "Converting from media with 2 audio tracks"
date: 2014-07-21
forum: Multimedia Software
---

### Post by budworthtdog2 on 2014-07-21
I have experience converting media using VLC but have run into something  somewhat unique from my usual conversion needs. I am trying to convert  an avi file that has 2 audio tracks. It is a German movie and track 1 is  Russian over-dub and track 2 is the original German audio. I want to  convert it to a mkv file with only the German audio. I can't find an  option in the convert tool where it will let me select what audio track  to use from the original media. 

Is this possible? If it's not a  direct option is there a multi-step workaround? My educated guess in  such a case would be to first extract the track 2 audio from the video  into an mp3 file and then combine just the video from the avi file with  the newley created mp3 file. I do know how to extract audio from a video  file using the convert tool but again I run into the problem that it is  track 2 I want and not track 1. Any ideas out there?

---

### Post by mikewhatever on 2014-07-21
You can use ffmpeg from the repositories for something like this, here are some examples: [https://trac.ffmpeg.org/wiki/How%20to%20use%20-map%20option](https://trac.ffmpeg.org/wiki/How%20to%20use%20-map%20option). Basically, you'll need to reincode while copying the video and the German audio.
If you need more help, please post the output of <ffmpeg -i filename.avi>.

PS: There is also a GUI called winff, but I don't know if it has that option.

---

### Post by budworthtdog2 on 2014-07-22
This deffinittly looks like what I am looking for, I will have to take  you up on the offer for more help though. I checked out the GUI but it  looks like it doesnt have the advanced option of selecting what audio  stream to copy. Here is the requested output from the command you posted  

Input #0, avi, from 'Friendship.avi':
  Metadata:
    encoder         : VirtualDubMod 1.5.10.2 (build 2540/release)
  Duration: 01:44:40.04, start: 0.000000, bitrate: 1873 kb/s
    Stream #0.0: Video: mpeg4 (Advanced Simple Profile), yuv420p, 720x400 [PAR 1:1 DAR 9:5], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
    Stream #0.2: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s


I believe Stream #0.2 is the audio track I am wanting in the output file and want to drop Stream #0.1 all together

---

### Post by ron998 on 2014-07-22
> **budworthtdog2 said:**
> Here is the requested output from the command you posted  

Input #0, avi, from 'Friendship.avi':
  Metadata:
    encoder         : VirtualDubMod 1.5.10.2 (build 2540/release)
  Duration: 01:44:40.04, start: 0.000000, bitrate: 1873 kb/s
    Stream #0.0: Video: mpeg4 (Advanced Simple Profile), yuv420p, 720x400 [PAR 1:1 DAR 9:5], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
    Stream #0.2: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s


I believe Stream #0.2 is the audio track I am wanting in the output file and want to drop Stream #0.1 all together

Hi
This is a command to use with FFmpeg:-
```
ffmpeg -i Friendship.avi -c copy -map 0:0 -map 0:2 Friendship.mkv
```

---

### Post by budworthtdog2 on 2014-07-22
I copied and pasted that command and this was the output

ffmpeg version 0.8.13-6:0.8.13-0ubuntu0.13.10.1, Copyright (c) 2000-2014 the Libav developers
  built on Jul 15 2014 13:48:35 with gcc 4.8.1
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[mpeg4 @ 0x24d8780] Invalid and inefficient vfw-avi packed B frames detected
Input #0, avi, from 'Friendship.avi':
  Metadata:
    encoder         : VirtualDubMod 1.5.10.2 (build 2540/release)
  Duration: 01:44:40.04, start: 0.000000, bitrate: 1873 kb/s
    Stream #0.0: Video: mpeg4 (Advanced Simple Profile), yuv420p, 720x400 [PAR 1:1 DAR 9:5], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
    Stream #0.2: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
Unrecognized option 'c'
Failed to set value 'copy' for option 'c'

---

### Post by ron998 on 2014-07-23
> **budworthtdog2 said:**
> ffmpeg version 0.8.13-6:0.8.13-0ubuntu0.13.10.1, Copyright (c) 2000-2014 the Libav developers
  built on Jul 15 2014 13:48:35 with gcc 4.8.1
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.A different command is needed for this program.:(

If you're not comfortable with FFmpeg, try using **mkvtoolnix-gui** instead.

This is result with **FFmpeg**.;)
```
@Xubuntu:~$ ffmpeg -i Friendship.avi -c copy -map 0:0 -map 0:2 Friendship.mkv
ffmpeg version 2.2.git-a613257 Copyright (c) 2000-2014 the FFmpeg developers
  built on Jul 23 2014 06:09:18 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
  configuration: 
  libavutil      52. 92.101 / 52. 92.101
  libavcodec     55. 69.100 / 55. 69.100
  libavformat    55. 48.101 / 55. 48.101
  libavdevice    55. 13.102 / 55. 13.102
  libavfilter     4. 11.102 /  4. 11.102
  libswscale      2.  6.100 /  2.  6.100
  libswresample   0. 19.100 /  0. 19.100
Input #0, avi, from 'Friendship.avi':
  Metadata:
    encoder         : Lavf55.47.100
  Duration: 00:00:50.02, start: 0.000000, bitrate: 1333 kb/s
    Stream #0:0: Video: mpeg4 (Simple Profile) (FMP4 / 0x34504D46), yuv420p, 512x288 [SAR 1:1 DAR 16:9], 931 kb/s, 25 fps, 25 tbr, 25 tbn, 25 tbc
    Stream #0:1: Audio: ac3 ([0] [0][0] / 0x2000), 48000 Hz, stereo, fltp, 192 kb/s
    Stream #0:2: Audio: ac3 ([0] [0][0] / 0x2000), 48000 Hz, stereo, fltp, 192 kb/s
Output #0, matroska, to 'Friendship.mkv':
  Metadata:
    encoder         : Lavf55.48.101
    Stream #0:0: Video: mpeg4 (FMP4 / 0x34504D46), yuv420p, 512x288 [SAR 1:1 DAR 16:9], q=2-31, 931 kb/s, 25 fps, 1k tbn, 25 tbc
    Stream #0:1: Audio: ac3 ([0] [0][0] / 0x2000), 48000 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:2 -> #0:1 (copy)
Press [q] to stop, [?] for help
frame= 1248 fps=943 q=-1.0 Lsize=    6873kB time=00:00:50.01 bitrate=1125.7kbits/s
```

---

### Post by andrew.46 on 2014-07-23
Perhaps try:

```

ffmpeg -i Friendship.avi \
        -map 0:0 -map 0:2 \
        -c:a copy -c:v copy \
         Friendship.mkv

```

and think about updating your installation of FFmpeg.....

**Edit: **Or perhaps for older versions of FFmpeg:

```

-acodec copy -vcodec copy

```

---

### Post by budworthtdog2 on 2014-07-23
[B]mkvtoolnix-gui worked perfectly, thanks for your help 
[/B]

---

