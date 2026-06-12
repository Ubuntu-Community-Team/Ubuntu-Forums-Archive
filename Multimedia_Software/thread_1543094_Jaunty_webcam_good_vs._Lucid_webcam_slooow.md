---
title: "Jaunty webcam good vs. Lucid webcam slooow"
date: 2010-07-31
forum: Multimedia Software
---

### Post by ziimen on 2010-07-31
I've just put a brand new Lucid installation on my F8SV-B1 Asus laptop. Jaunty was there previously working just fine, including webcam. Skype worked awesome.

Moved to Lucid because I just bought a new ssd drive. Everything seems to work except the webcam. It barely makes 0.50 fps. What gives?

Tested with Skype, Cheese and Guvcview. Ran gstreamer-properties and v4l2 is there and "working" .... sloooow. The webcam is built-in and reported as a usb 2.0 camera. lsmod | grep uvcvideo gives:

  uvcvideo               57022  0 
  videodev               34361  1 uvcvideo
  v4l1_compat            13251  2 uvcvideo,videodev

Spent 2 hours searching for a solution googling and reading fora to no avail. Anyone knows if there's a common problem to Lucid making webcams slow? Any ideas?

Otherwise I'll be moving back to Jaunty. Will just have to compile the new kernel for the ssd/trim is all.

Thanks,
Dan

---

### Post by gordintoronto on 2010-07-31
How does lsusb identify the webcam?

---

### Post by ziimen on 2010-07-31
> **gordintoronto said:**
> How does lsusb identify the webcam?

Bus 001 Device 002: ID 174f:5a31 Syntek Sonix USB 2.0 Camera

---

### Post by gordintoronto on 2010-08-01
> **ziimen said:**
> Bus 001 Device 002: ID 174f:5a31 Syntek Sonix USB 2.0 Camera

Son of a gun, I have the same thing. My webcam is a Z-Star ZC0303, and I'm running Cheese under Mint 9 (based on Lucid) on a persistent flash drive. 

But the audio (from a microphone which is part of a cheap headset). was perfect right out of the box, first time that's happened in two years!

---

### Post by no2498 on 2010-08-01
4 years for me webcam i have got to work i use the non uvc driver
5 fps now was 30 on 710 on/in 10.04 lucid
i have just in the last few days seen the uvc driver is not loading for you 2
i have just got 10.04 on that computer 3 days ago

was the same thing on/in 910 5 fps

think they need to take the settings from cheese

---

### Post by ziimen on 2010-08-01
Gonna try and recompile the new kernel tomorrow, see if that helps. If not, back to Jaunty. Damn I hate regressions...

---

### Post by ziimen on 2010-08-02
Installed 2.6.35.7 ... plain vanilla, no change, webcam is still slow. Back to jaunty then.

---

### Post by robert shearer on 2010-08-02
Have you tried installing  v4l2ucp from synaptic and using it to configure the cam ?

---

### Post by ziimen on 2010-08-02
I did just now that you recommended it... but that's pretty much the same as guvcview.... same available options don't seem to affect the frame rate. 

brightness/contrast/hue/saturation/gamma/sharpness/backlight-compensation

thought power-line-freq could have something to do with this problem... but no... not really sure what that does.

at least now I know of the new tool so thx! :)

---

### Post by robert shearer on 2010-08-02
In v4l2ucp I had some improvement by adjusting the exposure settings then going back to brightness and contrast adjustment for fine tuning.

Put the exposure into Manual then  the Exposure setting below that try increasing it (slowly with the mouse scrollwheel is best) while watching the result in Cheese.

Other resources that may be of use...

[http://gurrier.wordpress.com/2010/05/30/problem-with-running-logitech-webcam-working-in-skype-on-ubuntu-10-04-lucid-lynx/](http://gurrier.wordpress.com/2010/05/30/problem-with-running-logitech-webcam-working-in-skype-on-ubuntu-10-04-lucid-lynx/)
[http://wiki.archlinux.org/index.php/Webcam_Setup](http://wiki.archlinux.org/index.php/Webcam_Setup)
[http://en.gentoo-wiki.com/wiki/Webcam](http://en.gentoo-wiki.com/wiki/Webcam)

The command..
```
 LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so cheese
```
enabled my Logitech s7500 to work with Cheese.

If you run..
```
sudo apt-get install v4l-conf
```
Then..
```
v4l-info
```
you can get some info on your cam's set-up that may be helpful when viewing the links above.

also plugging your webcam in and running..
```
dmesg | tail
```
Should return some useful info.



The big problem i have with v4l2ucp is that i can't see the whole window.
For some reason it is not resize-able and even hiding the panels does not give the full window.

So excuse the off topic but anyone have a fix for that ??

---

### Post by ziimen on 2010-08-02
Interesting info. Managed to find a driver for this webcam on sourceforge through the first link you provided, will give it a shot later. This is a built-in cam so probably has less options than your external logitech. I did try the v4l2convert.so preload and it seems to have improved things a bit with cheese, but not with skype though.

---

### Post by SunnyRabbiera on 2010-08-03
give wxcam a shot sometime, it works better (for me at least)

---

### Post by ziimen on 2010-08-04
Wxcam works much better... avg 8fps (+/- 2fps) at 350x240 which is at least usable. So it can't be the driver. Thing is skype should work the same way. So I figure maybe it's just the skype options video test that's screwed up, so I tried setting up a quick call between my two skype accounts.

And, that actually worked at the wxcam level.... i.e. 640x350 or so was going at about 5fps. So it must be the video setup test that's either screwed up or trying to run the capture at the max 1.3mpx. I tried the max res with wxcam and it was back to 0.50fps.

Still think that the whole thing worked much better in Jaunty, but I've no explanation for that. And finally it should work much better than 5-10fps anyway... it's a dual core2 at 2.4ghz, this laptop is.

Now, just have to find how to set up skype to use 350x240 res and it should be usable.

Thanks for the wxcam tip.

EDIT: Hmm... wxcam now works at 17fps at 320x256... maybe it was lighting.
I edited skype's config xml for video capture settings... and it works very well. Man, finally!

---

