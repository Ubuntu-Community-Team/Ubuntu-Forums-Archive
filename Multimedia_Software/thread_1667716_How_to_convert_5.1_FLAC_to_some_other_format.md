---
title: "How to convert 5.1 FLAC to some other format?"
date: 2011-01-15
forum: Multimedia Software
---

### Post by Izmo on 2011-01-15
I have a problem playing a video file. The problem is it has audio which is encoded using 5.1 FLAC. When using mplayer I only get 2 of these channels (sounds truly awful, especially since speech isn't on either of them). VLC is the only Linux-program that I've found that seems to be able to deal with the audio. VLC, on the other hand doesn't play the video properly, since it's unable to use VDPAU.

What I'm trying to do is use VLC to convert the audio into another format (*any* format that mplayer can deal with - I don't care if it's mono as long as all the sounds are there). So far I have been completely unsuccessful. VLC does indeed *play* the 5.1 FLAC, but as soon as I ask it to output the ¤@%&!! thing to a file of another format I only get sputtering audio with tons of static completely regardless of the format I tried converting it to.

Has anyone else encountered this annoyance? And more importantly has anyone been able to convert the arcane 5.1 FLAC format to something more readily usable?

(I'm using kubuntu 10.04.)

---

### Post by solar george on 2011-01-15
Try installing handbrake from [www.handbrake.fr](www.handbrake.fr) its a dvd ripper/encoder but if you don't mind re-encoding the video as well it can be set mixdown to stereo. 

Getting proper audio sync without re-encoding the video is really a hit and miss process but you may beable to manage it by following parts of one of the many dvd ripping with ffmpeg tutorials you can find with google (i've never tried myself though).

---

### Post by BicyclerBoy on 2011-01-15
VLC plays 1080 H264 on a core2duo & no vdpau.
So you should be able to play it.

It does not look as good as MythTV or XBMC setup using vdpau etc..

ffmpeg will transcode FLAC5.1.
FLAC (& ogg) are arguably the best audio formats for the FOSS world.

Note: VLC defaults to playing the stereo 2 ch chopped of the 5.1 at every new track.
You need to reselect the audio 5.1 device once the track has started playing.
Does this in latest windoze version as well.
Fortunately my 5.1 music is > 1 hr long.

The ffmpeg 5.1 to 2ch downmix is broken/does not work.
So use 5.1 AAC or find a gstreamer program or ffmpeg wrapper that downmixes properly.

---

### Post by Izmo on 2011-01-16
> Try installing handbrake from [www.handbrake.fr](www.handbrake.fr) its a dvd ripper/encoder but if you don't mind re-encoding the video as well it can be set mixdown to stereo.

That seemed to work. Thanks.

> VLC plays 1080 H264 on a core2duo & no vdpau.

Maybe. My system is unfortunately a tad too slow for 1080p to be acceptable without VDPAU.

> ffmpeg will transcode FLAC5.1.

I tried that but couldn't get it to work. It may have been my lack of familiarity with the software, but the conversions I managed to produce were complete failures. :sad:

> So use 5.1 AAC or find a gstreamer program or ffmpeg wrapper that downmixes properly. 

I'll look into that if I run into problems with the handbrake approach. Thanks for the tips.

---

### Post by BicyclerBoy on 2011-01-16
Sorry should have said.
The stock std ffmpeg & ffmpeg shared libraries in the ubuntu repositories are all non-starters..
You have to replace all the libraries & build ffmpeg yourself.

HandBrake works out of the box but I think it still needs the ffmpeg derived shared libraries to be fixed. (libav*)

---

### Post by solar george on 2011-01-16
What about the ones from the medibuntu repos, do you know if they have the fix? This might also be connected to the vlc problems as it uses libavcodec as well...

---

### Post by BicyclerBoy on 2011-01-16
The medibuntu libav*-extra-52s should be okay

Worth getting w64codecs & nonfreecodecs

---

### Post by JohnAStebbins on 2011-01-16
> **BicyclerBoy said:**
> Sorry should have said.
The stock std ffmpeg & ffmpeg shared libraries in the ubuntu repositories are all non-starters..
You have to replace all the libraries & build ffmpeg yourself.

HandBrake works out of the box but I think it still needs the ffmpeg derived shared libraries to be fixed. (libav*)

HandBrake statically links the ffmpeg libraries it uses.  Distributions often provide broken/buggy versions of ffmpeg.  And ffmpeg isn't known for keeping their API/ABI stable.  So we pick an ffmpeg revision, test it, and ship it with our binary.

---

