---
title: "ffmpeg audio encoding problem"
date: 2010-03-20
forum: Multimedia Software
---

### Post by sideshowmel on 2010-03-20
I am experiencing an issue that is very difficult to narrow down.

I had installed ffmpeg a while ago in Jaunty, before the ffmpeg team removed AAC support.  When I upgraded to Karmic, I found AAC was missing.  After further research, I found several articles on the Ubuntu wiki and this forum on how to build ffmpeg from source and enable AAC support.  That procedure was successful.  

Now I have a new problem.  Encoding WAV-to-AAC or DTS-to-AAC (I know, DTS is AAC, but nonetheless I need to cut down from 5.1 to 2 channel audio due to the stupid XBox360 codec requirements) produces a significantly degraded audio file.  Just to make sure my source wasn't bad, I tried on audio that had previously worked with the exact same settings.  

So something has changed and I don't know how to proceed.  I have found no other posts anywhere by users with similar issues.  Basically the audio sounds "tinny" and every other word sounds very electronic... a bit like an mp3 that was ripped from a scratched CD.  Sorry I can't describe this situation better, but trust me... it sounds bad.

I've tried running ffmpeg with -debug in the parameters, but every time I get a message that -debug isn't recognized.  I'm thinking that may be due to the --disable-debug option added (per the Ubuntu wiki) during the initial build, but before I go about rebuilding all over again I thought I should ask for (a) confirmation of the debug issue, and (b) see if there were any other suggestions to get to the heart of the matter.

Currently, my only workaround is to (D'OH) use Windoze.  I'm already forced to use the XBox360 due to budget constraints, but I host content using UShare in Ubuntu so encoding in Ubuntu is FAR preferable.

Any suggestions are appreciated.  So far the only difference I can tell between the version I had previously used and my current one.  In the output now I see:

  Metadata:
    encoder         : Lavf52.54.0
    Stream #0.0: Audio: aac, 48000 Hz, 5.1, s16, 64 kb/s
    Stream #0.1: Audio: aac, 48000 Hz, 2 channels, s16, 384 kb/s

Where previously the "Metadata: encoder         : Lavf52.54.0" did not appear in the output.  I'm thinking the source build added a different encoder than was previously offered in the repo package, but unfortunately I don't know, and the ffmpeg documentation and website leave lots to be desired.

Suggestions?  Thoughts?  Anything I can try to get more details?

Thanks.

---

### Post by andrew.46 on 2010-03-20
Hi sideshowmel,

It was not actually the FFmpeg developers who removed aac encoding, that was a little closer to home I am afraid :(.

Depending on how you have compiled your copy of FFmpeg there are 2 possibilities for aac encoding. The newest FFmpeg has a native aac encoder and there is also encoding available from libfaac:

```

andrew@skamandros~$ **[COLOR="Red"]ffmpeg -codecs | grep aac[/COLOR]**
FFmpeg version SVN-r22602, Copyright (c) 2000-2010 the FFmpeg developers
  built on Mar 20 2010 11:25:04 with gcc 4.3.3
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc 
--enable-avfilter --enable-pthreads --enable-shared --disable-static 
--disable-ffserver --enable-libtheora --enable-libvorbis --enable-x11grab 
--enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libfaad 
--enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 
--enable-zlib --enable-nonfree --enable-gpl
  libavutil     50.12. 0 / 50.12. 0
  libavcodec    52.59. 0 / 52.59. 0
  libavformat   52.56. 0 / 52.56. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.18. 0 /  1.18. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[B][COLOR="Red"] DEA    aac             Advanced Audio Coding
  EA    libfaac         libfaac AAC (Advanced Audio Codec)[/COLOR][/B]


```

My ears are fairly terrible so I cannot tell the difference between the 2 but some have complained about the audio quality, the answer from the FFmpeg developers is that the native aac encoder is in its early days. They can be selected as *-ac aac* or *-ac libfaac*. Can you give an example of one of the conversions that is giving you trouble, with the full command and terminal output?

A final thought is neroAacEnc which even to my untutored ears gives pretty fine sounding aac sound. This might be worth a try as well?

All the best,

Andrew

---

### Post by sideshowmel on 2010-03-25
thanks for the response.  I don't have the best hearing the world, either, but this is VERY noticeable.  I suspect you are on to something, and I had no idea about that.  It seems I'm already using libfaac (I think, based on the output), so perhaps I need to give the other one I try.  As I said before, though, the line that includes "Lavf52.54.0" in the output is something new, and I suspect part of the problem.  Full command and output below.

```
+ /usr/local/bin/ffmpeg -i /fattie/stage/temp/0d3fe98f103cd2a7ec79351af3ed96.dts -acodec aac -ac 2 -ab 64kb -ar 48000 /fattie/stage/temp/0d3fe98f103cd2a7ec79351af3ed96.aac
FFmpeg version SVN-r22218, Copyright (c) 2000-2010 the FFmpeg developers
  built on Mar  4 2010 23:30:11 with gcc 4.3.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libxvid --enable-x11grab
  libavutil     50.10. 0 / 50.10. 0
  libavcodec    52.55. 0 / 52.55. 0
  libavformat   52.54. 0 / 52.54. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[dts @ 0xa0e53a0]max_analyze_duration reached
[dts @ 0xa0e53a0]Estimating duration from bitrate, this may be inaccurate
Input #0, dts, from '/fattie/stage/temp/0d3fe98f103cd2a7ec79351af3ed96.dts':
  Duration: 00:50:15.41, bitrate: 1536 kb/s
    Stream #0.0: Audio: dca, 48000 Hz, 5.1, s16, 1536 kb/s
Output #0, adts, to '/fattie/stage/temp/0d3fe98f103cd2a7ec79351af3ed96.aac':
  Metadata:
    encoder         : Lavf52.54.0
    Stream #0.0: Audio: aac, 48000 Hz, 2 channels, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=   25603kB time=3069.38 bitrate=  68.3kbits/s
video:0kB audio:24619kB global headers:0kB muxing overhead 3.995005%

```

Also, here is my output from the same command you pasted above:

```
$ ffmpeg -codecs | grep aac
FFmpeg version SVN-r22218, Copyright (c) 2000-2010 the FFmpeg developers
  built on Mar  4 2010 23:30:11 with gcc 4.3.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libxvid --enable-x11grab
  libavutil     50.10. 0 / 50.10. 0
  libavcodec    52.55. 0 / 52.55. 0
  libavformat   52.54. 0 / 52.54. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
 DEA    aac             Advanced Audio Coding
  EA    libfaac         libfaac AAC (Advanced Audio Codec)
```

Thanks again, any further suggestions are appreciated.  Maybe I should try to get a debug log after all... although I'm still unable to do so.

---

### Post by andrew.46 on 2010-03-25
Hey sideshowmel,

Perhaps try something like:

```

/usr/local/bin/ffmpeg -i /fattie/stage/temp/0d3fe98f103cd2a7ec79351af3ed96.dts \
                      **[COLOR="Red"]-acodec libfaac[/COLOR]** -ac 2 **[COLOR="Red"]-ab 128k[/COLOR]** -ar 48000 \
                      /fattie/stage/temp/0d3fe98f103cd2a7ec79351af3ed96.aac

```

All the best,

Andrew

---

### Post by sideshowmel on 2010-03-25
I just tried:

```
/usr/local/bin/ffmpeg -i /fattie/stage/temp/61594d647d8572fafdc15781097a21.dts -acodec libfaac -ac 2 -ab 384kb -ar 48000 /fattie/stage/temp/61594d647d8572fafdc15781097a21.aac
```

I'm remote currently, so I did that over SSH. The logs do still show "Lavf52.54.0," but as I mentioned, I'm not certain that's the problem.

Do you know of any way for ffmpeg to return the codec currently being used?  Or is giving it that argument sufficient?  What I'm getting at is, is there a way to look back at my previous attempts (I have logs) to see which codec (aac vs. libfaac) was used?

When I get home where the audio equipment is, I'll check and repost.  It has crossed my mind that maybe tweaking the audio bitrate (you suggested 128kb... I had already tried with 384kb) may prove fruitful, but as I previously mentioned I get this on audio that worked just fine with identical settings, so I'll let you know.

Thanks.

---

### Post by andrew.46 on 2010-03-25
Hi sideshowmel,

I think the best way to compare is to make a clean start and encode the same file with the same parameters except for codec, that is do 2 copies one using the native encoder as *-acodec aac* and one using the external encoder as *-acodec libfaac*. My own ears are not good for such work but certainly idle gossip has it that libfaac sounds better. What I can hear is that neroAacEnc definitely sounds better.

Interested to hear if this is the root of the problem...

Andrew

---

### Post by sideshowmel on 2010-03-26
Well I had previously tried many different bitrates, and 384kb was the one that had originally sounded bad with exact setting that had previously sounded fine.

Nonetheless, that discussion is moot, because I'm happy to report that using libfaac has resolved this issue!! :popcorn:

Thanks so much for the suggestion!  I guess the version I had previously been using was set to use libfaac as the default encoder.  This newer version was most definitely using the other aac encoder you mentioned.

---

### Post by andrew.46 on 2010-03-26
Hi sideshowmel,

> **sideshowmel said:**
> Nonetheless, that discussion is moot, because I'm happy to report that using libfaac has resolved this issue!! :popcorn:

Excellent news :).

Andrew

---

