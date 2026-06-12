---
title: "Logitech QuickCam Pro 5000 on 6.06 / installation of UVC driver"
date: 2006-08-22
forum: Multimedia &amp; Video
---

### Post by Fingolfin on 2006-08-22
Having unsuccessfully tried to install Logitech QuickCam Pro 5000 with spca5xx driver, I turned to uvc driver [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

As I reported in another thread ([http://www.ubuntuforums.org/showthread.php?t=239999)](http://www.ubuntuforums.org/showthread.php?t=239999)), I reached the stage when the spca5xx module was loaded but it didnt work and even disappeared from the kernel after the system has been rebooted (a bug?).

Now then, the developers of uvc did a great job and this driver should also work with several other webcams (check their web site for the list of supported models).

Before you begin, kernel headers and gcc compiler should be installed:

$ sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4

The source code of the current uvc driver is located at
[http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/](http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/)

After fetching the four files with
$ mkdir uvcdriver
$ cd uvcdriver

$ wget [http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/Makefile](http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/Makefile)

$ wget [http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/uvcvideo.c](http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/uvcvideo.c)

$ wget [http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/uvcvideo.h](http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/uvcvideo.h)

$ wget [http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/v4l2_enumfrmfmt.h](http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/v4l2_enumfrmfmt.h)

and compiling and installing the driver:

$ make
$ sudo make install

dmesg gives the following output:

$ dmesg | grep uvc 
[4294684.648000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c5)
[4294684.666000] usbcore: registered new driver uvcvideo

Starting Ekiga and going to the Menu/Edit/Pr eferences/Video Devices, Video plugin L4V2 should be selected and if everything went ok, something like USB VideClass Device will apear as the input video device.
Close the dialog and click on the small webcam icon in the main Ekiga window to activate your newly installed usb device. 
Happy chatting to all!

p.s. Uvc apears to be in development and for all who prefer the aforementioned spca5xx driver as more stable (wiser Ubuntu users will perhaps have more to say about this), detailed spca5xx installation guide has already been provided by Arnieboy: [http://www.ubuntuforums.org/showthre...gitech+usb+cam](http://www.ubuntuforums.org/showthre...gitech+usb+cam).

---

### Post by Zajjko on 2006-08-30
I've tried installing my Logitech QuickCam Pro 5000 using the UVC-drivers, but to no avail. No matter what capturing-software I try I get errors.

Ekiga tells me that the cam doesn't support the Pallettes Ekiga is trying to use.

amsn gives "error getting capabilities" upon choosing v4l-2 in webcam settings.

when $ dmesg | grep uvc , I get the following feedback:

[17179591.392000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c5)
[17179591.424000] usbcore: registered new driver uvcvideo
[17179718.428000] uvcvideo: Failed to query (130) UVC control 1 (unit 0) : -32.
[17179719.424000] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -32.
[17179721.960000] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110.
[17179723.200000] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110.
[17179724.912000] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110.
[17179726.112000] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110.
[17179813.496000] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110.
[17179860.848000] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110.
[17180718.680000] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110.
[17180720.552000] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110.


Would someone please advice?

Could it be that I have installed an older version of the UVC-driver earlier and it failed? How, in that case, do I uninstall the driver completely and start from the beginning?

[EDIT]
As if by magic, my cam has started working in Ekiga now. However, I have NO use whatsoever for Ekiga and my primary goal is to get it working in amsn. Anyone have any useful tips? [/EDIT]

---

### Post by DriftingDutchman on 2006-09-01
I have tried compiling and installing the UVC driver with gcc 4.0. The result in Ekiga as well as Kopete is the same: the LED on the top of camera is switched on, but I only see a black rectangle instead of video. I have tried compiling using gcc 3.4 as well, but the kernel is apparently compiled using gcc 4.0, resulting in an error message when using $dmesg | grep uvc. I also have xorg.conf configured to load v4l and selected Video plugin L4V2 in Ekiga.

$dmesg | grep uvc now gives
[17179598.404000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c5)
[17179598.428000] usbcore: registered new driver uvcvideo

Logitech QuickCam Pro 5000
I am using Ubuntu 6.06.1 (2.6.15-26-386 #1 PREEMPT), Logitech QuickCam Pro 5000
[B]
<EDIT>The camera now works more less (wrong colors/way too dark respectively) under Kopete and Ekiga after unplugging a Logitech USB joystick</EDIT>[/B]

Thanks!

---

### Post by Fe01 on 2006-09-10
also "by magic" I've go image in ekiga after reinstalling uvc (just repeated what I've done before) with my Logitech 08c3 (Notebooks Pro)

still here are the error msgs:

$ dmesg | grep uvc
[17179589.756000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c3)
[17179589.784000] usbcore: registered new driver uvcvideo
[17185036.012000] uvcvideo: Failed to query (1) UVC control 7 (unit 2) : -110.
[17185036.380000] uvcvideo: Failed to query (1) UVC control 2 (unit 2) : -110.

anyone knows what that is?

---

### Post by Bizmac on 2006-10-10
Perfect with a Logitech Quickcam Pro Notebook and Egika!!!!

Thank you Fingolfin....

---

### Post by verby on 2006-12-02
to those who have logitech notebook pro (08c3) ... did you get mic (build in web cam) to work as well?
I can see image in ekiga, but when i go to camorama i get:
"could not connect to video device (dev/videoO). Please check connection"
I'd like to use mic from my webcam to work under skype... but it doesn't work.

---

### Post by FingerPie on 2006-12-03
another request for anyone with 08c3 with sound.

---

### Post by wallacek on 2006-12-04
I also want to get my Logitech quickcam going. I use it in XP for Skype, need to have access to same in Ubuntu. I'm newbie enough that I haven't completely understood everything in this thread. If anyone knows what the problem is (why it's not being seen/heard; the Skype self-call test doesnt' record any sound at all), i can search for solutions here and elsewhere. thanks!
karinne (wallacek)

---

### Post by jiapei100 on 2006-12-07
I followed your staffs in my Ubuntu 6.06
version 2.6.15-27-386

The only result I could get so far is 

1) orginal settings without changing anything: 

/bin/sh: line 0: cd: /lib/modules/2.6.15-27-386/build: No such file or directory
make: *** [uvcvideo] Error 1


2) If I change in the Makefile :
KERNEL_DIR	:= /lib/modules/$(KERNEL_VERSION)/build
to 
KERNEL_DIR	:= /lib/modules/$(KERNEL_VERSION)/

I got the following:

make[1]: Entering directory `/lib/modules/2.6.15-27-386'
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-27-386'
make: *** [uvcvideo] Error 2

It seems I didn't install the source, so I installed it to /usr/src/linux-source-2.6.15/

What to do for the next??

Urgent to use Logitech 5000 Pro, please reply me at your earliest convenience.

cheers
JIA Pei

---

### Post by boulderbum on 2006-12-11
The instructions failed to mention actually loading the module after compiling.  I think that's why some people thought it wasn't working, then it 'magically' started working.  They probably rebooted in the interim...  hope that helps some people.

Edit: I just installed a new computer with the latest Dapper iso and v4l2 was already installed.  However, it still did NOT see the QuickCam Pro 5000.  Removing the package would require removing ubuntu-desktop... which did not please me.  However, compiling and reinstalling just as above, with a reboot, and the camera was working again,  This may be a bit brute-force-ish, to install a compiled module over top of a  package, but I can't argue with success.

Second Edit:  Ahhh... back to the drawing board.  It works for a bit, then bombs,

---

### Post by manu67 on 2006-12-29
I experienced problems with the Makefile (not finding the "modules" entry to compile the first "make").

Thanks to the spca5xx module I could find the missing bit in
the Makefile. Just add this line after the variable inits:

MODULE_INSTALLDIR = /lib/modules/$(KERNEL_VERSION)/kernel/drivers/usb/media/

After this it did compile alright and ... the QC Pro 5000 works !!

Thank you guys for your nice work.

---

### Post by Gouchi on 2006-12-30
Hi there,

just some update :

Logitech Quick Cam Pro 5000 works now with aMSN.
Just grab the last version of aMSN and UVC driver.

More information [here]("http://www.amsn-project.net/forums/viewtopic.php?p=13761#13761").

Works although with [Ekiga]("http://www.gnomemeeting.org/"), [luvcview]("http://mxhaard.free.fr/spca50x/Investigation/uvc/"), [ffmpeg]("http://article.gmane.org/gmane.linux.drivers.uvc.devel/503").

---

### Post by kopolov on 2007-07-30
Hi,
I jave a logitech quickcam pro 5000 and I wanted to thank you.
The HowTo worked out fine.

best regards,
hagai

---

### Post by gwanath on 2007-08-03
Thanks a lot...Logitech QuickCam pro for notebooks is working with aMSN...

Still Camorama can't detect it though...so I think I can't take snapshots for now..

---

### Post by gbolahr on 2007-08-19
hi guys,
i am trying to instal the logitech pro 5000 webcam on feisty.
after following a few of steps described here, this is what i got.

gbolahr@gbolahr-desktop:~$ sudo rmmod uvcvideo
gbolahr@gbolahr-desktop:~$ sudo modprobe uvcvideo trace=15
gbolahr@gbolahr-desktop:~$ dmesg | grep uvc 
[   16.950723] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08ce)
[   16.965980] usbcore: registered new interface driver uvcvideo
[21483.743529] usbcore: deregistering interface driver uvcvideo
[21508.192632] uvcvideo: Adding mapping Brightness to control 00000000-0000-0000-0000-000000000101/2.
[21508.192638] uvcvideo: Adding mapping Contrast to control 00000000-0000-0000-0000-000000000101/3.
[21508.192643] uvcvideo: Adding mapping Hue to control 00000000-0000-0000-0000-000000000101/6.
[21508.192647] uvcvideo: Adding mapping Saturation to control 00000000-0000-0000-0000-000000000101/7.
[21508.192651] uvcvideo: Adding mapping Sharpness to control 00000000-0000-0000-0000-000000000101/8.
[21508.192655] uvcvideo: Adding mapping Gamma to control 00000000-0000-0000-0000-000000000101/9.
[21508.192659] uvcvideo: Adding mapping Backlight Compensation to control 00000000-0000-0000-0000-000000000101/1.
[21508.192664] uvcvideo: Adding mapping Gain to control 00000000-0000-0000-0000-000000000101/4.
[21508.192668] uvcvideo: Adding mapping Power Line Frequency to control 00000000-0000-0000-0000-000000000101/5.
[21508.192673] uvcvideo: Adding mapping Hue, Auto to control 00000000-0000-0000-0000-000000000101/16.
[21508.192678] uvcvideo: Adding mapping Pan (relative) to control 63610682-5070-49ab-b8cc-b3855e8d2256/1.
[21508.192683] uvcvideo: Adding mapping Tilt (relative) to control 63610682-5070-49ab-b8cc-b3855e8d2256/1.
[21508.192688] uvcvideo: Adding mapping Pan/Tilt (reset) to control 63610682-5070-49ab-b8cc-b3855e8d2256/2.
[21508.192693] uvcvideo: Adding mapping Exposure, Auto to control 00000000-0000-0000-0000-000000000001/2.
[21508.192698] uvcvideo: Adding mapping Exposure (Absolute) to control 00000000-0000-0000-0000-000000000001/4.
[21508.192704] uvcvideo: Adding mapping White Balance Temperature, Auto to control 00000000-0000-0000-0000-000000000101/11.
[21508.192709] uvcvideo: Adding mapping White Balance Temperature to control 00000000-0000-0000-0000-000000000101/10.
[21508.192998] uvcvideo: Probing generic UVC device 2
[21508.193007] uvcvideo: Found format MJPEG.
[21508.193010] uvcvideo: - 160x120 (30.0 fps)
[21508.193013] uvcvideo: - 176x144 (30.0 fps)
[21508.193015] uvcvideo: - 320x240 (15.0 fps)
[21508.193018] uvcvideo: - 352x288 (15.0 fps)
[21508.193021] uvcvideo: - 640x480 (15.0 fps)
[21508.193024] uvcvideo: Found format Uncompressed.
[21508.193027] uvcvideo: - 160x120 (30.0 fps)
[21508.193029] uvcvideo: - 176x144 (30.0 fps)
[21508.193032] uvcvideo: - 320x240 (15.0 fps)
[21508.193034] uvcvideo: - 352x288 (15.0 fps)
[21508.193037] uvcvideo: - 640x480 (15.0 fps)
[21508.193044] uvcvideo: Found a Status endpoint (addr 87).
[21508.193048] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08ce)
[21508.193055] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/2 to device 2 entity 2
[21508.193060] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/3 to device 2 entity 2
[21508.193065] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/7 to device 2 entity 2
[21508.193070] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/8 to device 2 entity 2
[21508.193076] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/1 to device 2 entity 2
[21508.193080] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/4 to device 2 entity 2
[21508.193085] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/5 to device 2 entity 2
[21508.193092] uvcvideo: Added control 00000000-0000-0000-0000-000000000001/2 to device 2 entity 1
[21508.193096] uvcvideo: Added control 00000000-0000-0000-0000-000000000001/4 to device 2 entity 1
[21508.193101] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/11 to device 2 entity 2
[21508.193106] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/10 to device 2 entity 2
[21508.193110] uvcvideo: Scanning UVC chain: OT 5 (-> 12 8 10 11) <- Unit 4 (-> 13) <- Unit 3 <- Unit 2 <- IT 1
[21508.193123] uvcvideo: Found a valid video chain (1 -> 5).
[21508.207817] uvcvideo: UVC device initialized.
[21508.207832] usbcore: registered new interface driver uvcvideo
[21513.073255] usbcore: deregistering interface driver uvcvideo
[22119.282036] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08ce)
[22119.297131] usbcore: registered new interface driver uvcvideo
[22900.267396] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08ce)
[23683.370231] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -32 (exp. 26).
[23694.143491] uvcvideo: Failed to query (1) UVC control 2 (unit 0) : -32 (exp. 26).
[23694.737500] uvcvideo: Failed to query (131) UVC control 1 (unit 0) : -32 (exp. 26).
[23694.739371] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -32 (exp. 26).
[23695.041246] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[23695.344612] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[23695.647979] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[23695.951344] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[23696.254713] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[23696.558080] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[23696.861445] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[23804.657029] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[23804.960398] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[23805.263765] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[23818.755595] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[23819.058961] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[23819.362326] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[23928.431251] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[23928.734617] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[23929.037982] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[24670.124863] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[24848.985674] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[24849.964256] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[24850.263632] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[24850.563005] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[25159.779884] usbcore: deregistering interface driver uvcvideo
[25173.745378] uvcvideo: Adding mapping Brightness to control 00000000-0000-0000-0000-000000000101/2.
[25173.745386] uvcvideo: Adding mapping Contrast to control 00000000-0000-0000-0000-000000000101/3.
[25173.745390] uvcvideo: Adding mapping Hue to control 00000000-0000-0000-0000-000000000101/6.
[25173.745394] uvcvideo: Adding mapping Saturation to control 00000000-0000-0000-0000-000000000101/7.
[25173.745398] uvcvideo: Adding mapping Sharpness to control 00000000-0000-0000-0000-000000000101/8.
[25173.745402] uvcvideo: Adding mapping Gamma to control 00000000-0000-0000-0000-000000000101/9.
[25173.745423] uvcvideo: Adding mapping Backlight Compensation to control 00000000-0000-0000-0000-000000000101/1.
[25173.745436] uvcvideo: Adding mapping Gain to control 00000000-0000-0000-0000-000000000101/4.
[25173.745450] uvcvideo: Adding mapping Power Line Frequency to control 00000000-0000-0000-0000-000000000101/5.
[25173.745464] uvcvideo: Adding mapping Hue, Auto to control 00000000-0000-0000-0000-000000000101/16.
[25173.745478] uvcvideo: Adding mapping Pan (relative) to control 63610682-5070-49ab-b8cc-b3855e8d2256/1.
[25173.745490] uvcvideo: Adding mapping Tilt (relative) to control 63610682-5070-49ab-b8cc-b3855e8d2256/1.
[25173.745494] uvcvideo: Adding mapping Pan/Tilt (reset) to control 63610682-5070-49ab-b8cc-b3855e8d2256/2.
[25173.745499] uvcvideo: Adding mapping Exposure, Auto to control 00000000-0000-0000-0000-000000000001/2.
[25173.745511] uvcvideo: Adding mapping Exposure (Absolute) to control 00000000-0000-0000-0000-000000000001/4.
[25173.745516] uvcvideo: Adding mapping White Balance Temperature, Auto to control 00000000-0000-0000-0000-000000000101/11.
[25173.745558] uvcvideo: Adding mapping White Balance Temperature to control 00000000-0000-0000-0000-000000000101/10.
[25173.745923] uvcvideo: Probing generic UVC device 2
[25173.745932] uvcvideo: Found format MJPEG.
[25173.745935] uvcvideo: - 160x120 (30.0 fps)
[25173.745938] uvcvideo: - 176x144 (30.0 fps)
[25173.745941] uvcvideo: - 320x240 (15.0 fps)
[25173.745944] uvcvideo: - 352x288 (15.0 fps)
[25173.745947] uvcvideo: - 640x480 (15.0 fps)
[25173.745949] uvcvideo: Found format Uncompressed.
[25173.745952] uvcvideo: - 160x120 (30.0 fps)
[25173.745955] uvcvideo: - 176x144 (30.0 fps)
[25173.745957] uvcvideo: - 320x240 (15.0 fps)
[25173.745960] uvcvideo: - 352x288 (15.0 fps)
[25173.745963] uvcvideo: - 640x480 (15.0 fps)
[25173.745971] uvcvideo: Found a Status endpoint (addr 87).
[25173.745974] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08ce)
[25173.745982] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/2 to device 2 entity 2
[25173.745987] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/3 to device 2 entity 2
[25173.745992] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/7 to device 2 entity 2
[25173.745996] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/8 to device 2 entity 2
[25173.746002] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/1 to device 2 entity 2
[25173.746007] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/4 to device 2 entity 2
[25173.746011] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/5 to device 2 entity 2
[25173.746018] uvcvideo: Added control 00000000-0000-0000-0000-000000000001/2 to device 2 entity 1
[25173.746023] uvcvideo: Added control 00000000-0000-0000-0000-000000000001/4 to device 2 entity 1
[25173.746028] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/11 to device 2 entity 2
[25173.746033] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/10 to device 2 entity 2
[25173.746036] uvcvideo: Scanning UVC chain: OT 5 (-> 12 8 10 11) <- Unit 4 (-> 13) <- Unit 3 <- Unit 2 <- IT 1
[25173.746050] uvcvideo: Found a valid video chain (1 -> 5).
[25173.747422] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[25173.747428] uvcvideo: Failed to initialize the device (-5).
[25173.747448] usbcore: registered new interface driver uvcvideo
gbolahr@gbolahr-desktop:~$ 

i also get this error msg on ekiga...
Error while opening video device USB Video Class device

A moving logo will be transmitted during calls. Notice that you can always transmit a given image or the moving logo by choosing "Picture" as video plugin and "MovingLogo" or "StaticPicture" as device.

There was an error while opening the device. Please check your permissions and make sure that the appropriate driver is loaded.

pls help if you can.

thanks

---

### Post by gbolahr on 2007-08-19
my cam works guys....i guess i didnt wait for the settings to take effect. thanks for the sharing of info.... :)

---

### Post by Fingolfin on 2007-09-17
I didn't have much time recently to revisit these pages, and I can only hope that the problems some of you reported have disappeared in the meantime with more recent versions of Debian/Ubuntu installations.

My personal opinion is that the spca5xxx drivers should be given the first try (check the Arnieboy's thread dealing with their installation, many more users have reported that their webcams work fine with them).

Uvc drivers were, according to their authors, still in development at the time of writing and sometimes may work sometimes not. (I was like others, for example, unable to make Camorama working with my QuickCamPro 5000, but uvc drivers served me fine for Ekiga calls.)

I hope that the procedure will be of (some) help to many users.
Thanks extended to Boulderbum, Manu67 and all others for their valuable comments.

---

