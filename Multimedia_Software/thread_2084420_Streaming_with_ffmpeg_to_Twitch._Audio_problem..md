---
title: "Streaming with ffmpeg to Twitch. Audio problem."
date: 2012-11-15
forum: Multimedia Software
---

### Post by wirefly on 2012-11-15
Hiya,

I'm streaming to Twitch.TV everything working great, except I either have desktop audio, or microphone audio not both.

How can I get both?

I'm using avconv/ffmpeg with -f alsa -ac 2 -i pulse

also tried with hw:0

I've tried pavucontrol with the ffmpeg on pulse I can then choose game audio from the desktop or the microphone but not both.

What am I missing?

Thanks

Wirefly!

---

### Post by Halbblutplins on 2012-11-15
The thing you want to reach isn't directly possible ...

But it's possible .... therefore you need a script which makes two "listeners" which both put out their "sounds" in one source. Then you only have to choose this source for ffmpeg in pavucontrol.

Script content:

```
#!/bin/bash
pactl load-module module-null-sink sink_name=mix
pactl load-module module-loopback sink=mix
pactl load-module module-loopback sink=mix
exit
```

If you want more sources to stream just copy paste the second last line ;)

**btw.: To see the streams choose in pavucontrol "All Streams" !**


Peter

---

### Post by wirefly on 2012-11-15
Hi Peter,

sorry I should have gone into more details.

I've created those loopbacks and in pavucontrol setup one to Monitor of Internal Audio and the other to Webcam Microphone

When ffmpeg starts I set it to Monitor of Loopback, and no audio gets broadcast, if I then choose either of the original sources, they broadcast no problem.

Any ideas?

---

### Post by wirefly on 2012-11-15
Ah I think I may have cracked this

With those Loopbacks set to Null audio I get nothing,

If I set them to playback on say the HDMI on the video card, then set ffmpeg to record from HDMI, it works.

Hope that makes sense.  Seems it needs the loopback to be playing to an actual device.

I guess I could loopback the microphone to the internal audio, then just capture internal audio too?

---

### Post by dannyboy79 on 2012-11-15
SOrry, don't mean to hi-jack your thread but it seems like you know what you're doing

I'm wondering how it's possible to use ffmpeg to capture dv video from my firewire card and capture mic input form mic port, compress it and then stream it to twitch?

I have a Dazzle Hollywood DV Bridge that takes the composite input from my xbox and sends it over the firewire cable to my computer. I usually just make youtube video using Kdenlive but would love to stream realtime if I could.

What would the entire ffmpeg line be? Is it possible?

---

### Post by wirefly on 2012-11-15
dannyboy79,

Check this out: [Streaming to Twitch.TV with Linux]("http://www.creativetux.com/2012/11/streaming-to-twitchtv-with-linux.html")

Hope it helps.

---

### Post by FakeOutdoorsman on 2012-11-16
> **dannyboy79 said:**
> I'm wondering how it's possible to use ffmpeg to capture dv video from my firewire card and capture mic input form mic port, compress it and then stream it to twitch?

I know nothing of twitch, but I know ffmpeg can use firewire as an input device if it was compiled with "--enable-libiec61883".
```
ffmpeg -f iec61883 -i auto ... output
```

There is also the dv1394 input device, but I've never used it.

Another method is to use dvgrab and pipe to ffmpeg. Untested, basic example:
```
dvgrab - | ffmpeg -f dv -i - ... output
```

One advantage of dvgrab is that you can control your dv device, such as a deck or camera in playback mode. dvcont can also be used to play, stop, rewind, etc, but it is difficult to serialize in a script.

As for your mic see: [Capturing audio with FFmpeg and ALSA](https://ffmpeg.org/trac/ffmpeg/wiki/Capturing%20audio%20with%20FFmpeg%20and%20ALSA).

---

### Post by dannyboy79 on 2012-11-16
> **wirefly said:**
> dannyboy79,

Check this out: [Streaming to Twitch.TV with Linux]("http://www.creativetux.com/2012/11/streaming-to-twitchtv-with-linux.html")

Hope it helps.

awesome, is that your blog post? I can't seem to leave a comment. I am wondering how to change that twitch.sh so it uses dvgrab and then pipes it thru ffmpeg to capture the dv video from my firewire port (from xbox 360 480p input) and compress it to something that my ISP upload limit can handle. maybe like 640x360p flv. NOt even sure my 1.8ghz core2duo will be able to handle that.

---

### Post by dannyboy79 on 2012-12-10
> **wirefly said:**
> dannyboy79,

Check this out: [Streaming to Twitch.TV with Linux]("http://www.creativetux.com/2012/11/streaming-to-twitchtv-with-linux.html")

Hope it helps.
i tried using Linux Mint 14 with Mate and immediately I get this trying to run the twitch.sh script
```
sh twitch.sh 50 50
avconv version 0.8.4-6:0.8.4-0ubuntu0.12.10.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:49:20 with gcc 4.7.2
[x11grab @ 0x9dd1e40] device: :0.0+50,50 -> display: :0.0 x: 50 y: 50 width: 1440 height: 900
[x11grab @ 0x9dd1e40] shared memory extension  found
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  130 (MIT-SHM)
  Minor opcode of failed request:  4 (X_ShmGetImage)
  Serial number of failed request:  11
  Current serial number in output stream:  11
```

```
#! /bin/bash 
TOPXY="$1,$2" 
INRES="1440x900" 
OUTRES="852x480" 
FPS="30" 
QUAL="medium" 
STREAM_KEY=$(cat ~/.twitch_key) 
avconv \
-f x11grab -s $INRES  -r "$FPS" -i :0.0+$TOPXY \
-f alsa -ac 2 -i pulse \
-vcodec libx264 -s $OUTRES -preset $QUAL \
-acodec libmp3lame -ar 44100 -threads 4 -qscale 3 -b 712000  -bufsize 512k \
-f flv "rtmp://live.justin.tv/app/$STREAM_KEY"
```

UPDATE: I changed my INRES to 1280x720 and it was working. AWESOME!

---

### Post by dannyboy79 on 2012-12-15
really struggling with the audio capture! Can anyone help please? Here's screen grabs of pavucontrol.
[https://lh3.googleusercontent.com/-MpBEYeuuRf0/UMx_L_xXZFI/AAAAAAAAAtM/VT56ePKrEU8/s800/Screenshot%2520-%252012152012%2520-%252007%253A46%253A04%2520AM.png](https://lh3.googleusercontent.com/-MpBEYeuuRf0/UMx_L_xXZFI/AAAAAAAAAtM/VT56ePKrEU8/s800/Screenshot%2520-%252012152012%2520-%252007%253A46%253A04%2520AM.png)

[https://lh5.googleusercontent.com/-6zSLFR2tGQA/UMx_A145GsI/AAAAAAAAAtE/_FJy9gTn5hw/s912/Screenshot%2520-%252012152012%2520-%252007%253A44%253A49%2520AM.png](https://lh5.googleusercontent.com/-6zSLFR2tGQA/UMx_A145GsI/AAAAAAAAAtE/_FJy9gTn5hw/s912/Screenshot%2520-%252012152012%2520-%252007%253A44%253A49%2520AM.png)

---

