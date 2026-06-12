---
title: "Live Stream Desktop with VLC."
date: 2011-05-01
forum: Multimedia Software
---

### Post by The_Orange on 2011-05-01
Yes, I have looked at a ton of tutorials, but none of them seem to answer my questions. )= I was up till 3am last night trying to figure this out and then have been up since 8am working on it again. So, please don't shun me and say that I "didn't try hard enough." x-x

I know there are several HOWTO threads from Ubuntu Forms, one in particular that I looked at was talking about how to use myDesktopRecorder. Tried that, didn't work, so I later found out about VLC. I really, really, really love the VLC program, I just don't know the settings to make it work right for live streaming. 

Here's what I do and where I get stuck:
-Open VLC
-Media > Streaming... > Capture Device > Desktop 
--20 f/s? ( Too high? Too low? )
-Stream
-Source = screen://
-Next
-Destinations > HTTP > Add
--Port = 8080
--Path = / ( Do I put my IP here or...? )
--Activate Transcoding ( Yes or no? What does it do? )
--Profile = ? ( Not sure which one to use. )
-Next
-I was told to leave this page alone, but this is the "Generated stream output string" in case it helps you:
p, li { white-space: pre-wrap; } :sout=#transcode{vcodec=h264,vb=0,scale=0,acodec=mp4a,ab=128,channels=2,samplerate=44100}:http{mux=ffmpeg{mux=flv},dst=:8080/} :no-sout-rtp-sap :no-sout-standard-sap :ttl=1 :sout-keep
-Stream

Any help would be greatly appreciated. (=

---

### Post by Sand3r on 2011-05-22
I have got the exactly same question. Did you get it to work by now?

---

### Post by The_Orange on 2011-05-24
Nope. Gave up on it a bit really.

---

