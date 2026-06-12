---
title: "trying to use 'motion' package"
date: 2011-02-24
forum: Multimedia Software
---

### Post by leavitodeaver on 2011-02-24
let me preface by saying i'm not terribly savvy with ubuntu, i can handle basics but once i get into coding it confuses me.  i downloaded motion and webcam-server onto my other computer on the local network, but all i really want to do is access a live feed from my main box and be able to record a video if need be, for security purposes (we had a break-in awhile back).  after starting motion, it saved a few .jpgs to the tmp folder, then i shut it down and restarted it as a test, now it's not even doing that, i'll post the readout of what it spat out in a minute.  how do i (1) disable the .jpg saving feature, (2) enable video recording, (3) run it in the background (as a daemon?) without the terminal window being visible onscreen, and (4) access it on the main box?  also, i couldn't seem to edit the motion.conf file even though i'm an administrator, how i do solve that?  thank you so much!

---

### Post by leavitodeaver on 2011-02-24
here's what it spit out, had to run to the other box to get it

[0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Motion 3.2.11 Started
[0] ffmpeg LIBAVCODEC_BUILD 3412993 LIBAVFORMAT_BUILD 3415808
[0] Thread 1 is from /etc/motion/motion.conf
[1] Thread 1 started
[1] cap.driver: "uvcvideo"
[1] cap.card: "UVC Camera (046d:0824)"
[1] cap.bus_info: "usb-0000:00:1d.7-3"
[1] cap.capabilities=0x04000001
[1] - VIDEO_CAPTURE
[1] - STREAMING
[1] Error selecting input 0 VIDIOC_S_INPUT: 
[1] ioctl(VIDIOCGMBUF) - Error device does not support memory map
[1] V4L capturing using read is deprecated!
[1] Motion only supports mmap.
[1] Could not fetch initial image from camera
[1] Motion continues using width and height from config file(s)
[1] Resizing pre_capture buffer to 1 items
[1] bind(): 
[1] Problem enabling stream server in port 8081: 
[1] Thread exiting
[0] httpd bind(): 
[0] httpd thread exit
[0] Motion thread 1 restart
[1] Thread 1 started
[1] cap.driver: "uvcvideo"
[1] cap.card: "UVC Camera (046d:0824)"
[1] cap.bus_info: "usb-0000:00:1d.7-3"
[1] cap.capabilities=0x04000001
[1] - VIDEO_CAPTURE
[1] - STREAMING
[1] Error selecting input 0 VIDIOC_S_INPUT: 
[1] ioctl(VIDIOCGMBUF) - Error device does not support memory map
[1] V4L capturing using read is deprecated!
[1] Motion only supports mmap.
[1] Could not fetch initial image from camera
[1] Motion continues using width and height from config file(s)
[1] Resizing pre_capture buffer to 1 items
[1] bind(): 
[1] Problem enabling stream server in port 8081: 
[1] Thread exiting
[0] Motion thread 1 restart
[1] Thread 1 started
[1] cap.driver: "uvcvideo"
[1] cap.card: "UVC Camera (046d:0824)"
[1] cap.bus_info: "usb-0000:00:1d.7-3"
[1] cap.capabilities=0x04000001
[1] - VIDEO_CAPTURE
[1] - STREAMING
[1] Error selecting input 0 VIDIOC_S_INPUT: 
[1] ioctl(VIDIOCGMBUF) - Error device does not support memory map
[1] V4L capturing using read is deprecated!
[1] Motion only supports mmap.
[1] Could not fetch initial image from camera
[1] Motion continues using width and height from config file(s)
[1] Resizing pre_capture buffer to 1 items
[1] bind(): 
[1] Problem enabling stream server in port 8081: 
[1] Thread exiting
[0] Motion thread 1 restart
[1] Thread 1 started
[1] cap.driver: "uvcvideo"
[1] cap.card: "UVC Camera (046d:0824)"
[1] cap.bus_info: "usb-0000:00:1d.7-3"
[1] cap.capabilities=0x04000001
[1] - VIDEO_CAPTURE
[1] - STREAMING
[1] Error selecting input 0 VIDIOC_S_INPUT: 
[1] ioctl(VIDIOCGMBUF) - Error device does not support memory map
[1] V4L capturing using read is deprecated!
[1] Motion only supports mmap.
[1] Could not fetch initial image from camera
[1] Motion continues using width and height from config file(s)
[1] Resizing pre_capture buffer to 1 items
[1] bind(): 
[1] Problem enabling stream server in port 8081: 
[1] Thread exiting
[0] Motion thread 1 restart
[1] Thread 1 started
[1] cap.driver: "uvcvideo"
[1] cap.card: "UVC Camera (046d:0824)"
[1] cap.bus_info: "usb-0000:00:1d.7-3"
[1] cap.capabilities=0x04000001
[1] - VIDEO_CAPTURE
[1] - STREAMING
[1] Error selecting input 0 VIDIOC_S_INPUT: 
[1] ioctl(VIDIOCGMBUF) - Error device does not support memory map
[1] V4L capturing using read is deprecated!
[1] Motion only supports mmap.
[1] Could not fetch initial image from camera
[1] Motion continues using width and height from config file(s)
[1] Resizing pre_capture buffer to 1 items
[1] bind(): 
[1] Problem enabling stream server in port 8081: 
[1] Thread exiting
[0] Motion thread 1 restart
[1] Thread 1 started
[1] cap.driver: "uvcvideo"
[1] cap.card: "UVC Camera (046d:0824)"
[1] cap.bus_info: "usb-0000:00:1d.7-3"
[1] cap.capabilities=0x04000001
[1] - VIDEO_CAPTURE
[1] - STREAMING
[1] Error selecting input 0 VIDIOC_S_INPUT: 
[1] ioctl(VIDIOCGMBUF) - Error device does not support memory map
[1] V4L capturing using read is deprecated!
[1] Motion only supports mmap.
[1] Could not fetch initial image from camera
[1] Motion continues using width and height from config file(s)
[1] Resizing pre_capture buffer to 1 items
[1] bind(): 
[1] Problem enabling stream server in port 8081: 
[1] Thread exiting

---

### Post by leavitodeaver on 2011-02-25
anyone? i'm kind of at a loss here, and i could really use some help...

---

### Post by Yellow Pasque on 2011-02-25
I'm not a webcam expert, but does this help?: [http://forums.quickcamteam.net/showthread.php?tid=368&pid=5075#pid5075](http://forums.quickcamteam.net/showthread.php?tid=368&pid=5075#pid5075)

---

### Post by leavitodeaver on 2011-02-25
checked your link, it sounds like they're have some sort of issue with motion not supporting V4L2, but mine actually did work for a whole minute before it started freaking out, does that track with an unsupported version?  is there a newer package for motion?

---

### Post by no2498 on 2011-02-25
you said it does/did work
have you stopped motion and try to restart it
you will need to stop it before trying any other program
like xawtv or cheese
try xawtv just to see if the cam works

---

### Post by leavitodeaver on 2011-02-26
yeah i killed and restarted it several times, and it does work in cheese straight out of the box, so it can't be a driver issue or anything.  sorry about the lag in response time, i'm fairly busy this week, i'll try to monitor this thread more often.

---

### Post by leavitodeaver on 2011-02-26
i think i might be an idiot, apparently just exiting the terminal window doesn't kill the program, you have to either restart the box or use the restart command in terminal to restart the package.  sorry if i wasted anyone's time 8(

---

### Post by no2498 on 2011-02-27
so stopping  was what you needed glad you got it fixed

---

