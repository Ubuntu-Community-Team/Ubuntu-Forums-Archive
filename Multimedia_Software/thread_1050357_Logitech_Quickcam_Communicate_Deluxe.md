---
title: "Logitech Quickcam Communicate Deluxe"
date: 2009-01-25
forum: Multimedia Software
---

### Post by ChrisC098 on 2009-01-25
I am having troubles getting my new web cam to work.

Link: [http://www.logitech.com/index.cfm/webcam_communications/webcams/devices/3057&cl=us,en](http://www.logitech.com/index.cfm/webcam_communications/webcams/devices/3057&cl=us,en)

I am running Ubuntu 8.10 and have no idea what to do or where to begin. Thank you in advance.

---

### Post by BentSlightly on 2009-01-28
Yeah the one that is supposed to work right out of the box. I am sorry but I have spent the last 10 hours trying to solve this problem, and I keep hitting a dead end. 
Ubuntu support on the matter is dreadful.

---

### Post by ChrisC098 on 2009-02-12
Has anyone figured out how to make this thing work?

---

### Post by asheq on 2009-02-12
Usually the program "Cheese" works with webcams.
Oh, and try
system > preferences > multimedia systems selector > video 

Make sure your cam is plugged in, and test it.

After that, try "Cheese".  Lets your take pictures directly from your webcam and record video(i believe)

---

### Post by ChrisC098 on 2009-03-24
Cheese didnt work and I don't have multimedia systems selector in my pulldown.

---

### Post by yahs on 2009-03-24
I have what is probably an older model Quickcam Communicate STX which works perfectly under Ubuntu 8.04.

I have Intrepid on a separate partition and the webcam doesn't work as Ubuntu 8.04 uses Video for Linux One (v4l1) while Intrepid uses v4l2.

If you open a terminal and run the command gstreamer-properties, you get the multimedia referred to in previous post. Under the video settings you should be able to select v4l1 or v4l2 and to test the webcam. In Intrepid selecting v4l1 often gives a green screen, but v4l2 gives a normal picture.
However when you try Skype its usually back to a green screen in Intrepid.

---

### Post by chilisastry on 2009-04-12
May be related, so I am adding to this thread.

I have Ubunutu 8.04 running with Logitech QuickCam Communicate STX and Skype 2.0.0.x.

a. lsusb shows the following for USB devices:

Bus 001 Device 002: ID 046d:08D7 Logitech Inc.
Bus 001 Device 001: ID 0000:0000

ie, only one USB device.

b. In Skype > Options > Video Devices, the Logitech QuickCam Communicate S (/dev/video0) is selected (correctly!).  The video test works.

c. In Skype > Options > Sound Devices, all the selections are Default device (default).  I changed the Sound In selection to USB Device 0x46d:0x8d7 (hw:0x46d0x8d7,0)

d.  In the Volume Control: Intel 82801AA-ICH (Alsa Mixer), I ensured all the devices, in particular the microphone and the Playback Master are enabled (ie, not muted).

When I make a Skype Test Call, I can hear the prompt from the lady, but it does not seem lke my voice is captured (because it is not played back).

Any special tricks to get the audio capture to work?

---

### Post by yahs on 2009-04-13
I am running Ubuntu 8.04.2 using a Logitech Quickcam STX
If you open a terminal and run the command gstreamer-properties, you get a program called multimedia systems selector which has 2 tab headings audio and video. Under the video settings you should be able to select v4l1 or v4l2 and to test the webcam. In 8.04 you need v4l1, Intrepid uses v4l2. Under audio I've got output on auto detect or I can choose my soundblaster card. For input I've got custom and the pipeline is halaudiosrc udi=/org/freedesk/Hal/devices/pci_1102_4_sound_card_0_alsa_capture_1. I have found that you need to use these settings before you start changing Skype settings
My skype settings are Sound in: USB Device 0x46d:0x8ad Sound Out: Audigy 2 (SB0240). Webcam works perfectly in skype and cheese, camorama.
However getting webcam to work in Intrepid is not easy as Skype doesn't seem to like the v4l2 driver and the video is usually just a green screen.

---

