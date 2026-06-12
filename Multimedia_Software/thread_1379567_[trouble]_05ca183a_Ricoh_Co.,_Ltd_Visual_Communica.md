---
title: "[trouble] 05ca:183a Ricoh Co., Ltd Visual Communication Camera VGP-VCC7 [R5U870]"
date: 2010-01-12
forum: Multimedia Software
---

### Post by marbertone on 2010-01-12
Hello,
I have some troubles with my integrated webcam: it is a 05ca:183a Ricoh Co., Ltd Visual Communication Camera VGP-VCC7 [R5U870]
 on a sony vaio vgn-sz61xn. Yesterday I decided to switch to Linux :) and everything is perfect but my webcam, which has become very dark ... :/ instead on windows it was perfect! I use r5u870 drivers (not gspca). What should I do ?

Thanks
Mario Alberto

---

### Post by oooh on 2010-02-16
Same problem here !

I tried to tweak the driver code on brightness, but I it makes no difference. 

I suggest that we give a try to wxcam and gstfakevideo, they say they may work

---

### Post by no2498 on 2010-02-17
get programs cheese and wxcam if there settings dont work

open ekiga softphone an try its settings i have had to set its settings to 0 at times to get the others to work its hit an miss
hope this helps

---

### Post by marbertone on 2010-02-23
Hi guys,
I made it!
First, you have to install last repositories for uvcvideo from the site [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/), then you have to do 
```
sudo make menuconfig
```
and deselect [in my case] firedtv and piro radio (something like this, look that they are different objects, first one is in DBT or something like this, second one in 'radio codecs'), then do 
```
make
```
```
sudo make install
```
and then install ricoh camera drivers from [http://www.arakhne.org/ricoh/](http://www.arakhne.org/ricoh/)

I also suggest to install guvcview as a "Vaio Camera Utility". By doing this way video goes well, bright and most of all, Skype works! :KS

Tell me if you need more details, I will be more precise.
See you!

Mario Alberto :popcorn:

---

### Post by oooh on 2010-03-02
Hi there !

I have not tried the BERLIOS drivers yet, but I will.

So far I have tried:

- wxcam: it runs the camera well, but fails to control brightness or gamma, it tells me that v4l does not support brightness/gamma control

- v4lctl, v4l-conf: it tells me that the v4l does not support brightness control

So it seems that v4l does not support these changes in brighness. 

Question is: maybe it is a v4l problem, not a camera driver problem. In any case, do you know how to check the v4l logfile, to check for starting up problems in the module?

---

### Post by oooh on 2010-03-07
I changed to the r5870x driver and it goes perfect.

I highly recommend this one driver, you can find it in :

bitbucket.org/ahixon/r5u87x

Just follow the instructions in the web

Now I have brightness, saturation, contrast, control, and it works with cheese, skype, wxcam. I just needed to configure the config file of skype and update it to version 2.1.0.81.

Cheers

---

### Post by JanHJT on 2010-07-30
> **oooh said:**
> I changed to the r5870x driver and it goes perfect. To try this driver open a terminal and type

$ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
$ hg clone [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)
$ cd r5u87x
$ make
$ sudo make install
$ sudo r5u87x-loader --reload
	
The loader will automatically be run on boot when it detects your webcam.

My Logfile:```
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.628213] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183a)
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640293] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640543] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640603] uvcvideo: Failed to initialize the device (-5).
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640768] usbcore: registered new interface driver uvcvideo
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.641451] USB Video Class driver (v0.1.0)
```

related bugfile: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460290](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460290)

---

### Post by lunatico on 2010-08-01
> **JanHJT said:**
> 	
The loader will automatically be run on boot when it detects your webcam.

BIG THANKS! This works perfectly!

---

### Post by zazootheparrot on 2010-09-19
Thanks so much!!! It worked for me as well :)))))

---

Sony Vaio VGN-SZ740
Webcam: Motion Eye 05ca:183a Ricoh Co., Ltd Visual Communication Camera VGP-VCC7 [R5U870]
Operation System: Ubuntu 10.04 Lucid Lynx

---

### Post by THEHiTechRedneck on 2010-09-29
> **JanHJT said:**
> To try this driver open a terminal and type

$ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
$ hg clone [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)
$ cd r5u87x
$ make
$ sudo make install
$ sudo r5u87x-loader --reload
	
The loader will automatically be run on boot when it detects your webcam.

My Logfile:```
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.628213] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183a)
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640293] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640543] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640603] uvcvideo: Failed to initialize the device (-5).
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640768] usbcore: registered new interface driver uvcvideo
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.641451] USB Video Class driver (v0.1.0)
```

related bugfile: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460290](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460290)


Ok, got as far as the 'make' cmd and then got the following:
```


hitechredneck@hitechredneck-laptop:~/r5u87x$ make
cc -g -Wall -DHAVE_CONFIG_H -DUCODE_PATH=\"/usr/lib/r5u87x/ucode/r5u87x-%vid%-%pid%.fw\"  `pkg-config --cflags glib-2.0 libusb` -c loader.c loader.h
Package libusb was not found in the pkg-config search path.
Perhaps you should add the directory containing `libusb.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libusb' found
loader.c:28:18: error: glib.h: No such file or directory
loader.c:29:25: error: glib/gstdio.h: No such file or directory
loader.c:30:17: error: usb.h: No such file or directory
loader.c:41: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:45: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘force_clear’
loader.c:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘no_load’
loader.c:48: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:49: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘dump_ucode’
loader.c:50: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘reload’
loader.c:52: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘entries’
loader.c:77: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c: In function ‘find_device’:
loader.c:98: error: ‘gint’ undeclared (first use in this function)
loader.c:98: error: (Each undeclared identifier is reported only once
loader.c:98: error: for each function it appears in.)
loader.c:98: error: expected ‘;’ before ‘i’
loader.c:102: warning: implicit declaration of function ‘usb_get_busses’
loader.c:102: warning: assignment makes pointer from integer without a cast
loader.c:103: error: dereferencing pointer to incomplete type
loader.c:106: error: dereferencing pointer to incomplete type
loader.c:106: error: dereferencing pointer to incomplete type
loader.c:108: error: ‘i’ undeclared (first use in this function)
loader.c:109: error: dereferencing pointer to incomplete type
loader.c:110: error: dereferencing pointer to incomplete type
loader.c:111: error: dereferencing pointer to incomplete type
loader.c: At top level:
loader.c:128: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_image_flip’
loader.c:150: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_upload’
loader.c:232: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_status’
loader.c:249: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_version’
loader.c:268: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_enable’
loader.c:285: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_clear’
loader.c:306: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:320: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘load_firmware’
loader.c:436: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘main’
loader.h:21:18: error: glib.h: No such file or directory
make: *** [loader.o] Error 1

```

Halp!

btw, I'm running an Acer Aspire One D250 w/ Lucid Lynx (fresh install).

My problem is that Cheese won't record video correctly. It's jumpy, if it records at all.  

I need webcam recording to work at the same time as recordmydesktop (which is working perfectly, sound and all).

---

### Post by Charles07 on 2011-01-07
Thanks, [JanHJT]("http://ubuntuforums.org/member.php?u=1072005").

Worked perfectly.

---

### Post by Eric Aielli on 2011-01-23
> **JanHJT said:**
> To try this driver open a terminal and type

$ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
$ hg clone [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)
$ cd r5u87x
$ make
$ sudo make install
$ sudo r5u87x-loader --reload
	
The loader will automatically be run on boot when it detects your webcam.

My Logfile:```
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.628213] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183a)
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640293] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640543] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640603] uvcvideo: Failed to initialize the device (-5).
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640768] usbcore: registered new interface driver uvcvideo
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.641451] USB Video Class driver (v0.1.0)
```

related bugfile: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460290](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460290)
Thank you!  This worked perfect on my Vaio CR220E

---

### Post by grj23 on 2011-03-20
> **JanHJT said:**
> To try this driver open a terminal and type

$ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
$ hg clone [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)
$ cd r5u87x
$ make
$ sudo make install
$ sudo r5u87x-loader --reload
	
The loader will automatically be run on boot when it detects your webcam.

My Logfile:```
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.628213] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183a)
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640293] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640543] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640603] uvcvideo: Failed to initialize the device (-5).
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640768] usbcore: registered new interface driver uvcvideo
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.641451] USB Video Class driver (v0.1.0)
```

related bugfile: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460290](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460290)


Thanks very much!  This has got my camera working finally!  Only problem is that the picture looks red - almost like a negative, but maybe more like the blue is missing or something?  Is this a problem anyone else has come across or has any idea about?

---

### Post by parisseirios on 2011-04-17
> **JanHJT said:**
> To try this driver open a terminal and type

$ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
$ hg clone [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)
$ cd r5u87x
$ make
$ sudo make install
$ sudo r5u87x-loader --reload
    
The loader will automatically be run on boot when it detects your webcam.

My Logfile:```
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.628213] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183a)
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640293] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640543] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640603] uvcvideo: Failed to initialize the device (-5).
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.640768] usbcore: registered new interface driver uvcvideo
Jul 30 17:44:32 jan-vaio-vgn-tz31-vn kernel: [   33.641451] USB Video Class driver (v0.1.0)
```related bugfile: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460290](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460290)

THANKS MAN  I was looking for a solution for my SONY TZ SERiES with motion eye ricoh web camera .THANKS ALOT

---

### Post by adelani on 2011-07-06
Thanks it works with my laptop using Ubuntu 11.04 
for Sony Vaio VGN-FZ340E

I used
$ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
$ hg clone [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)
$ cd r5u87x
$ make
$ sudo make install
$ sudo r5u87x-loader --reload


Many Thanks

---

### Post by saerdnah on 2012-06-04
Worked perfectly for Ubuntu 12.04 LTS:
Machine: Sony Corporation VGN-TZ11XN_B/VAIO , BIOS R0052N7 07/11/2007
OS: Linux 3.2.0-24-generic-pae #39-Ubuntu SMP Mon May 21 18:54:21 UTC 2012 i686 i686 i386 GNU/Linux
Webcam: Ricoh Co., Ltd Visual Communication Camera VGP-VCC7 [R5U870]

I used exactly JanHJT's receipe:

[FONT=Courier New]sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
hg clone [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)
cd r5u87x
make
sudo make install
sudo r5u87x-loader --reload
[/FONT]
Thank you very much, JanHJT!
:KS:KS:KS:KS:KS

---

