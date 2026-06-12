---
title: "Encoding h.264/aac 5.1 in an mp4 container"
date: 2008-04-24
forum: Multimedia Software
---

### Post by booljayj on 2008-04-24
I need an easy way to back up dvds to my computer, and in the past I have done so by encoding Xvid/aac stereo in an avi container using mplayer. However, the resulting avi can only be played using mplayer because it is technically an invalid file. I want proper avc/aac mp4 files, and I want to preserve the 5.1 surround sound playback. I have managed to construct these scripting parameters using bits of information from all around:

```
#VIDEO Section
mencoder $TITLE.vob\
        -nosound\
        -vf crop=$CROP,dsize=$ASPECT,scale,harddup\
        -ovc x264 -x264encopts qp=26:subq=5:frameref=1:bframes=4:b_pyramid:weight_b:pass=1:bitrate=2000:turbo=1\
        -ofps 24000/1001 -of rawvideo\
        -o /dev/null

mencoder $TITLE.vob\
        -nosound\
        -vf pp=de,crop=720:480:0:0,dsize=$ASPECT,scale,hqdn3d=2:1:2,harddup\
        -ovc x264 -x264encopts qp=26:subq=6:frameref=3:me=hex:partitions=all:bframes=4:b_pyramid:8x8dct:pass=2:bitrate=2000\
        -ofps 24000/1001 -of rawvideo\
        -o $TITLE.h264

#AUDIO Section
	mkfifo audiodump.pcm

	faac -q 100 -I 5,6 -P -R 48000 -C 6 -X audiodump.pcm -o $TITLE.mp4 & mplayer $TITLE.vob\
	-aid $AID -vc dummy -vo null -ao pcm:nowaveheader -channels 6

rm audiodump.pcm

#MUXING Section
mp4creator -create=$TITLE.h264 -rate=23.976 $TITLE.mp4
```

The resulting mp4 file is garbage in terms of audio. Playing the resulting movie mp4 results in weird screeches and silences, while the video plays on perfectly. Playing the audio only mp4 file contains the entire movie soundtrack- except that it is like 5 times too fast. A two hour movie worth of audio is contained in a 30-minute file. Plus, it's stereo.

The main concern to me is fixing the audio encoding section. The output currently is a garbage stereo aac file in an mp4 container. I got all my information for the audio conversion from this: [http://forum.doom9.org/archive/index.php/t-75222.html]("http://forum.doom9.org/archive/index.php/t-75222.html")

Please, any help whatsoever would be so great. If you know anything about faac or pcm or mplayer at all, your input would be welcome.

---

### Post by cor2y on 2008-04-24
In the linux section of doom9 theres a post about h264enc a script that can encode correctly/standard profiles for the codec as well as the use of faac or the nero aac codec (non opensource but free).
It uses X264 and mencoder all you need is to have these installed.
Homepage  [http://h264enc.sourceforge.net/](http://h264enc.sourceforge.net/)
Doom9 thread : [http://forum.doom9.org/showthread.php?t=134652](http://forum.doom9.org/showthread.php?t=134652)

---

### Post by brewstah on 2008-04-27
You might also consider Avidemux.  Version 2.4.1, which is in the Hardy Heron repositories, supports encoding x264 video and aac audio into an mp4 container.  You also have the option of stream copying the ac3 audio by using an mkv container.

---

### Post by booljayj on 2008-04-27
@Cor2y

Well, I looked through the script and here's what I think: A) I can't use the script itself because it's huge overkill and I don't know the details of what it's doing to my files. B) I'm fixed on the h264 section, and I just need to modify the audio section to create valid 5.1 AAC files. C) I wasn't able to extract how to do so from the h264enc script.

@brewsta

Again, I need a script that can be run for each video file, and a gui program like Avidemux gives me no control over the encoding options. I am a big advocate of Matroska, but this is an inappropriate setting for me to use it. I want these video files quicktime-compatible, and mkv is definitely not.

---

### Post by brewstah on 2008-05-07
> I need a script that can be run for each video fileThis is what Avidemux's job control feature is for.  You can setup several jobs with different parameters regarding codecs, filters, and output containers.> a gui program like Avidemux gives me no control over the encoding options.This makes no sense to me.  I've looked at the options in your previous post and I really don't see anything that cannot be done in Avidemux using either codec settings or with the included filters.> I want these video files quicktime-compatibleI have encoded files that play using Quicktime player and on iPods with Avidemux.  And the quality was excellent.

---

### Post by andrew.46 on 2008-05-25
Perhaps it is not entirely what you are after but I have written a page on converting a DVD to h264 / ogg in a matroska container:

[http://www.andrews-corner.org/matrix.html](http://www.andrews-corner.org/matrix.html)

It does not entirely match your needs but perhaps you can use parts of it? Matroska might be a better choice than avi anyway and newer versions of mkvmerge handle a .264 video stream without MP4Box.

I can suggest a possible solution to you audio problem: you should perhaps lose the -nosound option with mencoder and simply use -oac copy and lose the sound from the video stream later. If you use matroska this is easily doen with mkvmerge -A video.264

               Andrew

---

### Post by booljayj on 2008-07-22
Thank you all for your very helpful responses. I have come to the conclusion that finding a clean, efficient, and correct way to encode 5.1 AAC via bash script is impossible/beyond me. I've found that extracting the raw ac3 and muxing the whole thing into a matroska file is really the better way to go. Only one drawback: mixed-rate videos don't encode properly. Oh well, that's something I can live with, and anyone who needs such a thing has the excellent [Handbrake]("http://handbrake.fr/") to manage it.

Now I'm just working on making my script smaller, smarter, and more user-friendly.

---

