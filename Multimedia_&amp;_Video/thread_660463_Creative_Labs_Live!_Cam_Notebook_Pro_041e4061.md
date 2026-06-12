---
title: "Creative Labs Live! Cam Notebook Pro 041e:4061"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by padlock.x on 2008-01-06
I recently obtained a Creative Labs Live! Cam Notebook Pro, ID 041e:4061, model VF0400.  I've attempted to get it working with Ubuntu 7.10 (2.6.22-14-generic) but with no luck.  Creative has it listed on their opensource page, but without a link to a driver that will work.  It's not listed as compatible with gspcav ([http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)) or with UVC ([http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)) but I gave both a shot anyways, with the results of it not working.  

Has anyone had any luck getting this particle model webcam to work?  I need to try and get it going asap if possible, or replace it with another model (rather not have to,) to do a bit of property surveillance (I know a webcam isn't the best choice, but when the price is free or low, I can't complain, and I'm on a serious budget and have a serious time frame from the missus.) 

Background on why I need to try and get it working, the neighbors kids think the tree outside of my office window is a great place to hang out, and they've already destroyed a nice handmade wooden flowerpot, my birdhouse, are stripping the branches off of the tree, burning candles (and other things,) broke a cellar window and are just being general nuisances.  I want to get them in the act, basically, because they run the minute a light in my house comes on according to another neighbor.  They're making me feel like an old man yelling at kids to get off my lawn, but they've already done a lot of property damage and I'm trying to minimize it.

Any help would be greatly appreciated.  I've never actually attempted to use a webcam before, I see enough of the people I talk to on a daily basis already =)

---

### Post by copilot on 2008-01-14
I couldn't get it working either. Thanks for posting, good to at least know someone is having the same issue.

---

### Post by Flash_Mordon on 2008-02-16
Creative's open source page now links to this driver:

[http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource]("http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource")

You have to use the latest tarball (1.5.6). The source package in the ubuntu repo does not work with this camera.

Funny thing is I intended this post to be something like "I found this driver and it didn't work...", but when I went back to the page to copy the URL I realised the repo driver was too old (1.5.1).
Anyway, parallell to writing this post I got the camera to work. :biggrin:

---

### Post by padlock.x on 2008-02-19
Thanks for the info that they finally updated the page, I'll have to try it out when I get home tonight.  I actually ended up setting up my Sony DV to record on motion which worked way too easy (never even thought to use my video cam originally.)  Still going to check out the link, so thanks again!

---

### Post by Radiobeamer on 2008-03-30
Hi, thanks for this information.  I have a Live! Cam Notebook (VF0470) which is supposed to work with ov51x-jpeg 1.5.6 and I'm really struggling to make it work.  I'm a bit new to Ubuntu so I am unsure that I have loaded this driver correctly.  I've been working on this for days now, learning as I go.  As far as I can tell, the correct steps I have taken are as follows:

1. Download ov51x-jpeg-source_1.5.6-2_all.deb from debian (not Ubuntu).

2. Open it with synaptic - warns me that an older version is available which I ignore and tells me that all dependencies are satisfied.  Installation finishes without any further errors or warnings.

3. Run 'sudo module-assistant -f a-i ov51x-jpeg' in terminal, using the -f option as this isn't the first time I've done this process.  Lots of output here and I don't know if the warnings are relavent or not.  Nevertheless, after this process I get the file ov51x-jpeg.ko in the '/lib/modules/2.6.22-14-generic/kernel/drivers/usb' folder.

4. Now I'm expecting the web cam to be installed but when I try lsmod it's not there (the web cam is plugged into USB and appears if I try lsusb).  So I try 'sudo insmod ov51x-jpeg.ko' and I get the error:
'insmod: error inserting 'ov51x-jpeg.ko': -1 Unknown symbol in module'

5. To debug this I try dmesg and it tells me:
[ 4743.681553] ov51x_jpeg: Unknown symbol video_devdata
[ 4743.681995] ov51x_jpeg: Unknown symbol video_unregister_device
[ 4743.682204] ov51x_jpeg: Unknown symbol video_device_alloc
[ 4743.682322] ov51x_jpeg: Unknown symbol video_register_device
[ 4743.682580] ov51x_jpeg: Unknown symbol video_usercopy
[ 4743.682689] ov51x_jpeg: Unknown symbol video_device_release

Where did I go wrong?

Thanks,

Paul

---

### Post by chomski on 2008-04-22
Any luck with this? I'm having the same problem on Hardy, just wondered if you got anywhere with your webcam.

---

### Post by nami on 2008-05-08
Try this: [**www.rastergeeks.org**]("http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall")

Taken from [**wiki.ubuntu.com**]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasCreative")

---

### Post by nami on 2008-05-08
How about [**this**]("http://connect.creativelabs.com/opensource/Lists/Webcam%20Support/DispForm.aspx?ID=75")?

---

### Post by johnmichale on 2008-05-08
Auto Tuning technology automatically produces optimum brightness and contrast levels 

=================================================================
johnmichale

---

### Post by leandromartinez98 on 2008-06-28
SOLVED HERE:

1) Create the /dev/vide0 and /dev/video devices (if ls /dev/video* finds nothing):

sudo mknod /dev/video0 c 81 0
sudo chmod 666 /dev/video0
sudo ln -s /dev/video0 /dev/video

2) Dowload the latest driver source from:

[http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource](http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource)

(not the debian package, the source, in my case it was [this]("http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.8.tar.gz") file)

3) Compile the driver:

tar -xvzf ov51x-jpeg-1.5.8.tar.gz
cd ov51x-jpeg-1.5.8
make
sudo make install

4) Add the new driver module like this (probably the make install should try already
to do this, so if "already loaded" messages appear here, don't worry). You
can check if the module is loaded by typing ("lsmod |grep ov51"). 

sudo modprobe videodev   #(not sure if it is required)
sudo modprobe ov51x-jpeg-1.5.8

Led light on! Works on Ekiga.
After a reboot (god knows why) worked on skype as well!
I hope it works for other people!

---

### Post by mashcaster on 2008-07-16
Hello

I followed these instructions and it does not seem to work propertly.  I tried using vlc and it displays the input for about 2 seconds and then vlc closes down, I also tried skype and nothing is displayed in the camera test, and also I tried camorama, which gave the results you can see in the attached file.

Basically, it shows 3 images from the camera at the same time and in black and white.

Please help

---

### Post by Ben Jao Ming on 2008-07-16
I had my "Creative Live! Cam Notebook" working pretty easily. And since it uses the same module as the pro-edition, I'm sure my howto will benefit you guys as well. Good luck and please let me know if something is broken in the howto.. hopefully I'll be able to correct it.

[http://overtag.dk/wordpress/2008/07/creative-live-cam-on-ubuntu-804-using-ov51x-jpeg/](http://overtag.dk/wordpress/2008/07/creative-live-cam-on-ubuntu-804-using-ov51x-jpeg/)

---

### Post by Ben Jao Ming on 2008-07-16
> **mashcaster said:**
> I tried camorama, which gave the results you can see in the attached file.

My camorama does the same. But everything is working fine in Cheese. So go apt-get install that guy, and see what happens. Also check your multimedia systems - you should enable v4l2 for video input. You can enable the Multimedia Systems Selector by right-clicking on your gnome menu bar and the navigating to Edit Menus->System->Preferences.

---

### Post by mashcaster on 2008-07-17
Cheese works nicely, Skype test does not work.  How do I get that to work?

I will try out v4l2 soon.

---

### Post by leandromartinez98 on 2008-07-21
> **mashcaster said:**
> Hello

I followed these instructions and it does not seem to work propertly.  I tried using vlc and it displays the input for about 2 seconds and then vlc closes down, I also tried skype and nothing is displayed in the camera test, and also I tried camorama, which gave the results you can see in the attached file.

Basically, it shows 3 images from the camera at the same time and in black and white.

Please help

My camorama also does that, but the camera works fine everywhere else.

---

