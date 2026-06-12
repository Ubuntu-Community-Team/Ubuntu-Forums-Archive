---
title: "Skype problem with logitech quickcam express plus lubuntu 13.10"
date: 2014-03-23
forum: Multimedia Software
---

### Post by thanos122 on 2014-03-23
Hello to all I just installed _**lubuntu 13.10 32bit and Skype 4.2.0.11**_. I have a Logitech Usb Quickcam Express Plus camera (Bus 003 Device 003: ID 046d:092f Logitech, Inc. QuickCam Express Plus). 
The camera is working out of the box through Guvcview. When I open skype the camera isn't working. After searching forums e.t.c and running commands in terminal like LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype e.t.c. .......the only that worked was  
"env LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype".....the video was working but I can't configure my cameras Microphone to get worked with skype.

Also I must mention that when I run "env LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype" in terminal I am getting 
"env LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skypeGtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkRange::activate-slider' of type `gboolean' from rc file value "((GString*) 0xb82a34b0)" of type `GString'
libv4l2: error allocating conversion buffer"

So with the latest command I have video but I can't get my cameras mic work.
What should I do in order to find a permanent solution with my video and my mic.....(what should I choose for my mic in skype Microphone options I have a huge list of devices.....
I have search all wiki help Skype,Cameras Ubuntu Lubuntu......everywhere say that it works out of the box with skype(older versions) I can't find the solution with my problem.

Any help would be much much appreciated!
Thank you

---

### Post by thanos122 on 2014-03-24
Anybody.....?Someone to help me? Thank you!

---

