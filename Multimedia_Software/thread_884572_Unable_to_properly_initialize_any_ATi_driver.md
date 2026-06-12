---
title: "Unable to properly initialize any ATi driver"
date: 2008-08-09
forum: Multimedia Software
---

### Post by BogdanV on 2008-08-09
Well, like most people before me, I'm having issues on installing a driver for my X1300 ATi card. Both the driver provided by Xubuntu and the official, closed-source driver from ATi's drivers page have failed to work on me.
 All attempts have lead to a black screen + system freeze after the loading screen so I had to go to recovery mode and use the fix X Server option (or similar).
 Basically this fix ended up in replacing the Xorg.conf file and reverting to the Mesa drivers. 
 Anyway, the methods I've tried setting up an ATi driver would be :

             ->1st one : from Restricted Drivers Manager (after installing Xubuntu)
               result : black screen + system freeze after system load

             ->2nd one : manual install as provided by the unofficial Linux ATi Drivers Wiki [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) (2nd step)
               result : black screen + system freeze after system load

             ->3rd one : executing the ".run" file and letting the driver's setup to do its job automatically
               result : black screen + system freeze after system load

             ->4rth one : followed the "BinaryDriverHowto ATI" from the Ubuntu site (used recovery mode to login as root because of an permission error given on the 2nd command)
               result : black screen + system freeze after system load

              ->5th and last one : 1st step (that involved setting-up the repository driver) as provided by the unofficial Linux ATi Drivers Wiki [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
               result: same as above

 Is there something I'm missing or is there anything I can do to enable 3d acceleration and DRI on my videocard (either through fglrx or anything else ? ) Because running on a Mesa driver isn't my idea of playing games or running a 3d modeling program.
 Also, should I try using a older version of fglrx or are there any alternatives ?

  Thanks in advance!

---

### Post by elcid89 on 2008-08-09
I had serious problems with this as well. What I did ...

I have onboard video as well as the added ATI card. I found that the driver for the onboard video was causing serious problems with getting the ATI driver to load. 

What I did to fix it, in order:

sudo apt-get remove xserver-xorg-video-intel

sudo apt-get install envyng-gtk

envyng-gtk

use the envy applet that pops up to install the driver. I selected ATI driver and "install the driver (automatic hardware detection)

rebooted and it worked just fine.

Good luck!

---

### Post by elcid89 on 2008-08-09
You may not need to remove the intel driver if you don't have onboard video or you aren't having problems with the drivers conflicting (and thereby loading Mesa all the time instead of the ATI driver).

---

### Post by BogdanV on 2008-08-09
Well, I don't have an onboard video card, just an X1300 on an AGP port. I'll try your suggestion and see if it works.

---

### Post by BogdanV on 2008-08-09
Okay, I've installed Envy and unfortunately, I got an package error. Judging from the terminal log, it seems that package "xorg-driver-fglrx-envy_ [...] i386.deb" triggered an read error. I tried getting the file from Synaptic and it gave me an install error related to the same issue.
 I also tried getting the package manually from Launchpad.net and I got the same error. Is there any other place where I can download the packages without them being corrupted or issuing read errors ?

 Or then again, is there another manager similar to Envy that might not have issues with its packages ?

---

### Post by elcid89 on 2008-08-09
> **BogdanV said:**
> Okay, I've installed Envy and unfortunately, I got an package error. Judging from the terminal log, it seems that package "xorg-driver-fglrx-envy_ [...] i386.deb" triggered an read error. I tried getting the file from Synaptic and it gave me an install error related to the same issue.
 I also tried getting the package manually from Launchpad.net and I got the same error. Is there any other place where I can download the packages without them being corrupted or issuing read errors ?

 Or then again, is there another manager similar to Envy that might not have issues with its packages ?

What version of Ubuntu are you running?

---

### Post by BogdanV on 2008-08-09
Hardy Heron, the latest found on the Ubuntu site. I didn't had any problems installing and opening Envy, just the packages seemed to have problems.

---

### Post by elcid89 on 2008-08-09
> **BogdanV said:**
> Hardy Heron, the latest found on the Ubuntu site. I didn't had any problems installing and opening Envy, just the packages seemed to have problems.

EnvyNG-gtk is the correct version for your situation then. I was worried that you were downlevel and I'd inadvertently directed you to the wrong resource. 

You might want to read through Alberto's FAQ - he wrote the thing, so his steps might be addressing a necessary step which I'm failing to include above. 

Give this a readthrough:

[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

### Post by elcid89 on 2008-08-09
> **BogdanV said:**
> Hardy Heron, the latest found on the Ubuntu site. I didn't had any problems installing and opening Envy, just the packages seemed to have problems.

Also, if possible, it might be helpful to copy the contents of the install dialogue for EnvyNG from the terminal window here. One of the more knowledgeable readers might spot something that's happening in there in a few seconds that could save you hours of frustration.

---

### Post by elcid89 on 2008-08-09
To actually answer your last question, however ... (sorry about that), there are about a gazillion mirrors you can download it from. Check here:

[http://packages.ubuntu.com/hardy-updates/i386/xorg-driver-fglrx-envy/download](http://packages.ubuntu.com/hardy-updates/i386/xorg-driver-fglrx-envy/download)

---

### Post by BogdanV on 2008-08-09
Thank you a lot for your continuous help!
  Anyway, about posting the install log, it seems that Envy doesn't let me copy the text from its terminal screen so I made a screen capture of the window and attached it to this post. Sorry if its going to be a pain for the eyes to read through the lines of text.

 In the meantime, I'll try and install the packages manually using the mirrors you provided.

---

### Post by elcid89 on 2008-08-09
> **BogdanV said:**
> Thank you a lot for your continuous help!
  Anyway, about posting the install log, it seems that Envy doesn't let me copy the text from its terminal screen so I made a screen capture of the window and attached it to this post. Sorry if its going to be a pain for the eyes to read through the lines of text.

 In the meantime, I'll try and install the packages manually using the mirrors you provided.

No problem. I fought with fglrx for days to get it working. It can be frustrating. 

I believe that Alberto is also pretty good about answering questions posed to him on his website. Since he's the developer of the app, if nothing else gives you joy, I'd suggest bouncing your problem off of him as well. If anybody knows how to solve it, he probably does.

Good luck!

---

### Post by BogdanV on 2008-08-09
I shall try to mail him. Anyway, I managed to make Envy work and install the fglrx driver. The bad part to this is that the reboot ended in a black screen + system freeze after system load.
 Another option would be to recycle my X1300 and with the money buy an nVidia card (but this won't be happening too soon).

---

### Post by elcid89 on 2008-08-09
> **BogdanV said:**
> I shall try to mail him. Anyway, I managed to make Envy work and install the fglrx driver. The bad part to this is that the reboot ended in a black screen + system freeze after system load.
 Another option would be to recycle my X1300 and with the money buy an nVidia card (but this won't be happening too soon).

He's probably the guy to be asking then. Did you get any notification about "input signal out of range" when GDM started?

As far as I know, the X1300 is supported. I have an HD 2400, which I believe is a newer chipset, and it is, so I'd think that yours would be as well. 

He's the go to guy though. I'd ask him before groping around in the dark with me any longer. I'm a novice who's still learning myself, he's da man. :-D

---

### Post by BogdanV on 2008-08-09
No. My monitor didn't even "sketch" a sign (power LED still green, no short "Entering Sleep Mode" message and definitely no "out of range" signal).
 It seems that some process/es really hate reading the line "Driver fglrx" in Xorg.conf .
 Well, I'll just have to hope that Mr. Milone will receive and reply to my mail.

 Ehh... at least I can play "Pingus" :)

---

