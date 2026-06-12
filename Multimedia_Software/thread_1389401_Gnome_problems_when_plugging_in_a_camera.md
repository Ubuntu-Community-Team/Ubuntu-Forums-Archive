---
title: "Gnome problems when plugging in a camera"
date: 2010-01-24
forum: Multimedia Software
---

### Post by honestguvnor on 2010-01-24
When I plug in my digital camera to the USB port I see:

(1) A small popup window stating:
      Unable to mount KODAK EasyShare P880 Zoom Digital Camera
      Error initializing camera: -60: Could not lock the device

(2) 2 popups asking me what I want to do with the default of opening F-Spot

(3) 2 background icons which when clicked show the locations:
      gphoto2://[usb:002,008]/store_00020001
      gphoto2://[usb:002,008]/store_00010001
      The first contains a couple of files which do not seem to mean much and the second a directory containing my photos which can be viewed and copied without problem.

Unfortunately, when I try to run f-spot, gthumb, digikam and the like they freeze when trying to import and have to be force quit. Unmounting the files first makes no difference.

However, if I "killall gvfs-gphoto2-volume-monitor" and then plug in the camera f-spot, digikam, gthumb, and the like can successfully view and import the files in the camera.

Conclusion: the environment seems to be broken rather than the user level programs. Any suggestion on how to fix the behaviour of gnome (if the problem lies here)?

(I have read various previous postings on the topic which is where I found the killall suggestion but did not find a fix.)

---

