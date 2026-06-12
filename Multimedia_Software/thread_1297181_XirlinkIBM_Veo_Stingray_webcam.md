---
title: "Xirlink/IBM Veo Stingray webcam"
date: 2009-10-21
forum: Multimedia Software
---

### Post by Mark_in_Hollywood on 2009-10-21
I've been playing with this for two days and am beyond my ability to know what to do next.

This is Jaunty. The webcam is a Veo Stingray (made by Xirlink)

mark@Lexington-19:~$ lsusb | grep Xirlink
Bus 003 Device 002: ID 0545:808b Xirlink, Inc. Veo PC Camera

I have read the following posts about this webcam:

[http://www.linux-usb.org/ibmcam/#VeoStingray_Note](http://www.linux-usb.org/ibmcam/#VeoStingray_Note)

[http://ubuntuforums.org/showthread.php?t=1213111&highlight=veo+webcam](http://ubuntuforums.org/showthread.php?t=1213111&highlight=veo+webcam)

[http://ubuntuforums.org/showthread.php?t=725179](http://ubuntuforums.org/showthread.php?t=725179)

[http://www.linux-usb.org/ibmcam/](http://www.linux-usb.org/ibmcam/)

and lastly:

[http://www.linux-usb.org/ibmcam/ibmcamFAQ.html](http://www.linux-usb.org/ibmcam/ibmcamFAQ.html)

Most of the above seems out-of-date. Because I also found:

From:

[http://tldp.org/HOWTO/html_single/Webcam-HOWTO/#MODELS](http://tldp.org/HOWTO/html_single/Webcam-HOWTO/#MODELS)

2.3.12. Xirlink C-it&#8482; HDCS-1000 based Webcams

This driver is for the USB webcams manufactured by Xirlink, IBM (PC Camera) and Veo Stingray model webcams. Support has been in the Linux kernel USB section since 2.2.12. The homepage is at [http://www.linux-usb.org/ibmcam](http://www.linux-usb.org/ibmcam).

and I'm:

mark@Lexington-19:/$ uname -r
2.6.28-15-generic

So I believe the driver is in-built? Am I understanding this?

I've installed and tried to find the camera with:

Camorama, Camstream, Cheese Photo Booth, gqcam, and effectv.

Camorama loads but the application is nothing more than a grey box with a white rectangle (blank) where the video image should be. It must be forcibly closed.

Camstream opened a window, which had a fabric like grey texture, but not picture. The terminal output:

mark@Lexington-19:/$ camstream
W: CamStream version 0.27 starting.
>> void CCamStreamApp::ReadConfigFile()
  W: Failed to open configuration file '/home/mark/.camstream/config.xml' for reading.
  D: creating <defaults> node
  D: creating <videodevices> node
  D: creating <audiodevices> node
<< void CCamStreamApp::ReadConfigFile()

and more errors omitted, available if you want to read them. 

Following one of the above posts, I tried: Cheese Photo Booth. It loads, the "loading" rosette spins, and nothing ever happens beyond that.

Next:
mark@Lexington-19:/$ gqcam

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
/dev/video: No such file or directory

Synaptic shows that all relevant libcanberra-gtk modules are loaded. How can I know if they are linked? Hardlinked?

and lastly, effectv runs, the terminal returns:

mark@Lexington-19:~$ effectv
video_init: Can't find a supported pixel format.
Video initialization failed.

I have downloaded:

gspcav1-20071224.tar.gz

from:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

that site says the Veo Stingray is working. The details:

Veo Stingray	124	0x0545	0x8333	Stingray webcam	lv532Av	tv_8532	 	Test	gbrg	spca5xx	*

So, the driver from this guy need to be installed, but he give no instructions. Please help me know what to do next. It's not in GDebi format, so what is the next step? Where do I put this compressed folder so it will uncompress into the correct directory or sub-directory?

Lastly, the device I have, ID 0545:808b Xirlink, Inc. Veo PC Camera doesn't seem to be mentioned specifically as to a driver. But it isn't specifically omitted, either.

---

### Post by Mark_in_Hollywood on 2009-10-24
I'm marking this as SOLVED. This is inaccurate. I believe there is **no driver** for this model of Veo Stingray webcam. Never the less, 33 people have spent time here.

Thank you, community.

---

