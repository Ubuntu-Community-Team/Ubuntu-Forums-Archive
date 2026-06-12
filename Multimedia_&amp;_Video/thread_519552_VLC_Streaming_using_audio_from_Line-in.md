---
title: "VLC Streaming using audio from Line-in"
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by LeGollemux on 2007-08-07
I have a successful video stream running over my LAN using an UBUNTU box with an SAA7134 TV card installed. 

The only way I can get audio is via the line in. 

I now need to point VLC to the line-in for audio, or route the Line-in audio to a sound device that VLC understands. 

VLC has some tools for sorting our lip-syncing once I have that problem.

any takers??

---

### Post by LeGollemux on 2007-08-08
Anybody...?   anybody..?

---

### Post by Strelock on 2007-08-08
can you please post your vlc command to stream from the tuner? I'm still struggling :)

---

### Post by LeGollemux on 2007-08-10
Sorry about the delay. Public holiday got in the way.

here is the command line Im using, youmay need to change the settings for channel etc. Im using composite in so VLC sees that as "channel-1".

> vlc v4l:/dev/video0:norm=pal:channel=1:size=320x240:/adev=/dev/dsp:audio=0 --sout '#transcode{vcodec=mp4v,acodec=mpga,vb=128,ab=16,vt=80000,keyint=80,deinterlace}:std{access=udp,mux=ts,url=234.5.6.7}' --ttl 12 

The "vb=128" is the video bandwidth, feel free to pump that up to whatever your link can handle. 1024 looks great on a LAN.

Hope this helps.

---

### Post by LeGollemux on 2007-08-10
woohoo! Solved!! 

I found a plugin for VLC that seems handle the audio routing somewhat.
Its called "vlc-plugin-alsa" imagine that.

I now have great video picture, and audio with perfect lip-sync over my LAN. 

now to set about tweaking it...see if I can break it.

---

