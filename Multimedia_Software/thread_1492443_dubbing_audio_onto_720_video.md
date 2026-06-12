---
title: "dubbing audio onto 720 video"
date: 2010-05-24
forum: Multimedia Software
---

### Post by JohnnyC35 on 2010-05-24
hey, I have a movies in .h264(think that's right) format that has a 5.1 speaker audio track, and I tried using avidemux and pitivi to try and add a 2.1 speaker audio track to it but both programs either crash or timeout when trying to import the video. I use XBMC to watch movies and it doesn't seem to be able to use alternate audio tracks from a separate file. VLC doesn't seem to have this issue. Is there a way to either get XBMC to use an external audio file, or get the external audio file dubbed onto the video file?
Thanks :)

---

### Post by ron999 on 2010-05-24
Hi
Think about using 'MKV files creator' to make an mkv file containing the h264 video track and the other audio track.
No 'dubbing' or 'converting' is necessary, just 'add' the tracks then 'start muxing'. 
The packages in Synaptic are:-
mkvtoolnix
and
mkvtoolnix-gui

---

### Post by JohnnyC35 on 2010-05-24
> **ron999 said:**
> Hi
Think about using 'MKV files creator' to make an mkv file containing the h264 video track and the other audio track.
No 'dubbing' or 'converting' is necessary, just 'add' the tracks then 'start muxing'. 
The packages in Synaptic are:-
mkvtoolnix
and
mkvtoolnix-gui

ok. hmm. trying it out right now.
took 2 min to add the 2speaker audio file as an attachment.
... still only have the 5.1 audio track available in xbmc but I do see that the file size is .1Gb larger than the orignal :P
will play with this some more :)

ooh. looks like I need to add a MIME type. doing that now

---

### Post by ron999 on 2010-05-24
Hi
For your mkv file, you don't need to include the 5.1 track.
Don't tick the box.

---

### Post by JohnnyC35 on 2010-05-24
ah there we go
I was being dense and adding it as an attachment and not as a track :S
all fixed now
thanks alot
this is my new favourite program

---

