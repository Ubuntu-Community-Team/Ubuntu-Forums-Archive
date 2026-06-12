---
title: "Ball-point Pen Spy Camera not recognized"
date: 2010-05-28
forum: Multimedia Software
---

### Post by gbrown on 2010-05-28
I recently got a [4GB USB MP9 Digital Pocket Video Recorder Ballpoint Pen w/Built-in pin-hole Camera]("http://www.yopool.com/products/4GB-USB-MP9-Digital-Pocket-Video-Recorder-Ballpoint-Pen.html") from a friend and I can't figure out how to get it working in Ubuntu 10.04.

When I plug the camera in I can access the on board memory, so right now it's basically an elaborate usb stick. Both Cheese and Skype do not recognize the camera. The camera came with a windows driver.

This is my first webcam and I don't have any experience getting multimedia devices to work with Ubuntu. 

Any help is much appreciated.

---

### Post by no2498 on 2010-05-28
you may need a driver but lets test it 

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1


hope it comes on

---

### Post by gbrown on 2010-05-28
I get the error messages: 
Video for Linux (v4l): Device "/dev/video0" does not exist.
and 
Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'.


Ubuntu seems like it just wants to use the pen-camera as a usb mass storage device instead of a webcam.

I tried another webcam a Logitech Quickcam Ultra Vision which according to the [list of webcams]("https://wiki.ubuntu.com/SkypeWebCams") that "just work" should "just work" and indeed it does (well actually there was some finagaling with the audio but nothing serious). So I have this camera now but I still would like to get this working just for the hell of it.

---

### Post by no2498 on 2010-05-29
have you tried its web site to see if they have a driver for linux/ubuntu

---

### Post by gbrown on 2010-05-29
No.
Since I got the camera from a friend I'm not sure who the manufacturer is. I can't find any identifying brands on the camera and when I googled I could only find websites trying to sell the camera but not identifying the manufacturer.

It's weird that there is no logo or anything. Check out the site I linked to in my first post, it says the camera works in linux.

---

### Post by no2498 on 2010-05-31
does it show if you do this in a terminal

lsusb

do it plugged in and unplugged

hope it shows up

---

### Post by pattigranda on 2011-06-24
@gbrown Did you try using a different USB port? sometimes I find that just switching ports causes the [pen camera]("http://www.spycameras.com/cameras,body-worn-camera,spy-pen-and-more.html") to show up on the desktop again.

---

### Post by no2498 on 2011-06-25
was just thinking you ever try the cam with out the memory in it

---

### Post by Rhubarb on 2011-06-25
I'm not sure if gbrown is listening here
As gbrown's original posts were from over a year ago.

---

### Post by gordintoronto on 2011-06-25
> **gbrown said:**
> I recently got a [4GB USB MP9 Digital Pocket Video Recorder Ballpoint Pen w/Built-in pin-hole Camera]("http://www.yopool.com/products/4GB-USB-MP9-Digital-Pocket-Video-Recorder-Ballpoint-Pen.html") from a friend and I can't figure out how to get it working in Ubuntu 10.04....

This is my first webcam and I don't have any experience getting multimedia devices to work with Ubuntu.

It's not a webcam, it's a video camera. It puts the video file in memory on the pen, then you can copy it to your computer.

---

### Post by no2498 on 2011-06-26
if you plug it in do you see it listed anyplace

---

### Post by devzero on 2011-07-05
hi,

> **gordintoronto said:**
> It's not a webcam, it's a video camera. It puts the video file in memory on the pen, then you can copy it to your computer.

I have a similar device, and that has a webcam mode.
You just need a installed driver and it needs to be on, before you plug it
in. But I think its the same sad story, as with the Huawei USB Modems, that you need to switch it to the cam mode.

Does anyone of you have such a device and got it to work?

cheers, devzero

---

### Post by davidjohnson on 2011-08-30
This is not a webcam. It is a video camera. It records videos and stores in the flash memory inside the pen. You have to install the driver in the disc and connect the pen with your computer to copy the videos to your hard disk. There are many [spy cameras]("http://www.meritline.com/spy-hidden-cameras---c-14127.aspx") like this one. They are commonly used for security surveillance, not usually as a webcam.

---

### Post by macf231 on 2011-09-06
Completely agreed with gordintoronto user id. 


Thanks

Mac
[spy camera]("http://www.dynaspy.com")

---

### Post by Kbess on 2011-10-15
Hello! I was just looking for a solution for the same problem!

My pen camera can work as a video recorder or as a webcam. There is a windows driver included in the box to that purpose.

Depending on how you connect the camera to your computer you will have two different ways Linux recognizes the device. 

In my case, when I only connect the cable with the device turned off, it is recognized as a storage device with the following lsusb results: 

Bus 005 Device 025: ID 0ad2:917a Service & Quality Technology Co., Ltd 
 
When I press the start button and  maintain it pressed while it's connected to the usb port, it's recognized like this:

Bus 005 Device 026: ID 0ad2:900a Service & Quality Technology Co., Ltd 

I think this last mode is for using the device as a webcam. I've been looking for a driver for it without success.

I hope it can help you in some way.

---

### Post by no2498 on 2011-10-16
i put this in google search
 ID 0ad2:900a Service & Quality Technology Co., Ltd

it come up with a lot of hits
kbess
install guvcview
see if it finds the cam

---

