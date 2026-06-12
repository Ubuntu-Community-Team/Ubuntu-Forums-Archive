---
title: "WinFF"
date: 2008-10-10
forum: Multimedia Software
---

### Post by kasio on 2008-10-10
Hi,

I am using WinFF on 8.0.4.1, and I am trying to convert an flv file for my Sansa E250, basically a MPEG file.

My problem is that it won't work. I get the terminal output popping up, but it says:
```

Unknown encoder 'mpeg2video'
Press Enter to Continue

```

I am using this FFmpeg:
```
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu1~ppa1h, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
```

---

### Post by FakeOutdoorsman on 2008-10-10
Where did you get this version of FFmpeg from?

---

### Post by kasio on 2008-10-10
It was from TJ's PPA: [https://launchpad.net/~intuitivenipple/+archive](https://launchpad.net/~intuitivenipple/+archive)

---

### Post by FakeOutdoorsman on 2008-10-10
I'm guessing it's a bug with TJ's ffmpeg, probably similar to this Medibuntu bug:
[Bug #269997: ffmpeg Unknown encoder 'mpeg2video' (Intredpid x64)]("https://bugs.launchpad.net/medibuntu/+bug/269997")

If you run:
```
ffmpeg -formats | grep mpeg2video
```

You should see:
```
E mpeg2video      MPEG2 video
DEVSDT mpeg2video
```

If there is no E, then encoding has been disabled.  The version of ffmpeg from the official Ubuntu repository may work for you.

---

### Post by kasio on 2008-10-10
Received this output:

> 
E mpeg2video      MPEG2 video
 D VSDT mpeg2video


Can't think whats wrong....

---

### Post by FakeOutdoorsman on 2008-10-10
Sorry about that, I wasn't very clear.  The mpeg2video codec does not show "E" which indicates that it can't encode.  You can report it as a bug to TJ, or try ffmpeg from the official repo, or [compile ffmpeg yourself]("http://ubuntuforums.org/showthread.php?t=786095").

---

### Post by kasio on 2008-10-10
Using the one from the official repo, I get "Unknown codec 'libmp3lame'".

---

### Post by Yellow Pasque on 2008-10-10
Add Medibuntu repos [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and use their ffmpeg package. In Synaptic, you might have to Force and Lock the version of ffmpeg (under the Package menu)

---

### Post by FakeOutdoorsman on 2008-10-10
Curses!  So many ffmpeg versions and their option names can all be different.  This time WinFF is using the new name (libmp3lame) for the mp3 encoder, but your version uses the old name (plain old "mp3" I think).  If you show me the command WinFF is passing to ffmpeg I can rewrite it to work for the old version.

Or you can skip all of the version issues and their assorted bugs by just compiling ffmpeg yourself.  Also, the Ubuntu repo version has not been compiled to support restricted formats, although it can still do some procedures with a few of them.  Or you can skip ffmpeg completely and try using mencoder, but I'm not very familiar with it.

---

### Post by kasio on 2008-10-10
I've tried the Medibuntu version, and I still get the unknown codec 'libmp3lame' error.

But this is the FFmpeg config:

> 
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug **--enable-libmp3lame** --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr



---

### Post by FakeOutdoorsman on 2008-10-10
What WinFF settings/presets/ffmpeg commands are you using?

---

### Post by kasio on 2008-10-10
Here's my presets that I'm using:

```

<e200FS>
<label>Sandisk Sansa e200 4:3</label>
&#8722;
<params>
-acodec libmp3lame -ab 128 -ar 44100 -vcodec mpeg2video -s 224x176 -b 320kb -strict -1
</params>
<extension>mpg</extension>
</e200FS>
&#8722;
<e200WS>
<label>Sandisk Sansa e200 16:9</label>
&#8722;
<params>
-acodec libmp3lame -ab 128 -ar 44100 -vcodec mpeg2video -s 224x128 -b 320kb -strict -1
</params>
<extension>mpg</extension>
</e200WS>

```

---

### Post by FakeOutdoorsman on 2008-10-10
Try this with Medibuntu's ffmpeg:
```
<e200FS>
<label>Sandisk Sansa e200 4:3</label>
&#8722;
<params>
-acodec mp3 -ab 128k -ar 44100 -vcodec mpeg2video -s 224x176 -b 320k -strict -1
</params>
<extension>mpg</extension>
</e200FS>
&#8722;
<e200WS>
<label>Sandisk Sansa e200 16:9</label>
&#8722;
<params>
-acodec mp3 -ab 128k -ar 44100 -vcodec mpeg2video -s 224x128 -b 320k -strict -1
</params>
<extension>mpg</extension>
</e200WS>
```

---

### Post by kasio on 2008-10-11
Here's the output:

> 
  Stream #0.0: Video: mpeg2video, yuv420p, 224x176, q=2-31, 320 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: 0x0000, 44100 Hz, mono, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1



---

### Post by kasio on 2008-10-12
Any help?

---

### Post by kasio on 2008-10-12
*bump*

---

### Post by FakeOutdoorsman on 2008-10-12
Let's cut out WinFF.  This worked for me on Hardy with Medibuntu's ffmpeg:
```
ffmpeg -i input.avi -acodec mp3 -ab 128k -ar 44100 -vcodec mpeg2video -s 224x176 -b 320k -strict -1 output.mpg
```

---

### Post by kasio on 2008-10-13
Here's the output:

> 
  Stream #0.0: Video: mpeg2video, yuv420p, 224x176, q=2-31, 320 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: 0x0000, 44100 Hz, mono, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1


---

### Post by kasio on 2008-10-19
*bump*

---

### Post by vishnu on 2008-10-21
I'm using this command.  Worked for me a week ago.

ffmpeg -i file.avi -s 320x240 -vcodec mpeg2video -b 200k -ab 192k -ac 2 -ar 44100 -acodec libmp3lame file.mpg

It worked great but today I ran it and got this error:
Unknown encoder 'mpeg2video'

I'm not sure what's changed.  Any ideas?  Or is there something else I can use instead of mpeg2video?

---

### Post by kasio on 2008-10-22
I have also started getting this error. Any help?

---

### Post by vishnu on 2008-10-22
I resolved the issue by installing "libavcodec-unstripped-51"

Next, I encountered an error related to the use of mp3 as an audio codec in my command so I used libmp3lame instead.  Hope this works for you.

---

### Post by kasio on 2008-10-22
I installed that. It fixed the mpeg2video error, but now I get the unknown encoder libmp3lame error.

---

### Post by vishnu on 2008-10-22
check to see that you have libmp3lame installed.  on my system it's a package called libmp3lame0

---

### Post by almostlinux on 2009-02-01
^ that helped. Thanks :)

---

