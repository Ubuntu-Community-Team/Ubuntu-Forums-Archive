---
title: "Media Streams"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by ssnitily on 2007-05-18
Hello,
Basically I'm looking for advice on a media steaming setup.
Here is what I have setup;
Machine A: Windows XP Desktop with media
Machine B: Low-end Laptop with Ubuntu 6.10 Edgy

Right now I'm streaming episodes from A to B with VLC. However I am not versed well enough to do anything other than just stream the video one by one to B, there is no control on B over the stream.

Conditions;
The OS on A and B will not change besides upgrading on B.
The media will stay on A because of the very small hard drive on B.
Control of the video should be on B (hitting next, pause, view the playlist, etc.).

Ok, what do I have to work with. Any ideas? Thanks.

---

### Post by dfreer on 2007-05-18
linux doesn't like streaming media much, in the case of streaming via a web browser. by that I mean in most cases you would need to start the file from the beginning and watch it to the end without any shutter control (change positions in the stream, rewind, etc). 
I'm thinking your best bet would be to share the media folder in question, access the share and mount it to a folder in ubuntu, and then try to play the file as if it is local. you should be able to build playlists and control media playback easily that way.
check out ubuntu guide in my sig (make sure to check the guide for edgy if that is what you are running), they should have a good guide on how to access and mount a windows share.

---

