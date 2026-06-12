---
title: "Webcam Problems"
date: 2012-02-04
forum: Multimedia Software
---

### Post by penguin25 on 2012-02-04
I just installed Ubuntu 11.10 alongside windows 7 on my Sony Vaio E series laptop.  VPCEB15FM.  Nothing is recognizing my webcam, cheese, skype ect.  I assume I need a driver but I dont know which one or where to get it.  Any help would be greatly appreciated.

Thanks

---

### Post by penguin25 on 2012-02-05
Bump

---

### Post by GhostOfTomJoad on 2012-02-05
Sony uses a MotionEye camera in all of the new VAIOs from what I understand.

The drivers for Debian are here.
[http://linuxappfinder.com/package/motioneye](http://linuxappfinder.com/package/motioneye)


Since Ubuntu is Debian based, they should work to get you running again.

---

### Post by dagroves on 2012-02-05
In order for me to get my webcam to work, I had to install 
```

sudo apt-get install v4l2ucp

```

---

### Post by penguin25 on 2012-02-05
> **GhostOfTomJoad said:**
> Sony uses a MotionEye camera in all of the new VAIOs from what I understand.

The drivers for Debian are here.
[http://linuxappfinder.com/package/motioneye](http://linuxappfinder.com/package/motioneye)


Since Ubuntu is Debian based, they should work to get you running again.

When I go to that link am I suppose to click install now?  When I do that my software center says there isnt a software package called motion eye in your current software sources.  I am pretty new to using ubuntu so if you wouldnt mind in being more specific in what I have to do that would be really helpful.

---

### Post by penguin25 on 2012-02-05
> **dagroves said:**
> In order for me to get my webcam to work, I had to install 
```

sudo apt-get install v4l2ucp

```

I put this code into the terminal and as far as I can tell it didnt do anything for me, is there something else I have to do in order for this to work?

---

### Post by dagroves on 2012-02-05
> **penguin25 said:**
> I put this code into the terminal and as far as I can tell it didnt do anything for me, is there something else I have to do in order for this to work?

Well did it install? If so, go to a terminal and type in 
```

sudo v4l2ucp

```

and configure it to work with whatever program you need. Keep it open to make the cam work, though it may not work with your cam... trial and error...

---

### Post by penguin25 on 2012-02-05
> **dagroves said:**
> Well did it install? If so, go to a terminal and type in 
```

sudo v4l2ucp

```and configure it to work with whatever program you need. Keep it open to make the cam work, though it may not work with your cam... trial and error...

When I type sudo v4l2ucp I get a box that pops up and it says

unable to open file /dev/video0 
No such file or directory

---

### Post by dagroves on 2012-02-06
> **penguin25 said:**
> When I type sudo v4l2ucp I get a box that pops up and it says

unable to open file /dev/video0 
No such file or directory

Is you cam plugged in?

---

### Post by penguin25 on 2012-02-06
> **dagroves said:**
> Is you cam plugged in?

My cam is built into my laptop, and as far as I can tell there are no function keys to turn it on or off.

---

### Post by penguin25 on 2012-02-09
Bump

---

### Post by GhostOfTomJoad on 2012-02-15
> **penguin25 said:**
> When I go to that link am I suppose to click install now?  When I do that my software center says there isnt a software package called motion eye in your current software sources.  I am pretty new to using ubuntu so if you wouldnt mind in being more specific in what I have to do that would be really helpful.

Sorry I've taken so long to respond.  Had some family stuff come up and forums have been the last thing on my mind.

I hope you've gotten your issue resolved by now but, just in case, when you click the link, you should see near the bottom of the page "Available deb Repositories."  Follow the instructions for adding their repository to apt-get.  Alternatively, there is an install now option.  I haven't used it but it's most likely a tarball that you can unpack locally on your machine.

---

### Post by GhostOfTomJoad on 2012-02-15
[http://popies.net/meye/](http://popies.net/meye/)

Found a direct link to download the tarball and install.  There's also instructions at the top of the page to which this link points about configuring the drivers to suit your needs.

---

### Post by penguin25 on 2012-02-16
> **GhostOfTomJoad said:**
> [http://popies.net/meye/](http://popies.net/meye/)

Found a direct link to download the tarball and install.  There's also instructions at the top of the page to which this link points about configuring the drivers to suit your needs.

Ok, so I have still not been able to get my camera to work.  I followed your link and extracted the file to my desktop, however after this I dont know what to do.  I read everything on that page and it really didnt make sense to me.  Once I have this file on my desktop: motioneye-1.3 what am I supposed to do?

Sorry for so many questions, just really want to get my camera working, and thanks for be so helpful up to this point!

---

### Post by GhostOfTomJoad on 2012-02-16
> **penguin25 said:**
> Ok, so I have still not been able to get my camera to work.  I followed your link and extracted the file to my desktop, however after this I dont know what to do.  I read everything on that page and it really didnt make sense to me.  Once I have this file on my desktop: motioneye-1.3 what am I supposed to do?

Sorry for so many questions, just really want to get my camera working, and thanks for be so helpful up to this point!

No need to apologize.  We like to help one another around here.  

I should have included this link.
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
It's the documentation from Cannonical on manually installing cameras and their drivers.  

Don't be intimidated by the wall of terminal commands.  They're all copy and paste.

---

### Post by penguin25 on 2012-02-17
> **GhostOfTomJoad said:**
> No need to apologize.  We like to help one another around here.  

I should have included this link.
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
It's the documentation from Cannonical on manually installing cameras and their drivers.  

Don't be intimidated by the wall of terminal commands.  They're all copy and paste.

Ok so I read through that whole page and tried the whole deal with installation of new drivers and still nothing.  I kept getting an error when ever I would tell it to sudo make install.  I was reading other forums and it said to check to see that my webcam is there by running lsusb.  I ran that and I didnt even see my webcam listed.  I think there must be something else holding me up besides just manually installing the driver.

And just so you know, I have this computer dual booted with windows 7 and the webcam works perfectly with windows 7 so it isnt a problem with the camera.

---

### Post by GhostOfTomJoad on 2012-02-17
> **penguin25 said:**
> Ok so I read through that whole page and tried the whole deal with installation of new drivers and still nothing.  I kept getting an error when ever I would tell it to sudo make install.  I was reading other forums and it said to check to see that my webcam is there by running lsusb.  I ran that and I didnt even see my webcam listed.  I think there must be something else holding me up besides just manually installing the driver.

And just so you know, I have this computer dual booted with windows 7 and the webcam works perfectly with windows 7 so it isnt a problem with the camera.


hhhhmmmmmmmm.  We run Linux almost exclusively at work.  I'll ask around and see if anyone else in IT has heard of such a problem.  Up until you said it works in your other partition I thought loose cable in the case but, since it works with Windows, I'll have to do some digging.

---

### Post by penguin25 on 2012-02-26
Bump

---

### Post by gordintoronto on 2012-02-26
> **penguin25 said:**
> I kept getting an error when ever I would tell it to sudo make install.

I was reading other forums and it said to check to see that my webcam is there by running lsusb.  I ran that and I didnt even see my webcam listed.

To solve the "make install" problem, you probably need to install "build-essential." If that's not it, please copy/paste the actual error message.

Please also copy/paste the output from lsusb.

---

### Post by penguin25 on 2012-03-01
ok so I installed build essential, and it didnt seem to make a difference, i continued to get the same errors

penguin@penguin-VPCEB15FM:~$ cd desktop
bash: cd: desktop: No such file or directory
penguin@penguin-VPCEB15FM:~$ cd Desktop
penguin@penguin-VPCEB15FM:~/Desktop$ cd motioneye-1.3
penguin@penguin-VPCEB15FM:~/Desktop/motioneye-1.3$ sudo make
[sudo] password for penguin: 
cc -Wall -Wstrict-prototypes -O2 -I/usr/X11R6/include -I/usr/src/linux/include -DWITH_X   -c -o motioneye.o motioneye.c
motioneye.c:36:28: fatal error: linux/videodev.h: No such file or directory
compilation terminated.
make: *** [motioneye.o] Error 1
penguin@penguin-VPCEB15FM:~/Desktop/motioneye-1.3$ make install
cc -Wall -Wstrict-prototypes -O2 -I/usr/X11R6/include -I/usr/src/linux/include -DWITH_X   -c -o motioneye.o motioneye.c
motioneye.c:36:28: fatal error: linux/videodev.h: No such file or directory
compilation terminated.
make: *** [motioneye.o] Error 1
penguin@penguin-VPCEB15FM:~/Desktop/motioneye-1.3$ 

and heres what I get when I run lsusb
penguin@penguin-VPCEB15FM:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse

hope this gives some insight to what my problem is

---

### Post by penguin25 on 2012-03-26
Still no luck in figuring this out, please help

---

### Post by BicyclerBoy on 2012-03-27
The compiling problem (use make without sudo) is caused by missing package
libv4l-dev or libv4l2-dev

If make completes without error then 
sudo make install

I don't think your webcam is a USB device..so it can not show with lsusb.
[http://www.popies.net/meye/2.6-meye.txt](http://www.popies.net/meye/2.6-meye.txt)

lspci

The above link suggests that the later models are not supported.

---

### Post by penguin25 on 2012-04-05
Ok so I had pretty much given up on figuring this out when all of a sudden my webcam started working.  It works in skype, cheese, everything works perfect.  Until I shut my computer down.  Then it no longer works.  If I suspend the computer, leave it overnight and come back the next morning it all works again.  This is very strange to me.  I was able to run lsusb though while the camera was working and I found out my camera is:

Bus 001 Device 010: ID 0c45:6409 Microdia Webcam

Dont know if anyone knows what is causing my camera to now have intermittent failure but any advice would be helpful.

Thanks

---

