---
title: "USB Microphone doesn't loopback through HDMI speakers"
date: 2013-01-12
forum: Multimedia Software
---

### Post by atomicspin on 2013-01-12
An exciting new problem has occurred! 

I have a USB microphone that I've plugged in.  I can see via the sound mixer that it is registering the input, but it is not playing out through the speakers.  So far I've tried:

```
pactl load-module module-loopback
```

I've also tried creating an RTP Server and setting it to loopback, but to no avail.  

I know this is probably a complicated one because of USB to HDMI.  Anyone know of anything I can do?

---

