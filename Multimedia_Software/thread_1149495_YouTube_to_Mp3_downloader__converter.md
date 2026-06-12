---
title: "YouTube to Mp3 downloader / converter"
date: 2009-05-05
forum: Multimedia Software
---

### Post by glowell on 2009-05-05
Hi,

I'm not sure if this is the right forum topic to post this thread in, if not I apologizes..

I am new to Ubuntu and I'm running Ubuntu 8.10 and I recently switched over from Windows XP Professional. 

There is a program called DVD Video Soft.

What it is, is it downloads Youtube videos and converts them to mp3 format and allows me to edit the id3 tags of the song,

Is there a program like that for Ubuntu 8.10?

Any help would be appreciate.

Thanks.

---

### Post by lukeiamyourfather on 2009-05-05
**Elan Sleazebaggano:** I wanna pirate some music from the internet.
**Obi-Wan:** *[using the Jedi mind trick]* You don't want to pirate music from the internet.
**Elan Sleazebaggano:** I don't want to pirate music from the internet.
**Obi-Wan:** You want to go home and rethink your life.
**Elan Sleazebaggano:** I want to go home and rethink my life.

---

### Post by FakeOutdoorsman on 2009-05-05
People who download low-quality audio from YouTube for personal use are sleazebags?  Could you not extend that rationale to simpily listening to audio on YouTube?  You would have to, because your browser downloads the file to your */tmp* directory each time you watch a video.  That would mean all YouTube visitors would then be Sleazebaggano's.

Anyway, one way to do this is by using your browser and FFmpeg.  Standard YouTube videos use the FLV container with MP3 audio.  The HD versions are a MP4 container with AAC audio.  There are many ways to do this, but here's how I would do it:
[indent]
1. Load video in browser.

2. Navigate to /tmp:
```
$ cd /tmp
```
3. Find the video.  It's usually Flashxxxxxx:
```
$ ls
FlasheQXK6Y  claws-mail-1000  mysql.sock
```
Copy it to your home folder:
```
$ cp FlasheQXK6Y ~/
```
This is a standard YouTube video, so I know the audio is already MP3.  Copy the audio stream from the FLV:
```
$ ffmpeg -i FlasheQXK6Y -acodec copy output.mp3
```
[/indent]
That's it.  No re-encoding, no quality loss.  If you want a good id3 tagger, check out **Easytag**.

---

### Post by Stochastic on 2009-05-05
Moved to Multimedia & Video.

---

### Post by dietschi2 on 2009-05-16
If you're looking for an easy way to extract sound from a flash video just install AVIDEMUX, load the video with it, go to the menu AUDIO an choose Save....

Thats all! Have fun!

---

### Post by logos34 on 2009-05-16
> **FakeOutdoorsman said:**
> 
```
$ ffmpeg -i FlasheQXK6Y -acodec copy output.mp3
```
[/indent]

When I run that I just get:
> 
[flv @ 0x7f68aa116160]Unsupported video codec (7)

---

### Post by SuperSonic4 on 2009-05-16
I would use [Downloadhelper](https://addons.mozilla.org/en-US/firefox/addon/3006) to get them as either flv or mp4 files on your pc (it's an easier to understand name too) and then use ffmpeg as stated in post 3.

Downloadhelper does have a built in converter (which uses ffmpeg as a backend) but I've never got it to work

---

### Post by logos34 on 2009-05-16
> **SuperSonic4 said:**
> I would use [Downloadhelper](https://addons.mozilla.org/en-US/firefox/addon/3006) to get them as either flv or mp4 files on your pc (it's an easier to understand name too) and then use ffmpeg as stated in post 3.

Downloadhelper does have a built in converter (which uses ffmpeg as a backend) but I've never got it to work

thanx i'll give it a shot

---

### Post by logos34 on 2009-05-16
well, this is strange, my compiled version of ffmpeg supports flash:

> $ ffmpeg -formats

**DEVSD  flv**

gues I'll have to try mencoder or something

---

### Post by SuperSonic4 on 2009-05-16
Why would you have to try something different if flash is supported?

---

### Post by alexandari on 2009-05-16
I think AcetoneISO will work like a charm :)

---

### Post by SuperSonic4 on 2009-05-16
> **alexandari said:**
> I think AcetoneISO will work like a charm :)

"AcetoneISO, is a feature-rich and complete software application to manage CD/DVD images. Thanks to powerful open source tools such as fuseiso, AcetoneISO will let You mount typical proprietary images formats of the Windows world such as ISO BIN NRG MDF IMG and do plenty of other things."

What does this have to do with audio ripping?

---

### Post by alexandari on 2009-05-16
> **SuperSonic4 said:**
> "AcetoneISO, is a feature-rich and complete software application to manage CD/DVD images. Thanks to powerful open source tools such as fuseiso, AcetoneISO will let You mount typical proprietary images formats of the Windows world such as ISO BIN NRG MDF IMG and do plenty of other things."

What does this have to do with audio ripping?


well believe it or not AcetoneISO also can download youtube videos,metacafe videos,convert flv to avi and extract audio from a video file + many more. That`s what the dude needs right?

---

### Post by logos34 on 2009-05-16
beasue i'm getting the same unsupported codec message

---

### Post by FakeOutdoorsman on 2009-05-16
> **logos34 said:**
> beasue i'm getting the same unsupported codec message

What is the complete output of the FFmpeg command?  Some YouTube videos are now using AAC audio and H.264 video in an FLV container (not usually a standard practice as far as I know) and some FFmpeg revisions choke on this; or, you may need to enable restricted encoders in FFmpeg:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by logos34 on 2009-05-16
> **FakeOutdoorsman said:**
> What is the complete output of the FFmpeg command?  Some YouTube videos are now using AAC audio and H.264 video in an FLV container (not usually a standard practice as far as I know) and some FFmpeg revisions choke on this; or, you may need to enable restricted encoders in FFmpeg:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

thought i had just about every codec enabled

> $ ffmpeg -v
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  [COLOR="Blue"]configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr[/COLOR]
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:11:10, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)


I get an mp3 file at the end, but it's silent (?)
> 

$ ffmpeg -i FlashJbU0ri -acodec copy stooges.mp3
...

[flv @ 0x7f219a810160]Unsupported video codec (7)
[flv @ 0x7f219a810160]Unsupported video codec (7)
[flv @ 0x7f219a810160]Unsupported video codec (7)
[flv @ 0x7f219a810160]Unsupported video codec (7)
[flv @ 0x7f219a810160]Unsupported video codec (7)
[flv @ 0x7f219a810160]Unsupported video codec (7)
size=    4587kB time=528.6 bitrate=  71.1kbits/s    
video:0kB audio:4587kB global headers:0kB muxing overhead 0.000000%

> 
user@ubuntu:~$ file stooges.mp3 
stooges.mp3: data

user@ubuntu:~$ mediainfo stooges.mp3 
General #0
Complete name                : stooges.mp3
File size                    : 4.48 MiB

---

### Post by FakeOutdoorsman on 2009-05-16
You didn't supply the complete FFmpeg output.  I was specifically looking for what FFmpeg thought the input file is, because if the input file does not contain mp3 audio, then *-acodec copy* will fail to create a valid file.  I'm guessing that your input file does not contain mp3 audio, but aac audio.  If that is the case, you can either copy the audio stream:
```
ffmpeg -i input -acodec copy output.aac
```
or you can re-encode to mp3:
```
ffmpeg -i input -acodec libmp3lame output.mp3
```
Also, as I mentioned earlier, some older FFmpeg revisions can't handle YouTube's H.264/AAC FLV files.

---

### Post by logos34 on 2009-05-16
> **FakeOutdoorsman said:**
> You didn't supply the complete FFmpeg output.  I was specifically looking for what FFmpeg thought the input file is

The output flies by so fast, 'Unsupported video codec (7)' repeated...I can't scroll [shift+pgUp] all the way to beginning...I tried aac and it appears to think it's 'flv':

(last part):
> 
[flv @ 0x7feaf0104160]Unsupported video codec (7)
[COLOR="Red"]Input #0, flv, from 'FlashJbU0ri':[/COLOR]
  Duration: 00:08:48.2, start: 0.000000, bitrate: N/A
  Stream #0.0: Video: 0x0007, 1000.00 fps(r)
  Stream #0.1: Audio: 0x000a, 44100 Hz, stereo
picture size invalid (0x0)

but aac file is silent too

and it is flash:
> $ file FlashJbU0ri 
FlashJbU0ri: Macromedia Flash Video

---

### Post by mc4man on 2009-05-16
@ logos34
I'm assuming that your still using hardy so I'm wondering where did your ffmpeg come from?

I have 2 hardy installs, one typical with an updated ffmpeg.( **installed to /usr/local**
The other is A/V based only so I went a bit overboard and re did all the ffmpeg libs, libxine1, and gstreamer libs and plug-ins  based on ffmpeg 0.5, and some other newer libs

In any case both have no problem with with the current you tube .flv's (the redone hardy has no issues with anything

from your post
> libavutil version: 1d.49.3.0
libavcodec version: 1d.51.38.0
libavformat version: 1d.51.10.0

Those are the old hardy ffmpeg libs (libavcodec1d, ect.

Edit 
If you built a new ffmpeg I won't install it to /usr with the --enable shared option, while they could co exist I think usr/local is more appropriate (shared or static

---

### Post by logos34 on 2009-05-16
> **mc4man said:**
> @ logos34
I'm assuming that your still using hardy so I'm wondering where did your ffmpeg come from?


yeah, still on 8.04 hardy heron

come to think of it, WHERE did it come from? :lolflag:

(answer: apparently the old 2007 version in Medibuntu repos)

seriously, I thought I got the latest ffmpeg source tarball from sourceforge...I remember enabling a lot of the codecs support because it kept complaining until I installed all the required -dev pkgs

so what should I do for it to be like your setup? 
0.5 version: 
[http://www.ffmpeg.org/RELEASE](http://www.ffmpeg.org/RELEASE)
?

do I custom compile the latest release of ffmpeg?  But what about the newest version of the -dev libs?
> 
libavcodec-dev - development files for libavcodec - Medibuntu package
libavformat-dev - development files for libavformat - Medibuntu package
libavutil-dev - development files for libavutil - Medibuntu package
libpostproc-dev - development files for libpostproc - Medibuntu package
libswscale-dev - development files for libswscale - Medibuntu package

---

### Post by mc4man on 2009-05-16
Why don't you try the guide here
[http://ubuntuforums.org/showpost.php?p=6963607&postcount=360](http://ubuntuforums.org/showpost.php?p=6963607&postcount=360)

Your probably going to want to add to the configure a bit, ck. ./configure --help to see what you want
Don't use your posted conf. at least one thing has changed (if you intend to build off of it then add enable postproc and swscale at a min.

Let it install to default of /usr/local, whether you enable-shared honestly I'm not 100% clear on that ( for the 'default' hardy I usually build to static (the default)
The other day I redid the build to shared (still in /usr/local) but that was to test something on a vlc build, 

Make sure you delete ffmpeg itself first (not the default libs, though any -dev's could go. (you'll get headers in /usr/local/include

---

### Post by logos34 on 2009-05-16
I think I'll just rip it out and follow F[akeOutdoorsmans guide here]("http://ubuntuforums.org/showpost.php?p=6963607&postcount=360")

be back soon with results.

(jeez, looks like I hijacked this thread...sorry!)

---

### Post by logos34 on 2009-05-17
got ffmpeg in, FINALLY (about time too)...kept failing checkinstall stage...maybe it was one of the ./configure options. i.e. '--enable=lib*' or the '--prefix=/usr/local'...Ended up falling back to FakeOutdoorsMan's entry...so none of the extra stuff I added like 3gp/amr support, libspeex, and some other not-so-important libs, no biggie i guess.

Thanx mc4man, FakeOutdoorsman for the help

> **mc4man said:**
> Why don't you try the guide here
[http://ubuntuforums.org/showpost.php?p=6963607&postcount=360](http://ubuntuforums.org/showpost.php?p=6963607&postcount=360)

Your probably going to want to add to the configure a bit, ck. ./configure --help to see what you want
Don't use your posted conf. at least one thing has changed (if you intend to build off of it then add enable postproc and swscale at a min.

Let it install to default of /usr/local, whether you enable-shared honestly I'm not 100% clear on that ( for the 'default' hardy I usually build to static (the default)
The other day I redid the build to shared (still in /usr/local) but that was to test something on a vlc build, 

Make sure you delete ffmpeg itself first (not the default libs, though any -dev's could go. (you'll get headers in /usr/local/include

yes, I deleted ffmpeg first AND the -devs, but put the latter back after I kept getting make errors...tried postproc but, again, I had to remove it because of errors (maybe unrelated, dunno)...like I said, tried a lot but ended up going with the line on the guide as that was the only one which resulted in successful .deb pkg build/checkinstall.

thanks again

---

### Post by logos34 on 2009-05-17
> **FakeOutdoorsman said:**
> What is the complete output of the FFmpeg command?  Some YouTube videos are now using AAC audio and H.264 video in an FLV container (not usually a standard practice as far as I know) and some FFmpeg revisions choke on this

You were exactly right.  It was aac not mp3:

> $ ffmpeg -i FlashJbU0ri -acodec copy stooges.aac
FFmpeg version 0.5, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  built on May 17 2009 01:19:28, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)

Seems stream 0 codec frame rate differs from container frame rate: 2000.00 (2000/1) -> 29.92 (359/12)
Input #0, flv, from 'FlashJbU0ri':
  Duration: 00:08:48.23, start: 0.000000, bitrate: 236 kb/s
    Stream #0.0: Video: h264, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 236 kb/s, 29.92 tbr, 1k tbn, 2k tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Output #0, adts, to 'stooges.aac':
    Stream #0.0: Audio: libfaac, 22050 Hz, stereo, s16
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
size=    4654kB time=528.67 bitrate=  72.1kbits/s    
video:0kB audio:4576kB global headers:0kB muxing overhead 1.700540%

---

### Post by mc4man on 2009-05-17
@ logos34
Sorry about the swscale, I've been using the 0.5 source to maintain consistency in checking something else out (in that configure it must be enabled
That's why it's always good to run. read ./configure --help first

I'm surprised about the rest though

While i usually don't enable all these things what you mentioned should work

Ex
> ./configure --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid  --enable-avfilter --enable-avfilter-lavf --enable-libamr-nb --enable-libamr-wb --enable-libvorbis --enable-libspeex --enable-postproc --enable-libgsm

After a ffmpeg configure finishes scroll back a ways

> install prefix            /usr/local
source path               /home/doug/ffmpeg
C compiler                gcc
.align is power-of-two    no
ARCH                      x86 (generic)
big-endian                no
runtime cpu detection     no
yasm                      yes
MMX enabled               yes
MMX2 enabled              yes
3DNow! enabled            yes
3DNow! extended enabled   yes
SSE enabled               yes
SSSE3 enabled             yes
CMOV enabled              no
CMOV is fast              no
EBX available             yes
EBP available             yes
10 operands supported     yes
gprof enabled             no
debug symbols             yes
strip symbols             yes
optimizations             yes
static                    yes
shared                    no
[COLOR="Blue"]postprocessing support    yes[/COLOR]
new filter support        yes
filters using lavformat   yes
network support           yes
IPv6 support              yes
threading support         pthreads
SDL support               yes
Sun medialib support      no
AVISynth enabled          no
[COLOR="Blue"]libamr-nb support         yes
libamr-wb support         yes[/COLOR]
libdc1394 support         no
libdirac enabled          no
libfaac enabled           yes
libfaad enabled           yes
libfaad dlopened          no
[COLOR="Blue"]libgsm enabled            yes[/COLOR]
libmp3lame enabled        yes
libnut enabled            no
libopenjpeg enabled       no
libschroedinger enabled   no
[COLOR="Blue"]libspeex enabled          yes[/COLOR]
libtheora enabled         yes
[COLOR="Blue"]libvorbis enabled         ye[/COLOR]s
libx264 enabled           yes
libxvid enabled           yes
zlib enabled              yes
bzlib enabled             yes



The reason to remove in synaptic the existing -devs from the ffmpeg lib's (usually 5), would be to make sure if you built an app that used the headers it would use the new, updated ones in /usr/local/include

(I'm not sure if there is a "pecking' order or not (usr/local before /usr

Better to get rid of them

Edit : if you were seeing this error, then it's an issue with the latest svn (0.5 can be fully configured on hardy
> mpeg12.c: At top level:
mpeg12.c:608: error: static declaration of 'mpeg1_decode_block_intra' follows non-static declaration
mpeg12.c:323: note: previous implicit declaration of 'mpeg1_decode_block_intra' was here
make[1]: *** [mpeg12.o] Error 1


---

### Post by logos34 on 2009-05-17
> **mc4man said:**
> @ logos34
Sorry about the swscale, I've been using the 0.5 source to maintain consistency in checking something else out (in that configure it must be enabled
That's why it's always good to run. read ./configure --help first

I'm surprised about the rest though

While i usually don't enable all these things what you mentioned should work


actually swscale wasn't included for some reason..but here's what I initially tried without success, adding to FakeOutdoorsman's line:
> 
~$ ./configure [COLOR="Blue"]--prefix=/usr/local --enable-postproc --enable-avfilter --enable-avfilter-lavf [/COLOR]--enable-gpl --enable-nonfree --enable-pthreads -[COLOR="Blue"]-enable-x11grab --enable-libamr-nb --enable-libamr-wb --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libvorbis --enable-mlib[/COLOR] --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid 

I kept omitting stuff after the errors, until finally left with fakeoutdoorsman's line. (didn't know '/usr/local' was default either)

Maybe I'll try again, but I really don't need support for a lot of it...So you're saying I should delete these:

> libavcodec-dev - development files for libavcodec - Medibuntu package
libavformat-dev - development files for libavformat - Medibuntu package
libavutil-dev - development files for libavutil - Medibuntu package
libpostproc-dev - development files for libpostproc - Medibuntu package
libswscale-dev - development files for libswscale - Medibuntu package

?? and then recompile?

---

### Post by mc4man on 2009-05-17
> So you're saying I should delete these:
Yes, you should at some point delete them.* IF you build other apps against the ffmpeg lib.'s* you want to make sure they use the the new ones. (which will be in /usr/local/include for the headers and /usr/local/lib/pkgconfig for the .pc's

**In a 'standard' hardy enabling libspeex will fail,** the hardy lib is too old.. ( I was checking last night from my other install where libspeex is updated

If you intend to build other media apps I'd try for a bit fuller build, for instance vlc would require postproc and swscale 

Otherwise if what you built is doing what you need then your ok.

A configure for **latest svn **on hardy to build all headers and pkgconfig's (noting that I enabled 'shared' for external reasons

> ./configure --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid  --enable-avfilter --enable-avfilter-lavf --enable-libamr-nb --enable-libamr-wb --enable-libvorbis  --enable-postproc  [COLOR="Blue"]--enable-shared[/COLOR]



A  configure for the **0.5 release** version to build all headers and pkgconfig's

> ./configure --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid  --enable-avfilter --enable-avfilter-lavf --enable-libamr-nb --enable-libamr-wb --enable-libvorbis  --enable-postproc  --enable-swscale 

**If you add --enable-shared** you should run after installing ( the default is "static" which is sufficient and doesn't need to be in the ./configure

```
sudo ldconfig
``` 

Notice **7** elements built
> FFmpeg version SVN-r18864, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-avfilter --enable-avfilter-lavf --enable-libamr-nb --enable-libamr-wb --enable-libvorbis --enable-postproc [COLOR="Blue"]--enable-shared[/COLOR]
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.29. 0 / 52.29. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on May 17 2009 09:39:43, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu4)


Are you able to work with the .flv now?, if not post a link to a problem one
Out of curiosity are you seeing a video thumbnail on these .flv's or are they just a plain icon?

---

### Post by logos34 on 2009-05-17
> **mc4man said:**
> 
A configure for latest svn on hardy (noting that I enabled 'shared' for external reasons


ok, that worked perfectly (I chose without shared)...thanks
> 
$ ffmpeg
FFmpeg version 0.5, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-avfilter --enable-avfilter-lavf --enable-libamr-nb --enable-libamr-wb --enable-libvorbis --enable-postproc
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on May 17 2009 14:19:44, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
At least one output file must be specified


ripped out the aforementioned -devs.

So in the future if necessary I need to build against the svn headers installed with ffmpeg, and use '--prefix=/usr/local/include' , is that right?

---

### Post by mc4man on 2009-05-17
> So in the future if necessary I need to build against the svn headers installed with ffmpeg, and use '--prefix=/usr/local/include' , is that right?

In most cases they'll be found automatically.

If not you'll need to check the ./configure --help, there is no 'standard' way

Actually the first thing one should do is ck. the help and after a configure, even if successful, scroll back and read thru before make.
Many apps will pass the configure and fail the build or build successfully but not to your expectations.

If you find your still 'hobbled' by the unfortunate timing of hardy's release, and have some spare space for a test install I have a complete set of debian packages for hardy I built or rebuilt to move hardy away from libavcodec1d ect. 

I think you should be fine as is.

---

### Post by logos34 on 2009-05-17
> **mc4man said:**
> In most cases they'll be found automatically.

ok great

If not you'll need to check the ./configure --help, there is no 'standard' way

> Actually the first thing one should do is ck. the help and after a configure, even if successful, scroll back and read thru before make.
Many apps will pass the configure and fail the build or build successfully but not to your expectations.

I normally do that...everything seems right, although at first glance I thought maybe it got a couple of the default settings which I didn't override wrong ('no' vs. 'yes'/enable vs. disable), but I could be wrong myself...Also I saw this:
> 
--arch=ARCH              select architecture [x86_64]

I assumed it detected my arch (i.m running AMD64 version of ubuntu) and choose that as default, but after configure it just lists 'x86'...not sure what the deal is there

I think I'll just leave it like it is

---

### Post by mc4man on 2009-05-17
> I normally do that...everything seems right

Actually I was referring to the ./configue --help of some source you may wish to build from here on, not ffmpeg. ( your done there)

---

### Post by logos34 on 2009-05-17
> **mc4man said:**
> Actually I was referring to the ./configue --help of some source you may wish to build from here on, not ffmpeg. ( your done there)

oh, ok

thanks

---

### Post by luwen on 2009-05-18
Online downloader/ converter:
[www.vixy.net](www.vixy.net)
[www.zamzar.com](www.zamzar.com)

This [Mac YouTube Downloader]("http://www.applemacvideo.com/mac-youtube-downloader.html#119") works nice.

---

### Post by mc4man on 2009-05-20
logos34
One more post here (the limit of 1k on messages is a pain

If you want the patched ffmpeg for your hardy 64 bit this should work 

Remove your current ffmpeg  thru synaptic

We'll use a specific ffmpeg version, to see why read [here]("http://ubuntuforums.org/showthread.php?p=7311230#post7311230") 
(picked somewhat at random, only a few days old anyway


For these commands using a new folder in home named ffmpeg2

So make the ffmpeg2 dir. in home and cd to it. (this prompt ~/ffmpeg2$
```

svn co -r 18839 svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
```

```
cd ffmpeg
```

```
svn co -r [COLOR="Blue"]4276[/COLOR] svn://svn.ffmpeg.org/soc/wmapro wmapro
```

```
cp wmapro/wma* libavcodec
```
```

patch -p0 <wmapro/wmapro_ffmpeg.patch
```

```
patch -p0 <wmapro/audioframesize.patch
```
```

./configure --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-avfilter --enable-avfilter-lavf --enable-libamr-nb --enable-libamr-wb --enable-libvorbis --enable-postproc [COLOR="Blue"]--enable-shared[/COLOR]
```

(--enabled-shared is optional

```
make
```

```
sudo checkinstall --pkgname=ffmpeg --pkgversion "3:0.svn`date +%Y%m%d`-12ubuntu3" --default

```

If you used --enabled -shared than after the install 

```
sudo ldconfig
```

Same Ex. I used in mplayer thread (on my standard hardy install - wma3(pro) to aac, about the same bitrate, vbr LC

> doug@doug-desktop:~$ ffmpeg -i wpro.wma -acodec libfaac -aq 320 wpro.m4a
FFmpeg version [COLOR="Blue"]SVN-r18839,[/COLOR] Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-avfilter --enable-avfilter-lavf --enable-libamr-nb --enable-libamr-wb --enable-libvorbis --enable-postproc
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.29. 0 / 52.29. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on May 20 2009 00:59:36, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu4)
Input #0, asf, from 'wpro.wma':
  Duration: 00:01:14.34, start: 1.451000, bitrate: 293 kb/s
    Stream #0.0(eng): Audio: wmapro, 48000 Hz, stereo, s16, 287 kb/s
[wmapro @ 0x8a335e0][18] [0] [3] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [e0] [0] [0] [0] 
[wmapro @ 0x8a335e0] ed sample bit depth = 16
[wmapro @ 0x8a335e0] ed decode flags = e0
[wmapro @ 0x8a335e0] samples per frame = 2048
[wmapro @ 0x8a335e0] log2 frame size = 18
[wmapro @ 0x8a335e0] max num subframes = 16
[wmapro @ 0x8a335e0] len prefix = 1
[wmapro @ 0x8a335e0] num channels = 2
[wmapro @ 0x8a335e0] lossless = 0
Output #0, ipod, to 'wpro.m4a':
    Stream #0.0(eng): Audio: libfaac, 48000 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    1937kB time=75.63 bitrate= 209.8kbits/s    
video:0kB audio:1909kB global headers:0kB muxing overhead 1.486027%
doug@doug-desktop:~$ 




Edit: and obviously, in the context of this thread, you should have no issues decoding, extracting or converting the .aac audio from the newer youtube videos

I found for some players (to view the video itself) they work better if you use ffmpeg to 
> ffmpeg -i name.flv -acodec copy -vcodec copy name.mp4

---

### Post by logos34 on 2009-05-20
I did everything as you said, but got this error at the end of make:

> [B]libavcodec/wma3dec.c: In function &#8216;wma3_decode_init&#8217;:
libavcodec/wma3dec.c:315: error: too many arguments to function &#8216;ff_mdct_init&#8217;
make: *** [libavcodec/wma3dec.o] Error 1
[/B]

---

### Post by mc4man on 2009-05-21
This is why I dislike using svn versions, you never now what to expect.
(From now on I'm creating a text file in the build folder to note -r's used 

The problem seems to be the wmapro checkout version

I built it twice last night no problem (one with -shared, one without

Just tried again ,same error you see 

Couldn't get it to build.

Took a wmapro folder I had on the desktop ([COLOR="Blue"]-r unknown[/COLOR]), patched, built, and works fine and doesn't need bitstream.h

> [COLOR="Blue"]FFmpeg version SVN-r18839[/COLOR], Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-avfilter --enable-avfilter-lavf --enable-libamr-nb --enable-libamr-wb --enable-libvorbis --enable-postproc --enable-shared
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.29. 0 / 52.29. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on [COLOR="Blue"]May 21 2009 00:44:37,[/COLOR] gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu4)
Input #0, asf, from 'wpro.wma':
  Duration: 00:01:14.34, start: 1.451000, bitrate: 293 kb/s
    Stream #0.0(eng): Audio: wmapro, 48000 Hz, stereo, s16, 287 kb/s
File 'wpro.m4a' already exists. Overwrite ? [y/N] y
[wmapro @ 0x80775e0][18] [0] [3] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [e0] [0] [0] [0] 
[wmapro @ 0x80775e0] ed sample bit depth = 16
[wmapro @ 0x80775e0] ed decode flags = e0
[wmapro @ 0x80775e0] samples per frame = 2048
[wmapro @ 0x80775e0] log2 frame size = 18
[wmapro @ 0x80775e0] max num subframes = 16
[wmapro @ 0x80775e0] len prefix = 1
[wmapro @ 0x80775e0] num channels = 2
[wmapro @ 0x80775e0] lossless = 0
Output #0, ipod, to 'wpro.m4a':
    Stream #0.0(eng): Audio: libfaac, 48000 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    1937kB time=75.63 bitrate= 209.8kbits/s    
video:0kB audio:1909kB global headers:0kB muxing overhead 1.486027%





Just doing a built using wmapro -r 4276 now, will let you now how it works.

( I may just upload the wmapro folder from last night and the unknown one to mediafire

---

### Post by logos34 on 2009-05-21
> **mc4man said:**
> This is why I dislike using svn versions, you never now what to expect.
(From now on I'm creating a text file in the build folder to note -r's used 

The problem seems to be the wmapro checkout version

I built it twice last night no problem (one with -shared, one without

Just tried again ,same error you see 

Couldn't get it to build.

Is there any way to perhaps substitute a non-SVN wmapro? 

BTW, the patches reported 'success' after each command...configure step looked good...so I don't think a mistake crept in (I copied an pasted everyhting you posted).

What if I removed bitstream.h?

---

### Post by mc4man on 2009-05-21
Edited in a specific -r in the instructions. I'd delete the ffmpeg folder in ffmpeg2 and start over (went back 5 revisions, follow all the posted instructions as before (including adding bitstream.h

Otherwise I'll upload the unknown version that doesn't need the bitstream.h and i'll upload the one from last nights build (mediafire seems to be having an issue atm

---

### Post by logos34 on 2009-05-21
ok, be back with make results (not-so-soon--I've only got a single-core entry-level Sempron)

---

### Post by mc4man on 2009-05-21
Turns out in the wmapro folder there is a .svn that shows revision number, last nights was 4279

> I've only got a single-core entry-level Sempron)

I can see why your sticking with hardy,

I have 2 p4 desktops, the better one, 3.4/1 gig ram runs intrepid fine, could probably run jaunty ok, but hardy runs great so I'm keeping that

The 3.02 with 1/2 gb ram doesn't cut it on jaunty at all

(my little dell m1330 (core2duo) laptop flys on jaunty live cd, it's like another world


Edit 
-r 4279 built without the added bitstream.h, I don't think it hurts to have in just in case.

The libavcodec/wma3dec.c error when you need to add it is different than you posted above and is a ton of error lines, easy to distinguish.

The too "many arguments to function &#8216;ff_mdct_init&#8217;" error means either the wmapro version won't work, or the ffmpeg version won't work or neither will work.

---

### Post by logos34 on 2009-05-21
last part of make:

> ...
In file included from libavcodec/motion_est.c:226:
libavcodec/motion_est_template.c:237: warning: C99 inline functions are not supported; using GNU89
libavcodec/motion_est_template.c:237: warning: to disable this warning use -fgnu89-inline or the gnu_inline function attribute
libavcodec/motion_est_template.c:1156: warning: C99 inline functions are not supported; using GNU89
libavcodec/motion_est.c: In function &#8216;interlaced_search&#8217;:
libavcodec/motion_est.c:689: warning: &#8216;P[2][0]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:689: warning: &#8216;P[2][1]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:689: warning: &#8216;P[3][0]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:689: warning: &#8216;P[3][1]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:689: warning: &#8216;P[4][0]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:689: warning: &#8216;P[4][1]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c: In function &#8216;h263_mv4_search&#8217;:
libavcodec/motion_est.c:539: warning: &#8216;P[2][0]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:539: warning: &#8216;P[2][1]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:539: warning: &#8216;P[3][0]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:539: warning: &#8216;P[3][1]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:539: warning: &#8216;P[4][0]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:539: warning: &#8216;P[4][1]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c: In function &#8216;ff_estimate_b_frame_motion&#8217;:
libavcodec/motion_est.c:1749: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.2/README.Bugs>.
make: *** [libavcodec/motion_est.o] Error 1

---

### Post by mc4man on 2009-05-21
Putting aside this wma 'nonsense' for a second, did the last build that succeeded do what you want otherwise? And was it a svn or the 0.5 release

If you were to follow FO's guide using the latest svn did the build succeed?

I'm asking because those lines will show up, but you should move past the 'warning's, not get a seg fault.

Ex. using Fo's guide, (latest svn, no wmapro, his configure, in other words exactly as the guide shows.
> 
In file included from libavcodec/motion_est.c:226:
libavcodec/motion_est_template.c:237: warning: C99 inline functions are not supported; using GNU89
libavcodec/motion_est_template.c:237: warning: to disable this warning use -fgnu89-inline or the gnu_inline function attribute
libavcodec/motion_est_template.c:1156: warning: C99 inline functions are not supported; using GNU89
libavcodec/motion_est.c: In function &#8216;interlaced_search&#8217;:
libavcodec/motion_est.c:689: warning: &#8216;P[2][0]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:689: warning: &#8216;P[2][1]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:689: warning: &#8216;P[3][0]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:689: warning: &#8216;P[3][1]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:689: warning: &#8216;P[4][0]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:689: warning: &#8216;P[4][1]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c: In function &#8216;h263_mv4_search&#8217;:
libavcodec/motion_est.c:539: warning: &#8216;P[2][0]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:539: warning: &#8216;P[2][1]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:539: warning: &#8216;P[3][0]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:539: warning: &#8216;P[3][1]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:539: warning: &#8216;P[4][0]&#8217; may be used uninitialized in this function
libavcodec/motion_est.c:539: warning: &#8216;P[4][1]&#8217; may be used uninitialized in this function [COLOR="Blue"] <- compiler may pause [/COLOR]
gcc -DHAVE_AV_CONFIG_H -I. -I"/home/doug/Desktop/ffiie/ffmpeg" -D_ISOC99_SOURCE -D_POSIX_C_SOURCE=200112 -std=c99 -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -fomit-frame-pointer -pthread -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -Wcast-qual -Wwrite-strings -Wundef -O3 -fno-math-errno        -c -o libavcodec/ratecontrol.o libavcodec/ratecontrol.o
....and continues successfully


I guess what I'm asking have you built any recent svn version successfully?




Edit: Actually the point your failing is fairly early in the build, just checked the complete output. It's from lines 337 to 355 (give or take a few

The wmapro lines are at 604-605 (this is what's shown when things go 'right'
> fomit-frame-pointer -pthread -g -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -Wcast-qual -Wwrite-strings -Wundef -O3 -fno-math-errno          -c -o libavcodec/wma3dec.o libavcodec/wma3dec.c

So somethings changed, (because you were getting there before, with an error, but still getting there

Maybe your box has had enough of building tonight, I'd try again later (using fresh sources

That point, at around 355 or so is one of the couple of times the compiler pauses for a bit (somewhat suspect you get a segfault there

---

### Post by logos34 on 2009-05-21
> **mc4man said:**
> Putting aside this wma 'nonsense' for a second, did the last build that succeeded do what you want otherwise? And was it a svn or the 0.5 release

yes.  As I said, I believe it was SVN, but not sure because ffmpeg version just says '0.5'

> If you were to follow FO's guide using the latest svn did the build succeed?

yes, already did that

> 
So somethings changed, (because you were getting there before, with an error, but still getting there

Maybe your box has had enough of building tonight, I'd try again later (using fresh sources

ok.  I retried it and it appears to have worked, despite some complaints at the end (but not seg faults or fatal errors). 
> 
$ ffmpeg
FFmpeg version [COLOR="Red"]**SVN-r18839,**[/COLOR] Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-avfilter --enable-avfilter-lavf --enable-libamr-nb --enable-libamr-wb --enable-libvorbis --enable-postproc
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.29. 0 / 52.29. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on May 21 2009 13:57:06, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
At least one output file must be specified


**[COLOR="Red"]ffmpeg_3:0.svn20090521-12ubuntu3-1_amd64.deb[/COLOR]**

Now lemme try converting a wmapro file...

---

### Post by logos34 on 2009-05-21
ok, here's what 'ffmpeg -formats shows:

>  [COLOR="Red"]D A    wmapro          Windows Media Audio 9 Professional[/COLOR] [[COLOR="Blue"]that right, decoder ONLY?[/COLOR]]
 DEA    wmav1           Windows Media Audio 1
 DEA    wmav2           Windows Media Audio 2
 DEVSD  wmv1            Windows Media Video 7
 DEVSD  wmv2            Windows Media Video 8
 D V    wmv3            Windows Media Video 9


I tried conversion with this alleged wma pro file:

> $ mediainfo CapaRezza_Intro.wma 
General #0
Complete name                : CapaRezza_Intro.wma
Format                       : Windows Media
File size                    : 1.86 MiB
PlayTime                     : 1mn 20s
Bit rate                     : 194 Kbps
Maximum bit rate             : 193 Kbps
Encoded date                 : UTC 2008-05-18 19:58:43.892

Audio #0
Codec                        : WMA2
Codec/Info                   : Windows Media Audio 2
Codec description            :  - 
Bit rate                     : 192 Kbps
Channel(s)                   : 2 channels
Sampling rate                : 44.1 KHz

> $ ffmpeg -i CapaRezza_Intro.wma -acodec libfaac -aq 320 wpro.m4a
FFmpeg version SVN-r18839, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-avfilter --enable-avfilter-lavf --enable-libamr-nb --enable-libamr-wb --enable-libvorbis --enable-postproc
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.29. 0 / 52.29. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on May 21 2009 13:57:06, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, asf, from 'CapaRezza_Intro.wma':
  Duration: 00:01:19.04, start: 1.580000, bitrate: 197 kb/s
    Stream #0.0: Audio: wmav2, 44100 Hz, stereo, s16, 192 kb/s
Output #0, ipod, to 'wpro.m4a':
    Stream #0.0: Audio: libfaac, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    2286kB time=80.41 bitrate= 232.9kbits/s    
video:0kB audio:2258kB global headers:0kB muxing overhead 1.227771%


---

### Post by mc4man on 2009-05-21
Looks like you've made some progress. 
That sample is wma2 (not pro ([COLOR="Blue"]wma3[/COLOR])

Here's some wmapro samples (audio and audio with an hd video 

[http://samples.mplayerhq.hu/A-codecs/WMA9/wmapro/](http://samples.mplayerhq.hu/A-codecs/WMA9/wmapro/)

Atm moment decoding only

For 64 bit what's probably a bit more useful for playback is a patched mplayer build
(not a factor for mplayer in 32 bit which uses the w32 or win32 codecs

---

### Post by logos34 on 2009-05-21
cool, I think I'm in business now:

> $ mediainfo New\ Stories\ \(Highway\ Blues\)-2.wma 
General #0
Complete name                : New Stories (Highway Blues)-2.wma
Format                       : Windows Media
File size                    : 1.44 MiB
PlayTime                     : 1mn 33s
Bit rate                     : 129 Kbps
Maximum bit rate             : 129 Kbps
Encoded date                 : UTC 2006-02-15 10:17:33.532

Audio #0
Codec                        : WMA3
Codec/Info                   : Windows Media Audio 3
Codec description            :  - 
Bit rate                     : 128 Kbps
Channel(s)                   : 2 channels
Sampling rate                : 44.1 KHz


> $ ffmpeg -i New\ Stories\ \(Highway\ Blues\)-2.wma -acodec libfaac -aq 320 wpro2.m4a
FFmpeg version SVN-r18839, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-avfilter --enable-avfilter-lavf --enable-libamr-nb --enable-libamr-wb --enable-libvorbis --enable-postproc
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.29. 0 / 52.29. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on May 21 2009 13:57:06, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, asf, from 'New Stories (Highway Blues)-2.wma':
  Duration: 00:01:32.04, start: 1.579000, bitrate: 131 kb/s
    Stream #0.0(eng): Audio: wmapro, 44100 Hz, stereo, s16, 128 kb/s
[wmapro @ 0x108df10][18] [0] [3] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [e0] [0] [0] [0] 
[wmapro @ 0x108df10] ed sample bit depth = 16
[wmapro @ 0x108df10] ed decode flags = e0
[wmapro @ 0x108df10] samples per frame = 2048
[wmapro @ 0x108df10] log2 frame size = 16
[wmapro @ 0x108df10] max num subframes = 16
[wmapro @ 0x108df10] len prefix = 1
[wmapro @ 0x108df10] num channels = 2
[wmapro @ 0x108df10] lossless = 0
Output #0, ipod, to 'wpro2.m4a':
    Stream #0.0(eng): Audio: libfaac, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
[wmapro @ 0x108df10]input buffer to small
size=    2289kB time=93.51 bitrate= 200.6kbits/s    
video:0kB audio:2257kB global headers:0kB muxing overhead 1.423391%

Thanks again...interesting learning experience...real pain to get support for some codecs...Now I'll have to go out of my way to download wmapro audio just to feel it was time well spent!

---

### Post by mc4man on 2009-05-21
I think this may be one of those cases where the journey may prove more useful than the destination.

I'd assume/hope the orig. issue (.flv  h.264 with aac audio) is improved

---

### Post by andrew.46 on 2009-05-21
Hi mc4man,

> **mc4man said:**
> For 64 bit what's probably a bit more useful for playback is a patched mplayer build
(not a factor for mplayer in 32 bit which uses the w32 or win32 codecs

For those running the 32 bit MPlayer patched for ffwmapro there is still some satisfaction in using one less external windows codec though :-).

Andrew

---

### Post by mc4man on 2009-05-21
> For those running the 32 bit MPlayer patched for ffwmapro there is still some satisfaction in using one less external windows codec though

I've done that for myself (only have 32 bit installs

It has a more interesting 'info box' also

---

### Post by ikt on 2009-11-06
> **SuperSonic4 said:**
> I would use [Downloadhelper](https://addons.mozilla.org/en-US/firefox/addon/3006) to get them as either flv or mp4 files on your pc (it's an easier to understand name too) and then use ffmpeg as stated in post 3.

Downloadhelper does have a built in converter (which uses ffmpeg as a backend) but I've never got it to work

I would actually prefer to use Downloadhelper, I'm interested in figuring out why it doesn't work, has anybody got it to work? 

If not I might email the author of the addon.

---

### Post by bulletxt on 2009-11-09
AcetoneISO can download videos from youtube and extract the audio to wav within 2 clicks.

---

### Post by Rated on 2010-11-19
I find using online convertors faster way to do the same thing [www.listentoyoutube.com](www.listentoyoutube.com)

---

