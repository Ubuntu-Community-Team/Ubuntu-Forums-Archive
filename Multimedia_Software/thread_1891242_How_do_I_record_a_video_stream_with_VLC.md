---
title: "How do I record a video stream with VLC"
date: 2011-12-05
forum: Multimedia Software
---

### Post by bakelitedoorbell on 2011-12-05
Hello,

I have an old video-disc player connected to my computer through a "Hauppauge WinTV" USB video encoder device.  The device appears as /dev/video1 on my system.  I am running Oneric Ocelot.

When I type "mplayer /dev/video1" I get a window that displays the video and audio.  mplayer writes a message saying my computer is too slow to play this, and the video does stutter.  This seems unlikely as I have a laptop with a 2.8 GHz Core2Duo and a NVidia graphics card.

When I type "vlc /dev/video1" I can see the video/audio playing smoothly on my screen.

MY GOAL is to create an archival digital copy of this old video disc, which plays for about an hour.  The recording should be as high quality as is reasonable for an NTSC video.  There is a huge amount of info on the web which is overwhelming.  I just want to do something that seems to be simple, record a video stream to a file (mpeg?).

Can someone please give me an example of what I can type on the command line to use VLC to record from this device, in the proper resolution and aspect ratio.  And how do I stop it when the program is done?

Thanks

---

### Post by ron999 on 2011-12-05
> **bakelitedoorbell said:**
> ... I just want to do something that seems to be simple, record a video stream to a file (mpeg?).

Can someone please give me an example of what I can type on the command line to use VLC to record from this device, in the proper resolution and aspect ratio.  And how do I stop it when the program is done?

Thanks

Hi
To make an mp4 file with h264/aac the basic command looks like this:-
```
cvlc /dev/video1 --sout "#transcode{vcodec=h264,acodec=mp4a,ab=128,channels=2,samplerate=44100}:std{access=file,mux=mp4,dst=output.mp4}" vlc://quit
```
But after a minute or two, interrupt it (control-C) and check the resolution/quality/aspect_ratio/etc.
You may need to add some extra parameters after 'vcodec=h264'.

And how do I stop it when the program is done?
"vlc://quit" should stop the recording when it's finished.

---

### Post by bakelitedoorbell on 2011-12-07
Thank you

I'm trying this, but now I can't get a picture, just the audio with a green screen.  Still trying to figure this out.

---

