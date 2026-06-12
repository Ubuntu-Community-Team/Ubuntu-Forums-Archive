---
title: "Cinelerra Audio Issues - Intrepid"
date: 2010-01-20
forum: Multimedia Software
---

### Post by uncle*wally on 2010-01-20
Cinerella experts -  

I am relatively new to Linux and Ubuntu and am trying to get cinelerra working.  The install went without issue using the Synaptic Package Manager.  I can load an MP4 file and the video channel is perfect frame for frame. Nothing shows up in the audio channel and when I play the video in the viewer I get this message repeated continuously in its own window:

virtual int FileMOV:: read_samples(double*, int64_t):quick_time_decode_audio failed.

Any help would be greatly appreciated.   

This file plays perfectly in Totem-movie player VLC and all my other video players.

---

### Post by wildhostile on 2010-01-20
> **uncle*wally said:**
>  . 

Hi uncle wally,

Seems that Cinelerra can't recognize the audio part of your video.
what are the format(videocodec,audiocodec) and the resolution of your media? (midentify yourfile in a terminal)
Cinelerra can't read all format/codecs. You will have to make tests to find your perfect workflow. 
You can convert your video in a format readable by Cinelerra. I know avi(mjpeg,pcm) works fine.
If you don't want to convert, another solution could be to export the audio part (with a converter in .wav format for example) and load it separately into Cinelerra. Got it?

---

### Post by uncle*wally on 2010-01-20
midentify did not work in my terminal - command not found.
I tried identify and got--  no decode delegate for this image format my_file.mp4

Reformatting and exporting in Kino- to video-Generic mpeg2 and audio- wave internal helped a lot.

I now have all the video and the audio channels.  

When I play in viewer the audio plays but the video does not change but catches up to the audio when I pause the replay.

Is this what I should be seeing??

---

### Post by wildhostile on 2010-01-20
> **uncle*wally said:**
>  . 

I think midentify is in mplayer package. I guess you don't have mplayer installed on your system.
You should use a converter to convert your video. Kino is not really a converter.
video converter (frontend): tabencode, handbrake, avidemux, winff, ...
Try to change the audio device in Settings -> Preferences -> Playback to see if it's better.
You can also uncheck the "play every frame" option.
You can get "live help" on the Cinelerra IRC channel on freenode.net.

PS: use the quote button to alert me.

---

### Post by uncle*wally on 2010-01-21
> **wildhostile said:**
> I think midentify is in mplayer package. I guess you don't have mplayer installed on your system.
You should use a converter to convert your video. Kino is not really a converter.
video converter (frontend): tabencode, handbrake, avidemux, winff, ...
Try to change the audio device in Settings -> Preferences -> Playback to see if it's better.
You can also uncheck the "play every frame" option.
You can get "live help" on the Cinelerra IRC channel on freenode.net.



Thank you Wildhostile.  All is working in Cinelerra at least I can load a video, successfully-  I just now need to learn how to use the software package.  I think the hardest part is over.

I do have mplayer and a call to "mplayer filename" in the terminal window gives me the video and audio info, but midentify as a command itself is not recognized. Could that be a search path issue?

Also what is your preferred converter software?

I will look into freenode.net.  Sounds interesting.

---

### Post by wildhostile on 2010-01-21
> **uncle*wally said:**
>  . 

No problem uncle*wally,
As I have a DV PAL camcorder. I don't really need to convert my videos before using them.
In case I need to use other sources that cinelerra can't read, I use to convert them with tabencode (avi for ZS4 compositing which is avi(mjpeg,pcm)) or tovid-interactive (the mpeg2 format). To export for the internet I prefer handbrake.

Have fun.

---

