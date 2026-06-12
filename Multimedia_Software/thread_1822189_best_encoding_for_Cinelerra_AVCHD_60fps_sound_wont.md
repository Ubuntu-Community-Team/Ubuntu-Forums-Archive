---
title: "best encoding for Cinelerra AVCHD 60fps sound wont play"
date: 2011-08-10
forum: Multimedia Software
---

### Post by streamsanddragonflies on 2011-08-10
hello,

I am using a Panasonic HDC-TM700 camera shot at 1080p60p and the compression is MPEG-4 AVC/H.264 with bitrate? of 28Mbps (VBR). Sound is dolby 5.1 2 ch with MTS or m2ts extension. I need to confirm the best encoding to edit in cinelerra with a Phenom II X4 965 4 Gig DDR3 memory AMD system and NVIDIA GTS 250 PCI e graphics card...

I see the CPU cores working hard when Viewing clips with "Play every frame" option disabled and I fiddled with "background rendering" -not quite sure what settings are best...Don't know how things will go when I render effects...
So I can playback fine MP4 and mov and MV4 - tried various scripts posted to convert with ffmpeg and also tried handbrake and Arista converter and avidemux and even transmageddon Video Transoder.

Some worked better then others...but I can't get SOUND to work in Cinelerra. I had gotten sound to work encoded to MP3 in Kdenlive though...I have ALSA enabled in cinelerra preferences, with 4800HZ sample rate.

So what is the exact script for my video source for cinelerra then? and the appropriate sound and video bitrate? There are so many options in: FFmpeg Howto for example - DNxHD supposedly is a good proxy to use for cinelerra but the script doesn't include anything for sound. Then there is : H.264 Long GOP Encoding that includes code for sound but I couldn't figure out the right bitrate for it to even work.  In another thread, someone suggested to just change the container, which I tried but this time only got the sound in VLC and movie player and coudn't import video properly at all in cinerlerra:   > ffmpeg -i filename.mts -acodec copy -vcodec copy filename.mp4 changed output ext to .mv4 and .mov and still no good...

Hopefully someone can help me get started so I can use Cinelerra!

---

### Post by Eric_the_Red on 2011-11-22
Hey this is the setting that I use to convert my cannon MTS files to cinelerra and it works great
  ffmpeg -i <file name.mts> -sameq -ab 256k -ac 2 -ar 48000 <output.mp4>

I believe that you should be able to change -ac 2 to -ac 6 to keep the 5.1 audio

---

