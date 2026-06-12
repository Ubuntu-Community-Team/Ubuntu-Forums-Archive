---
title: "Webcam works in skype/kopete but not with anything else"
date: 2009-01-12
forum: Multimedia Software
---

### Post by thursty on 2009-01-12
Hi,

I'm running 7.10 and specifically bought a Creative Live! Cam Optia to use with Linux. It works with Skype and kopete "out of the box", but I cannot seem to capture from the command line, following probs: 
```

camorama 
could not connect to /dev/video0

```
```
streamer -o outfile.jpeg: 
no way to get: 320x240 JPEG (JFIF) 
movie writer initialisation failed
```
```
cat /dev/video0 > test.mpg
cat: /dev/video0: No such device
```
(Odd considering:
```
ls -l /dev/video0
crw-rw---- 1 root video 81, 0 2009-01-12 03:27 /dev/video0
```
and /dev/video0 is where skype and kopete get vid from perfectly fine).
streamer and xawtv don't work either.

Any tips please?

---

