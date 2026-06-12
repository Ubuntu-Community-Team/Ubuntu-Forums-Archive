---
title: "avconv AAC-&gt;MP3 audio files don't seek"
date: 2012-06-13
forum: Multimedia Software
---

### Post by Anusien on 2012-06-13
Hi guys. I have a weird sort of issue that's going to reveal some of my glaring holes in the way computers process audio, but that's okay.

I have some video files I'm ripping to .mp3 with ffmpeg and/or avconv. For a while these were XViD .avis. (I don't have any handy to check how the audio was encoded). The backing media source changed to .mp4s encoded with x264, and the audio track is now .aac.

The new .mp3 files, created from ffmpeg, don't seek on my iPhone. They play fine on iTunes, and as long as the device doesn't go to sleep on my phone. If it does, it skips the track rather than try to seek to a specific position. This is leading me to believe there's some issue with the .mp3.

I removed flag after flag, but I am basically doing:
avconv -i FileName.mp4 [-vn] Filename.mp4.mp3

I've tried re-playing the older audio files and they work fine; it's a problem with the audio files and not the playback device.

Any thoughts? I have been messing with flags to ffmpeg and avconv for a week or so; I'm willing to try some off the wall ideas.

---

### Post by roelforg on 2012-06-13
Try this to convert:
```

ffmpeg -i inputfile.mp4 outputfile.mp3

```
make sure you've installed libavcodec-extra-53 (otherwise there is bad/no mp3 support)!
Workes for me just fine.

---

### Post by Anusien on 2012-06-13
> **roelforg said:**
> Try this to convert:
```

ffmpeg -i inputfile.mp4 outputfile.mp3

```
make sure you've installed libavcodec-extra-53 (otherwise there is bad/no mp3 support)!
Workes for me just fine.
I have. I've also verified that libmp3lame is in the ffmpeg -codecs list.

The problem is that this creates a .mp3 file, but it doesn't playback correctly on the iPhone.

Here's a transcode log:
> avconv version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2000-2011 the Libav develop                          ers
  built on Mar 22 2012 05:09:06 with gcc 4.6.3
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'The.Colbert.Report.2012.06.12.Will.Alle                          n.HDTV.x264-LMAO.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isom
    creation_time   : 2011-09-08 11:43:25
  Duration: 00:21:29.19, start: 0.000000, bitrate: 1061 kb/s
    Stream #0.0(und): Video: h264 (High), yuv420p, 720x404 [PAR 404:405 DAR 16:9                          ], 906 kb/s, 29.97 fps, 29.97 tbr, 30k tbn, 59.94 tbc
    Metadata:
      creation_time   : 2011-09-08 11:43:25
    Stream #0.1(und): Audio: aac, 48000 Hz, stereo, s16, 147 kb/s
    Metadata:
      creation_time   : 2011-09-08 11:43:25
Output #0, mp3, to 'The.Colbert.Report.2012.06.12.Will.Allen.HDTV.x264-LMAO.mp4.                          mp3':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isom
    TDEN            : 2011-09-08 11:43:25
    TSSE            : Lavf53.21.0
    Stream #0.0(und): Audio: libmp3lame, 48000 Hz, stereo, s16, 200 kb/s
    Metadata:
      creation_time   : 2011-09-08 11:43:25
Stream mapping:
  Stream #0:1 -> #0:0 (aac -> libmp3lame)
Press ctrl-c to stop encoding
size=   30217kB time=1289.23 bitrate= 192.0kbits/s
video:0kB audio:30216kB global headers:0kB muxing overhead 0.000805%

---

### Post by roelforg on 2012-06-13
Try using ffmpeg itself instead of avconv, they seem to produce different results on my systems (ffmpeg's files were of better quality).

---

### Post by Anusien on 2012-06-13
Same issue.

---

### Post by FakeOutdoorsman on 2012-06-13
You can use ffmpeg to pipe to lame. Perhaps there is a bug in avconv that is causing your issue and going straight to lame might be an alternative:
```
ffmpeg -i input.mp4 -f wav - | lame -V 4 - output.mp3
```
If that works then you can do a batch command like this:
```
mkdir ~/mp3output
for file in *.mp4; do ffmpeg -i "$file" -f wav - | lame -V 4 - ~/mp3output/"${file%.mp4}.mp3"; done
```
The mp3 files will appear in the *mp3output* directory in your home.

Alternatively I'd be interested to know if recent ffmpeg from FFmpeg (not ffaux-"ffmpeg"/avconv from libav) also creates an non-seeking output in your device. Here are instructions that will locally compile ffmpeg, but it won't be installed so it won't mess with your currently installed ffmpeg/avconv from the repo. Instrucitons (adapted from [How To Compile FFmpeg and x264 on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)):

```
sudo apt-get install build-essential libmp3lame-dev yasm
cd
wget -O ffmpeg.tar.gz "http://git.videolan.org/?p=ffmpeg.git;a=snapshot;h=HEAD;sf=tgz"
tar xzvf ffmpeg.tar.gz
cd ffmpeg-HEAD-*
./configure
make -j2

```
Then try these commands:
```
cd ~/ffmpeg-HEAD-*
./ffmpeg -i ~/input.mp4 -acodec libmp3lame -aq 4 ~/output-v.mp3
./ffmpeg -i ~/input.mp4 -acodec libmp3lame ~/output-b.mp3
```
If the files work correctly then we know the issue is with avconv and not real ffmpeg. If they do not then perhaps a bug exists.

---

### Post by Anusien on 2012-06-14
After installing lame, the first bit solved it! I'll try compiling ffmpeg from source to see if it makes a difference, but this did the trick. Thanks!

---

### Post by roelforg on 2012-06-14
> **Anusien said:**
> After installing lame, the first bit solved it! I'll try compiling ffmpeg from source to see if it makes a difference, but this did the trick. Thanks!
 
I can advise doing
```

sudo apt-get build-deb ffmpeg

```
to get the dependencies.
 
though 
```

apt-install ffmpeg

```
worked for me just fine (apt-install is an alias to sudo apt-get install (saves me a lot of typing, same for apt-search=apt-cache search))

---

### Post by andrew_j_w on 2012-06-14
Hi,

I'm having exactly the same issue. Unfortunately it was not solved for me either by piping to lame, or by building ffmpeg from source.

This issue started occurring when I upgraded from 11.10 to 12.04. Given that building ffmpeg didn't solve the issue I suspect that the change is in libmp3lame.

For reference it's not just my iPhone that can't seek in the files, it's my Sonos as well.

Andrew

---

### Post by mc4man on 2012-06-14
> **andrew_j_w said:**
> Hi,

I'm having exactly the same issue. Unfortunately it was not solved for me either by piping to lame, or by building ffmpeg from source.

This issue started occurring when I upgraded from 11.10 to 12.04. Given that building ffmpeg didn't solve the issue I suspect that the change is in libmp3lame.

For reference it's not just my iPhone that can't seek in the files, it's my Sonos as well.

Andrew

If you think it's the lame version then just use an older one. The above is piping to lame so you could simply - 
remove current lame package (not 100% necessary but might as well

install the build-dep for lame, plus checkinstall if desired
grab the 11.10 source for lame ([source only from here]("https://launchpad.net/ubuntu/+source/lame") or 
```
wget https://launchpad.net/ubuntu/+archive/primary/+files/lame_3.98.4.orig.tar.gz
```
extract in a folder, cd to folder & configure to build static only

quick ex.  - screen is folder, ect.
```
./configure --disable-shared
```
Then ```
make
```

```
sudo checkinstall --pkgname=lame-old --backup=no --deldoc=yes --fstrans=no --deldesc=yes --delspec=yes --default

```

I'm on 12.10 but lame now is - 
> doug@doug-XPS-M1330:~$ lame
LAME 64bits version 3.98.4 ([http://www.mp3dev.org/](http://www.mp3dev.org/))

You also _may_ need to consider your lame encoding parameters

To return to current lame remove the lame-old package & re-install lame if you removed

---

### Post by Anusien on 2012-06-27
> **FakeOutdoorsman said:**
> ```
sudo apt-get install build-essential libmp3lame-dev yasm
cd
wget -O ffmpeg.tar.gz "http://git.videolan.org/?p=ffmpeg.git;a=snapshot;h=HEAD;sf=tgz"
tar xzvf ffmpeg.tar.gz
cd ffmpeg-HEAD-*
./configure
make -j2

```
This needs to be ./configure --enable-libmp3lame, right?

---

### Post by Anusien on 2012-06-27
It works with ffmpeg built from source. Seems like a bug in avconv.

---

### Post by FakeOutdoorsman on 2012-06-27
> **Anusien said:**
> This needs to be ./configure --enable-libmp3lame, right?
Yes, good catch. Unfortunately posts can't be edited anymore if they are older than 24 hours and scheduling an edit time with a forum moderator is too inconvenient.

> **Anusien said:**
> It works with ffmpeg built from source. Seems like a bug in avconv.
This finding seems to be a current trend amongst avconv users asking for help in #ffmpeg IRC.

---

### Post by Merrattic on 2012-07-23
I can confirm similar behaviour from avconv when converting mp4 to mp3 (e.g. youtube video to mp3 audio file) and trying playback in Audacious. Audacious reports what would normally be a 3.5 minute track as @ 25 minutes and are not seekable. This issue does not show if played in VLC or rhythmbox.

Not had a chance to compile proper ffmpeg yet on this install to test against it, but was getting no problems with previous install using compiled ffmpeg.

**[EDIT] **Problem solved by using compiled proper ffmpeg

---

