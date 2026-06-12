---
title: "Logitech QuickCam Vision Pro for Mac AWOL"
date: 2008-12-24
forum: Multimedia Software
---

### Post by casbahdk on 2008-12-24
I just purchased a Logitech QuickCam Vision Pro for Mac and am running Ubuntu on my Mac G5 (PPC). The QuickCam is supposed to be in practice cross-platform according to [ASE Labs]("http://www.aselabs.com/articles.php?id=268"), as the webcam has no drivers. Unfortunately, neither Ekiga nor Cheese seem to recognize the webcam. Is that because this is a UVC device?

I have tried checking to see if the device is recognized by the system, so I ran:

lsusb

The result was: 

Bus 002 Device 004: ID 046d:09a6 Logitech, Inc.

I have also looked at the Logitech support, but couldn't find anything. 

The webcam is plugged directly into a USB port.

Cheers

---

### Post by brnetonboy on 2009-02-26
Did you ever get this figured out?

---

### Post by casbahdk on 2009-02-26
No, unfortunately. Any ideas?

---

### Post by ender1598 on 2009-02-26
I *just* bought one of these and it's working great.  I'm running on an Intel platform though but it's Ubuntu 8.10 64bit.  I had to plug and unplug it a couple times but Skype loaded it just fine.  Did you try rebooting after plugging it in?

---

### Post by brnetonboy on 2009-03-02
> **casbahdk said:**
> No, unfortunately. Any ideas?

No. Man, I'm really getting frustrated with video and webcam capabilities in Ubuntu. Maybe I just don't know which programs I ought to be using, but everything I read about doesn't work for me and nobody on the forums seems to know how to do anything. :(

Sorry, I'm being pessimistic--I will definitely keep looking for info and I will share my findings. If enough of us try to get stuff to work and then share, we'll get a good solution.

---

### Post by casbahdk on 2009-03-03
Yeah, I am still having problems finding programs that can record streaming audio/video output, in case someday I get it working or breakdown and get a different webcam for Linux. Maybe I should try the webcam on my Lenovo T60 and see if I can get it working there. I was hoping to be able to dump OS X Leopard on my G5, but won't do that as long as OS X is the best platform of the two for recording and editing streaming audio/video.

---

### Post by casbahdk on 2009-03-03
I just tried the webcam with Cheese on two Ubuntu derivatives (Intrepid) and a Fedora Live CD on my Lenovo T60. The webcam refused to play with Cheese on any of them.

---

### Post by casbahdk on 2009-03-05
I contacted Logitech's QuickCam team about the issue: Here is the reply I received:

> Setting up the Linux UVC driver (uvcvideo) is enough. Just make sure it can be loaded automatically or try to load it manually. You can also keep an eye on your syslog to see if it gets recognized.

Any idea how to do any of what is suggested?

---

