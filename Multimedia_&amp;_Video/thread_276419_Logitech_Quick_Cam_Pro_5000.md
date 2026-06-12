---
title: "Logitech Quick Cam Pro 5000"
date: 2006-10-12
forum: Multimedia &amp; Video
---

### Post by Deka on 2006-10-12
I just bought this webcam, and apparently it has some issues with linux. I got it working in Ekiga, but nothing else. Anyone else had this problem? I cant even get camorama to load. I immediately get "could not connect to video device (/dev/video0). Please check connection."

In amsn, it finally started seeing I had something, but when I click "configure webcam" and select either driver (v4l, v4l2) I get "error getting capabilities." and it wont let me chose "change video settings"

has anyone gotten this cam working out of ekiga?

---

### Post by Deka on 2006-10-12
It doesnt work in Gyachi either. I get "error while querying mmap-buffers"

---

### Post by Deka on 2006-10-12
after a restart it wont even work in ekiga, but now I get this from gyachi.

---

### Post by Deka on 2006-10-17
Nothing?

---

### Post by miahfost on 2006-11-08
Sorry Deka, I am having the same problems. Here is the information from my machine: Linux shadowfax 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux 

I am running Edgy Eft and have followed the procedure to install the proper driver etc. It seems that Logitech does not even make a drive for the 5000 that will run on Apple hardware. Bad logitech, no soup for you.

---

### Post by styven on 2006-12-30
I can't get mine to do anything, it is seen in lsusb as .....
Bus 005 Device 026: ID 046d:08ce Logitech, Inc.

If i plug into usb, there is no indication that it is on, no led.

I have attempted to install driver from qc-usb-messenger-1.6.tar.gz, which runs in a terminal asking various questions, with this i managed to get my old quickcam to work, but no joy with new one. I don't think now that this is what i require.

I cannot find the correct driver, any ideas anyone?

Steve

---

### Post by budgie9 on 2006-12-30
I don't think this is going to help a great deal, but have any of you tried Easycam2. This program found the correct drivers for my Logitech camera.  I tried loading the drivers myself and it refused to work.
I do use Dapper.

---

### Post by Gouchi on 2006-12-30
Hi there,

just some update :

Logitech Quick Cam Pro 5000 works now with aMSN.
Just grab the last version of aMSN and UVC driver.

More information [here]("http://www.amsn-project.net/forums/viewtopic.php?p=13761#13761").

Works although with [Ekiga]("http://www.gnomemeeting.org/"), [luvcview]("http://mxhaard.free.fr/spca50x/Investigation/uvc/"), [ffmpeg]("http://article.gmane.org/gmane.linux.drivers.uvc.devel/503").

---

