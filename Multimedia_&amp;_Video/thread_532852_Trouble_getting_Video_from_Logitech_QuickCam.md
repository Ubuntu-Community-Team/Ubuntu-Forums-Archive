---
title: "Trouble getting Video from Logitech QuickCam"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by evolve on 2007-08-23
I'm running Feisty and I'm having problems getting video from my new Logitech QuickCam Deluxe for Notebooks.  the device is being recognized, as lsusb gives me:

Bus 005 Device 005: ID 046d:09c1 Logitech, Inc. 

Audio is being recognized, but Ekiga and Camorama are telling me that they can't connect to the USB video device.  I have both gspca-source and spca5xx-source installed from the repositories, and I followed Randy Scarberry's procedure from [this thread]("http://ubuntuforums.org/showthread.php?t=500114") with no luck.

I've also tried installing the UVC driver from [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) using the following commands:

svn checkout [http://svn.berlios.de/svnroot/repos/linux-uvc/](http://svn.berlios.de/svnroot/repos/linux-uvc/)
cd linux-uvc/linux-uvc/trunk
make
sudo make install

My webcam is among those supported by the UVC driver, but it's still not working for me.  Does anyone know how to get this webcam working?  Thank you.

---

### Post by evolve on 2007-08-27
UPDATE:  I found from the berlios wiki that the version of Ekiga from the Ubuntu repositories (2.0.6 I think) doesn't play well with the UVC driver from berlios.

I updated Ekiga to the latest version 2.0.9 from their repositories and after some fiddling around in the preferences menu somehow stumbled into my my webcam working, but only in Ekiga.  It was pretty touchy, but opening the Picture: tab in Video Devices somehow aligned the planets properly and brought the webcam back online.

I just tried to connect to another computer, and the webcam immediately shut down and I can't bring it back up anymore.

Could someone please take the time to help walk me through some solutions to this problem so I can get my Logitech QuickCam up and running with Ekiga?

---

### Post by evolve on 2007-08-27
Also, dmesg gives me this as part of the output:

[   19.848000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09c1)
[   19.864000] usbcore: registered new interface driver uvcvideo
[   19.864000] USB Video Class driver (v0.1.0)
[   19.888000] usbcore: registered new interface driver snd-usb-audio

Ekiga is giving me an error message that "Your driver doesn't seem to support any of the color formats supported by Ekiga.  Please check your kernel driver documentation in order to determine which Palette is supported."

How do I do this, and how would I align the two formats to get the webcam and Feisty/Ekiga to work together?

---

### Post by evolve on 2007-08-27
Am I not asking this in the right forum?  Or is this problem too weird to tackle?

If someone could please lend some time to help me, I desperately need to get this webcam working.

Should I just uninstall the drivers and start from scratch?  How would I even go about doing this?  I don't even know if the steps I've taken to install these drivers (listed above) are correct.  If they're not, could someone walk me through installing them?  Thank you.

---

### Post by SamMessing on 2008-01-27
I am having the same problem. I haven't tried Ekiga, but also using a Logtiech quickcam deluxe for notebooks I get no video. Skype "sees" the camera, as UVC Camera (046d:09c1), (/dev/video0), which matches the lsusb output, but I don't see anything besides a blank screen.

Trying to start camorama just gives me the error message "Could not connect to video device (/dev/video0), try checking connection)."

I'm going to also look around, and see if I can figure something out. I'll let you know if I discover anything. Please do the same!

---

### Post by m9dhatter on 2008-02-11
well, i just want to say that i have the same problem and bought the same webcam.will be looking into this myself and i'll post updates if i manage to figure it out.

---

### Post by m9dhatter on 2008-02-13
> **m9dhatter said:**
> well, i just want to say that i have the same problem and bought the same webcam.will be looking into this myself and i'll post updates if i manage to figure it out.

seems like ekiga works out of the box. just select V4L2.

---

### Post by lbharti on 2008-02-22
Yes, Ekiga works with V4L2, but how do I make it work with applications like VLC Player?

---

### Post by Jcink on 2008-05-07
Exact same problems you guys are all having. I'm just about ready to give up on this cam ( 046d:09c1  ).

It works just fine in Ekiga but not anywhere else, no matter what I do. I have a really old logitech quickcam that works. It feeds to /dev/video0. This one I can't even cat /dev/video0,1,2,3 - it sees absolutely _nothing_ even with Ekiga open.

It definitely needs V4L2, but I still can not figure out how to make that work with VLC, and it also screws flash over completely since I read V4L2 isn't supported by flash.

[http://www.swift-tools.net/Flashcam/](http://www.swift-tools.net/Flashcam/) does not work for me either for flash.

Any suggestions?

---

