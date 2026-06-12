---
title: "Problem Converting MKV to AVI"
date: 2011-01-11
forum: Multimedia Software
---

### Post by Gex010 on 2011-01-11
Hi guys, I am using winff to convert an MKV file into a AVI but I get the following error:
Unknown encoder 'libxvid'

I remember at some stage installing this libxvid because it was a dependency for another program (can't remember what)

But now it seems like it is causing a problem, I read that I need to change the encoder that I am using from this libxvid to the xvid encoder, but not really sure if that is true or how to go about doing that.

---

### Post by cotcot on 2011-01-11
It might be because the default ffmpeg version misses some codecs because of license problems.

Uninstalling the default ffmpeg and installing ffmpeg from the [[COLOR="blue"]medibuntu repositories[/COLOR]]("https://help.ubuntu.com/community/Medibuntu") or [[COLOR="Blue"]compiling ffmpeg [/COLOR]]("http://pasindudps.blogspot.com/2010/12/compiling-ffmpeg-in-ubuntu-1010.html")could be a solution.

---

### Post by inobe on 2011-01-11
i am getting a .mkv video clip to test for you.

i will post back my finding in a few.

side notes, i have the medibuntu repo w- ffmpeg and restricted extras

---

### Post by inobe on 2011-01-11
it's working without error in winff, handbrake works too converting to m4a.

---

### Post by Gex010 on 2011-01-11
> **cotcot said:**
> It might be because the default ffmpeg version misses some codecs because of license problems.

Uninstalling the default ffmpeg and installing ffmpeg from the [[COLOR=blue]medibuntu repositories[/COLOR]]("https://help.ubuntu.com/community/Medibuntu") or [[COLOR=Blue]compiling ffmpeg [/COLOR]]("http://pasindudps.blogspot.com/2010/12/compiling-ffmpeg-in-ubuntu-1010.html")could be a solution.

Meh this is starting to get really irritating I have tried a couple other programs but it seems they all give me the same error!

I uninstalled ffmpeg, added medibuntu to my repositories but there does not seem to be a ffmpeg under packages for 10.10 so I just reinstalled from the normal source, which made no difference.

Then I tried compiling ffmpeg by following the link but I get stuck because the installation can find a specific file. (error from log attached)

What is libxvid anyway?

---

### Post by inobe on 2011-01-11
here's what i do when i install k/ubuntu.

run updates

get the restricted extras

add the medibuntu repo.... get the w codecs

install ffmpeg

winff

handbrake

done.

i think you need to update the repos via terminal

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

then 

```

sudo apt-get install ffmpeg
```

---

### Post by cotcot on 2011-01-11
Have you installed x264 first ? (followed the complete tutorial of the link ?)

[[COLOR="Blue"]Here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095") is another howto for compiling ffmpeg. This is the one I always use.

libxvid is an open source codec for mpeg-4 video.

---

### Post by FakeOutdoorsman on 2011-01-11
> **Gex010 said:**
> Hi guys, I am using winff to convert an MKV file into a AVI but I get the following error:
Unknown encoder 'libxvid'

I remember at some stage installing this libxvid because it was a dependency for another program (can't remember what)

But now it seems like it is causing a problem, I read that I need to change the encoder that I am using from this libxvid to the xvid encoder, but not really sure if that is true or how to go about doing that.

If you want libxvid support in the repository FFmpeg then install **libavcodec-extra-52** (assuming you're using Maverick). See the following for more information:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by Gex010 on 2011-01-11
> **inobe said:**
> here's what i do when i install k/ubuntu.

run updates

get the restricted extras

add the medibuntu repo.... get the w codecs

install ffmpeg

winff

handbrake

done.

i think you need to update the repos via terminal

```
sudo apt-get update
``````
sudo apt-get upgrade
```then 

```

sudo apt-get install ffmpeg
```

Well I think my installation is a bit stuffed after all the messing around I have been doing over the last few weeks so I will give this a shot after I re-install.

> **cotcot said:**
> Have you installed x264 first ? (followed the complete tutorial of the link ?)

[[COLOR=Blue]Here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095") is another howto for compiling ffmpeg. This is the one I always use.

libxvid is an open source codec for mpeg-4 video.

Yeah I installed x264 first, and I tried that tutorial aswell with the same result.. honestly I think my install is stuffed, but will let you know how it goes after re-install tomorrow.

Thanx for the help thus far though.

---

### Post by Gex010 on 2011-01-14
> **FakeOutdoorsman said:**
> If you want libxvid support in the repository FFmpeg then install **libavcodec-extra-52** (assuming you're using Maverick). See the following for more information:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg]("http://ubuntuforums.org/showthread.php?t=1117283")

Hi guys, Just wanted to let you know that the above was the solution to my problem.

Thanx FakeOutdoorsman!

---

### Post by Gex010 on 2011-01-14
> **FakeOutdoorsman said:**
> If you want libxvid support in the repository FFmpeg then install **libavcodec-extra-52** (assuming you're using Maverick). See the following for more information:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg]("http://ubuntuforums.org/showthread.php?t=1117283")

Hi guys, Just wanted to let you know that the above was the solution to my problem.

Thanx FakeOutdoorsman!

---

### Post by andrew.46 on 2011-01-14
Mind you rather than use the external libxvid you could use FFmpeg's native implementation by using the following in your string:

```

-vcodec mpeg4 -vtag xvid

```

Plus sound and quality / bitrate settings of course :)

Andrew

---

