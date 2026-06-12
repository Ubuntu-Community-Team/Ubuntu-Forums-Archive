---
title: "record audio output"
date: 2008-03-24
forum: Multimedia &amp; Video
---

### Post by blakecraw on 2008-03-24
Is there a way to capture the audio that gets sent to the speaker (for example, from a song playing in a youtube video) and save it in a file?

I've tried sox but I could only get it to record from a microphone, which isn't what I want; I'm trying to send the sound card's output to a file, and would appreciate any help!

thanks,

blake

---

### Post by Bubba64 on 2008-03-25
Download helper in Firefox add ons will save video and sound converter which is in add remove will covert it to audio. Sound recorder in sound and video will capture live stream audio, but you have to find what channel it will capture through and what type of file mp3, flac, ogg, will work. There are probably easier ways hopefully somebody else will comment.

---

### Post by warp99 on 2008-03-25
I use a program called Kwave that will capture a stream file direct from the ALSA output. This works nicely if I need to capture a sound file with DRM since I can play the file under Windows XP  in a VMware image and capture the sound.

If you want to capture the sound from a youtube video you could always download the .flv file using either a Greasemonkey script for youtube or use youtube-dl:

[http://www.arrakis.es/~rggi3/youtube-dl/](http://www.arrakis.es/~rggi3/youtube-dl/)

Then you can can strip the sound from the file using ffmpeg:

```
ffmpeg -i foo.flv -ab 64 foo.mp3 
```

This will output a mp3 at a bitrate of 64. For more options type 'man ffmpeg' for a complete description. 

You can always capture the file using mplayer by using the -dumpstream -dumpfile or -dumpaudio -dumpfile parameters:

```
mplayer rtsp://streamsrus/foo_stream.rm -dumpstream -dumpfile foo.rm
```

This works for .avi, .wav, .flv or any other file format that mplayer can stream as long as you have a valid url to the file. For more options type 'man mplayer' for a complete description :)

---

### Post by blakecraw on 2008-03-25
thanks warp99, mplayer with -dumpaudio is working great. 

I couldn't get kwave to work since I'm using gnome and it wanted me to do something with kde; I'm not too worried about messing with that right now, although it sounds like that's what I was looking for (save alsa output). Is there a way to use alsa's output as the input file for ffmpeg, and save it like that? I tried to work that out but wasn't able to.

---

### Post by warp99 on 2008-03-25
ffmpeg I believe does not have ALSA support, but if you redirect the file to /dev/dsp then you could capture the audio:

```
ffmpeg -f audio_device -i /dev/dsp -ab 64 -acodec mp2 output.mp2
```

There are most likely some native gnome applications that capture the ALSA output, but I'm not sure. Maybe someone else can chime in or you could use the search feature in Synaptic to find what you're looking for. Good luck. :)

---

