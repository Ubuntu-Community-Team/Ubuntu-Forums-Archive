---
title: "avidemux and AVCHD (.MTS)"
date: 2009-06-06
forum: Multimedia Software
---

### Post by mashedbear on 2009-06-06
Hi - I recently bought a Sony HDR-TG3 handycam and am looking for an NLE to do some basic video editing with the video I have taken. 

The files are AVCHD (*MTS) format - the codec is MPEG-4 / h.264. I can play the files OK with VLC 0.9.4 (with some changes to the default settings to avoid dropping frames) 

After doing some research avidemux appears to be a good editor that supports MPEG and .h264. However when I try with avidemux 2.4.3 I can't open the files.

Is there a way for avidemux to work with AVCHD format? Is there an alternative / better NLE for AVCHD video on ubuntu?

My system is 64-bit Ubuntu 8.10 Intel Core2 Duo E7300 @ 2.66GHz

Thanks

---

### Post by Backharlow on 2009-06-07
It depends on what kind of editing you need to do. If you just need to do some direct file trimming and such utilitiary tasks then stick with Avidemux.
For a real pro NLE that can actually handle editing of compressed source like that try:
Cinelerra CV (community version)
This is the only really professional NLE for linux. They have their own Ubuntu repo. Get it here. [http://cinelerra.org/](http://cinelerra.org/)
I have cut MPEG-4 source on there, including effects, etc. and it's fine. It also can do HD resolutions, which it sounds like your AVCHD probably is.
Also, it is really not good practice to compress your source footage to begin with if its a project of any size. It uses a lot of cpu to play back that stuff and should really be only done for the final master. If I were you would use Avidemux to convert from whatever strangeness AVCHD is, to uncompressed or DV format in a .avi or .mov. This will take a lot of harddrive but make really usable source footage for a NLE like Cinelerra. Then when you finish projects, go to DVD format and/or make other compressions with Avidemux, like to MPEG-4 / h.264 for distribution.

---

### Post by xc3RnbFO8P on 2009-06-07
> **mashedbear said:**
> Hi - I recently bought a Sony HDR-TG3 handycam and am looking for an NLE to do some basic video editing with the video I have taken. 

The files are AVCHD (*MTS) format - the codec is MPEG-4 / h.264. I can play the files OK with VLC 0.9.4 (with some changes to the default settings to avoid dropping frames) 

After doing some research avidemux appears to be a good editor that supports MPEG and .h264. However when I try with avidemux 2.4.3 I can't open the files.

Is there a way for avidemux to work with AVCHD format? Is there an alternative / better NLE for AVCHD video on ubuntu?

My system is 64-bit Ubuntu 8.10 Intel Core2 Duo E7300 @ 2.66GHz

Thanks
Here is a HOWTO (better if **andrew.46** or **FakeOutdoorsman** check this out):)
[http://faemalia.org/wiki/view/Technical/CanonVixiaHF10InLinux]("http://faemalia.org/wiki/view/Technical/CanonVixiaHF10InLinux")
> I recommend downloading ffmpeg and using it to do the conversion for you. First, get ffmpeg from source (required as of 16 November 2008, but maybe an "aptitude install ffmpeg" will work in the near future). Compile it with libmp3lame support or not, if you don't want to use MP3 audio in your output stream. Note that in my example below I'm using AC3, not MP3, because all my players can play AC3 audio, and that's the closest format to the source stream.

sudo aptitude install lame lame-extras liblame-dev libx264-dev
wget [http://ffmpeg.mplayerhq.hu/ffmpeg-export-snapshot.tar.bz2](http://ffmpeg.mplayerhq.hu/ffmpeg-export-snapshot.tar.bz2)
bzip2 -dc ffmpeg-export-snapshot.tar.bz2
cd FFMPEGSOURCEDIR/
./configure --enable-libmp3lame --enable-libx264 --enable-gpl
make
sudo make install

What we've done here: use aptitude to get libmp3lame support (and lame itself, too, but you may not want/need that), get into ffmpeg source directory, compile it with libmp3lame support. Install it (into /usr/local).

Now we use ffmpeg to convert the .MTS file into something common Linux video players can play:

f=00000
/usr/local/bin/ffmpeg -y -itsscale 0:0.40681 -i $f.mts \ 
  -f avi -vcodec mpeg4 -b 6000000 -acodec ac3 -ab 128000 -s 854x480 $f.avi
mplayer -vo sdl -vfm ffmpeg -lavdopts fast:skiploopfilter=all $f.avi

What it all means:

f=00000 :: The $f.mts file to work with. Convert it to $f.avi leaving the original MTS in place. 

---

### Post by Malcy on 2009-06-07
Kdenlive (in the repositories) works well with AVCHD. I have used it frequently to edit shorts from AVCHD source material. It has an easy leaning curve but is quite capable.

---

### Post by mashedbear on 2009-06-07
Thanks - i got > /usr/bin/ffmpeg: unrecognized option '-itsscale' using the ffmpeg commands above. 

I have tried to work out the problem and simplify the commands but still getting errors - see: 

> ~/Desktop$ /usr/bin/ffmpeg -y -i test.MTS -f avi -vcodec mpeg4 -b 6000000 -acodec ac3 -ab 128000 -s 1440x1080 testavi.avi
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:52:45, gcc: 4.3.2
Input #0, mpegts, from 'test.MTS':
  Duration: 00:06:48.7, start: 1.040000, bitrate: 12286 kb/s
  Program 1 
    Stream #0.0[0x1011]: Video: h264, yuv420p, 1440x1080 [PAR 4:3 DAR 16:9], 25.00 tb(r)
    Stream #0.1[0x1100]: Audio: liba52, 48000 Hz, 5:1, 448 kb/s
Output #0, avi, to 'testavi.avi':
    Stream #0.0: Video: mpeg4, yuv420p, 1440x1080 [PAR 4:3 DAR 16:9], q=2-31, 6000 kb/s, 25.00 tb(c)
    Stream #0.1: Audio: ac3, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

Any help appreciated

---

### Post by mashedbear on 2009-06-07
Thanks - I have downloaded Cinelerra CV and am trying to learn how to use it! Does not want to open / edit AVCHD. Is there an option to be able to do this? Tks again.

---

### Post by mashedbear on 2009-06-10
I found a post [here]("http://www.linuxquestions.org/questions/linux-software-2/mts-video-conversion-672091/") which has given me some clues on how to use ffmpeg to convert AVCHD. 

This works for me ...... 

```
ffmpeg -i 00000.mts -sameq -an -f yuv4mpegpipe - | yuvfps -s 60000:1001 -r 60000:1001 | ffmpeg -f yuv4mpegpipe -sameq -i - -sameq -s 1280x720 -f mpeg2video -r 60000/1001 video_only.mpeg
```

.. but is with no audio - so you would need to extract the audio and then merge. Is there a better and easier way?

---

### Post by Malcy on 2009-06-10
As I said earlier, Kdenlive will edit AVCHD and is in my opinion a lot easier to use than Cinelerrra. Give it a go, it's in the repositories.

If you still need to convert AVCHD, both WinFF and Handbrake will do this with ease.

---

### Post by xzero1 on 2009-06-10
First of all, -an says no audio. But you shouldn't need to convert -- just change the container. Try this:
```
ffmpeg -i filename.mts -acodec copy -vcodec copy filename.mp4
```

---

### Post by Backharlow on 2009-06-19
From the website of Kdenlive:
> Kdenlive is a free open-source video editor for GNU/Linux and FreeBSD, which supports DV, AVCHD (experimental support) and HDV editing. Kdenlive relies on several other open source projects, such as FFmpeg and MLT video framework. 

From the wikipedia page for AVCHD:
> AVCHD is a format for recording and playback of high definition video. Video is compressed in MPEG-4 AVC/H.264 format, and audio is recorded in Dolby Digital.

In my opinion, given that direct editing of AVCHD in Kdenlive is still "experimental" and that by definition AVCHD is a compressed MPEG video, with compressed AC3 audio, AVCHD in really not intended to be source footage format. It is intended to be a viewing medium.
I would still recommend converting it to .DV or uncompressed .avi, with uncompressed .wav audio, and then editing that intermediate copy. Even if you CAN edit mpeg-4/h.264 with an ac3 track, it is just much more sensible not to. You don't want to be wasting all your CPU just trying to maintain playback nevermind compositing, etc.
Plus if you go to .dv or .avi and .wav these are universal standards so you aren't stuck with one editing app with only partial support.

Next.. ffmpeg
I would continue to fight to get ffmpeg or mencoder or something to convert before your edit, because Kdenlive is uses ffmpeg under the hood anyway. What you could do maybe is import your avchd into Kdenlive, then drop your assets one at a time into the timeline, and export them (unaltered) back out to disk in a sane format. Then import those new copies and edit.

---

### Post by xzero1 on 2009-06-19
> I would continue to fight to get ffmpeg or mencoder or something to convert before your edit, because Kdenlive is uses ffmpeg under the hood anyway.If quality is important, then the decoding/re-encoding of the video will not be lossless and will be time consuming. Yes, it is harder to get video editors to only edit the sections that are affected by the editing process but if this can be done for other codecs, why not x264? Are there not commercial software programs that already do this? If one only needs to do a cut and paste here and there why should this require re-encoding the entire video? Still, there are other perfectly valid reasons for using the process you describe.

---

### Post by mashedbear on 2009-06-21
> **xzero1 said:**
> First of all, -an says no audio. But you shouldn't need to convert -- just change the container. Try this:
```
ffmpeg -i filename.mts -acodec copy -vcodec copy filename.mp4
```

Thanks. Tried this but got the following error:
```
ffmpeg -i 00000.MTS -acodec copy -vcodec copy test.mp4FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:52:45, gcc: 4.3.2
Input #0, mpegts, from '00000.MTS':
  Duration: 00:06:48.7, start: 1.040000, bitrate: 12286 kb/s
  Program 1 
    Stream #0.0[0x1011]: Video: h264, yuv420p, 1440x1080 [PAR 4:3 DAR 16:9], 25.00 tb(r)
    Stream #0.1[0x1100]: Audio: liba52, 48000 Hz, 5:1, 448 kb/s
Output #0, mp4, to 'test.mp4':
    Stream #0.0: Video: libx264, yuv420p, 1440x1080 [PAR 0:1 DAR 0:1], q=2-31, 25.00 tb(c)
    Stream #0.1: Audio: ac3, 48000 Hz, 5:1, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mp4 @ 0x7f6271be7040]track 1: could not find tag for codec
Could not write header for output file #0 (incorrect codec parameters ?)

```

I think this is to do with the audio - perhaps mp4 doesn't support AC3? I have tried various different acodec settings

adpcm_ima_wav - *results in* Floating point exception
ac3 - *results in* Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height
mp3 - *results in* Unknown encoder 'mp3'

Am shooting in the dark a bit.  Any light appreciated!

---

### Post by xzero1 on 2009-06-22
Try adding the "-f mp4" parameter. The original command works for me converting a similar ".ts" format (h.264, 5.1) file. If that does not work, you may need to update ffmpeg and its libraries.

In the command line, I used "FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6" compiled according to this thread:
[http://ubuntuforums.org/showthread.php?t=1049449&highlight=ffmpeg-mt](http://ubuntuforums.org/showthread.php?t=1049449&highlight=ffmpeg-mt)

---

### Post by mashedbear on 2009-06-26
> **xzero1 said:**
> Try adding the "-f mp4" parameter. The original command works for me converting a similar ".ts" format (h.264, 5.1) file. If that does not work, you may need to update ffmpeg and its libraries.

In the command line, I used "FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6" compiled according to this thread:
[http://ubuntuforums.org/showthread.php?t=1049449&highlight=ffmpeg-mt](http://ubuntuforums.org/showthread.php?t=1049449&highlight=ffmpeg-mt)

Thanks have tried the "-f mp4" parameter and this also errored ```

ffmpeg -i 00001.MTS -f mp4 -vcodec copy -acodec copy test.mp4
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:52:45, gcc: 4.3.2
Input #0, mpegts, from '00001.MTS':
  Duration: 00:00:35.3, start: 1.040000, bitrate: 12466 kb/s
  Program 1 
    Stream #0.0[0x1011]: Video: h264, yuv420p, 1440x1080 [PAR 4:3 DAR 16:9], 25.00 tb(r)
    Stream #0.1[0x1100]: Audio: liba52, 48000 Hz, 5:1, 448 kb/s
Output #0, mp4, to 'test.mp4':
    Stream #0.0: Video: libx264, yuv420p, 1440x1080 [PAR 0:1 DAR 0:1], q=2-31, 25.00 tb(c)
    Stream #0.1: Audio: ac3, 48000 Hz, 5:1, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mp4 @ 0x7f6b2cbcd040]track 1: could not find tag for codec
Could not write header for output file #0 (incorrect codec parameters ?)

```

My version of ffmpeg is ```

ffmpeg -version
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:52:45, gcc: 4.3.2
FFmpeg r11872+debian_3:0.svn20080206-12ubuntu3.1
libavutil   3212800
libavcodec  3355136
libavformat 3409664
libavdevice 3407872

```

Do i need to upgrade this? Is there a way to do this without building from source?

I still think this could be to do with the audio formats that mp4 supports. 

Thanks again for any help

---

### Post by mashedbear on 2009-06-27
> **xzero1 said:**
> Try adding the "-f mp4" parameter. The original command works for me converting a similar ".ts" format (h.264, 5.1) file. If that does not work, you may need to update ffmpeg and its libraries.

In the command line, I used "FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6" compiled according to this thread:
[http://ubuntuforums.org/showthread.php?t=1049449&highlight=ffmpeg-mt](http://ubuntuforums.org/showthread.php?t=1049449&highlight=ffmpeg-mt)

I have upgraded my system from ubuntu 8.10 to 9.04 and now have the same version of ffmpeg ie. 0.5-svn17737+3:0.svn20090303-1ubuntu6 and guess what this now works! 

Brilliant. Thanks for your help!

---

### Post by Backharlow on 2009-07-03
Excellent.

---

### Post by mashedbear on 2009-07-06
Ah not quite. Got the ffmpeg command to work - and have a way to automate running the command over a directory of files. Only problem is neither Cinelerra 2.1CV or Avidemux 2.4.4 will open them. 

Am i going in circles or getting close?

---

### Post by mashedbear on 2009-07-14
Have found a post on using mencoder to convert AVCHD to avi and am trying to get this to work. 

The post is [here]("http://ubuntuforums.org/showthread.php?p=7605440#post7605440") in case this is of any help to others. 

[http://ubuntuforums.org/showthread.php?p=7605440#post7605440](http://ubuntuforums.org/showthread.php?p=7605440#post7605440)

---

### Post by DaveQB on 2010-09-07
This might help [http://linux-tipps.blogspot.com/2010/01/transcoding-50-fps-interlaced-avchd-to.html](http://linux-tipps.blogspot.com/2010/01/transcoding-50-fps-interlaced-avchd-to.html)

---

