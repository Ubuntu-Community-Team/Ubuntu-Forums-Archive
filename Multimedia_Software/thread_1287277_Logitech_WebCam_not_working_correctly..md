---
title: "Logitech WebCam not working correctly."
date: 2009-10-09
forum: Multimedia Software
---

### Post by oldsoundguy on 2009-10-09
Running 8.4 LTS with gangs of memory and storage and a hyperthreaded .. no issues otherwise.

Logitech QuickCam Pro 5000 plugged into the USB

run luvcview from terminal and the cam is there .. but it won't let me make any adjustments!

run cheese .. NOTHING (camera light comes on then goes off)

try to use on FaceBook and it's there, but NO CONTROLS so the image is on extreme zoom and totally useless. (it uses Flash, I think.) (have the latest on the latest Fire Fox.)

Ekiga: the audio works (poorly with no volume control) but NO video.

EasyCam2 does not work at all (installed it twice).

Go easy guys .. know I have upscrewed something here, but at a loss.  Still want to get Skype up and talking, but until I gain control of the stinkin' camera, not!!

---

### Post by oldsoundguy on 2009-10-10
still have NOT got this to work correctly so 

BUMP

---

### Post by oldsoundguy on 2009-10-12
bump one mo tahm!

---

### Post by rb0171610 on 2009-10-12
> **oldsoundguy said:**
> Running 8.4 LTS with gangs of memory and storage and a hyperthreaded .. no issues otherwise.

Logitech QuickCam Pro 5000 plugged into the USB

run luvcview from terminal and the cam is there .. but it won't let me make any adjustments!

run cheese .. NOTHING (camera light comes on then goes off)

try to use on FaceBook and it's there, but NO CONTROLS so the image is on extreme zoom and totally useless. (it uses Flash, I think.) (have the latest on the latest Fire Fox.)

Ekiga: the audio works (poorly with no volume control) but NO video.

EasyCam2 does not work at all (installed it twice).

Go easy guys .. know I have upscrewed something here, but at a loss.  Still want to get Skype up and talking, but until I gain control of the stinkin' camera, not!!
which video driver does this cam use? Do you know?
I use the Logitech quickcam pro 9000.  Mine uses the uvcvideo driver.
I would suggest running *lsmod | grep video* to see what drivers are loaded.

If it is not loaded you will see output similar to this:

$lsmod | grep video
video                  25872  0
output                 11008  1 video
videodev               41600  0
v4l1_compat            21764  1 videodev

If it is loaded you should see output similar to this:

$ lsmod | grep video
uvcvideo               63368  0
video                  25872  0
output                 11008  1 video
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev

If it uses this same driver, you could try to reload the module.

[I]sudo rmmod -f uvcvideo && sudo modprobe uvcvideo
[/I]
and try again.
Also, camorama works similar to cheese. You can install this and see if it helps.

---

### Post by oldsoundguy on 2009-10-13
got this:
video                  19856  0 
output                  4736  1 video
uvcvideo               58244  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
usbcore               146412  6 uvcvideo,snd_usb_audio,snd_usb_lib,ehci_hcd,u

Not quite sure what is what .. not really used to delving deeply into the system.  Know how, just not done it much.

---

### Post by rb0171610 on 2009-10-13
> **rb0171610 said:**
> which video driver does this cam use? Do you know?
I use the Logitech quickcam pro 9000.  Mine uses the uvcvideo driver.
I would suggest running *lsmod | grep video* to see what drivers are loaded.

If it is not loaded you will see output similar to this:

$lsmod | grep video
video                  25872  0
output                 11008  1 video
videodev               41600  0
v4l1_compat            21764  1 videodev

If it is loaded you should see output similar to this:

$ lsmod | grep video
uvcvideo               63368  0
video                  25872  0
output                 11008  1 video
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev

If it uses this same driver, you could try to reload the module.

[I]sudo rmmod -f uvcvideo && sudo modprobe uvcvideo
[/I]
and try again.
Also, camorama works similar to cheese. You can install this and see if it helps.
When you run the lsmod command, you are basically just **l**i**s**ting the **mod**ules (kernel drivers) that are loaded on your system and the | grep portion says to just return the  lines containing the word video.  
So, as you can see, your output is similar to mine.  The first thing you should notice is that the uvcvideo driver is loaded.  You will notice it several times in your output.  If  you are having a problem with the webcam not starting or showing black output, it sometimes helps to remove and then reinstall the driver from the kernel.  This works similar to rebooting in Windows.  The cool thing about Linux is that you do not have to reboot to restart your system drivers.  You can use  sudo and the rmmod followed by the moprobe commands to reload the webcam driver. In this case:

*sudo rmmod -f uvcvideo && sudo modprobe uvcvideo*


Did you follow this advice from my previous post?

Also, if I recall correctly from your original post, you were trying to use your webcam with Skype?  If that is correct, you will need to open Skype, click on the Skype symbol on the bottom left, and select Options as shown in the first picture I have attached below.
Once the Options window has opened, click on Video devices on the left, as pictured in the second picture I have attached.  In the middle on the right you will see a drop down box titled "Select Webcam".  Make sure that your video device is selected.  In my case, I have two.  I have an integrated webcam, and a USB Logitech Webcam.  If I want to select my USB webcam, I select UVC camera /dev/video1.  If your webcam is the only one you have installed, it will probably be the listed as /dev/video0.  In Linux, device enumeration starts with 0, so the first device attached to the system will be 0, the second 1, and so on.  
After you make sure your webcam is selected in the drop down box, hit apply at the bottom.  Now, on the black box just to the right of the drop down box, hit the button that says test. Give your camera just a moment to start.  If all is working you should see your image in the box, as pictured in the third picture attached below.  Hit ok and you should be good to go as far as video. If your webcam has a built-in microphone, you will need to go to sound devices and make sure your webcam is selected in the drop down box that says "Sound In".  Hit  Appy if necessary, and then Close.  You should now be able to use your webcam and built-in microphone with Skype correctly.  

If you have more questions or this does not fix your problem, please leave another post. I will be happy to try and help you.

Good Luck.

---

### Post by oldsoundguy on 2009-10-13
TANKS!! A BUNCH .. will give that a shot WHEN I get some time.  Really appreciate the response. IF this solves the issue, will mark the thread solved. (may be a day or so, though!)

---

