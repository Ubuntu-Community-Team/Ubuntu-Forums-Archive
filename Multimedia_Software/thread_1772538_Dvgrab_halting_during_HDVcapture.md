---
title: "Dvgrab halting during HDVcapture"
date: 2011-05-31
forum: Multimedia Software
---

### Post by !CoffeeTable on 2011-05-31
Running DVgrab with my Canon XH-A1S in HDV mode I get the following.
```
deanb@deanb-MCP7A:~$ dvgrab
Found AV/C device with GUID 0x0000850001d00f31
libiec61883 error: Failed to get channels available.
Waiting for HDV...
Capture Started
"dvgrab-003.m2t":     0.80 MiB 4 frames timecode 00:30:55.13 date 2011.05.31 14:21:11
Capture Stopped
```

A m2t file is generated and VLCplayer will open it but there is nothing in it. I can pipe dvgrab into ffmpeg and get video with a couple frames every second. but I think thats jus the result of dvgrab starting and stopping. FFmpeg also throws a couple errors as a result of the data (or lack thereof) coming from dvgrab.

---

### Post by !CoffeeTable on 2011-06-03
Not really sure what changed... I removed the tape from the device and I was able to live capture, put the tape back in and now it work. :|

---

