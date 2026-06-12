---
title: "Using ffmpeg to increase volume of mp3 files"
date: 2010-07-20
forum: Multimedia Software
---

### Post by cygnis1 on 2010-07-20
I was wondering how to increase the volume of ogg and mp3 files using ffmpeg.  Some of the podcasts that I listen to are not loud enough, and I have my media player set to the highest volume.
Thanks,
Cygnis1

---

### Post by ron999 on 2010-07-20
Hi
There's a **-vol** option with ffmpeg.
It's like this:-
```
ffmpeg -i <input_file> -vol <audio_volume> -acodec <audio_codec> <other_parameters> <output_file>
```

The **<audio_volume>** is a number.
256 is normal.
I think if you use 512 then it will double the volume.
I got the information from here:-[http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2008-February/013869.html]("http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2008-February/013869.html")

---

### Post by sextheorist on 2011-10-01
You can use lame program to increase volume easily...
To install lame:

```
sudo apt-get install lame
```
General options:

```
lame [options] <infile> <outfile>
```

Lets say ur input file is luke3.mp3 and to double the volume use code:

```
lame --scale 2 luke3.mp3 luke3out.mp3
```

This will create new file luke3out.mp3 with double volume.
Instead of "2" u can use 3 or 4 for greater volume increase.

For full detail man page click [here.]("http://manpages.ubuntu.com/manpages/gutsy/man1/lame.1.html")

---

### Post by Jose Catre-Vandis on 2012-04-15
Can you use ffmpeg or lame to test the volume level in an audio file, say if you wanted to batch run a set of audio files so they all had the same volume level, or do you need sox for that?

---

