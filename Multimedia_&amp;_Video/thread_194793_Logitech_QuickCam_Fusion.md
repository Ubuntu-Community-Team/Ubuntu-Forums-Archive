---
title: "Logitech QuickCam Fusion"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by samotano on 2006-06-11
I'm trying to make my Logitech QuickCam Fusion webcam work.  I've looked in the forums but have not had any luck finding help.  Has anyone been able to install this camera in Ubuntu?
thx
s.

---

### Post by mscman on 2006-06-11
Depends on what functionality you want with it.  You'll have to install the UVC drivers for it.  Those can be found [HERE]("http://developer.berlios.de/projects/linux-uvc").  To compile them, you'll need to install the linux headers for your kernel.
NOTE: These drivers require kernel 2.6.x to compile.  If you're using Dapper you'll be fine, but I'm not sure what kernel Breezy uses; you may have to recompile the kernel or upgrade to Dapper.  If you need any help let me know.

---

### Post by samotano on 2006-06-11
Thanks for the quick reply, mscman!
Actually, I need lots of help since I'm quite a beginner....
I'm using Dapper and would only need basic functionality for the webcam (i.e. basic camera + mic).  As a matter of fact I just came a cross the website you mention, but I have no clue of what to do.
Any "idiot proof" help wouuld be great :-)
S.

[QUOTE=mscman]Depends on what functionality you want with it.  You'll have to install the UVC drivers for it.  Those can be found [HERE]("http://developer.berlios.de/projects/linux-uvc").  To compile them, you'll need to install the linux headers for your kernel.
NOTE: These drivers require kernel 2.6.x to compile.  If you're using Dapper you'll be fine, but I'm not sure what kernel Breezy uses; you may have to recompile the kernel or upgrade to Dapper.  If you need any help let me know.[/QUOTE]

---

### Post by mscman on 2006-06-12
Well, I'll try to "idiot-proof" this as much as possible.  I'm not sure how well the mic works with this, you may end up having to use a separate microphone.  For more info you may want to read the documentation on the BerliOS page.  Now for the fun part!

To start with, we're going to need some build tools for you to be able to compile.  Go ahead and open a terminal and issue the command:
```
sudo apt-get install build-essential
```

This will get you gcc, make, and all of the tools necessary to build this file.  You'll also want to get the linux headers for your kernel.  To find out what kernel you're using, type:

```
uname -r
```  
Once you have that, you can get the headers by typing:

```
sudo apt-get install linux-headers-<kernel type>
``` 

For example, if you're using a 386 kernel, type: 

```
sudo apt-get install linux-headers-386
```

Now that we have our basic tools, we'll need the actual source code for the drivers.  Head over to the Berlios link from the above post and scroll down to the bottom of the page.  Normally to get the files from SVN Repositories, we could use svn checkout.  Unfortunately, the BerliOS site doesn't accept my attempts to connect to the repositories, so I'll tell you how to get them via the web interface (even though it's a little more of a hassle...)  Click on the link that says "Browse SVN with HTTP."  Then you'll want to click on "linux-uvc" and then click on "trunk."  You may want to create a folder in your home directory to save these files in.  (I called mine "UVC")  Right click on each of the files listed (Makefile, uvcvideo.c, and uvcvideo.h) and click "save link as..."  Then move to the directory you want to save them in.

***NOTE***:  Make sure that the file "Makefile" is saved without a '.htm' tag at the end.  Firefox adds this extension by default, but make sure to delete it before you click save!!! (END NOTE)

Now that that annoying process is over with, we can finally compile the driver.  Assuming your folder is named UVC and is in your home directory, launch a terminal and type:
```
cd UVC
```

To make sure the files are there, type:
```
ls
```

Now we build it by typing:
```
make
```

And finally we install it with:
```
sudo make install
```

Hopefully, if all goes well, you should have the UVC drivers installed and working.  To test this, plug your camera in and type
```
dmesg
``` in a terminal.  You should see something like "UVC video class device" or something of that nature in the printout.

Let me know if you have any problems! :D

---

### Post by samotano on 2006-06-13
Wow!!! Thank you for the detailed instructions, can't wait to try it (not home right now).  BTW the mic part works already, so it's just a matter of making the camera part work now.
I will let u know how it goes.

---

### Post by samotano on 2006-06-13
Not much luck :-(
I followed the instructions and everything went smooth (no errors). However, when i type dmesg I don't see any video device.  Also tried to check Ekiga (gnomemeeting) but did not show any video device. What should I do?

---

### Post by mscman on 2006-06-19
Hmm...  I wonder why it isn't recognizing the device.  Perhaps you could try downloading another tool designed to work with UVC devices, just to test if it's working correctly.  If you visit [http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20060207.tar.gz]("http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20060207.tar.gz"), you will be able to download the source code for luvcview, a simple program for viewing and capturing from UVC devices.  If you need help compiling let me know.  Sorry for the late reply!  I've been a little busy...

---

### Post by xtaski on 2006-06-25
I'm having the exact same issue. I installed the module and it shows up in dmesg... but Ekiga won't see the device and that utility you pointed me to won't compile - looks like some coding errors... :-? 

Does anyone actually have this working? What software tools allow you to get the device started?

---

### Post by AltoMelto on 2006-06-26
Yes, i have the logitech fusion working

just follow the procedure outlined here and then install the kernel module. If make and make install are successful, then to install the kernel module you shoud type modprobe uvcvideo

I have the video working, does anyone know if it's possibile to have the mic working too?

---

### Post by mscman on 2006-06-26
> **xtaski]Does anyone actually have this working? What software tools allow you to get the device started?[/QUOTE]
I DO actually have it working said:**
> If make and make install are successful, then to install the kernel module you shoud type modprobe uvcvideo
I guess the machine I used loaded the module automatically when I inserted the device.  Modprobe uvcvideo should do the trick though.

The OP of this thread says he already has the mic working, perhaps he can lend some advice on what that took.

---

### Post by AltoMelto on 2006-06-28
Obviously I didn't get any help, he solved his problem and run away, anyways I managed to solve it on my own, the problem was that the kernel update to subversion -25 didn't have the module for the usb audio, on top of some other modules i wanted, so i yust fell back to -23, and living happily ever after!

---

### Post by mcewanbr on 2006-08-24
well, followed your instructions here (thanks!), but no dice.

No errors, but my logitech quickcam fusion still isn't functional.  Not sure what logs you would like to see, however I would be happy to give you whatever info you need to aid me in this!

Thanks in advance!

Brenden

---

### Post by godtvisken on 2006-12-28
I have just followed the exact same steps, compiling the UVC drivers from the linux-uvc.berlios.de site, and dmesg reported:

```
[17226885.972000] usb 4-6: new high speed USB device using ehci_hcd and address 5
[17226886.244000] usb 4-6: configuration #1 chosen from 1 choice
[17226886.392000] Linux video capture interface: v1.00
[17226886.396000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08ca)
[17226886.452000] usbcore: registered new driver uvcvideo
[17226886.452000] USB Video Class driver (v0.1.0)
```

It seems to detect when I press the button on the device:

```
[17226913.344000] uvcvideo: Button event (1).
[17226913.696000] uvcvideo: Button event (0).
```

Here's what happens when I try to run camorama:

```
[17228066.292000] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[17228066.592000] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
```

And camorama itself reports:

```
Could not connect to video device (/dev/video0)
```

Well, any advice? :neutral:

---

### Post by godtvisken on 2006-12-28
Bump ](*,)

---

### Post by longinus on 2006-12-28
I got mine to work, thanks!!

After I did the make/make install, I used a sudo modprobe uvcvideo (don't know why, but at first, without the sudo, it gave some errors).

Then I went to Ekiga, and played with the video settings a little.. At first it didn't work, I had to choose VRL2 on the video devices, and the 'USB video class device' (and set the format to Auto I think). Then it started working.

Just a quick question... I can't get any other program to use it (camorama, etc). Is there a way to make them use uvc? Or any other software that uses it? Just to capture still frames and video..
**EDIT: **Nevermind... I just saw mscman link to luvcview (to compile, just add the package libsdl-dev, and do a make/make install), and it works!

Thanks!

---

### Post by FlashOmega on 2006-12-29
I am in the same boat with mine.... detects the button and all that jazz but just refuses to work... the closest I get is if I try an amsn webcam conversation the blue light on my cam blinks and then the person can see a white box

Anyone got an idea?
again that was the logitech fusion (unless I am mis posting)

---

### Post by longinus on 2006-12-30
> **FlashOmega said:**
> I am in the same boat with mine.... detects the button and all that jazz but just refuses to work... the closest I get is if I try an amsn webcam conversation the blue light on my cam blinks and then the person can see a white box

Did you try it on Ekiga? There I'm sure it should work (on amsn I didn't try).

---

### Post by FlashOmega on 2006-12-31
Well can anyone help me get it working in amsn or another msn client... ekiga serves me no purpose... and it crashes when autodetecting my NAT so i cant try anyway

---

### Post by [Jen0] on 2007-01-09
Hi there,

I got the same problem. Have you found any solution?

Thanks,

J.

---

### Post by FlashOmega on 2007-01-12
I have no unfortunatly.... nobody else seems to know what to do either... lol or they are all gone off enjoying their webcams

---

### Post by mscman on 2007-01-22
> **FlashOmega said:**
> I have no unfortunatly.... nobody else seems to know what to do either... lol or they are all gone off enjoying their webcams

Sorry guys, I haven't checked my e-mail in awhile and I didn't realize this thread had been updated.

Unfortunately, I don't have much advice for you. I don't use the webcams for video chat. Instead we use it in our lab for monitoring who's in the lab. The cameras take a picture every minute and upload to a webserver. We use a program called fswebcam to accomplish this.

What errors are you encountering when you try to connect?

---

### Post by Peter Howard on 2007-02-05
> **AltoMelto said:**
> Obviously I didn't get any help, he solved his problem and run away, anyways I managed to solve it on my own, the problem was that the kernel update to subversion -25 didn't have the module for the usb audio, on top of some other modules i wanted, so i yust fell back to -23, and living happily ever after!

Did you have to do anything special to get the microphone working once it was detected?  My system is picking it up as a usb-audio device (and another usb-audio device is working fine), I've un-muted it and bumped up the gain in alsamixer, but no sound seems to be going into the system.  :(

---

### Post by andersja on 2007-03-30
I get it working in ekiga (only) using the reciepe above, 

suggest you report any bugs / feature requests on launchpag, e.g.:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/77456](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/77456)

---

### Post by Thiesen on 2007-04-09
Weeeee... my Logitech Fusion now not only works in Windows... it works in Ubuntu Feisty Fawn too... ty very much for that very easy guide... nemas problemas to compile and install that driver... and the camera is actually FASTER than it is in Windows...

Only thing is that Ekiga seems to loose the connection with the camera once in a while and no other application (Camorama nor Camstream) knows of it...

caminfo gives this:

```

$ caminfo
CVideoDeviceInput: Warning: no channel info available.
Detected 1 Video4Linux devices.
Device node      : /dev/video0
Name of device   : "USB Video Class device"
Minimum size     : 48x32
Current size     : 0x0
Maximum size     : 960x720
Video inputs     : 1
 Input 0
  Name             : "(null)"
  Type             : Unknown
  Audio            : no
  Tuners           : 0
Audio inputs     : 0

```


And dmesg gives alot of errors but it eventually seems to find the cam...

---

### Post by rahulthewall3000 on 2007-04-17
Yea,, it is the same for me, the webcam only works in Ekiga, but as I do not use that software, it is really useless for me, so I do not know what to do. The webcam microphone works fine with this methd though, and that is also good as I can make voice calls with Skype.
If anyone is aware of an application to record video, that would be awesome!

If you have any ideas, share!

Cheers
Rahul Jain
&#2352;&#2366;&#2361;&#2369;&#2354; &#2332;&#2376;&#2344;

---

### Post by stickperson on 2007-05-22
Ok, so does anyone have an update on how to get this working in amsn?

---

### Post by alfredska on 2007-05-29
For those interested in checking out the Berlios drivers via svn (not through html), the svn address the page provides is slightly incorrect.  For annonymous svn checkout, try this:
```
svn checkout http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk
```

---

### Post by MFulgo on 2007-06-14
I had the same problems running Feisty.  

After installing the v4l2 package (libpt-plugins-v4l2) and switching ekiga's preferences from v4l to v4l2, it worked.

Now to get it working in Kopete...  =o/

---

### Post by astralboy79 on 2007-07-04
hi guys my logitech quick cam is also not working despite following the steps provided. i finally found out the reason is because it is not detected as a usb device. when i plug the cam in the usb and start ubuntu it will take a long time for the mouse and keyb to be responsive during startup. on removing the cam, there is no such problem during startup. on trying to plug it in while the system is already running cause the lsusb to be non responsive for a while. in anycase it is not detected.  

I am running Ubuntu 6.06.1 LTS dapper on an amd64 4800 dual code proc & my mboard is dfi lanpart ultra nf4. here is what lsusb shows me
Bus 002 Device 003: ID 046d:c041 Logitech, Inc.
Bus 002 Device 002: ID 1267:0103 Logic3 / SpectraVideo plc
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

the first device is my logitech gaming mouse and the second one is my i-rocks usb keyboard. the logitech quick cam as you can see is no where to be found. :(

and here is what dmesg says after plugging in the logitech quick cam fusion usb
[   97.674766] usbcore: registered new driver usbhid
[   97.674769] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   97.730076] Bluetooth: RFCOMM socket layer initialized
[   97.730091] Bluetooth: RFCOMM TTY layer initialized
[   97.730092] Bluetooth: RFCOMM ver 1.7
[   97.752616] ts: Compaq touchscreen protocol output
[  126.143348] Linux video capture interface: v1.00
[  126.152074] usbcore: registered new driver uvcvideo
[  126.152078] USB Video Class driver (v0.1.0)
[  533.037567] usb 1-5: new high speed USB device using ehci_hcd and address 8
[  534.332104] usb 1-5: device descriptor read/64, error -110
[  540.661697] usb 1-5: device descriptor read/64, error -110
[  540.751547] usb 1-5: new high speed USB device using ehci_hcd and address 9
[  542.046085] usb 1-5: device descriptor read/64, error -110
[  548.375677] usb 1-5: device descriptor read/64, error -110
[  548.468855] usb 1-5: new high speed USB device using ehci_hcd and address 10
[  550.560437] usb 1-5: device descriptor read/8, error -110
[  552.690284] usb 1-5: device descriptor read/8, error -110
[  552.780096] usb 1-5: new high speed USB device using ehci_hcd and address 11
[  554.868386] usb 1-5: device descriptor read/8, error -110
[  556.998182] usb 1-5: device descriptor read/8, error -110

---

### Post by happyxix on 2007-07-04
Is this only for the fusion or any of logitech's webcams?

---

### Post by keithrennie on 2007-09-15
Just wanted to say a great big thanks to you guys on this thread, I was mostly participating on another thread on webcams started by gatman3, spent many days doing much research, but your thread provided the key advice.  - for me it was getting logitech QC fusion working on feisty kubuntu, and the v4l2 plugin on Ekiga finally got the webcam to go.

The webcam information is very scattered, some of the best stuff is in French, and no this should not be just about fusion.  I am not an expert, more a seasoned tinkerer, but I will do my bit by posting on both threads, hopefully in not more than a week, the list of the most useful websites, threads etc.  Some of the better stuff is actually in French, (they cope reluctantly with English and the swiss site is also well maintained in French, German and italian, and I will post these too.  If anybody wants help with translation, I'll try to find time if it is really relevant but a lot of the stuff is self evident.

---

### Post by keithrennie on 2007-09-21
Here are some useful webcam driver sites


1.  Ubuntu websites and threads

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
Ubuntu community documentation on installing webcam drivers, software and troubleshooting.  Written for Edgy, needs to be updated.

[https://help.ubuntu.com/community/InstallingLogitechQuickcamPro5000OnEdgy](https://help.ubuntu.com/community/InstallingLogitechQuickcamPro5000OnEdgy)
Ubuntu community documentation on installing Logitech Quickcam Pro 5000 on Edgy. 

[http://ubuntuforums.org/showthread.php?t=53755&highlight=quickcam+driver](http://ubuntuforums.org/showthread.php?t=53755&highlight=quickcam+driver) 
Ubuntu tutorial on how to install qc-usb driver.

[https://help.ubuntu.com/community/Ov51x](https://help.ubuntu.com/community/Ov51x)
Ubuntu community documentation on Ov51x driver

Some helpful forum threads on getting webcams to work, some have more links
[http://ubuntuforums.org/showthread.php?t=194793](http://ubuntuforums.org/showthread.php?t=194793)
31 postings, June 2006 &#8211; September 2007
[http://ubuntuforums.org/showthread.php?t=321862](http://ubuntuforums.org/showthread.php?t=321862)
15 postings, December 2006 &#8211; June 2006
[http://ubuntuforums.org/showthread.php?t=194793](http://ubuntuforums.org/showthread.php?t=194793)
37 postings, August &#8211; September 2007
[http://ubuntuforums.org/showthread.php?t=551231](http://ubuntuforums.org/showthread.php?t=551231)
5 posts, September 2007.  Smplayer media repository

2.  Some other sites, drivers and repositories

[http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)
The Linux qc-usb project originally developed a driver for the Logitech Quickcam Express, but now has expanded to other models.  
&#8220;The current version of the qc-usb driver is 0.6.5. This release fixes a compilation problem on kernel version 2.6.18 (and probably on 2.6.17, too)
The site has a list of cameras known to work with this driver, another list of cameras know not to work. However, more complete listings of webcams and drivers are available.

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)
USB Video Class (UVC) drivers, focusing on webcams - V4l2 driver

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
Probably the authoritative site for cameras, ID codes, drivers, regularly updated
[http://www.saillard.org/linux/pwc/](http://www.saillard.org/linux/pwc/)
Philips USB webcam driver for Linux

---

### Post by bazkit on 2007-09-24
Hi, I followed your advice on installing the Logitech QuickCam Fusion and I also cannot get the webcam to work.

Upon typing dmesg I find the line:
[B]
[ 2819.985603] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08ca)[/B]

but camorama does not recognise any webcam device. I'm a newbie to Ubuntu and I'm running 7.04 Feisty Fawn.

Thank you.

---

### Post by priegog on 2007-11-07
Problem:
```

jerry@jerry-laptop:~/UVC$ make
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
make[2]: *** No rule to make target `/home/jerry/UVC/uvc_driver.o', needed by `/home/jerry/UVC/uvcvideo.o'.  Stop.
make[1]: *** [_module_/home/jerry/UVC] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [uvcvideo] Error 2

```

Help please...
And you might start to get a lot of these questions again because skype for linux just launched a beta with video. Before this, I had no incentive to get my webcam to work... 
Anyways, any ideas?

Edit: I'm using gutsy, maybe this has something to do with it? I didn't think so either. but I'll be glad to supply any information you need to make this work.

---

### Post by vinzan on 2008-01-14
I would love to know how the OP made his/her mic working too !!!!!

---

### Post by psycardis on 2008-04-27
Ok, last night I had both working fine, I read somewhere that if the mic doesn't get initialized first it won't work. how do I change how it initializes the modules for the cam, or, how do I make it not initialize the mic?

This is what I get when I run dmesg:

[  949.884706] usb 2-6: new high speed USB device using ehci_hcd and address 5
[  950.193097] usb 2-6: configuration #1 chosen from 1 choice
[  950.262746] Linux video capture interface: v2.00
[  950.281508] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c1)
[  951.277845] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -110 (exp. 26).
[  952.276211] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -110 (exp. 26).
[  952.276217] uvcvideo: Failed to initialize the device (-5).
[  952.276266] usbcore: registered new interface driver uvcvideo
[  952.276270] USB Video Class driver (v0.1.0)
[  953.238642] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/usb/usbaudio.c:1289: 5:3:3: cannot set freq 16000 to ep 0x86
[  953.337967] usbcore: registered new interface driver snd-usb-audio
[ 1458.034693] usb 2-1: reset high speed USB device using ehci_hcd and address 2

---

### Post by valuntahr on 2008-06-12
I'm getting the same error message, From the looks of things it sees the webcam, but for some reason it can't communicate with it. Which is rather odd considering that the webcam's microphone works properly out of the box.

---

### Post by ericesque on 2008-07-15
I keep getting 

```
$ make
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/eric/UVC/uvc_driver.o
  LD [M]  /home/eric/UVC/uvcvideo.o
  Building modules, stage 2.
  MODPOST 1 modules
**WARNING: could not open /home/eric/UVC/version.h: Invalid argument**
  LD [M]  /home/eric/UVC/uvcvideo.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'

```

tried downloading the files again and running make again... no avail.  Any ideas?

---

