---
title: "MP3 Conversion / LAME installation"
date: 2012-06-18
forum: Multimedia Software
---

### Post by Moif_Murphy on 2012-06-18
Hello,

I have an Ubuntu VPS with remote root access with lots of MP3s on that I'd like to re-encode to a lower bit rate. I've done some research and have found this page: [http://en.linuxreviews.org/HOWTO_Convert_audio_files#Using_lame](http://en.linuxreviews.org/HOWTO_Convert_audio_files#Using_lame)

However, when I try to install LAME I get the following:

> root@123.123.123.123:/# apt-get install lame
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package lame is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lame has no installation candidate

I've tried: ```
dpkg --get-selections | grep lame
```

..with no results so I'm thinking I need to install LAME manually or am I  missing something obvious here.

Thanks

---

### Post by Moif_Murphy on 2012-06-18
Problem solved. I had to enable multiverse.

All I need to do know is find a script to transcode MP3's whilst maintaining id3v2 tags :)

---

### Post by FakeOutdoorsman on 2012-06-18
Recent ffmpeg automatically attempts to preserve most metadata. First enable *libmp3lame* in ffmpeg:
```
sudo apt-get install libavcodec-extra-53
```
Now use ffmpeg. Example command:
```
ffmpeg -i input.ogg -acodec libmp3lame -aq 4 output.mp3
```
Are you using Lucid as shown under your name? In that case install *libavcodec-extra-52* instead and then use:
```
ffmpeg -i input.ogg -acodec libmp3lame -aq 4 -map_meta_data 0:0 output.mp3
```
For a "batch" command:
```
mkdir ~/mp3out
for f in *.ogg; do ffmpeg -i "$f" -acodec libmp3lame -aq 4 -map_meta_data 0:0 ~/mp3out/"${f%.ogg}.mp3"; done
```
The *-aq* in my examples is mapped to *lame -V*.

---

