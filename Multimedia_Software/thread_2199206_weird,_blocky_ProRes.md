---
title: "weird, blocky ProRes"
date: 2014-01-12
forum: Multimedia Software
---

### Post by szegedin74 on 2014-01-12
Hi All, 
I am trying to edit video with ProRes encoding. I am running 12.10. The encoding works and I can see video files encoded with prores, but it looks all blocky (please see picture). 

Can anyone tell me what is wrong? Please let me know what info about my setup to provide. I am using the latest stable release of ffmpeg/mplayer. 
ProRes files look like this regardless of whether I view them in VLC, kdenlive, etc. I don't have problems with any other codec. 

thanks

[IMG]http://ubuntuone.com/1127cqiP1JhJ98aMdziRBy[/IMG]

---

### Post by FakeOutdoorsman on 2014-01-12
Does it play normally in QuickTime, Final Cut, or some other Apple product? Can you provide a sample file (I know it's probably huge)?

---

### Post by szegedin74 on 2014-01-13
I took the file over to a Windows XP machine and it plays fine in Quicktime there. The problem resides somewhere in my Ubuntu setup, I think, for playback. 
-
By the way, I have since found that an encoding using FFmbc produces a ProRes file that plays fine in Ubuntu. But I still need to resolve why this is happening with FFMpeg (and I suppose others must also have this problem) -- I need to FFMpeg encoder to work.

---

### Post by FakeOutdoorsman on 2014-01-13
Do you believe this is an encoding and/or a decoding bug with ffmpeg? Did you encode these files? If yes, how were they encoded? Please provide a sample, the ffmpeg command, and the complete ffmpeg console output.

---

### Post by szegedin74 on 2014-01-13
Thanks for the response. Yes I encoded them with ffmpeg like this: 

```
ffmpeg -r 23.98 -i %06d.tif -vcodec prores btif.mov
```

if I encode the same thing with ffmbc it comes out fine: 

```
 ffmbc -r 23.98 -i %06d.tif -vcodec prores btif.mov
```

It's  confusing; if I encode with ffmpeg, it looks messed up in Ubuntu, but  it looks fine in windows. If I encode in ffmbc it is fine either way. So it's the ffmpeg encoding, I guess. 

Here's the output
```
szegedin@szegedin-G31T-M:/media/szegedin/ide200/2raw/b/tif$ ffmpeg -r 23.98 -i %06d.tif -vcodec prores messedup.mov
ffmpeg version git-2014-01-05-f5f6e59 Copyright (c) 2000-2014 the FFmpeg developers
  built on Jan  5 2014 02:31:29 with gcc 4.7 (Ubuntu/Linaro 4.7.2-2ubuntu1)
   configuration: --prefix=/home/szegedin/ffmpeg_build  --extra-cflags=-I/home/szegedin/ffmpeg_build/include  --extra-ldflags=-L/home/szegedin/ffmpeg_build/lib  --bindir=/home/szegedin/bin --extra-libs=-ldl --enable-gpl  --enable-libass --enable-libfdk-aac --enable-libmp3lame --enable-libopus  --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264  --enable-nonfree --enable-x11grab
  libavutil      52. 60.100 / 52. 60.100
  libavcodec     55. 47.100 / 55. 47.100
  libavformat    55. 22.102 / 55. 22.102
  libavdevice    55.  5.102 / 55.  5.102
  libavfilter     4.  0.103 /  4.  0.103
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.104 /  0. 17.104
  libpostproc    52.  3.100 / 52.  3.100
Input #0, image2, from '%06d.tif':
  Duration: 00:00:19.72, start: 0.000000, bitrate: N/A
    Stream #0:0: Video: tiff, rgb24, 1280x720, 25 tbr, 25 tbn, 25 tbc
[prores @ 0xb384920] encoding with ProRes standard (apcn) profile
[prores @ 0xb3990c0] encoding with ProRes standard (apcn) profile
[prores @ 0xb386b40] encoding with ProRes standard (apcn) profile
Output #0, mov, to 'messedup.mov':
  Metadata:
    encoder         : Lavf55.22.102
    Stream #0:0: Video: prores (apcn) (apcn / 0x6E637061), yuv422p10le, 1280x720, q=2-31, 200 kb/s, 19184 tbn, 23.98 tbc
Stream mapping:
  Stream #0:0 -> #0:0 (tiff -> prores)
Press [q] to stop, [?] for help
frame=     7 fps=0.0 q=0.0 size=    1993kB time=00:00:00.20  bitrate=78313.4kbits/frame=   13 fps= 12 q=0.0 size=    4389kB  time=00:00:00.45 bitrate=78389.8kbits/frame=   18 fps= 11 q=0.0 size=     6387kB time=00:00:00.66 bitrate=78417.5kbits/frame=   26 fps= 12 q=0.0  size=    9582kB time=00:00:01.00 bitrate=78433.1kbits/frame=   31 fps=  12 q=0.0 size=   11576kB time=00:00:01.20 bitrate=78414.0kbits/frame=    38 fps= 12 q=0.0 size=   14375kB time=00:00:01.50  bitrate=78442.7kbits/frame=   45 fps= 12 q=0.0 size=   17161kB  time=00:00:01.79 bitrate=78397.9kbits/frame=   52 fps= 12 q=0.0 size=    19957kB time=00:00:02.08 bitrate=78409.5kbits/frame=   57 fps= 12 q=0.0  size=   21963kB time=00:00:02.29 bitrate=78444.0kbits/frame=   59 fps=  11 q=0.0 size=   22763kB time=00:00:02.37 bitrate=78449.1kbits/frame=    66 fps= 11 q=0.0 size=   25563kB time=00:00:02.66  bitrate=78463.1kbits/frame=   71 fps= 11 q=0.0 size=   27560kB  time=00:00:02.87 bitrate=78464.2kbits/frame=   78 fps= 11 q=0.0 size=    30349kB time=00:00:03.16 bitrate=78445.6kbits/frame=   83 fps= 11 q=0.0  size=   32338kB time=00:00:03.37 bitrate=78427.0kbits/frame=   90 fps=  11 q=0.0 size=   35117kB time=00:00:03.66 bitrate=78392.6kbits/frame=    96 fps= 11 q=0.0 size=   37498kB time=00:00:03.91  bitrate=78364.4kbits/frame=  102 fps= 11 q=0.0 size=   39887kB  time=00:00:04.17 bitrate=78356.6kbits/frame=  106 fps= 11 q=0.0 size=    41478kB time=00:00:04.33 bitrate=78347.7kbits/frame=  107 fps= 10 q=0.0  size=   41878kB time=00:00:04.37 bitrate=78348.6kbits/frame=  112 fps=  10 q=0.0 size=   43856kB time=00:00:04.58 bitrate=78320.8kbits/frame=   117 fps= 10 q=0.0 size=   45838kB time=00:00:04.79  bitrate=78301.4kbits/frame=  123 fps= 10 q=0.0 size=   48225kB  time=00:00:05.04 bitrate=78293.9kbits/frame=  130 fps= 10 q=0.0 size=    51014kB time=00:00:05.33 bitrate=78292.5kbits/frame=  135 fps= 10 q=0.0  size=   53013kB time=00:00:05.54 bitrate=78301.7kbits/frame=  140 fps=  10 q=0.0 size=   55002kB time=00:00:05.75 bitrate=78296.4kbits/frame=   146 fps= 10 q=0.0 size=   57389kB time=00:00:06.00  bitrate=78289.4kbits/frame=  152 fps= 10 q=0.0 size=   59770kB  time=00:00:06.25 bitrate=78276.1kbits/frame=  154 fps=9.8 q=0.0 size=    60565kB time=00:00:06.33 bitrate=78273.8kbits/frame=  161 fps=9.9 q=0.0  size=   63374kB time=00:00:06.63 bitrate=78298.6kbits/frame=  166  fps=9.9 q=0.0 size=   65376kB time=00:00:06.83  bitrate=78308.8kbits/frame=  173 fps= 10 q=0.0 size=   68159kB  time=00:00:07.13 bitrate=78300.5kbits/frame=  180 fps= 10 q=0.0 size=    70938kB time=00:00:07.42 bitrate=78288.5kbits/frame=  186 fps= 10 q=0.0  size=   73336kB time=00:00:07.67 bitrate=78295.7kbits/frame=  192 fps=  10 q=0.0 size=   75748kB time=00:00:07.92 bitrate=78316.6kbits/frame=   199 fps= 10 q=0.0 size=   78553kB time=00:00:08.21  bitrate=78331.1kbits/frame=  205 fps=9.9 q=0.0 size=   80943kB  time=00:00:08.46 bitrate=78328.6kbits/frame=  211 fps=9.9 q=0.0 size=    83314kB time=00:00:08.71 bitrate=78308.8kbits/frame=  217 fps=9.9 q=0.0  size=   85679kB time=00:00:08.96 bitrate=78284.7kbits/frame=  223  fps=9.9 q=0.0 size=   88061kB time=00:00:09.21  bitrate=78276.1kbits/frame=  230 fps= 10 q=0.0 size=   90837kB  time=00:00:09.50 bitrate=78264.7kbits/frame=  236 fps= 10 q=0.0 size=    93207kB time=00:00:09.75 bitrate=78247.7kbits/frame=  243 fps= 10 q=0.0  size=   95937kB time=00:00:10.05 bitrate=78200.4kbits/frame=  249 fps=  10 q=0.0 size=   98269kB time=00:00:10.30 bitrate=78155.1kbits/frame=   255 fps=9.9 q=0.0 size=  100594kB time=00:00:10.55  bitrate=78107.4kbits/frame=  260 fps=9.9 q=0.0 size=  102543kB  time=00:00:10.75 bitrate=78077.3kbits/frame=  266 fps=9.9 q=0.0 size=   104883kB time=00:00:11.00 bitrate=78044.0kbits/frame=  272 fps=9.9 q=0.0  size=  107218kB time=00:00:11.25 bitrate=78008.7kbits/frame=  278 fps=  10 q=0.0 size=  109535kB time=00:00:11.50 bitrate=77961.7kbits/frame=   283 fps= 10 q=0.0 size=  111471kB time=00:00:11.71  bitrate=77928.4kbits/frame=  290 fps= 10 q=0.0 size=  114205kB  time=00:00:12.01 bitrate=77898.8kbits/frame=  295 fps= 10 q=0.0 size=   116178kB time=00:00:12.21 bitrate=77892.4kbits/frame=  301 fps= 10 q=0.0  size=  118550kB time=00:00:12.46 bitrate=77888.0kbits/frame=  304  fps=9.9 q=0.0 size=  119727kB time=00:00:12.59  bitrate=77879.7kbits/frame=  309 fps=9.9 q=0.0 size=  121690kB  time=00:00:12.80 bitrate=77867.5kbits/frame=  314 fps=9.9 q=0.0 size=   123665kB time=00:00:13.01 bitrate=77862.8kbits/frame=  319 fps=9.8 q=0.0  size=  125635kB time=00:00:13.21 bitrate=77855.5kbits/frame=  325  fps=9.9 q=0.0 size=  127993kB time=00:00:13.46  bitrate=77843.6kbits/frame=  331 fps=9.9 q=0.0 size=  130360kB  time=00:00:13.71 bitrate=77837.1kbits/frame=  338 fps=9.9 q=0.0 size=   133124kB time=00:00:14.01 bitrate=77831.8kbits/frame=  343 fps=9.9 q=0.0  size=  135099kB time=00:00:14.22 bitrate=77828.3kbits/frame=  349  fps=9.9 q=0.0 size=  137457kB time=00:00:14.47  bitrate=77817.1kbits/frame=  354 fps=9.9 q=0.0 size=  139405kB  time=00:00:14.67 bitrate=77799.4kbits/frame=  357 fps=9.8 q=0.0 size=   140573kB time=00:00:14.80 bitrate=77788.3kbits/frame=  362 fps=9.8 q=0.0  size=  142513kB time=00:00:15.01 bitrate=77766.3kbits/frame=  366  fps=9.8 q=0.0 size=  144067kB time=00:00:15.17  bitrate=77750.4kbits/frame=  371 fps=9.8 q=0.0 size=  146013kB  time=00:00:15.38 bitrate=77732.7kbits/frame=  377 fps=9.8 q=0.0 size=   148353kB time=00:00:15.63 bitrate=77715.1kbits/frame=  382 fps=9.8 q=0.0  size=  150305kB time=00:00:15.84 bitrate=77701.3kbits/frame=  387  fps=9.8 q=0.0 size=  152242kB time=00:00:16.05  bitrate=77680.4kbits/frame=  392 fps=9.8 q=0.0 size=  154167kB  time=00:00:16.26 bitrate=77654.1kbits/frame=  396 fps=9.7 q=0.0 size=   155697kB time=00:00:16.43 bitrate=77629.1kbits/frame=  400 fps=9.6 q=0.0  size=  157233kB time=00:00:16.59 bitrate=77606.7kbits/frame=  405  fps=9.6 q=0.0 size=  159156kB time=00:00:16.80  bitrate=77581.3kbits/frame=  411 fps=9.6 q=0.0 size=  161458kB  time=00:00:17.05 bitrate=77548.9kbits/frame=  417 fps=9.6 q=0.0 size=   163756kB time=00:00:17.30 bitrate=77515.7kbits/frame=  422 fps=9.6 q=0.0  size=  165677kB time=00:00:17.51 bitrate=77491.0kbits/frame=  427  fps=9.6 q=0.0 size=  167592kB time=00:00:17.72  bitrate=77464.7kbits/frame=  432 fps=9.6 q=0.0 size=  169504kB  time=00:00:17.93 bitrate=77437.3kbits/frame=  438 fps=9.6 q=0.0 size=   171797kB time=00:00:18.18 bitrate=77405.0kbits/frame=  443 fps=9.6 q=0.0  size=  173710kB time=00:00:18.39 bitrate=77379.5kbits/frame=  450  fps=9.6 q=0.0 size=  176388kB time=00:00:18.68  bitrate=77344.8kbits/frame=  456 fps=9.6 q=0.0 size=  178682kB  time=00:00:18.93 bitrate=77315.0kbits/frame=  461 fps=9.6 q=0.0 size=   180594kB time=00:00:19.14 bitrate=77291.2kbits/frame=  468 fps=9.7 q=0.0  size=  183269kB time=00:00:19.43 bitrate=77257.7kbits/frame=  474  fps=9.7 q=0.0 size=  185562kB time=00:00:19.68  bitrate=77230.2kbits/frame=  479 fps=9.7 q=0.0 size=  187475kB  time=00:00:19.89 bitrate=77208.2kbits/frame=  484 fps=9.6 q=0.0 size=   189385kB time=00:00:20.10 bitrate=77186.0kbits/frame=  485 fps=9.5 q=0.0  size=  189767kB time=00:00:20.14 bitrate=77181.4kbits/frame=  488  fps=9.5 q=0.0 size=  190914kB time=00:00:20.26  bitrate=77168.5kbits/frame=  493 fps=9.4 q=0.0 Lsize=  193595kB  time=00:00:20.55 bitrate=77141.2kbits/s    
video:193591kB audio:0kB subtitle:0 global headers:0kB muxing overhead 0.001863
```

---

### Post by FakeOutdoorsman on 2014-01-14
Can you provide your output file (messedup.mov)?

---

### Post by szegedin74 on 2014-01-14
Video file looks like the picture, above, on Ubuntu. 

It's stored [here]("http://ubuntuone.com/1SdMgTfDMHDnrsb0ivfckf"), but will not download, presumably because of the encoding problem.

---

### Post by mc4man on 2014-01-14
Your seven.mov plays back fine here, tested with mpv, vlc, totem
(to download > right click > save link as.....

---

### Post by szegedin74 on 2014-01-14
> **mc4man said:**
> Your seven.mov plays back fine here, tested with mpv, vlc, totem
(to download > right click > save link as.....

Thanks for that. Are you on ubuntu 12.10? 

Does this point to my ffplay? Anyone know?

---

### Post by FakeOutdoorsman on 2014-01-14
On 12.10 recent ffplay and ffmpeg from FFmpeg decode it properly, but Libav products (avplay and fake "ffplay") in the repo do not decode it properly. Since it also works in QuickTime, but not in Libav stuff, I do not believe this is a(n existing) FFmpeg bug.

---

### Post by szegedin74 on 2014-01-14
How do I make it work?

I downloaded a "static build" of ffmpeg from ffmpeg, but I don't know how to get a different version of ffplay than the one in the build -- I don't understand what you mean by "fake ffplay" -- is there a different one I can use?

---------------

I figured out how to use the version of ffplay that was in the ffmbc that I downloaded, rather than the default in the build. This will work for my puposes. Sorted.

---

### Post by mc4man on 2014-01-14
The "static" ffmpeg build you downloaded may not contain an ffplay binary so in that case you would of been using whatever 12.10 provides for 'ffplay'. 
Either it's a link to the crappy avplay or actually ffplay from an old outdated FFmpeg source.

---

### Post by szegedin74 on 2014-01-14
I wasn't using the "static" one I mentioned (for encoding). I had downloaded it and didn't see an ffplay. I re-compiled ffmpeg as per their instructions at [https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide](https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide) so I don't see how it's old and outdated, and I still don't get how it's working on other people's systems not mine.

---

### Post by FakeOutdoorsman on 2014-01-14
> **szegedin74 said:**
> I don't understand what you mean by "fake ffplay"
See [Who can tell me the difference and relation between ffmpeg, libav, and avconv?](http://stackoverflow.com/a/9477756/1109017).

> **szegedin74 said:**
> Is there a different one I can use?
I followed the compile guide you linked to and it provided a new ffmpeg and ffplay (and ffserver which I've never used) which played it normally. Then I tried the Libav stuff in the repo (avplay and fake "ffplay") and they were both crappy. Then I tried the newer Libav stuff on Ubuntu 13.10 and the artifacts are still present.

> **szegedin74 said:**
> I wasn't using the "static" one I mentioned (for encoding). I had downloaded it and didn't see an ffplay.
The static builds are supplied by third-parties (FFmpeg does not supply any binaries), but none of the Linux builds contain ffplay.

> **szegedin74 said:**
> I re-compiled ffmpeg as per their instructions at [https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide](https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide) so I don't see how it's old and outdated, and I still don't get how it's working on other people's systems not mine.
The VLC and Kdenlive from the repo are using the broken Libav fork. VLC and Kdenlive that use recent FFmpeg stuff as dependencies instead will play the prores properly.

---

### Post by szegedin74 on 2014-01-14
Thanks that goes a long way toward explaining it. 
It's funny because kdenlive allows you to "point" it to a particular ffmpeg and ffplay, but that doesn't make a difference. 
I don't know how to get VLC or kdenlive to > use recent FFmpeg stuff as dependencies instead
Looked at recompiling MELT as advised [here]("http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/installing-source/installing-mlt-rendering-engine") but it looks daunting. 

I thought I had this solved because I can at least play back the files in Ubuntu, but VLC and kdenlive are still broken.

---

