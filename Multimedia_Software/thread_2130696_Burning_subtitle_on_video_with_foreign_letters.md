---
title: "Burning subtitle on video with foreign letters"
date: 2013-03-30
forum: Multimedia Software
---

### Post by hyfanious on 2013-03-30
Hi,
I wanna burn an Italian Subtitle on a video, Currently I use this line code:
```
mencoder movie.avi -sub movie.srt -subfont-text-scale 6 -o movie.hardsubs.avi -oac copy -ovc lavc -lavcopts vbitrate=1200
```
But Italian letters Like (è,ì,ù, ...) show as "??".
what can I do?
Tnx alot.;)

---

### Post by SeijiSensei on 2013-03-30
You need to specify the character set that the subtitles file are encoded with.  Take a look at the [-subcp option]("http://linux.die.net/man/1/mencoder") to mencoder.  The file might be in UTF-8, for instance, while mencoder is expecting something like ISO-8859-1.

Have you tried playing the movie with mplayer?  You can play with the character set and see which one displays correctly, then use the same one with mencoder.  If you install smplayer from the repositories, you can change the character set from the Options > Preferences > Subtitles screen.  That's probably easier than futzing with mplayer from the command line.

---

### Post by hyfanious on 2013-03-30
Thank you for helping
I found that whit this encode: ISO-8859-3, the smplayer shows subtitle fine, 
I added this code to command "-subfont-encoding ISO-8859-3" but neither mplayer nor mencoder show any different in results
?!

---

### Post by SeijiSensei on 2013-04-01
Did you try "-subcp"?

---

### Post by hyfanious on 2013-04-01
> **SeijiSensei said:**
> Did you try "-subcp"?

This one helped me out :)
thank u very much
BTW is there any command that put the Subtitle on the CENTER on video instead of bottom?

---

### Post by SeijiSensei on 2013-04-01
You can use other mencoder switches to position fonts, I believe, but I, for one, would never want to watch a show with subtitles in the center.  Having to read while watching is bad enough, but having the subtitles overlay much of actual image would make them incredibly annoying, at least for me.  And I watch a lot of subtitled material so I'm speaking from experience here.

---

### Post by ProgramErgoSum on 2013-11-19
I have tried the -subcp option for a sub-title file in Indian language. The command works; but, either I see ??? or wide dashes only. What am I missing ? :( 

This option results in messages while encoding as 'Subtitle word '&#65533;?&#65533; ?&#65533;??&#65533;?&#65533;??&#65533;??&#65533;??&#65533; ' too long !
[FONT=Courier New] mencoder movie.mp4 -sub movie_kn.srt -oac lavc -ovc lavc -o movie-subs.mp4[/FONT]

Next attempt was with -subcp whose value is set to utf8 because I don't know what is the code page for Kannada language.
[FONT=Courier New] mencoder movie.mp4 -sub movie_kn.srt -subcp utf8 -oac lavc -ovc lavc -o movie-subs.mp4[/FONT]
The resulting file does not show sub-title but just wide white dashes. The same behavior is seen with values utf-8 or unicode. The only difference I noticed is, with unicode the message about long words is seen again.

With -subcp enca:kn:en, the same message about long words is seen again.
[FONT=Courier New] mencoder movie.mp4 -sub movie_kn.srt -subcp enca:kn:en -oac lavc -ovc lavc -o movie-subs.mp4[/FONT]

With -subfont-encoding unicode, the same message about long words is seen again.
[FONT=Courier New] mencoder movie.mp4 -sub movie_kn.srt -subfont-encoding unicode -oac lavc -ovc lavc -o movie-subs.mp4[/FONT]

With -subfont-encoding as utf8 or utf-8, the sub-title is not seen at all.
[FONT=Courier New] mencoder movie.mp4 -sub movie_kn.srt -subfont-encoding utf8 -oac lavc -ovc lavc -o movie-subs.mp4[/FONT]

---

### Post by ProgramErgoSum on 2013-11-19
I came across this [archived post]("http://ubuntuforums.org/archive/index.php/t-1609127.html") which refers to providing path to a TTF font file. I used it for my case; the problem with dashes/lines still exist. :( 

[FONT=Courier New]mencoder movie.mp4 -sub movie_kn.srt -subcp utf8 -font /usr/share/fonts/truetype/ttf-kannada-fonts/lohit_kn.ttf -oac lavc -ovc lavc -of mpeg -o movie-subs.mp4[/FONT]

---

### Post by FakeOutdoorsman on 2013-11-21
Does ffmpeg have the same issue? You'll have to get the real ffmpeg because the fake one in the repo does not have this feature.

1. Download and extract (if this example does not work then just get it via the [FFmpeg Download](http://ffmpeg.org/download.html#LinuxBuilds) page):
```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date +"%F").tar.gz
tar xzvf ffmpeg.static.32bit.$(date +"%F").tar.gz
```

2. Then run it (notice the ./ before ffmpeg):
```
./ffmpeg -i movie.mp4 -vf subtitles=movie_kn.srt -codec:v libx264 -crf 23 -preset medium -codec:a copy movie-subs.mp4
```

**Also see:**
[list]
[*][How To Compile FFmpeg and x264 on Ubuntu](https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide)
[*][FFmpeg and x264 Encoding Guide](https://trac.ffmpeg.org/wiki/x264EncodingGuide)
[*][FFmpeg and AAC Encoding Guide](https://trac.ffmpeg.org/wiki/AACEncodingGuide)
[*][FFmpeg Wiki: How to burn subtitles into the video](https://trac.ffmpeg.org/wiki/How%20to%20burn%20subtitles%20into%20the%20video)
[/list]

---

### Post by ProgramErgoSum on 2013-11-22
Thanks for the response. 
This seems to be right version of the ffmpeg command. 
[FONT=Courier New]ffmpeg -i movie.mp4 -scodec movie_kn.srt -vcodec libx264 -crf 23 -preset medium -acodec copy movie-subs.mp4[/FONT]

The version of ffmpeg used is : 
[FONT=Courier New]ffmpeg version 0.8.9-4:0.8.9-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:08:00 with gcc 4.6.3
[/FONT]

The resulting video has no subtitles at all. I am trying other options now.

BTW, ffmpeg is supposed to be deprecated soon and avconv is expected to be the replacement. Have you worked with avconv too ?

---

### Post by FakeOutdoorsman on 2013-11-22
> **ProgramErgoSum said:**
> Thanks for the response. 
This seems to be right version of the ffmpeg command. 
[FONT=Courier New]ffmpeg -i movie.mp4 -scodec movie_kn.srt -vcodec libx264 -crf 23 -preset medium -acodec copy movie-subs.mp4[/FONT]
This thread is about burning in (hardsubbing) subtitles. Your command attempts to copy a subtitle stream into the file.

> **ProgramErgoSum said:**
> The version of ffmpeg used is : 
[FONT=Courier New]ffmpeg version 0.8.9-4:0.8.9-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:08:00 with gcc 4.6.3
[/FONT]

The resulting video has no subtitles at all. I am trying other options now.
As I mentioned in my previous post the fake ffmpeg (what you're using) does not have this functionality and that is why I gave instructions to download real ffmpeg.

> **ProgramErgoSum said:**
> BTW, ffmpeg is supposed to be deprecated soon and avconv is expected to be the replacement. Have you worked with avconv too ?
The fake so-called "ffmpeg" from a fork called Libav is deprecated for avconv, which is also from Libav. I've never used it. Development for ffmpeg from FFmpeg is white-hot and it is not being deprecated for anything. The "deprecated" message was worded to intentionally confuse users. See [Who can tell me the difference and relation between ffmpeg, libav, and avconv?](http://stackoverflow.com/a/9477756/1109017) and [The FFmpeg/Libav situation](http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html).

---

### Post by SeijiSensei on 2013-11-22
What character set was used to create the subtitles file?  Without that information, you're going to be taking shots in the dark.

Use the command "file --mime-encoding movie_kn.srt" to see the character encoding used.

Alternatively just open the file in a browser with the URL file:///path/to/the/file/movie_kn.srt, then change character sets.  In Firefox, press Ctrl+i or use Tools > Page Info to see a variety of the file's characteristics including its character encoding.  (This page, rather surprisingly, is reported as encoded with the Windows-1252 character set!  I'd have thought UTF-8 was the proper choice in a global forum.)

Are you sure you have installed font files for all the encodings you tried?  Does the subtitle file display with the proper fonts in a text editor like gedit or kate?

What happens if you watch the movie with smplayer and use Options > Preferences > Subtitles > Font > Enable normal subtitles to select the correct font file?

Options > Preferences > Subtitles > Subtitles doesn't show any character encodings for Indian languages.   Maybe you should take a look at [http://askubuntu.com/questions/140975/how-do-i-apply-an-indian-language-system-wide](http://askubuntu.com/questions/140975/how-do-i-apply-an-indian-language-system-wide).

---

### Post by ProgramErgoSum on 2013-11-23
> **FakeOutdoorsman said:**
> This thread is about burning in (hardsubbing) subtitles. Your command attempts to copy a subtitle stream into the file.
When I used ffmpeg command you provided, not all the switches and flags were considered the valid. That is why I used other command. (I think, that is why you mentioned ./ffmpeg. Otherwise, the ffmpeg that runs could be the one from mencoder or whatever.)

With hardsubbing, the resulting video would not allow retrieval of sub-titles ?  My goal is to make a DVD of this video and sub-titles of couple of other Indian languages. A viewer can then select the language of the sub-titles at play-back. So, silly question (perhaps)...should I use hardsubbing or copying a sub-title stream for my goal ?

> **FakeOutdoorsman said:**
> As I mentioned in my previous post the fake ffmpeg (what you're using) does not have this functionality and that is why I gave instructions to download real ffmpeg. Just curious...how do you know I was using the 'fake ffmpeg' ? Was it the disclaimer I saw ? I don't recall if I installed ffmpeg first and then mencoder or avconv or WinFF or avidemux. (As you can, I am losing myself.... :confused: ). The installation has always been via sudo apt-get.

If I were to install ffmpeg via apt-get, will I get the real ffmpeg ?

> **FakeOutdoorsman said:**
> The "deprecated" message was worded to intentionally confuse users.  Disappointing ! :-?

This is the ffmpeg version I have. How does the output of the version switch look like for the 'real' ffmpeg ?
```

user@host:~$ ffmpeg -version
ffmpeg version 0.8.9-4:0.8.9-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:08:00 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
ffmpeg 0.8.9-4:0.8.9-0ubuntu0.12.04.1
libavutil    51. 22. 1 / 51. 22. 1
libavcodec   53. 35. 0 / 53. 35. 0
libavformat  53. 21. 1 / 53. 21. 1
libavdevice  53.  2. 0 / 53.  2. 0
libavfilter   2. 15. 0 /  2. 15. 0
libswscale    2.  1. 0 /  2.  1. 0
libpostproc  52.  0. 0 / 52.  0. 0

```

---

### Post by ProgramErgoSum on 2013-11-23
> **SeijiSensei said:**
> What character set was used to create the subtitles file?  Without that information, you're going to be taking shots in the dark.

Use the command "file --mime-encoding movie_kn.srt" to see the character encoding used.
Thanks for the tip. The encoding is utf-8.

In this attempt, I can see the sub-titles; but, the rendering is completely wrong. In Kannada language, the conjugation of a vowel and consonant is a symbol that is different than both. This is not seen in the sub-titles; instead, they are seen individually.

---

### Post by ProgramErgoSum on 2013-11-23
> **ProgramErgoSum said:**
> If I were to install ffmpeg via apt-get, will I get the real ffmpeg ? No; as mentioned at [ffmpeg, libav and avconv differences]("http://stackoverflow.com/questions/9477115/who-can-tell-me-the-difference-and-relation-between-ffmpeg-libav-and-avconv")  (the link you posted earlier).

---

### Post by ProgramErgoSum on 2013-11-23
I went to ffmpeg.org, added Jon Severinsson's PPA for ffmpeg (Ubuntu-13.10 64-bit) and isntalled ffmpeg. Then, I ran the command that you mentioned. However, it gives an error as shown below. 
```

user@dabba:~/expt$ ffmpeg -i movie.mp4 -vf subtitles=kn.srt -codec:v libx264 -crf 23 -preset medium -codec:a copy movie_kn.srt
ffmpeg version 0.10.9-7:0.10.9-1~saucy1 Copyright (c) 2000-2013 the FFmpeg developers
  built on Oct 18 2013 17:40:10 with gcc 4.8.1
  configuration: --arch=amd64 --disable-stripping --enable-pthreads --enable-runtime-cpudetect --extra-version='7:0.10.9-1~saucy1' --libdir=/usr/lib/x86_64-linux-gnu --prefix=/usr --enable-bzlib --enable-libdc1394 --enable-libfreetype --enable-frei0r --enable-gnutls --enable-libgsm --enable-libmp3lame --enable-librtmp --enable-libopencv --enable-libopenjpeg --enable-libpulse --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-vaapi --enable-vdpau --enable-libvorbis --enable-libvpx --enable-zlib --enable-gpl --enable-postproc --enable-libcdio --enable-x11grab --enable-libx264 --shlibdir=/usr/lib/x86_64-linux-gnu --enable-shared --disable-static
  libavutil      51. 35.100 / 51. 35.100
  libavcodec     53. 61.100 / 53. 61.100
  libavformat    53. 32.100 / 53. 32.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 61.100 /  2. 61.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  6.100 /  0.  6.100
  libpostproc    52.  0.100 / 52.  0.100
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'movie.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: isommp42
    creation_time   : 2010-11-23 20:08:54
  Duration: 00:11:11.59, start: 0.000000, bitrate: 244 kb/s
    Stream #0:0(und): Video: h264 (High) (avc1 / 0x31637661), yuv420p, 1280x720 [SAR 1:1 DAR 16:9], 163 kb/s, 15 fps, 15 tbr, 1k tbn, 30 tbc
    Metadata:
      creation_time   : 1970-01-01 00:00:00
      handler_name    : VideoHandler
    Stream #0:1(und): Audio: aac (mp4a / 0x6134706D), 44100 Hz, mono, s16, 75 kb/s
    Metadata:
      creation_time   : 2010-11-23 20:08:57
      handler_name    : 
File 'movie_kn.srt' already exists. Overwrite ? [y/N] y
Output #0, srt, to 'movie_kn.srt':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: isommp42
    creation_time   : 2010-11-23 20:08:54
Output file #0 does not contain any stream


```

---

### Post by SeijiSensei on 2013-11-23
> **ProgramErgoSum said:**
> Thanks for the tip. The encoding is utf-8.

In this attempt, I can see the sub-titles; but, the rendering is completely wrong. In Kannada language, the conjugation of a vowel and consonant is a symbol that is different than both. This is not seen in the sub-titles; instead, they are seen individually.

And you're sure you have a matching font file in UTF-8 that displays those symbols?  As I asked earlier, do they display properly if you open the file in a text editor like gedit or kate?

---

### Post by ProgramErgoSum on 2013-11-23
> **SeijiSensei said:**
> And you're sure you have a matching font file in UTF-8 that displays those symbols?  

```

user@dabba:/usr/share/fonts/truetype/ttf-kannada-fonts$ ls -la
total 664
drwxr-xr-x  2 root root   4096 Nov 23 21:01 .
drwxr-xr-x 23 root root   4096 Nov 23 21:01 ..
-rw-r--r--  1 root root 108988 Nov  5  2010 Kedage-i.ttf
-rw-r--r--  1 root root 105692 Nov  5  2010 Kedage-t.ttf
-rw-r--r--  1 root root 198584 Nov  5  2010 lohit_kn.ttf
-rw-r--r--  1 root root 134288 Nov  5  2010 Malige-i.ttf
-rw-r--r--  1 root root 116324 Nov  5  2010 Malige-t.ttf

```

And, just checked; they are all charset=binary.
```

nsubrahm@dabba:/usr/share/fonts/truetype/ttf-kannada-fonts$ file --mime-encoding *
Kedage-i.ttf: binary
Kedage-t.ttf: binary
lohit_kn.ttf: binary
Malige-i.ttf: binary
Malige-t.ttf: binary

```

```

user@dabba:~/expt$ ls -la
total 20132
drwxr-xr-x  2 nsubrahm nsubrahm     4096 Nov 23 23:39 .
drwx------ 19 nsubrahm nsubrahm     4096 Nov 23 23:35 ..
-rw-r--r--  1 nsubrahm nsubrahm       84 Nov 23 20:28 cmd.txt
-rw-r--r--  1 nsubrahm nsubrahm    37579 Nov 23 12:06 kn.srt
-rw-r--r--  1 nsubrahm nsubrahm 20535482 Nov 25  2010 movie.mp4
nsubrahm@dabba:~/expt$ file -i kn.srt 
kn.srt: text/plain; charset=utf-8

```

> **SeijiSensei said:**
> As I asked earlier, do they display properly if you open the file in a text editor like gedit or kate?
Yes, I can read them clearly in gedit.

How do the font files affect ffmpeg ? I am asking this because there seems to be option for subtitles file; not fonts.

---

### Post by ProgramErgoSum on 2013-11-23
Here is the latest update.

I went to ffmpeg site and downloaded the 64-bit binary and executed the ffmpeg command from the unzipped folder. I did this because, the ffmpeg from [Jon's PPA]("https://launchpad.net/~jon-severinsson/+archive/ffmpeg") is not compiled with --enable-libass. I then ran the command as provided to me by FakeOutdoorsman.

```

./ffmpeg -y -i movie.mp4 -vf subtitles=kn.srt -codec:v libx264 -crf 23 -preset medium -codec:a copy movie_kn.mp4

```

The mux/demux happens correctly except for the messages below.

```

[Parsed_subtitles_0 @ 0x347ff60] Neither PlayResX nor PlayResY defined. Assuming 384x288
[Parsed_subtitles_0 @ 0x347ff60] fontconfig: Selected font is not the requested one: 'Liberation Sans' != 'Arial'
[Parsed_subtitles_0 @ 0x347ff60] Glyph 0xC85 not found, selecting one more font for (Arial, 80, 0)
[Parsed_subtitles_0 @ 0x347ff60] fontconfig: Selected font is not the requested one: 'Lohit Kannada' != 'Arial'

```

When I play the resulting mp4, I can see the sub-titles in smplayer. But, the rendering is wrong. Could this be because of font settings ? fc-list does show lohit_kn.ttf.

I noticed that the subtitles file (kn.srt) is having Windows line-ending. Changing to Linux line-endings did not help. 

Finally, I tried with ass filter as below after I generated the ass file from srt.

```

./ffmpeg -i kn.srt kn.ass
./ffmpeg -y -i movie.mp4 -vf ass=kn.ass -codec:v libx264 -crf 23 -preset medium -codec:a copy movie_kn.mp4

```

The result is the same; i.e. I can see sub-titles now, but the rendering is all wrong.

---

### Post by ProgramErgoSum on 2013-11-23
--- deleted post ---

(Duplicate of previous one by me.)

---

### Post by FakeOutdoorsman on 2013-11-23
Can you provide the srt file or show its contents?

---

### Post by ProgramErgoSum on 2013-11-24
Here is a screen-shot of the incorrectly rendered sub-titles.
[ATTACH=CONFIG]248053[/ATTACH]

And, this is the correctly rendered text as seen in the kn.srt file (line 54). I have purposely added the screen-shot instead of regular text so as to avoid any encoding issues in forum posts or elsewhere.
[ATTACH=CONFIG]248054[/ATTACH]

When I converted the kn.srt to ass format, I noticed that the Styles part was referring to font name as Arial. I edited to Lohit Kannada (as seen by fc-list). This had no effect on the final result.

---

### Post by FakeOutdoorsman on 2013-12-02
Looks like you found the answer (libass needs harfbuzz support): [#3165 Kannada language sub-titles are not rendered correctly](https://trac.ffmpeg.org/ticket/3165).

Perhaps you can file a feature request in the Ubuntu bug tracker to get this implemented in libass(-dev).

If others are interested, see the additional install notes to [compile libass with harfbuzz support](https://trac.ffmpeg.org/attachment/ticket/3165/installNotes) (written by ProgramErgoSum I believe).

---

