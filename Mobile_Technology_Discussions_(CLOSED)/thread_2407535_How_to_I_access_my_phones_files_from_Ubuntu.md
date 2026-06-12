---
title: "How to I access my phones files from Ubuntu?"
date: 2018-12-05
forum: Mobile Technology Discussions (CLOSED)
---

### Post by k9r4n on 2018-12-05
Hey, this is an ongoing problem, and haven't found anything on the case yet. I have a Galaxy J3 Emerge (ARC1, Sprint) which I cannot access from Ubuntu. I haven't tried any other device, so I'm not sure if that helps improve the situation or not. Do I need a specific driver for my phone or the Android OS? The phone is rooted as well by the way. 

Thanks!

k9r4n

---

### Post by TheFu on 2018-12-05
If it is recognized and the phone is in MTP mode, when connected it should show up as storage (not really, but close enough) in any Ubuntu File Manager.  I use caja.

If it isn't showing up within 5 seconds of the USB connection, post the output from **lsusb -t** here and tell us which device is the phone.

For someone to be able to tell you exactly the next steps, we need to know the release you are running.  16.04.5 or something else?

---

### Post by k9r4n on 2018-12-05
It is a Galaxy J3 Emerge, running on Android 6.0.1 and Ubuntu 14.04 and Ubuntu versions 18.04 + 18.10. I've tested it on multiple versions of Ubuntu and same output.

---

### Post by coffeecat on 2018-12-05
> **k9r4n said:**
> Android 6.0.1

In my limited experience, it's that old version of Android that is the problem, rather than Ubuntu. With Android 8 and Ubuntu 16.04, it all "just works". With Android 6, I had to put Android in developer mode (it sounds as though you've already done this) and then fiddle about with the USB settings under developer mode settings. Whatever I chose wouldn't stick, and each time I connected my Android device to my Ubuntu machine, I had to change the USB setting from MTP to USB charging and then back to MTP before it would mount in Ubuntu. Or something like that - I'm going from memory from earlier this year. Try all the USB settings under developer mode and you should be able get it to work.

Also - I think with Ubuntu 14.04, there was something you needed to install, but I can't remember the details. You should be OK with Ubuntu 18.04 though.

---

### Post by TheFu on 2018-12-05
lsusb -t?

---

### Post by k9r4n on 2018-12-06
Oh wow, Android 6.0.1 isn't that old? How come Ubuntu doesn't support Android? Yeah the only problem is i can't upgrade to 18.10 yet, because I need a new computer. I only have 300 Gb HDD, and it's from like 2010. I need Windows 10, which runs perfectly at the moment with 14.04.5, but 18.10 wouldn't run properly even by itself.

---

### Post by coffeecat on 2018-12-06
Android 6 is ancient. My (Nokia) phone has just upgraded itself to from Android 8 to Android 9. It originally came with Android 7. 

Anyway, that's all moot. TheFu has now asked you for information on two occasions, and twice you have apparently ignored this request. Apart from being discourteous to those trying to help you, failing to provide requested information is counter-productive. Help others to help you.

I have nothing more to offer you.

---

### Post by TheFu on 2018-12-06
Support by Google of Android 6 ended last August.  Last release was October 3, 2017.

If you are here to complain, please post to the "Chat" subforum.
If you want constructive help to solve issues, please answer the questions, otherwise nobody can help and it is a waste of our time.

Linux supports standard protocols because it is impossible to support every 1-off device made on Earth.  MTP is one of those protocols and it is supported, provided the config files know about the device and are told which usb IDs should use MTP.  There are hundreds or thousands of new USB devices released every year.  The vendors can update the device lists that Linux knows about, but most don't.  Every USB device type has a unique ID.

If you want to complain, call the company that made the phone for not being proactive within the F/LOSS community and pre-emptively providing useful data to those teams.  Also complain about only providing a few years of security patches while you are at it. Good luck with that.

Support for 14.04 will be ending in a few months. Most people here haven't used a 14.04-based desktop since 2016, so how to deal with those specific issues isn't at the front of their memory.  
You will need to move to either a 16.04 or 18.04 release soon-ish.  On older hardware it is better to avoid "Ubuntu Desktop" proper and go with a lighter desktop.  Which would work best depends on your current hardware.  Probably best to open a new thread for that question, assuming a quick search of the forums doesn't provide enough guidance.

---

### Post by k9r4n on 2018-12-11
I'm sorry, I didn't see what you said, and then when you said that last message, I ignored it because I didn't know what you meant. I'm sorry about that. I can't check at the moment, but I will try and get the log to you soon.

---

### Post by vidtek on 2018-12-11
> **k9r4n said:**
> Hey, this is an ongoing problem, and haven't found anything on the case yet. I have a Galaxy J3 Emerge (ARC1, Sprint) which I cannot access from Ubuntu. I haven't tried any other device, so I'm not sure if that helps improve the situation or not. Do I need a specific driver for my phone or the Android OS? The phone is rooted as well by the way. 

Thanks!

k9r4n

Easy way out- install Kubuntu with KDE, it has a brilliant piece of software called KDE connect.  It can connect in many different formats, will give on-screen notifications and monitoring of 'phone calls in real-time, folder discovery etc.  Cut and paste file operations too (permissions allowing).  
I have been using it since I had my old Samsung S3, so it works on really old Android versions.
It connects easily to my now 2-year old ZTE Axon Elite and a one year old Huwei too.

Cheers Tony.

---

### Post by SeijiSensei on 2018-12-11
KDE Connect is a good choice.  Also you could try the Android app called Wifi File Transfer Pro.  It turns the phone into a mini webserver.  You open a browser and point to that server, then use the browser interface to upload/download files over the network.  It's especially helpful with bulk transfers rather than a file or two.

I paid $3 for a license and have used it many times when nothing else seemed to connect properly.

---

### Post by lisati on 2018-12-11
I think there's probably a modicum hope after an informal test.

I just fired up my other laptop, with Ubuntu 18.04, and hooked up a new-sh (for me, at least) phone, not a Samsung, running Android 6.01. Although the phone initially switched to charge-only, switching it to MTP mode allowed me to access the SD card. Similarly with an older laptop running 14.04.

Don't give up just yet!

---

### Post by TheFu on 2018-12-22
KDE is nice, but you don't need to swap your desktop to use KDE-connect.  I saw there was a Gnome Shell solution a few months ago : [https://www.omgubuntu.co.uk/2018/05/ubuntu-18-10-gsconnect-extension-by-default](https://www.omgubuntu.co.uk/2018/05/ubuntu-18-10-gsconnect-extension-by-default)

[https://askubuntu.com/questions/1036351/how-to-install-and-run-gsconnect-to-have-android-integration-fransfer-files-se](https://askubuntu.com/questions/1036351/how-to-install-and-run-gsconnect-to-have-android-integration-fransfer-files-se)

But I doubt any of these will make udev work with any specific android device.  Way back in the 12.04-14.04 times, I had to setup specific udev rules manually to get a Nexus4 recognized at all.

With my newer devices, connecting a minimal Ubuntu desktop (just openbox) with my phone and a Fire 8 tablet "just work", nothing manual necessary.

So ... no chance of an **lsusb -t** output?   Open a terminal.  Connect the phone via USB, run that command and post it back here.

---

### Post by ajgreeny on 2018-12-22
> **lisati said:**
> I think there's probably a modicum hope after an informal test.

I just fired up my other laptop, with Ubuntu 18.04, and hooked up a new-sh (for me, at least) phone, not a Samsung, running Android 6.01. Although the phone initially switched to charge-only, switching it to MTP mode allowed me to access the SD card. Similarly with an older laptop running 14.04.

Don't give up just yet!
I'm pretty sure lisati has got it right.

Go into the Android settings and in the connections/usb section change it to whatever works for simply copying or moving files; I'm not sure how that's described in Android 6.01 but it should be obvious.

I had (and still have) an old Android 4.1 system which connected fine to my Xubuntu OSs (yes, even 12.04) once I enabled the mass storage setting in the phone.  

As Android 4.1 would connect easiy, I'm sure 6.01 will do so too.

---

