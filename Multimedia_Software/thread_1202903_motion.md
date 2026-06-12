---
title: "motion"
date: 2009-07-02
forum: Multimedia Software
---

### Post by mbzn on 2009-07-02
Hi, to anyone that knows this app, Please Help.

I installed motion and had i workin previously for a while. now i get

<CODE>
me@x:~/motion$ motion
[0] could not open configfile /etc/motion/motion.conf: Permission denied
[0] Not config file to process using default values
[0] Motion 3.2.11 Started
[0] ffmpeg LIBAVCODEC_BUILD 3410688 LIBAVFORMAT_BUILD 3414017
[1] Thread 1 started
[1] cap.driver: "uvcvideo"
[1] cap.card: "VF0410 Live! Cam Video IM Pro"
[1] cap.bus_info: "0000:00:1d.7"
[1] cap.capabilities=0x04000001
[1] - VIDEO_CAPTURE
[1] - STREAMING
[1] Supported palettes:
[1] 0: YUYV (YUV 4:2:2 (YUYV))
[1] 1: MJPG (MJPEG)
[1] index_format 2 Test palette MJPG (352x288)
[1] Using palette MJPG (352x288) bytesperlines 0 sizeimage 203341 colorspace 00000008
[1] VIDIOC_G_JPEGCOMP not supported but it should be (does your webcam driver support this ioctl?)
[1] found control 0x00980900, "Brightness", range -64,64 
[1] 	"Brightness", default 0, current 0
[1] found control 0x00980901, "Contrast", range 0,64 
[1] 	"Contrast", default 32, current 32
[1] found control 0x00980902, "Saturation", range 0,128 
[1] 	"Saturation", default 64, current 64
[1] found control 0x00980903, "Hue", range -40,40 
[1] 	"Hue", default 0, current 0
[1] found control 0x00980910, "Gamma", range 72,500 
[1] 	"Gamma", default 100, current 100
[1] found control 0x00980913, "Gain", range 0,100 
[1] 	"Gain", default 0, current 0
[1] mmap information:
[1] frames=4
[1] 0 length=203341
[1] 1 length=203341
[1] 2 length=203341
[1] 3 length=203341
[1] Using V4L2
[1] Resizing pre_capture buffer to 1 items
Not a JPEG file: starts with 0x03 0x11
Invalid component ID 255 in SOS
^C[1] Thread exiting
[1] Calling vid_close() from motion_cleanup
[1] Closing video device /dev/video0
[0] Motion terminating
me@x:~/motion$ sudo motion
[sudo] password for martin: 
[0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Motion 3.2.11 Started
[0] ffmpeg LIBAVCODEC_BUILD 3410688 LIBAVFORMAT_BUILD 3414017
[0] Thread 1 is from /etc/motion/motion.conf
[1] Thread 1 started
[1] cap.driver: "uvcvideo"
[1] cap.card: "VF0410 Live! Cam Video IM Pro"
[1] cap.bus_info: "0000:00:1d.7"
[1] cap.capabilities=0x04000001
[1] - VIDEO_CAPTURE
[1] - STREAMING
[1] Supported palettes:
[1] 0: YUYV (YUV 4:2:2 (YUYV))
[1] 1: MJPG (MJPEG)
[1] index_format 2 Test palette MJPG (320x240)
[0] motion-httpd/3.2.11 running, accepting connections
[0] motion-httpd: waiting for data on port TCP 8080
[1] Using palette MJPG (320x240) bytesperlines 0 sizeimage 154189 colorspace 00000008
[1] VIDIOC_G_JPEGCOMP not supported but it should be (does your webcam driver support this ioctl?)
[1] found control 0x00980900, "Brightness", range -64,64 
[1] 	"Brightness", default 0, current 0
[1] found control 0x00980901, "Contrast", range 0,64 
[1] 	"Contrast", default 32, current 32
[1] found control 0x00980902, "Saturation", range 0,128 
[1] 	"Saturation", default 64, current 64
[1] found control 0x00980903, "Hue", range -40,40 
[1] 	"Hue", default 0, current 0
[1] found control 0x00980910, "Gamma", range 72,500 
[1] 	"Gamma", default 100, current 100
[1] found control 0x00980913, "Gain", range 0,100 
[1] 	"Gain", default 0, current 0
[1] mmap information:
[1] frames=4
[1] 0 length=154189
[1] 1 length=154189
[1] 2 length=154189
[1] 3 length=154189
[1] Using V4L2
[1] Resizing pre_capture buffer to 1 items
Not a JPEG file: starts with 0x03 0x11
Invalid component ID 255 in SOS
[1] Started stream webcam server in port 8081
^C[1] Thread exiting
[1] Calling vid_close() from motion_cleanup
[1] Closing video device /dev/video0
[0] httpd - Finishing
[0] httpd Closing
[0] httpd thread exit
[0] Motion terminating
</CODE>

I need it to save 1 image per second when it detects motion, and cant find the problem in the config file. can someone please show me what the config file should look like as the original file does not save images.

I wil post my config if needed.

Thanx for any help

P.S. how do i do the code box right..

---

### Post by Boondoklife on 2009-07-02
I would first try backing out the config file and then completely reinstalling the app and try it with the default config.

---

### Post by Hernâni on 2010-09-16
Hi!

 I had exactly the same problem and I solved the problem this way:
 *Go to: aplications &#8211; accessories &#8211; terminal * 
 Here, in the terminal, you rite: *sudo gedit /etc/motion/motion.conf*
 
This will open the window of ***gedit. ***Now, click in "*File"* *. *In the menu that apears choose *&#8220;save as&#8221;. *This will open another window for you to choose where to save the file. Then choose the folder &#8220;home&#8221; (or personal folder) and save there this file. The new location of the motion .conf will be something like this: */home/the name that you gave to your computer/motion.conf * 
 
May be in your case it can be only: */home/motion.conf. *In my case the result was as fallows:
prof@prof:~$ sudo motion
  [sudo] password for prof:  
  [0] Processing thread 0 - config file **/home/prof/motion.conf**
 [0] Motion 3.2.11 Started
  [0] ffmpeg LIBAVCODEC_BUILD 3412993 LIBAVFORMAT_BUILD 3415808
  [0] Thread 1 is from /home/prof/motion.conf
  [1] Thread 1 started
  [0] motion-httpd/3.2.11 running, accepting connections
  [0] motion-httpd: waiting for data on port TCP 8080
  [1] cap.driver: "uvcvideo"
  [1] cap.card: "CNF7051"
  [1] cap.bus_info: "usb-0000:00:1a.7-2"
  [1] cap.capabilities=0x04000001
  [1] - VIDEO_CAPTURE
  [1] - STREAMING
  [1] Supported palettes:
  [1] 0: YUYV (YUV 4:2:2 (YUYV))
  [1] index_format 6 Test palette YUYV (320x240)
  [1] Using palette YUYV (320x240) bytesperlines 640 sizeimage 153600 colorspace 00000008
  [1] found control 0x00980900, "Brightness", range -64,64  
  [1]     "Brightness", default 0, current 0
  [1] found control 0x00980901, "Contrast", range 0,95  
  [1]     "Contrast", default 25, current 25
  [1] found control 0x00980902, "Saturation", range 0,128  
  [1]     "Saturation", default 64, current 64
  [1] found control 0x00980903, "Hue", range -40,40
[1]     "Hue", default 0, current 0
  [1] found control 0x00980910, "Gamma", range 72,500  
  [1]     "Gamma", default 100, current 100
  [1] mmap information:
  [1] frames=4
  [1] 0 length=153600
  [1] 1 length=153600
  [1] 2 length=153600
  [1] 3 length=153600
  [1] Using V4L2
  [1] Resizing pre_capture buffer to 1 items
  [1] Started stream webcam server in port 8081
  
Now my Motion works perfectly. I'm very happy with it.
 I hope I helped you.
 Regards
 Hernâni

---

### Post by maximumNoob on 2011-02-01
I got the same error message, and applied the same recommended solution (moving the config file to /home/user directory.  However, I am getting the following error message:

[1] Started stream webcam server in port 8081
[1] Problem creating directory /userAccount: 
[1] ffopen_open error creating (new) file [/userAccount/Videos/Webcam//01-20110201162025.swf]: 
[1] Problem creating directory userAccount: 
[1] Can't write picture to file /userAccount/Videos/Webcam//01-20110201162025-01.jpg - check access rights to target directory: 
[1] Thread is going to finish due to this fatal error: 
[0] httpd - Finishing
[0] httpd Closing
[0] httpd thread exit
[1] Thread exiting
[1] Calling vid_close() from motion_cleanup
[1] Closing video device /dev/video0
[0] Motion terminating

Also, I still get the following error message during startup of motion:

[1] VIDIOC_G_JPEGCOMP not supported but it should be (does your webcam driver support this ioctl?)


Not sure what's going on here; please help!

---

### Post by jgrevich on 2012-09-27
> **maximumNoob said:**
> I got the same error message, and applied the same recommended solution (moving the config file to /home/user directory.  However, I am getting the following error message:

[1] Started stream webcam server in port 8081
[1] Problem creating directory /userAccount: 
[1] ffopen_open error creating (new) file [/userAccount/Videos/Webcam//01-20110201162025.swf]: 
[1] Problem creating directory userAccount: 
[1] Can't write picture to file /userAccount/Videos/Webcam//01-20110201162025-01.jpg - check access rights to target directory: 
[1] Thread is going to finish due to this fatal error: 
[0] httpd - Finishing
[0] httpd Closing
[0] httpd thread exit
[1] Thread exiting
[1] Calling vid_close() from motion_cleanup
[1] Closing video device /dev/video0
[0] Motion terminating

Also, I still get the following error message during startup of motion:

[1] VIDIOC_G_JPEGCOMP not supported but it should be (does your webcam driver support this ioctl?)


Not sure what's going on here; please help!

According to your post motion is trying to write to /userAccount/Videos/Webcam.  I have a feeling your User Account is not named, "userAccount".  Open a new terminal and type pwd, that will give you location of your home dir.  You want to change it to something like /home/YourUserName/Videos/WebCam (you also have two /'s).


justin

---

