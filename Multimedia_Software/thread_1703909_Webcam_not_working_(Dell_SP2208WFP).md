---
title: "Webcam not working (Dell SP2208WFP)"
date: 2011-03-09
forum: Multimedia Software
---

### Post by LMendy on 2011-03-09
I just installed Ubuntu on a partition on my Dell Studio desktop and my webcam is not working. My monitor model is SP2208WFP (webcam is built into monitor). 

The lsusb command gives:
Bus 001 Device 004: ID 05a9:2643 OmniVision Technologies, Inc. Monitor Webcam

My syslog has these error messages:
Mar  9 20:37:28 lee-Studio-540 kernel: [    6.537426] uvcvideo: Found UVC 1.00 device Monitor Webcam (SP2208WFP) (05a9:2643)
Mar  9 20:37:28 lee-Studio-540 kernel: [    6.537782] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
Mar  9 20:37:28 lee-Studio-540 kernel: [    6.538039] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
Mar  9 20:37:28 lee-Studio-540 kernel: [    6.538070] uvcvideo: Failed to initialize the device (-5).

I have found some old threads about re-building and installing uvcvideo, but I'm not sure how to go about this (I think some of the information out there is outdated). Any help would be appreciated, as I am a complete newbie! Thanks!!

---

### Post by no2498 on 2011-03-10
try this program xawtv
it loads a cam grabber
look in your package manager for it and install it
try the cam in it first

---

### Post by LMendy on 2011-03-10
Great! This fixed the issue. Thanks for the help! :)

---

### Post by Angelbrand on 2011-03-16
hey i had same issue with my laptop cam but when i installed that program it wont open.. i click on it to open and nothing happens

---

### Post by no2498 on 2011-03-16
open a terminal type webcam click enter
sudo apt-get install cheese click enter
try your cam in cheese
full name cheese webcam booth
look in sound and video for it

---

### Post by LMendy on 2011-04-09
It looks like the fix above was only a temporary fix. I have both XawTV installed and Cheese Webcam Booth. For a while, my webcam was working. Now it does not. When I try to open XawTV, nothing happens. When I open Cheese Webcam Booth, it says "No Device Found".

The following appears in my message system log:

Apr  9 21:31:10 lee-Studio-540 kernel: [    9.596320] Linux video capture interface: v2.00
Apr  9 21:31:10 lee-Studio-540 kernel: [    9.604129] uvcvideo: Found UVC 1.00 device Monitor Webcam (SP2208WFP) (05a9:2643)
Apr  9 21:31:10 lee-Studio-540 kernel: [    9.604443] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
Apr  9 21:31:10 lee-Studio-540 kernel: [    9.604914] usbcore: registered new interface driver uvcvideo
Apr  9 21:31:10 lee-Studio-540 kernel: [    9.604916] USB Video Class driver (v0.1.0)

---

### Post by no2498 on 2011-04-10
open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find the cam

---

### Post by LMendy on 2011-04-10
Just tried this - :

When I select v4l and click test, I get an error message: "Video for Linux (v4l): Device "/dev/video0" does not exist."

When I select v4l2 and click test, I get an error message: "Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'."

Any ideas for a next step?

Thanks for your help!

---

### Post by no2498 on 2011-04-11
open a terminal type dmesg click enter

after its done type lsusb click enter

this should show the number and name of the cam

and did you set the plugin to auto find the cam

---

### Post by LMendy on 2011-04-14
I tried dmesg and found this:

[    9.524656] uvcvideo: Found UVC 1.00 device Monitor Webcam (SP2208WFP) (05a9:2643)
[    9.524722] usbcore: registered new interface driver hiddev
[    9.533858] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[    9.534010] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[    9.534066] uvcvideo: Failed to initialize the device (-5).
[    9.534140] usbcore: registered new interface driver uvcvideo
[    9.534142] USB Video Class driver (v0.1.0)

lsusb gave me this:

Bus 001 Device 005: ID 05a9:2643 OmniVision Technologies, Inc. Monitor Webcam


When I use the gstreamer-properties command and click the video tab, I have the following settings:
Default Output: plugin = Autodetect
Default Input: plugin = Video for Linux (v4l)

The only other choices for the Default Input plugin are: Test Input, Video for Linux 2 (v4l2), and custom.

So far I'm still out of luck

---

### Post by no2498 on 2011-04-14
try the v4l2 plugin and test it

---

### Post by LMendy on 2011-04-14
When I select v4l2 and click test, the following error message appears:

Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'.

This appears in the terminal:

gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src2:
system error: No such file or directory]

---

### Post by no2498 on 2011-04-15
this program aways find my cams wxcam

you can get it in a deb file
i had to try a few to get 1 that would load
on 1 computer i have 1.0.5
on the second 1 i have 1.0.6
both have 10.04 on them

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

or you can try guvcview

both of them should be in your package manager

---

### Post by BicyclerBoy on 2011-04-15
Try from terminal
[I][I]rmmod uvcvideo
modprobe uvcvideo
dmseg

Repeat these (<5) until the camera initialises okay..

You could try this ppa to update some v4l components..

[https://launchpad.net/~libv4l/+archive/ppa?field.series_filter=maverick](https://launchpad.net/~libv4l/+archive/ppa?field.series_filter=maverick)
[/I][/I]

---

### Post by LMendy on 2011-04-15
[COLOR=Black]Thanks BicyclerBoy for your help, this fixed it![/COLOR] :guitar:
[]("http://ubuntuforums.org/member.php?u=816321")

---

### Post by BicyclerBoy on 2011-04-15
Remember this is just a band-aid ..

The real fix will have to be in v4l dvb code..

---

### Post by no2498 on 2011-04-16
BicyclerBoy

how did you find this out

Repeat these (<5) until the camera initialises okay..

---

### Post by BicyclerBoy on 2011-04-16
[SIZE=2]Just searching on the USB id & then searching v4l or uvc forums
[/SIZE][B][SIZE=2]Linux-uvc-devel  forum had some clues..
[/SIZE][/B]

---

### Post by no2498 on 2011-04-16
BicyclerBoy
am  glad you have my back
 lyle  stooped helping
ive been on my own
after they put the drivers in the kernel

---

