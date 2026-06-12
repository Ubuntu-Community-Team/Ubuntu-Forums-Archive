---
title: "Error trying to play video files in vlc"
date: 2009-10-23
forum: Multimedia Software
---

### Post by andynatt on 2009-10-23
Hey,

I've just started getting an error when playing video files (mov, avi etc) in VLC

[I]No suitable decoder module:
VLC does not support the audio or video format "avc1". Unfortunately there is no way for you to fix this.[/I]


I've tried to reinstall vlc and any relevant codecs with no joy.  If i try and play the file in mplayer, it works fine.

Can anyone help? I prefer vlc over mplayer and would like it back!


Andy.

---

### Post by RichardLinx on 2009-10-23
Remove and reinstall VLC media player. Did you install all multimedia codecs or just the ubuntu-restricted-extras package? Before reinstalling VLC download the codecs listed below if you haven't already.

```
sudo apt-get install ubuntu-restricted-extras
```

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```

For encrypted DVD playback:
```
sudo apt-get install libdvdcss2
```

w32 codecs: (.rm, rmvb, etc)
```
sudo apt-get install w32codecs
```

For future reference see this guide: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by vinutux on 2009-10-23
becoz of third party repos............

Systems > Administration > Synaptiv package manager

Settings menu > repositories > Third party software(other software in karmic)

untick all repos there.... reload synaptic remove vlc and reinstall

---

### Post by andynatt on 2009-10-23
Have tried what was suggested, I did have all the right components on there.

After a bit of time on google I believe the problem to be related to ffmpeg (which makes sense as I installed this yesterday).

I've removed ffmpeg and re-installed vlc but still no luck.

Is it possible that the codecs haven't been removed that ffmpeg installed?

Here is the command line error :

```
[00000001] main libvlc debug: translation test: code is "en_GB"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000427] avcodec decoder error: cannot open codec (H264 - MPEG-4 AVC (part 10))
[00000427] main decoder error: no suitable decoder module for fourcc `avc1'.
VLC probably does not support this sound or video format.

```

---

### Post by andynatt on 2009-10-23
Fixed it - [http://ubuntuforums.org/showthread.php?t=1281367](http://ubuntuforums.org/showthread.php?t=1281367)

It was a problem with openshot.

---

### Post by vinutux on 2009-10-23
> **andynatt said:**
> Fixed it - [http://ubuntuforums.org/showthread.php?t=1281367](http://ubuntuforums.org/showthread.php?t=1281367)

It was a problem with openshot.

Yeh... it is problem of using third party repos.........

plz....mark thread SOLVED

---

