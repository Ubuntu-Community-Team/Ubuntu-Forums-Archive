---
title: "&quot;Enable support for Sonix SN9C1XX&quot;?"
date: 2008-11-20
forum: Multimedia Software
---

### Post by sondosia on 2008-11-20
So, I recently bought a Clique HUE HD Webcam on Woot.com, because the Amazon page for it said that it supports linux kernel 2.6 and above. So I bought it. Upon installing it, I discovered that, naturally, it doesn't work at all because the drivers are for Windows.

Then I found some instructions saying that this webcam has the Sonix SN9C1XX series of chips and that you can enable support for them in the kernel.

I'm relatively new to linux, so I have NO idea how to do that...anybody want to help? Thanks.

---

### Post by psyke83 on 2008-11-20
You should search Launchpad for information on your issue.

This appears to be your bug, but there could be others (with instructions/workarounds): [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280657](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280657)

---

### Post by rustutzman on 2008-11-22
I just got this in from woot also and have it working in Intrepid. Actually it was pretty easy by following the instructions here:

[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

I don't have the audio yet though and not sure if I will but the video works. I didn't think it did at first but it was just a very dark picture.

I got it working in aMSN and with the video options was able to lighten it up. 

If anyone gets the audio working I'd appreciate a post on how you did it.

HTH
Russ

---

### Post by EvilMarshmallow on 2008-11-26
I've been watching this post for a couple of days.  I too bought one of these cams and I've had a devil of a time getting it to work.  I tried to follow the instructions on that microdia site that's linked above, but apparently my Linux-fu isn't strong enough to follow those directions.  I found another place that talks about a program called "EasyCam 2", available from a custom set of repos.

[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

I'm in the process of installing now, I'll post again after a while and let you know how it goes.  The program recognized the cam immediately and prompted me to install the drivers.  It's apparently just a script that automates the compiling, etc. of the drivers, so I'm having to pull down linux-source packages right now (cheap internet service, I don't have a lot of bandwidth).

---

### Post by demc on 2008-12-07
I too have purchased the same webcam, and gone through the steps on the microdia google group.

I had to change one of their instructions, as 'libv4l' is not installed, but instead libv4l-0. Maybe this is where I've gone wrong?

 Their mplayer test works, but the colors are all ugly, kind of brown and dark red, and i get the following error:
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits

 My dmesg is as follows

[ 9265.253119] microdia: Unknown symbol video_ioctl2
[ 9265.254787] microdia: Unknown symbol video_devdata
[ 9265.256829] microdia: Unknown symbol video_unregister_device
[ 9265.257438] microdia: Unknown symbol video_device_alloc
[ 9265.257727] microdia: Unknown symbol video_register_device
[ 9265.259086] microdia: Unknown symbol video_device_release
[ 9286.665284] microdia: Unknown symbol video_ioctl2
[ 9286.666955] microdia: Unknown symbol video_devdata
[ 9286.668996] microdia: Unknown symbol video_unregister_device
[ 9286.669611] microdia: Unknown symbol video_device_alloc
[ 9286.669920] microdia: Unknown symbol video_register_device
[ 9286.671280] microdia: Unknown symbol video_device_release
[ 9300.415630] Linux video capture interface: v2.00
[ 9302.561950] microdia: Microdia USB 2.0 webcam driver loaded
[ 9302.564093] microdia: Microdia USB 2.0 Webcam - 0C45:6282 plugged-in.
[ 9302.564109] microdia: Detected SN9C20X Bridge
[ 9302.594928] microdia: Detected MT9M111 Sensor
[ 9302.630137] microdia: Microdia USB 2.0 Webcam is now controlling video device /dev/video0
[ 9302.634344] usbcore: registered new interface driver usb_microdia_driver
[ 9302.634361] microdia: v2008.11 : Microdia USB 2.0 Webcam Driver
[ 9343.833987] microdia: [E] Empty buffer queue.
[10329.400118] microdia: [E] Empty buffer queue.

ekiga gives an oddly distorted image made up of horizontal lines, and cheese only gives me the tv test image.

Any ideas as to what I've done wrong?

---

### Post by lwhitmore on 2008-12-18
Did anyone get this camera working?  Is it worth buying?

---

### Post by tbaleno on 2008-12-19
Yeah.  I got it working.

I found a kernel module called microdia.  It requires kernel 2.6.22 in order for it to be compiled.

I then loaded videodev and then the microdia module and it seems to have worked.

Here is a picture from it.  It isn't a great picture because the room it is in is very bright.  But it is working.

[http://www.mysimplehomegarden.com/garden/mgarden/garden.jpg](http://www.mysimplehomegarden.com/garden/mgarden/garden.jpg)

I probably won't be visiting this thread again, so if you have any questions or whatever, you can find me at the site I just mentioned.

BTW, mine was a woot special.

Edit: Well, while I did get it to work, I decided to go back to the logitec camera I was using as it produced a cleaner image.

---

### Post by alof8k on 2009-09-18
just a suggestion as I myself was browsing this and found the solution while viewing the manual for *Cheese* .

my webcam is one of those cheap 6-led webcams that's found on ebay and is noted as being sn9c1xx under linux.  The webcam used to work some times back but stopped working lately.  If I open cheese, I get horizontal lines with a still image even if I click on video. The picture is severely dark aswell.

i've found the issue is that if you go to gstreamer-properties (launch that from terminal), you'll find under the video tab that the default output plugin is set to either Xv or No Xv.  Mines was set to Xv and that caused the issue since Xv means that video processing is going to be put on the graphics card.  This became an issue for me personally because right now I'm using integrated graphics (unichrome to be exact) as opposed to the radeon 9200 agp I had prior when it was working. This integrated card is not sufficient.  So what I did was change the setting to No Xv and this allowed the video processing to be put on the CPU (in my case, athlon xp).

Now cheese and ekiga both show video properly like it should  :)

---

