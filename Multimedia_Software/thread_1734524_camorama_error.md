---
title: "camorama error"
date: 2011-04-20
forum: Multimedia Software
---

### Post by livelong on 2011-04-20
camorama application giving error "could not connect to video device (dev/video0) check connections" 
any suggestions to solve ........I am using Ubuntu 10.1 and intel webcam CS110. Also the webcam is not working on facebook/meebo live chat applications.

---

### Post by no2498 on 2011-04-20
open a terminal type dmesg click enter

after it stops type lsusb click enter

this should list a number and name of the cam

now in a terminal type sudo apt-get install cheese click enter
it ask for your pass word you do not see any thing as you type click enter

try the cam in cheese first
is comes up in sound and video as cheese webcam booth

after you get the cam working in cheese 
all the rest is at the adobe site in the settings manager
you need to go to the sites you use then go to adobe and allow and rember for the sites you use

---

### Post by livelong on 2011-04-21
Thanks for the Help.
I have done the steps and installed Cheese, but cheese is showing blank screen. have checked the prefrences. webcam is shown in the device box but still there is no video. still looking for help......

---

### Post by no2498 on 2011-04-21
open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find the cam

i hope the cam come on in gstreamer-properties 

try cheese 

if still blank in cheese click edit preference  try some settings

---

### Post by livelong on 2011-05-03
Have done as instructions. but the cam worked when I changed the USB slot. Anyway cam is working now but the picture quality is too bad. Its like I am using black and white cam. I have tried Gstreamer-properties but every setting I apply, the result is same. Does anyone have suggestions to solve this color problem.

---

### Post by no2498 on 2011-05-03
install v4l2ucp
it comes up/in system/preferences
as video4linux control panel
you can set things in it has a preview window
i do think all other cam programs  must be off to get it to work

---

