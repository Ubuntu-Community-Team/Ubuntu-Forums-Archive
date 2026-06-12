---
title: "VLC Streaming"
date: 2009-08-01
forum: Mythbuntu
---

### Post by GMU_ninja on 2009-08-01
Hello all!

This is a somewhat related question to Mythbuntu because that is the platform I am using.  I guess the question refers more to VLC streaming.  Any assistance would be appreciated.

So I figured out how to use VLC to "play" the video stream from my PVR-150 card.  I use VLC's open capture device with these settings:
```
Video device name:  /dev/video0
Audio device name:  /dev/video0
Advanced settings...
Input:  2
Audio input:  1
```

After changing those values, I click play and I can see and hear my video/audio stream from the correct inputs.  It works perfectly!

Next, I use the same settings.  Instead of clicking "play" I click the down arrow and click "stream."  For the stream settings I check off "Play Locally" and "HTTP" with the local IP address and port 8080.

When the local stream comes up, it is just fuzz, like it is using the Tuner input (input = 0) instead of the Composite input (input = 2), like I wanted.

Any idea what would be causing this and how I can fix it?

After that, does anyone have an easy way to get the live stream onto a web page (maybe in a flash player) for me to view from any computer?

---

