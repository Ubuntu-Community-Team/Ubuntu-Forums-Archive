---
title: "Webcam (using gspca) and TV Tuner (using em28xx) will not work together"
date: 2008-09-01
forum: Multimedia Software
---

### Post by keplerspeed on 2008-09-01
Hi,

I have be working with this issue for a while now. I can get my logitech webcam working fine using this tutorial:

[http://ubuntuforums.org/showthread.php?t=651375](http://ubuntuforums.org/showthread.php?t=651375)

And I can get my Pinnacle tv tuner working using this:

[http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices)

BUT the probem starts when I have the webcam working, then install the em28xx driver for my tv tuner. By installing the tv tuner driver the webcam will not work. it is still visible with lsusb:

Bus 002 Device 003: ID eb1a:2870 eMPIA Technology, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:092f Logitech, Inc. QuickCam express Plus
Bus 001 Device 001: ID 0000:0000  

but dmesg:

[  882.942729] gspca_main: Unknown symbol video_register_device
[  882.947315] gspca_spca561: Unknown symbol gspca_frame_add
[  882.947356] gspca_spca561: Unknown symbol gspca_debug
[  882.947461] gspca_spca561: Unknown symbol gspca_disconnect
[  882.947497] gspca_spca561: Unknown symbol gspca_resume
[  882.947533] gspca_spca561: Unknown symbol gspca_dev_probe
[  882.947568] gspca_spca561: Unknown symbol gspca_suspend

to get the webcam working again i have to reinstall the linux-image-`uname -r`, and reboot. after that i can sudo modprobe gspca, and the cam works, but now the tv tuner doesnt work. It has a similar dmesg output as above. And a simialr process to get the tv tuner working again.

So as far as i can work out there is some issue between the gspca driver and the em28xx driver. Also, v4l, video 4 linux is related, I dont know enough about this to know whats going on.

Solutions have been found, at:

[https://answers.launchpad.net/ubuntu/+question/21889](https://answers.launchpad.net/ubuntu/+question/21889)
[http://gkiagia.freehostia.com/2008/02/09/installing-avermedia-m115-drivers-on-ubuntudebian/](http://gkiagia.freehostia.com/2008/02/09/installing-avermedia-m115-drivers-on-ubuntudebian/)

I have tried these but by trying to recompile the kernel with the v4l module, my graphics driver was experiencing issues, I had no graphics, and still a webcam/tv tuner conflict. this is the only thing my ubuntu system does not do that win* will, and that annoys me.

Even if some cant help me, can someone explain a bit about modules, drivers, the v4l tree if they know about it, and how all that works with the kernel?

Also I have found this, which explains a few things but doesnt all make sense to me:

[http://mcentral.de/pipermail/em28xx/2007-August/000722.html](http://mcentral.de/pipermail/em28xx/2007-August/000722.html)


Cheers

---

### Post by keplerspeed on 2008-09-02
I dont like this bumping business.... but anyway. Bump

---

### Post by keplerspeed on 2008-09-21
Currently I have zero progress with this issue.... though after some reading apparently Markus Rechberger, who wrote the v41 driver (a deduction I have made lol) and he is apparently developing a new driver without these issues. So Ill just sit and wait!

---

### Post by keplerspeed on 2008-09-25
Im sure I cant be the only one that wants to use both a webcam and tv tuner..... hm. well if anyone is following my quest: 

[http://mcentral.de/pipermail/em28xx/2007-June/000547.html](http://mcentral.de/pipermail/em28xx/2007-June/000547.html)

So a solution. Its painfully painful though. maybe ill give it a go. if it works, u will hear about it!

Sneek.

---

### Post by keplerspeed on 2008-10-12
I have found a better tutorial for installing the firmware and driver for a PCTV tv tuner:

[http://www.zimbio.com/Ubuntu+Linux/articles/151/Ubuntu+And+Pinnacle+PCTV+HD](http://www.zimbio.com/Ubuntu+Linux/articles/151/Ubuntu+And+Pinnacle+PCTV+HD)

Very similar, but seems easier.

---

### Post by piratebill on 2008-11-07
I too am having the same issue.  Did you get it fixed?

---

### Post by keplerspeed on 2008-11-08
No, no fix yet... been busy, but when I get a chance I will try gkiagia's solution, by compiling a vanilla kernel. Ill keep you posted.

---

### Post by cariboo on 2008-11-08
I have sort of the same problem, the web cam takes over video0 until I set the options for my TV tuner card, to use TV TIme I have to edit the TV time configuration file to use video1, then after a the first reboot the Web cam reverts to video1 and the TV tuner card takes video0. I then of course have to reedit tvtime.conf to use video0. I know I could solve this problem by just rebooting and not editing the configuration file, but why reboot if you don't have to.

The moral of the story is check which video device youe web cam and tv tuner card are using and make sure the programs you are using are aware of which video device to use.

Jim

---

### Post by keplerspeed on 2008-11-27
Unfortunately I believe that my issue is driver related, when both drivers are installed only 1 can be loaded, and to load the other driver module I must remove the other driver module. Thanks.

---

### Post by kkady32 on 2008-11-27
i solved this problem for my webcam Z-Star Vimicro ZC0303 with install new libv4l from:[https://launchpad.net/~stemp/+archive](https://launchpad.net/~stemp/+archive)

---

### Post by keplerspeed on 2008-12-19
kkady32, can you give some more info how you used libv4l? with what tv tuner and what driver did you use with the tv tuner?

EDIT: I have solved this issue, simply with intrpeid ibex and the new kernel. I will post my exact method when I get a chance. Hooray!!! All is fixed! It only took 6 months!

---

### Post by keplerspeed on 2009-01-07
For me, I just followed this guide. Then it all worked!

[http://mtuxland.blogspot.com/2008/11/how-to-webcam-tv-tuner-at-same-time.html](http://mtuxland.blogspot.com/2008/11/how-to-webcam-tv-tuner-at-same-time.html)

Cheers to mtux land!

---

### Post by kkady32 on 2009-01-11
hy,now reinstall ubuntu 8.10 and i cannot make my webcam to work again :))
ubuntu 8.10 64 ,ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam,"AverTV Studio 303 (M126)tvtuner
i install the new v4l exactly how i say in another post and now cannot make to work

---

