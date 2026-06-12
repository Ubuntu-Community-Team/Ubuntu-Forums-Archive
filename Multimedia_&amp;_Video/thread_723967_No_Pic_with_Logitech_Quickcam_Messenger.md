---
title: "No Pic with Logitech Quickcam Messenger"
date: 2008-03-14
forum: Multimedia &amp; Video
---

### Post by iced.empire on 2008-03-14
Hi Folks...first Post..first little Problem...

I came from Fedora to Ubuntu...everything works fine.  But not my webcam.

So I now..that the Quickcam Messenger is supported by the current kernel out-of-the-box.

So I put the camera in...and I start Camorama...and nothing happens...only the programm shows some coloured lines in the pic window and than freezes.

Same problem with cheeze..but there is only a gray screen and a freeze. amsn shows me that he found a cam...but I only get a black screen..but fortunately no freeze!

So i try the qc-usb-source (as I know it from Fedora) and I have done an m-a prepare and so on...but nothing happend...afte reboot the same...

No pic at all.

Can anybody out there give me a hand?

---

### Post by linuxwizard on 2008-03-14
I would check and see if their is a newer version of the driver for your webcam and install it. Alot of the Logitech webcams do work out of the box.

---

### Post by swudee on 2008-03-15
I had that problem with Gutsy, but it worked with Kopete, except sound. I plan to install the beta of Hardy next week to see if it will work. Pulse audio that comes with Hardy may be a help.

---

### Post by iced.empire on 2008-03-16
I think there is the problem.

I use the driver which comes with the kernel...an there are freezes.

I use the qc out of the repos....freeze.

With Windows the cam works...so there is no prob with the cam.

And I know that the cam is working with the native kernel driver under debian, suse and sidux.

---

### Post by linuxwizard on 2008-03-17
Post the results of the command > lsusb

---

### Post by iced.empire on 2008-03-17
Nothing easier than this..

```
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 005: ID 057c:6201 AVM GmbH 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 001 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 046a:0101 Cherry GmbH 

```

---

### Post by linuxwizard on 2008-03-17
You might want to try this driver > [http://home.mag.cx/messenger/](http://home.mag.cx/messenger/)

---

### Post by iced.empire on 2008-03-18
Sorry I know this driver...and as I written in the first topic I already try it....because I know the driver from Fedora.

So..i take the qc-source out of the repos and and than m-a prepare and the other stuff. No problem Driver is compiling but after a modprobe nothing happens.

So I try to set up the cam with Easycam but nothing happens.

So I look for the modules and found two cam-modules. 

quickcam_messenger.c and quickcam.ko. The first module is from the out-of-the-box driver and the second is the qc-usb.

So I put the quickcam_messenger on a blacklist (so that he don't start at boottime) and told the qc-usb to start at boot.

But after reboot Gutsy or Camorama told me, that there is no cam available. So I put the quickcam_messenger back in action and I have the freezes.

So where is my mistake?? I know that the cam is working with Linux. And by the way..the cam is ok...I have tried it under Windows yesterday.

---

