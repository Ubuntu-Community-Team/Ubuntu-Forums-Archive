---
title: "Does Microsoft LifeCam VX-5000 work with Ubuntu?"
date: 2008-07-21
forum: Multimedia Software
---

### Post by kwilliam on 2008-07-21
Probably nobody knows the answer, but does the **Microsoft LifeCam VX-5000** webcam work with Linux? I'm thinking of getting either that or a Logitech Quickcam Deluxe for Notebooks (or Logitech Quickcam Communicate).

If anybody has any advice, I'm looking for a sub $50 webcam for my laptop. Once I buy one, I'll let you know how it works out.

---

### Post by thirstyghost on 2008-08-27
If they're the same as the other Lifecam models, then probably no.
I have a VX-6000, NX-6000, VX-7000 and have tried a VX-3000, 
and none of them work with Linux, yet.

Get a Logitech model.  I have a Quickcam STX that works 
out-of-the-box, and a Pro 5000 that works mostly 
(Have to reboot to get it to work again occasionally).

Here's a link to supported Logitech-brand webcams for Ubuntu:
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech)

You can find good deals on Ebay or Craigslist.  Look for a 
webcam that has at least a VGA sensor (640 x 480).  The Lifecams 
have a CMOS sensor, which is why the picture is grainy (so does 
the STX but the pic is better).  The discontinued Pro 5000 has a 
CCD sensor and the pic is better.

---

### Post by kwilliam on 2008-08-27
I'm sorry, I forgot to follow up this post! I was unable to find the Microsoft webcam at any stores nearby, so I got a Logitech Quickcam Deluxe for Notebooks for ~$45 from Wal-Mart, and have been very happy with it. (I'd have prefered a lower price tag, but I was willing to pay a little extra for the convenience of buying from a local store where it would be easy to return if it wasn't Linux-compatible, versus buying a cheaper webcam online and having to pay shipping.) It worked out-of-the-box with Kubuntu 8.04; I just plugged it in and Skype could see it. Windows specific featues like face-tracking aren't supported in Linux (because Linux uses a generic driver) but that's OK because the face-tracking kind of sucked in Windows anyway. The only complaint is that the built-in microphone seems to insert a faint clicking sound when using it in Linux, but since it didn't do that in Windows, I expect it was a driver issue. More of a minor inconvenience than anything, and not a problem if you are using a headset microphone instead of the built in one. See: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/151890]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/151890")

But I guess the conclusion of this thread is: Does Microsoft LifeCam VX-5000 work with Ubuntu? Probably not. Logitech is currently the best-supported brand of webcam.

---

### Post by tony_wh on 2008-12-26
It Worked Out of the Box for Me !!!!:):)!!!!

I was given a VX-5000 for Christmas.  I plugged it into my VAIO TX2 running ubuntu 8.10 and downloaded Skype 2.00 from their website and installed the .deb  (with the camera plugged into the USB - don't know if that was important or not) and it all worked.  The only thing I had to change was the video and sound capture source in Skype where, magically, LifeCam options had appeared.

Thanks to all those clever progammers in the community (and perhaps at Skype).

---

### Post by brentvincent on 2008-12-28
Based on tony_wh's comment I went ahead and bought the VX-5000 on sale (after Christmas) to use as a Skype webcam (with Ubuntu 8.10).  While I can get an image in luvcview and it seems to connect with the uvcvideo driver, I wasn't able to get an image with any of the applications I tried (Skype, Kopete, aMSN, Cheese, Camorana) on two machines (an Alienware desktop and a Thinkpad T41).  While I'm tempted to try to debug this given that there's some indication that it should work, it's just not worth the time for me (returning the webcam now).  

I just wanted to post my experience as a warning for others who might be tempted to try the VX-5000 in Ubuntu (8.10) ... mileage may vary.

Good luck!

---

### Post by nategerr on 2010-07-06
Yes it works just fine with skype. had to mess around with some settings a little but if I can get it to work it's basically plug and play.

---

### Post by Elena_cm on 2010-08-05
Hi!
I just wanted to confirm that my VX-5000 also works fine in Ubuntu 10.04 which I just installed on my Acer Aspire 5715z. I had made a couple of attempts at Ubuntu before but ended up giving up due to lack of time. This version does seem to be more user friendly. I burnt the ISO, installed it and I ran a search in Firefox as the Webcam appeared to be the only thing that was not up and running from the beginning. I found this thread, downloaded Skype from their website. I installed the package (everything by default), I had to make sure that my webcam was set as the videosource in Skype (sometimes I also have to check this again in Windows XP). The integrated mic would not work and I could not find it in the Sound devices (within Skype). I thought of what I usually would have done in Windows and quickly found my way to the settings. I had to go to System > Preferences > Sound > Input, and here I could select my VX-5000 as the source microphone. I went back to Skype and made a test call and it worked. I then tried a video call to my other computer and it worked too. The only thing... when the call was started, I had to click on the fourth icon at the bottom and then click on "Start my video". The picture quality is as good as with Windows XP. Oh, and I changed the style in Skype as well as I could only read the menu options once I rolled over them. I changed the "Clean" style (any of the other ones would allow to see the options properly).
Nice one, I have to leave further tests for later, but I am quite happier with this first run of Ubuntu this time. *To be continued...*
Thanks to you, guys, for pointing me the way on this one :KS

---

### Post by appen on 2010-08-17
Hello all.

I am running Kubuntu 10.04.
The video works in skype with no issues.
But the microphone does not work. I go to sound and video configuration, it sees a usb mic, but it is grayed out. I can't up the preference list.

Appen

---

### Post by jelera on 2010-08-18
The webcam and the mic from the LifeCam VX-5000 works just fine in Ubuntu 10.04

The cam works right of the box.
The mic, well you just have to select LifeCam VX-5000 as your input device in the Sound Preferences. You can access Sound Preferences from clicking the Speaker Icon in the top left corner of the screen.

---

### Post by appen on 2010-08-19
> **jelera said:**
> The webcam and the mic from the LifeCam VX-5000 works just fine in Ubuntu 10.04

The cam works right of the box.
The mic, well you just have to select LifeCam VX-5000 as your input device in the Sound Preferences. You can access Sound Preferences from clicking the Speaker Icon in the top left corner of the screen.

I went to Sound & Configuration, Audio Capture.  The mic is refured to as a Generic FREETALK Evreyman (USB Audio). It is grayed out, when I put my mouse over it it says: 

"The device is currently not available(Either it is unpluged or the driver is not loaded).

I am using KDE 4.4.5.

Thanks for the quick reply.
Appen

---

### Post by appen on 2010-08-19
> **jelera said:**
> The webcam and the mic from the LifeCam VX-5000 works just fine in Ubuntu 10.04

The cam works right of the box.
The mic, well you just have to select LifeCam VX-5000 as your input device in the Sound Preferences. You can access Sound Preferences from clicking the Speaker Icon in the top left corner of the screen.

I went to Sound & Configuration, Audio Capture.  The mic is refured to as a Generic FREETALK Evreyman (USB Audio). It is grayed out, when I put my mouse over it it says: 

"The device is currently not available(Either it is unpluged or the driver is not loaded).

I am using KDE 4.4.5.

Thanks for the quick reply.
Appen

---

### Post by jjpcexpert on 2010-12-10
> **kwilliam said:**
> Probably nobody knows the answer, but does the **Microsoft LifeCam VX-5000** webcam work with Linux? I'm thinking of getting either that or a Logitech Quickcam Deluxe for Notebooks (or Logitech Quickcam Communicate).

If anybody has any advice, I'm looking for a sub $50 webcam for my laptop. Once I buy one, I'll let you know how it works out.

The VX-500 works (no mic tho)

---

### Post by fonkamex on 2011-05-08
I just bought the vx-5000 and I have UBUNTU 11.00. Video works fine  on Skype but all the sound desapeared. I going to try again after reading some forums.

---

