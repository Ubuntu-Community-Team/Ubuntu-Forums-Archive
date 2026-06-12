---
title: "trying to install video camera"
date: 2016-05-17
forum: Multimedia Software
---

### Post by jgw on 2016-05-17
I am trying to setup a new external camera.  My machine sees it but there is no video.  I am currently trying to run gvcuviewer.  It sees the camera but the screen is black.  I have also run:
 lsmod | grep uvcvideo
uvcvideo                      81073  1 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_core           59104  1 uvcvideo
videodev                     153793  4 uvcvideo,v4l2_common,videobuf2_core
media                          21903  2 uvcvideo,videodev

lsusb gives me:         Bus 002 Device 005: ID eb1a:2890 eMPIA Technology, Inc. 
guvcviewer tells me: UVC Camera (eb1a:2890)

I am plugging a composite video wire into a video capture device that is supposed to not need a specific driver.  I suspect the problem is in the video0 file.  This file is currently in my home directory in .config  When I read the file says its for /dev/video0   So my thought was to copy that file to /dev  It would not allow that and told me video0 was not a regular file.  Then, given that the video0, in /dev, has zero bytes I thought to edit the file and insert the contents of video0, in my home directory, to /dev but, yet again it was not a regular file.  I don't even know if this is my problem but, if it is, then there is a problem.

I should also add that I have split the composite video wire.  I connected one directly to my monitor/tv and the other to the computer I am dealing with.  I have a picture on the direct connection to the monitor.  

Thank you..............

---

### Post by goofprog on 2016-05-19
If your computer sees it maybe try **cheese** just to see if there is something else not working.  There was also a set up to get **VLC** to record with it too.  I would not edit *video0 *that is just a device in **/dev.  **I do not believe editing it will get what you want.

---

### Post by jgw on 2016-05-19
thanks for the reply.  

I think I know what is going on but I have to do more testing to make sure.  The first thing is that there is an abundance of choices to make and the default camera is wrong (was yuyv)   is wrong.  Its going to take me some time to figure this one out.  I have now tried 2 other cameras and find that they all have different defaults.  This is waay more complicated that I had first thought.  

there are some files referenced, such as /dev/video0, /dev/video1, /dev/video2, etc (they appear and go away depending on what cameras are attached).  these are not real files, I have no idea what they are but there are REAL files, with the same name, under .config/guvcview in the home directory - these too appear when something new is attached but remain even after camera is unattached.  These files are real and hold real information.  I am going to spend some time figuring this one out as it would seem to be yet another magical ubuntu thing.

---

### Post by coldraven on 2016-05-20
If you just see black try running guvcview,  disable any "Autolevel" and adjust the brightness.

---

### Post by jgw on 2016-05-21
Thanks for the reply.

I couldn't find any references to autolevel in guvcview (the only auto was auto white - which didn't change anything one way or another).  I overcame the black screen by choosing rgb3.  The frame rate seems to be a moving target, depending on the camera being used. guvcview has it set at 1/1 and my actual rate seems to go from 1 tro 20, depending on the camera being used.  I have yet to figure out howto control the output size of the video but I suspect I will figure that out eventually.  My mail problem, now, is to get some hardware so I can go from female bnc to male/female rca (where is there a radio shack when needed?)  Anyway, I will get that on Monday and then I can continue my testing.

---

### Post by jgw on 2016-05-27
I have been spending a lot of time trying to figure this all out.  I suspect that nobody has actually been able to make any usb video capture devices work.  I have read any number of posts about this and, as far as I can tell, nobody really has made it work.  Those who say they have tell what they did but, when I do the same thing, nothing.  I now have two of these and have been trying to make them work to no avail.  lsusb gives me:
Bus 001 Device 004: ID 1c88:0007 Somagic, Inc. SMI Grabber (EasyCAP DC60+ clone) (no firmware) [SMI-2021CBE]
Bus 001 Device 003: ID eb1a:2890 eMPIA Technology, Inc.  (this one, bought on ebay for not much, said it would work with linux)

I have absolutely no problem with usb cameras which mine is not.  
If I could mark this thread, and one other "waste of time" I would be delighted to do so.  I can't mark them 'solved' as neither are and both just natter on about failure, hence, "waste of time"

---

