---
title: "hard inserting subs"
date: 2013-11-10
forum: Multimedia Software
---

### Post by jmachacek13 on 2013-11-10
I have a mkv video and external srt subs. How to hard insert the subs into a new video file? (mp4, preferably) I studied mencoder parameters for over an hour but couldn't find it out :( Tnx for any help!

---

### Post by FakeOutdoorsman on 2013-11-11
1. You'll need the real ffmpeg from FFmpeg because the junkfood (the [fake, so-called "ffmpeg"](http://stackoverflow.com/a/9477756/1109017)) they feed you from the repo is lacking in usefulness. You can forge your own path and refer to a [step-by-step guide to compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide), or you can simply download a [Linux build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds) which will work too:

```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date +"%F").tar.gz
tar xzvf ffmpeg.static.32bit.$(date +"%F").tar.gz

```

If this doesn't work then just go to the [FFmpeg Download](http://ffmpeg.org/download.html) page.

2. Now run the command (note the ./ before ffmpeg):
```
./ffmpeg -i video.mkv -vf subtitles=subtitles.srt -codec:v libx264 -crf 23 -preset medium -codec:a copy output.mkv
```

[Stream copying](http://ffmpeg.org/ffmpeg.html#Stream-copy) the audio is recommended if your [output container can support the audio format](http://en.wikipedia.org/wiki/Comparison_of_container_formats). If not (ffmpeg may complain in the console output), then instead of "-codec:a copy" use "-c:a aac -strict experimental -b:a 192k" if you're using static build that you simply downloaded, or "-c:a libfdk_aac -vbr 5" if you compiled ffmpeg.

Using video filters requires re-encoding of the video.

Also see:
[list]
[*][FFmpeg and x264 Encoding Guide](https://trac.ffmpeg.org/wiki/x264EncodingGuide)
[*][FFmpeg and AAC Encoding Guide](https://trac.ffmpeg.org/wiki/AACEncodingGuide)
[*][FFmpeg Documentation: subtitles video filter](http://ffmpeg.org/ffmpeg-filters.html#subtitles-1)
[*][FFmpeg Wiki: How to burn subtitles into the video](https://trac.ffmpeg.org/wiki/How%20to%20burn%20subtitles%20into%20the%20video)
[/list]

---

### Post by jmachacek13 on 2013-11-11
Thank you for your reply, FakeOutdoorsman!
I compiled ffmpeg from git with no parameters. When I run your command I get this error:

```
au@howth:~/tmp/ffmpeg$ ./ffmpeg -i ~/f/PTP2/B1.mkv -vf subtitles=~/f/PTP2/B1.srt -codec:v libx264 -crf 23 -preset medium -c:a libfdk_aac -vbr 5 outOOO.mp4
ffmpeg version N-58020-gbdab242 Copyright (c) 2000-2013 the FFmpeg developers
  built on Nov 11 2013 20:47:07 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: 
  libavutil      52. 52.100 / 52. 52.100
  libavcodec     55. 41.100 / 55. 41.100
  libavformat    55. 21.100 / 55. 21.100
  libavdevice    55.  5.100 / 55.  5.100
  libavfilter     3. 90.102 /  3. 90.102
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.104 /  0. 17.104
Unrecognized option 'crf'.
Error splitting the argument list: Option not found


```

---

### Post by FakeOutdoorsman on 2013-11-11
> **jmachacek13 said:**
> 
```

  configuration:

```

Your ffmpeg was not configured to support libx264 (the H.264 video encoder). You at least need --enable-gpl and --enable-libx264. The compile guide should have provided this.

Or you can just download one of the ffmpeg builds.

---

### Post by jmachacek13 on 2013-11-12
thank you again! I downloaded the build and it works! Now only one problem: I want a small cut only. But with these parameters:

```
./ffmpeg -ss 01:41:03 -i ~/f/PTP2/B1.mkv -t 26 -vf subtitles=~/f/PTP2/B2srt.srt -codec:v libx264 -crf 23 -preset medium -c:a copy OUT4.mp4
```

it is cut properly but the subs are not embeded. Could you help me with this one too, please?

---

### Post by FakeOutdoorsman on 2013-11-12
Please show the complete ffmpeg console output that goes with your command.

---

### Post by jmachacek13 on 2013-11-12
There is also another problem, in 0:00:26 it jumbs to s 0:00:31 (no idea why) (the whole video takes 31s instead of 26 but the last five are empty)

```

au@howth:~/tmp/ffmpeg-static$ ./ffmpeg -ss 01:41:03 -i ~/f/PTP2/B1.mkv -t 26 -vf subtitles=~/f/PTP2/B2srt.srt -codec:v libx264 -crf 23 -preset medium -c:a copy OUT8.mp4
ffmpeg version N-58039-gda9d360 Copyright (c) 2000-2013 the FFmpeg developers
  built on Nov 12 2013 05:14:43 with gcc 4.6 (Debian 4.6.3-1)
  configuration: --prefix=/root/ffmpeg-static/32bit --arch=x86_32 --extra-cflags='-m32 -I/root/ffmpeg-static/32bit/include -static' --extra-ldflags='-m32 -L/root/ffmpeg-static/32bit/lib -static' --extra-libs='-lxml2 -lexpat -lfreetype' --enable-static --disable-shared --disable-ffserver --disable-doc --enable-bzlib --enable-zlib --enable-postproc --enable-runtime-cpudetect --enable-libx264 --enable-gpl --enable-libtheora --enable-libvorbis --enable-libmp3lame --enable-gray --enable-libass --enable-libfreetype --enable-libopenjpeg --enable-libspeex --enable-libvo-aacenc --enable-libvo-amrwbenc --enable-version3 --enable-libvpx
  libavutil      52. 52.100 / 52. 52.100
  libavcodec     55. 41.100 / 55. 41.100
  libavformat    55. 21.100 / 55. 21.100
  libavdevice    55.  5.100 / 55.  5.100
  libavfilter     3. 90.102 /  3. 90.102
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.104 /  0. 17.104
  libpostproc    52.  3.100 / 52.  3.100
Input #0, matroska,webm, from '/home/au/f/PTP2/B1.mkv':
  Metadata:
    creation_time   : 2011-04-14 01:15:57
  Duration: 01:42:58.13, start: 0.000000, bitrate: 2022 kb/s
    Stream #0:0(fre): Video: h264 (High), yuv420p, 704x480 [SAR 10:11 DAR 4:3], 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc (default)
    Metadata:
      title           : Video Track
    Stream #0:1(fre): Audio: ac3, 48000 Hz, stereo, fltp, 192 kb/s (default)
    Metadata:
      title           : Audio Track
    Stream #0:2(eng): Subtitle: subrip (default)
    Metadata:
      title           : Subtitle Track
Fontconfig error: Cannot load default config file
[Parsed_subtitles_0 @ 0xa7dbb00] No usable fontconfig configuration file found, using fallback.
Fontconfig error: Cannot load default config file
[libx264 @ 0xa7d90a0] using SAR=10/11
[libx264 @ 0xa7d90a0] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2 AVX
[libx264 @ 0xa7d90a0] profile High, level 3.0
[libx264 @ 0xa7d90a0] 264 - core 129 r2230 1cffe9f - H.264/MPEG-4 AVC codec - Copyleft 2003-2012 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=6 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=23 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00
[mp4 @ 0xa8c1380] track 1: codec frame size is not set
Output #0, mp4, to 'OUT8.mp4':
  Metadata:
    encoder         : Lavf55.21.100
    Stream #0:0(fre): Video: h264 (libx264) ([33][0][0][0] / 0x0021), yuv420p, 704x480 [SAR 10:11 DAR 4:3], q=-1--1, 24k tbn, 23.98 tbc (default)
    Metadata:
      title           : Video Track
    Stream #0:1(fre): Audio: ac3 ([165][0][0][0] / 0x00A5), 48000 Hz, stereo, 192 kb/s (default)
    Metadata:
      title           : Audio Track
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> libx264)
  Stream #0:1 -> #0:1 (copy)
Press [q] to stop, [?] for help
[Parsed_subtitles_0 @ 0xa7dbb00] Neither PlayResX nor PlayResY defined. Assuming 384x288
frame=   21 fps=0.0 q=0.0 size=       0kB time=00:00:01.37 bitrate=   0.3kbits/sframe=   58 fps= 57 q=28.0 size=     156kB time=00:00:02.65 bitrate= 481.4kbits/frame=   75 fps= 49 q=28.0 size=     236kB time=00:00:03.42 bitrate= 563.5kbits/frame=   90 fps= 44 q=28.0 size=     300kB time=00:00:04.19 bitrate= 586.4kbits/frame=  107 fps= 42 q=28.0 size=     369kB time=00:00:04.96 bitrate= 609.0kbits/frame=  126 fps= 41 q=28.0 size=     436kB time=00:00:05.72 bitrate= 624.2kbits/frame=  143 fps= 40 q=28.0 size=     491kB time=00:00:06.36 bitrate= 631.9kbits/frame=  161 fps= 39 q=28.0 size=     555kB time=00:00:07.13 bitrate= 636.7kbits/frame=  178 fps= 38 q=28.0 size=     635kB time=00:00:07.90 bitrate= 657.9kbits/frame=  193 fps= 37 q=28.0 size=     711kB time=00:00:08.44 bitrate= 689.7kbits/frame=  211 fps= 37 q=28.0 size=     769kB time=00:00:09.21 bitrate= 683.5kbits/frame=  231 fps= 37 q=28.0 size=     841kB time=00:00:10.20 bitrate= 675.0kbits/frame=  249 fps= 37 q=28.0 size=     904kB time=00:00:10.72 bitrate= 690.8kbits/frame=  265 fps= 37 q=28.0 size=     970kB time=00:00:11.29 bitrate= 703.8kbits/frame=  280 fps= 36 q=28.0 size=    1019kB time=00:00:12.09 bitrate= 690.1kbits/frame=  301 fps= 36 q=28.0 size=    1124kB time=00:00:13.08 bitrate= 703.7kbits/frame=  320 fps= 36 q=28.0 size=    1184kB time=00:00:13.85 bitrate= 699.7kbits/frame=  339 fps= 36 q=28.0 size=    1279kB time=00:00:14.62 bitrate= 716.6kbits/frame=  358 fps= 36 q=28.0 size=    1332kB time=00:00:15.29 bitrate= 713.2kbits/frame=  381 fps= 37 q=28.0 size=    1397kB time=00:00:16.28 bitrate= 702.5kbits/frame=  400 fps= 37 q=28.0 size=    1437kB time=00:00:17.05 bitrate= 690.1kbits/frame=  417 fps= 36 q=28.0 size=    1531kB time=00:00:17.82 bitrate= 703.7kbits/frame=  431 fps= 36 q=28.0 size=    1569kB time=00:00:18.33 bitrate= 701.0kbits/frame=  449 fps= 36 q=28.0 size=    1621kB time=00:00:19.10 bitrate= 695.1kbits/frame=  469 fps= 36 q=28.0 size=    1680kB time=00:00:20.00 bitrate= 688.3kbits/frame=  485 fps= 36 q=28.0 size=    1727kB time=00:00:20.76 bitrate= 681.2kbits/frame=  502 fps= 35 q=28.0 size=    1774kB time=00:00:21.31 bitrate= 682.0kbits/frame=  522 fps= 35 q=28.0 size=    1844kB time=00:00:22.08 bitrate= 684.3kbits/frame=  540 fps= 35 q=28.0 size=    1917kB time=00:00:22.84 bitrate= 687.2kbits/frame=  559 fps= 35 q=28.0 size=    2007kB time=00:00:23.80 bitrate= 690.7kbits/frame=  577 fps= 35 q=28.0 size=    2079kB time=00:00:24.54 bitrate= 693.8kbits/frame=  594 fps= 35 q=28.0 size=    2133kB time=00:00:25.31 bitrate= 690.3kbits/frame=  608 fps= 35 q=28.0 size=    2202kB time=00:00:25.69 bitrate= 702.1kbits/frame=  623 fps= 35 q=28.0 size=    2326kB time=00:00:23.81 bitrate= 799.9kbits/frame=  624 fps= 32 q=-1.0 Lsize=    2722kB time=00:00:26.01 bitrate= 857.1kbits/s    
video:1976kB audio:728kB subtitle:0 global headers:0kB muxing overhead 0.660614%
[libx264 @ 0xa7d90a0] frame I:8     Avg QP:20.71  size: 31786
[libx264 @ 0xa7d90a0] frame P:191   Avg QP:22.82  size:  6412
[libx264 @ 0xa7d90a0] frame B:425   Avg QP:24.65  size:  1279
[libx264 @ 0xa7d90a0] consecutive B-frames:  2.2% 17.9%  8.7% 71.2%
[libx264 @ 0xa7d90a0] mb I  I16..4:  3.7% 88.0%  8.3%
[libx264 @ 0xa7d90a0] mb P  I16..4:  0.3%  4.5%  0.4%  P16..4: 46.9% 15.1%  8.9%  0.0%  0.0%    skip:23.9%
[libx264 @ 0xa7d90a0] mb B  I16..4:  0.0%  0.2%  0.0%  B16..8: 47.9%  2.0%  0.2%  direct: 0.6%  skip:48.9%  L0:42.8% L1:54.3% BI: 2.9%
[libx264 @ 0xa7d90a0] 8x8 transform intra:87.1% inter:81.1%
[libx264 @ 0xa7d90a0] coded y,uvDC,uvAC intra: 83.9% 0.0% 0.0% inter: 14.2% 0.0% 0.0%
[libx264 @ 0xa7d90a0] i16 v,h,dc,p: 25% 27% 19% 29%
[libx264 @ 0xa7d90a0] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 10% 16% 28%  5%  8%  7%  9%  6%  9%
[libx264 @ 0xa7d90a0] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 15% 20% 15%  6% 10%  9% 11%  6%  7%
[libx264 @ 0xa7d90a0] i8c dc,h,v,p: 100%  0%  0%  0%
[libx264 @ 0xa7d90a0] Weighted P-Frames: Y:14.7% UV:0.0%
[libx264 @ 0xa7d90a0] ref P L0: 58.0% 20.7% 15.1%  5.4%  0.7%
[libx264 @ 0xa7d90a0] ref B L0: 88.4%  9.7%  1.9%
[libx264 @ 0xa7d90a0] ref B L1: 95.0%  5.0%
[libx264 @ 0xa7d90a0] kb/s:621.73


```

---

### Post by FakeOutdoorsman on 2013-11-12
Can you provide the input srt file (B2srt.srt) and the output (OUT8.mp4)?

---

### Post by jmachacek13 on 2013-11-12
[http://www.ulozto.net/x4fdLmQT/b2srt-srt](http://www.ulozto.net/x4fdLmQT/b2srt-srt)
[http://www.ulozto.net/xBVyTuwJ/out8-mp4](http://www.ulozto.net/xBVyTuwJ/out8-mp4)
hope you're able to download it

---

### Post by shantiq on 2013-11-13
also mkvmerge is a route one can take if using mkv obviously

```
 sudo apt-get install mkvtoolnix
```



**&#9679; Basic Info**

```
 mkvmerge -i MovieFile.mkv
```

You’ll see a listing similar to this:

File 'MovieFile.mkv': container: Matroska
Track ID 1: subtitles (S_TEXT/ASS)
Track ID 2: audio (A_MPEG/L3)
Track ID 3: video (V_MPEG4/ISO/AVC)
Next, use mkvextract to extract certain tracks / attachments based on the output from the above command:

mkvextract tracks MovieFile.mkv 1:thesubtitles.srt
2:theaudio.mp3 3:thevideo.mp4





** &#9679;  TO  add sub default or forced**   [here replace --default-track with  --forced-track]

```
 mkvmerge -o <output>.mkv --default-track 0 --language 0:<language> <subtitles>.srt <input> 
```

ex:    ```
mkvmerge -o <output>.mkv --default-track 0 --language 0:eng <subtitles>.srt <input>
```

You can list the language codes by invoking mkvmerge with the --list-languages (e.g. eng for English, ger for German) parameter. The --default-track parameter just sets the newly muxed subtitles as default for the player to use. If you are muxing multiple subtitles, you of course have to change the language code preceding number.


Nota Bene: pay attention to the fact that output is first and input last in this syntax  ... not intuitive in my view ...   great program tho

---

### Post by shantiq on 2013-11-13
[**[COLOR=#000000]jmachacek13[/COLOR]**]("http://ubuntuforums.org/member.php?u=1879887")   the video you posted lasts 31 seconds

the srt you posted starts at 55 seconds and lasts 1h 41mn    this cannot work:KS   you may have posted the wrong srt ::]]

maybe av a look again  ,,   shan

PS   none of the spoken French is present in the English text [I am bilingual FR-ENG]

PS 2 : film looks brilliant what is the title please? ::]

---

### Post by jmachacek13 on 2013-11-13
> **shantiq said:**
> [**[COLOR=#000000]jmachacek13[/COLOR]**]("http://ubuntuforums.org/member.php?u=1879887")   the video you posted lasts 31 seconds

the srt you posted starts at 55 seconds and lasts 1h 41mn    this cannot work:KS   you may have posted the wrong srt ::]]

maybe av a look again  ,,   shan

PS   none of the spoken French is present in the English text [I am bilingual FR-ENG]

PS 2 : film looks brilliant what is the title please? ::]

FakeOutdoorsman asked for the INPUT srt file and OUTPUT video of his command which I provided. 

//
The title is "Bob le flambeur" (1956) and it's the best noir I've ever seen. Very good film! Recommended btw.
What I'd like is cut the funny part (some 24 seconds) and provide it with Czech subtitles. However I haven't succeeded yet :/

---

### Post by shantiq on 2013-11-13
thank you J   best of luck with srt  [i do not understand what is going on clearly ::]] ,  will check the movie ,   it is famous but have never seen it


i get it now


> 851
01:41:05,135 --> 01:41:08,127
Pokus a úmysl p&#345;ímý,
to je 5 let nepodmín&#283;n&#283;.

852
01:41:08,204 --> 01:41:10,069
Dobrý právník by to mohl sní&#382;it

853
01:41:10,140 --> 01:41:13,166
na 3 roky.

854
01:41:13,243 --> 01:41:14,574
*Skv&#283;lý* právník

855
01:41:14,644 --> 01:41:17,977
vylou&#269;í úmysl a bude zpro&#353;t&#283;ní viny.

856
01:41:18,047 --> 01:41:20,572
A TOP právník

857
01:41:20,650 --> 01:41:22,948
vás bude &#382;alovat o náhradu &#353;kody.

that is the Czech for the spoken French

Would not using a subtitle editor be the best route here on such a short piece of video?   any of those  ...   i have used most of them and all good

[ATTACH=CONFIG]247805[/ATTACH]

---

