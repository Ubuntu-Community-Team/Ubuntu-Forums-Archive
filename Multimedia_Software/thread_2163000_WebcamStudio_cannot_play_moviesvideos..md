---
title: "WebcamStudio cannot play movies/videos."
date: 2013-07-16
forum: Multimedia Software
---

### Post by ResurrectedJesus on 2013-07-16
I installed the latest WebcamStudio version but it was giving me some  error, "No Output", so I installed Webcam Studio 0.57 which there, it  works. 


It cannot play movies, it doesn't show anything. just blank. 

Same source/root/Downloads/francisco.avi 
filesrc location="/root/Downloads/francisco.avi" ! decodebin   name=decode  ! ffmpegcolorspace qos=true  ! videorate !  video/x-raw-yuv,framerate=24/1 ! videoscale !  video/x-raw-yuv,width=320,height=240 ! alpha ! ffmpegcolorspace !  video/x-raw-rgb,bpp=32,depth=24, red_mask=65280, green_mask=16711680,  blue_mask=-16777216 ! ffmpegcolorspace name=tosink qos=true  decode. !  queue ! volume name=volume volume=0.1 ! audioconvert ! autoaudiosink  
Movie Error:  BaseSrc: [filesrc1],3, Resource not found. 
Movie Error:  BaseSrc: [filesrc1],3, Resource not found. 
Starting pos: 0 






It doesn't show anything, and installing the latest WebcamStudio version doesn't solve this problem either.  


How can I display .avi, .mp4, or .flv movies/videos on WebcamStudio?

---

### Post by QIII on 2013-07-16
This is a duplicate of [http://ubuntuforums.org/showthread.php?t=2162999](http://ubuntuforums.org/showthread.php?t=2162999)

Please do not start identical threads in separate areas of the Forum.  If you wish to have a thread moved, please use the "Report Post" button and ask the Staff to move the thread.

---

