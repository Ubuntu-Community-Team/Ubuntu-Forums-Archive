---
title: "&quot;Motion&quot; Error?"
date: 2009-03-09
forum: Multimedia Software
---

### Post by kevin11951 on 2009-03-09
```
[0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Motion 3.2.9 Started
[0] ffmpeg LIBAVCODEC_BUILD 3355136 LIBAVFORMAT_BUILD 3409664
[0] Thread 1 is from /etc/motion/motion.conf
[1] Thread 1 started
[1] cap.driver: "uvcvideo"
[1] cap.card: "USB 2.0 Camera"
[1] cap.bus_info: "0000:00:1a.7"
[1] cap.capabilities=0x04000001
[1] - VIDEO_CAPTURE
[1] - STREAMING
[1] Error selecting input 0
[1] VIDIOC_S_INPUT: Device or resource busy
[1] ioctl(VIDIOCGMBUF) - Error device does not support memory map
[1] V4L capturing using read is deprecated!
[1] Motion only supports mmap.
[1] Capture error calling vid_start
[1] Thread finishing...

```

This is the output of Motion, I don't know what to do to get it to work. :(

---

### Post by Sef on 2009-03-09
Moved to Multimedia and Video.

---

### Post by Housing GrantsApplication on 2009-10-21
Motion error: Can't call method "outfile" on an undefined value
  I upgraded to 4.25 - everything went well.
  I created a new blog to test Motion - pretty good.
  I then went to an 'old' blog same installation - chose "Refresh Blog Templates" and changed to Motion.
  go to rebuild 'old blog' a get this error:: Can't call method "outfile" on an undefined value
  Tried rebuilding just main index - same stuff - different rebuild...
  So, I'm checking templates line by line - all looks well. A little Google research looks like OUTFILE is a Perl command. 
  Where do i start looking?
  Why would it work on a new blog - same install but not the old??
  Help please - I'm ready to get in MOTION - so far all my Motion is backwards
  Thanks in advance
================================================
[COLOR=#800080]**[http://www.granthelpline.com/Housing-grants-given-to-Topeka/Y2009-06-29.htm](http://www.granthelpline.com/Housing-grants-given-to-Topeka/Y2009-06-29.htm)**[/COLOR]

---

