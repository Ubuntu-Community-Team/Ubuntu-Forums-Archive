---
title: "Logitech webcam works but audio has clicking noise"
date: 2009-07-29
forum: Multimedia Software
---

### Post by bw44 on 2009-07-29
I just purchased a Logitech QuickCam Delux for Notebooks.  It works very well with no audio problems under XP with Skype .  It also works under Ubuntu with Linux Skype, but there is a regular (every 1 and 1/2 sec) clicking noise in the audio stream.  I installed Ekiga to test if the clicking was peculiar to Skype, but it's also present with Ekiga (though Ekiga doesn't recognize the Logitech camera, only the mic!)

I tried switching the USB port to which the webcam is connected but this didn't make any difference.

I have a cheap microphone I've been using with Skype with no problems, and I can continue to use it for audio input, so it's not critical, but it would be nice to be able to use the Logitech mic.

Has anyone else experienced this probelm and found a solution?

Thanks for any suggestions.

bw44

PS:  This is apparently a known problem/bug: It's reported at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/151890](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/151890).  No solution appears likely; the problem is apparently in the firmware and the M$ driver filters it out, but the Linux one doesn't.  (The power of M$!) Bummer.

---

### Post by igorzwx on 2009-07-29
The best solution for Ubuntu 9.04 with Skype and Ekiga
is a mic for 10 Euro 
and OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Fantastic quality!
no noise, no delay, no latency.

---

### Post by bw44 on 2009-07-29
> **igorzwx said:**
> The best solution for Ubuntu 9.04 with Skype and Ekiga
is a mic for 10 Euro 
and OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Fantastic quality!
no noise, no delay, no latency.

Thanks for that.  As I mentioned I do have a mic which works and that will have to do (and it only cost about $10 CAD).

---

### Post by igorzwx on 2009-07-29
When you make a test call to Ekiga server, do you have a delay?

---

### Post by igorzwx on 2009-07-29
your webcam is not in the list
[http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux](http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux)
   140oss_usb	usbif46d,8b2	Logitec Quickcam Pro 4000 (mic) (BETA)

   141oss_usb	usbif46d,a01	Logitec USB Headset

---

### Post by bw44 on 2009-07-29
> **igorzwx said:**
> your webcam is not in the list
[http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux](http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux)
   140oss_usb	usbif46d,8b2	Logitec Quickcam Pro 4000 (mic) (BETA)

   141oss_usb	usbif46d,a01	Logitec USB Headset

> **igorzwx said:**
> When you make a test call to Ekiga server, do you have a delay?

In answer to your question:  no there is no delay, although as I said Ekiga does not seem to support the video component of my webcam.  The audio steam has the annoying click however.

As for the webcam not being in the list you mention, I don't really understand the list elements -- it doesn't look as though ANY Logitech devices are supported except the one you mention, which surpirises me.

I purchased the Logitech QuickCam Delux for Notebooks on the basis of the following list at the Ubuntu Wiki site:

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech)

It says there that the device works out of the box with Hardy Heron (8.04). That's why I bought it.  There was no mention of problems with the audio component. Live and learn. :(

---

### Post by igorzwx on 2009-07-30
USB devices are not supported by OSS4.
A few of them are supported, not more.

What is your real goal?

Do you want to have a good sound quality,
or you want to find a way how to utilize your WebCam mic?

---

### Post by bw44 on 2009-07-30
> **igorzwx said:**
> USB devices are not supported by OSS4.
A few of them are supported, not more.

What is your real goal?

Do you want to have a good sound quality,
or you want to find a way how to utilize your WebCam mic?

I've accomplished my goal: it was to determine if I could use both the video and audio components of my webcam with Skype (and/or Ekiga) under Ubuntu.  The answer is "No."

The video works adequately with Skype (but not with all the feature support available with the Widoze driver).  The audio does not work satisfactorily under Linux because there is a firmware bug in the Logitech device, which M$ has conveniently coded a workaround correction for in their driver.  (The problem with Ekiga is that, as you have suggested the video implementation of the device is question is not supported.  Since, I only want to use Skype this is not, for me, and issue.)

My solution is to use the webcam for video and the microphone I already own for audio.  If I ever want a better solution I will have to buy another (better) webcam that is fully supported under Linux.

Thanks for your help and suggestions.  I think I will mark this thread "SOLVED" since there really is no solution at hand.

bw44

PS.  I just learned that the "SOLVED" function was disabled so I can't mark this thread "SOLVED".  Sorry.

---

