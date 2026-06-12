---
title: "Problems with 'motion' webcam motion sensor app"
date: 2008-03-19
forum: Multimedia &amp; Video
---

### Post by andrewsawyer on 2008-03-19
Hi all,

I'm having a problem with a program called motion that senses motion on your webcam and records a short length of vid, making it a security camera.

I have it installed following the directions here: [http://infectedproject.wordpress.com/2007/06/26/set-up-a-webcam-security-system/](http://infectedproject.wordpress.com/2007/06/26/set-up-a-webcam-security-system/) however when running it I get an error 'No mmap'.  The whole output is below:

```
andrews@andrew-laptop:~$ motion -s
[0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Processing config file /etc/motion/thread0.conf
[0] Motion running in setup mode.
[0] Webcam port 0
[0] Thread device: /dev/video0 input 8
[1] Thread is from /etc/motion/thread0.conf
[0] Waiting for threads to finish, pid: 8117
[1] Thread started
[0] motion-httpd/3.2.3 running, accepting connections
[0] motion-httpd: waiting for data on port TCP 8000
[1] No mmap falling back on read
[1] V4L capturing using read is deprecated!
[1] Motion now only supports mmap.
[1] Motion Exits.
andrews@andrew-laptop:~$ 

```

Would anyone be able to tell me how I might fix this?  The webcam works and can be viewed through Ekiga.  Any help would be much appreciated.

Regards,

Andy

---

### Post by Peturrr on 2008-03-19
"Motion only supports the mmap way of reading images from the [V4L]("http://www.lavrsen.dk/twiki/bin/view/Motion/V4L") device. read is not supported. So if this is the only mode the driver supports then the card is not compatible with Motion. Maybe you should contact the driver team and ask.  Motion needs the image in either YUV420P[?]("http://www.lavrsen.dk/twiki/bin/edit/Motion/YUV420P?topicparent=Motion.SupportQuestion2005x06x02x143352") , YUV422 or RGB24 to work. (or greyscale)" [http://www.lavrsen.dk/twiki/bin/view/Motion/SupportQuestion2005x06x02x143352](http://www.lavrsen.dk/twiki/bin/view/Motion/SupportQuestion2005x06x02x143352)

---

### Post by Dr_Snapid on 2008-06-15
I have the same problem. Whats interesting is that it says it NOW only supports mmap. Does this mean it used v4l in the past?

I wish I knew how to find an older one to try.

---

### Post by Dr_Snapid on 2008-06-17
The version in the repos is too old, thats all. I compiled the latest one from source and all is good. Some of the options in the default config needed tweaking though.

---

