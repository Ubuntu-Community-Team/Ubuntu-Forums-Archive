---
title: "low-latency IP audio streaming?"
date: 2009-06-12
forum: Multimedia Software
---

### Post by tnttrx on 2009-06-12
hello.

I'm trying to stream audio over IP from one linux box to another (ethernet based LAN for example), but I need low-latencies.

the best result I've got with VLC is about 1000ms and that is far too high.

is there any way/software/technique to lower those latencies below 500ms?

I've found proprietary commercial windows software called AudioTX Communicator, but I'd like to stick with linux if it's possible...

thx.

---

### Post by nIce Cream on 2009-06-13
Hi there TRX, you mighty big man (okrim2000) not to mess with :D

Before PulseAudio I tried several solutions, but non of them worked with low latency. LVC was around 1s latency, which is to high. 

I actually have very similar problem like you, I have a small radio station. 
 
Studio and analog FM transmitter are on two different locations. Locations are connected over two routers.  
 
I need to setup topology like this: 
 
Analog mixer <> analog input on sound card <> PC with linux <> router <> router <> PC with linux <> analog output on sound card <> FM transmitter. 
 
Crucial thing is that latency need to be as low as possible, primarily because of listeners who need to be connected to program when they call over their phone. If there is big latency, there will be echo and loop caused by time line difference, so I need to reduce latency to minimum. 
 
I would like to add that delay between routers (2x cisco 1800) is minimal (1 ms).

Is pulseaudio right solution for this particular situation? 
 
I believe it is.

I am currently having a fight with pulseaudio. I have successfully streamed audio from music application RhytmBox Music Player to another computer, but i can't find a way how to stream audio coming from LINE-IN on the same machine that is running rhytmbox. 
 
I don't know how to do that. I actually see the volume analyser pulsing on the remote machine but i don't know how to redirect that from LINE-IN to speakers. LINE-IN is not muted, i actually can hear everything properly on the machine (on speaker attached to studio machine) in studio.

I have spent 2 days on this, trying to make it work, but i don't have any success.

I am using Desktop UBUNTU 9.04.

Maybe i should try this on older UBUNTU?
[B]
Has anyone streamed LINE-IN or MIC to remote machine using PulseAudio?
[/B]
Thank you so much guys, and girls :D :D .

---

