---
title: "Connecting Digital Camera Sony DSC-W55?"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by scradock on 2007-06-04
I've been using Feisty most of the time for the last few weeks, with various interesting excursions chasing video drivers, 3D and now the kernel 2.6.20 problems. I still don't want to go back to WXP!!

BUT.....I just bought a Sony digital camera, and of course I want to download the pictures into my laptop, preferably in Feisty. The camera has a USB connection, so I thought - Oh! that will autodetect and I'll just copy the pictures into a folder, even if there isn't any specialist software to do it for me, Windows-style.

I'm having problems..... the camera shows up in the "lsusb" output, with sensible information that shows it's the right machine. But there is no additional drive listed in "blkid" after I connect it up, so I can't tell where to look for files.

I've tried F-Spot, which claims there is no camera available.

Digikam found it once, for a brief moment - correctly named and all - but now refuses to see it again. The "lsusb -v" output shows it has changed its device number from Bus#2 device 006 to Bus#2 device 007 - without being unplugged or turned off. Turning the camera off and on again also changes the device # by another +1 to 008.

Any ideas - is there a standard utility for finding and connecting to a USB device simply as a storage device, given that it isn't listed by "blkid"? Any clues as to how to get my camera connecting in Linux?

Thanks, everyone.......

____________________________________
HP Pavilion zv6000; amd64 Athlon; Feisty with 2.6.20-16 kernel; ........

---

### Post by scradock on 2007-06-04
It's getting to be a bad habit, answering my own posts.

I found a thread on the Hardware category, which connected to someone who discovered after much trial and error that the camera needs to be told to use PTP connect mode - AUTO doesn't do it. Change mode, and Presto! - gthumb sees the camera and imports the pics.

Hope that helps someone else who's looking in the wrong place for the answer....

---

### Post by klep on 2007-06-05
hey, 

I just wanted to say thanks for posting what the solution was.. I don't have this camera yet but I *think* I will be buying it shortly and it being sony and us using Linux I was afraid it might not play nice.


Offtopic a little: what's the camera like? good picture quality? quite a lot of smaple pictures i saw for lots of cameras have blurring round the edges of the photos which worries me a bit.


Cheers,

---

### Post by Sadhiq4 on 2007-06-12
Thanks, I can now view and edit my pictures with Ubuntu :)
That was the last thing I couldn't do with Linux ! :D

---

### Post by marty757 on 2007-06-13
I have a Digital Camera Sony DSC-W55 and have it set to USB PTP Class Camera, but I still get this error message in gThumb:
An error occurred in the io-library ('Could not find the requested device on the USB port'): Could not find USB device (class 0x6, subclass 0x1, protocol 0x1). Make sure this device is connected to the computer.

Does anyone have a solution?

---

### Post by justink on 2008-01-01
getting the same error as you bro, if someone could help us out that'd be amazing

---

### Post by gav616 on 2008-01-02
iam having the same really annoying problem.. HELP! :(

---

### Post by gav616 on 2008-01-03
bump!!

anyone?!!

---

### Post by rustybronco on 2008-01-03
[http://sg.answers.yahoo.com/question/index?qid=20070823165105AAQHUH8](http://sg.answers.yahoo.com/question/index?qid=20070823165105AAQHUH8)
> If you already made sure of that, then press the “MENU” button in the camera, and navigate through the various menu options until, in “Setup 2” menu page, you find the “USB Connect:” option. Ideally, it should be set to “Auto” -and it should work, of course. If it doesn't, set it to “Mass Storage”, then set the camera into Play mode, and see if the computer recognizes it. If it doesn't, and just for the heck of it, try the “USB Connect:” > “PTP” mode, and try again.

---

### Post by gav616 on 2008-01-03
many many thanks rustybronco, switching to "mass storage" did work. :guitar:

---

### Post by rustybronco on 2008-01-03
Welcome...

---

### Post by justink on 2008-01-03
Thank You So Much!!!! :d

---

### Post by chappejw on 2008-06-04
Great thanks..!! :)

---

### Post by mihai.ile on 2008-06-12
Hello.
My brother has this cammera.
I switced it on (without connecting to usb), then Menu button -> Setup -> Setup2 -> USB Connect: PTP
Then I swithed on with the USB cable connected and worked flawlessly under Ubuntu Hardy Heron 8.04 with gThumb

Note: gThumb does not come pre-installed so you have to install it if want to use it and then under System -> Preferences -> Removable Drives and Media -> Digital Camera, I entered: gthumb --import-photos

---

### Post by staciedaisy on 2008-06-23
many thanks...this was the last thing i needed for my wonderful computer to be flawless!!  haha and it was the easiest solution!

---

### Post by TheAJKMan on 2008-07-04
rustybronco, should you ever read this thread know that your suggestion saved me a lot of frustration and what little hair I have left. Tried fiddling with the settings menu as you suggested and I now have all the pics d/l to my pc.

---

### Post by jsaulters on 2008-07-12
Thank you, scradock.  It worked like a charm.

---

