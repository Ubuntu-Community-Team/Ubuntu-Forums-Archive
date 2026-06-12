---
title: "Capturing and Streaming Video"
date: 2006-12-25
forum: Multimedia &amp; Video
---

### Post by EneWolverine on 2006-12-25
Hi all,

I was just wondering if you might be able to help me out setting up a capture and subsequent streaming server.

I have a dreambox (satellite receiver box) on my LAN network at home. I've tried to open up my router port to allow me to watch the streaming video directly from the dreambox but it doesn't really work and I think it's primarily because of the heavily load on the internet connection.

So I've come up with a plan to solve this but I don't really know if it's possible.

What I want to do is capture video over the network from my dreambox and then simultaneously stream this video from my computer using a server.

I have Ubuntu server installed right now.

I don't if it's possible to simultaneously capture and stream video data. I doubt this would be possible.

Anyhow, if this isn't possible, I thought it might be possible to do it using some sort of batch format with a delay. So basically my computer would capture let's say 10 min of video from the dreambox and save this as a single file. Then a new file would be created to continue capture for the next 10 mins. Meanwhile, some sort of script on my computer would process the first file of 10 mins and stream this on my video streaming server. After having streamed this first file, the script would then delete it and move on to the next file as when the capture for those 10 mins is done.

If possible it would great if the video streaming quality could be reduced so that my server doesn't hog the bandwidth on my network: so stream at like 256 kbps.

Not sure if it's clear what I mean.

Basically it boils down to the fact that I want to be able to watch a tv channel from my dreambox from outside my network, but without directly accessing my dreambox as this uses up too much bandwidth. My server on the network would serve as a means to relay the tv channel.

Any thoughts would be greatly appreciated.

Thanks a lot,

The Wolverine :D

---

### Post by BungaMan on 2007-01-17
If your router is capable of it then set up QoS for data coming from the dreambox to the internet.  Then you don't need to use your pc in between.  If you'll limit bandwith then make sure there's still enough to pass the stream so that your video player does not have to wait for data to arrive.  If 256 is not enough for the stream you'll have to downscale the quality on  your pc and stream from there.  This is not a step-by-step guide but I hope it helps.

---

