---
title: "Webcam Woes Continue"
date: 2008-12-05
forum: Multimedia Software
---

### Post by macpointman on 2008-12-05
SO I have gotten my Ubuntu Hardy 8.04 install pretty much working the way I want it to.  After coming off of a Intrepid install Both on the 64 bit and 34 bit versions used way way too many resources taxing one or the other of my AMD Athlon X2 4000+ at over 100% and using nearly ALL available memory.  I expected the 64 bit version to use a considerably larger amount of memory but not nearly 2 GB.  THe process that took up the major portion of the CPU and memory Sources was the network manager.

With that being said I think I will stick with LTS releases.

My current issue is with getting my webcam working.  I have a Logitech Quickcam communicate STX It works especially well on my Dell Inspiron 1505E notebook (configuration listed in my sig).  running a Hardy Upgrade.  I will also add that My DV camcorder works well with Kino.

After working on this issue for a while It suddenly started working after a reboot then on the next it quit.  Currently the Blue light is on completely and during the boot process it flashes when the Kernel activates the drivers and discovers the webcam.  This confirms that Ubuntu sees that the webcam is connected.

Does anyone have any Ideas?

My current Configuration follows

DFI Infinity CFX3200-M2/G Mainboard
AMD Athlon X2 4000+ Processor
2 GB Corsair Value Select PC2-5300 667MHz DDR2 Memory
VisionTec ATI HD2600XT 512 MB DDR3
Seagate Barracuda 7200.7 160 GB PATA harddrive
Seagate Barracuda 7200.10 250 GB SATA 3 Hard Drive (Disconnected Windows XP Pro Drive)
Emprex Dual Layer DVD R/RW burner
802.11G Wireless LAN card (Generic Atheros) 

Thanks,
MacPointMan

---

### Post by macpointman on 2008-12-10
no help out there?

---

### Post by macpointman on 2008-12-10
Well It seems that I may have gotten my webcam to work finally.  We will see how long it works.  All I did was try every USB port on my computer.  It seems that Ubuntu does not like any of the external ports (i.e. Fromt usb or usb hub ports).  Plugged into the back of my computer it seems to be working.

Now all I need to be able to do is Use my Camcorder as a Webcam.  Any Ideas on that?  I am all ears.

MacPointMan

---

### Post by macpointman on 2008-12-11
It is apparent that After a reboot that my previous post is not the fix.  I am having a hard time understanding why it will work at one given time and then after rebooting it will not.  Am I missing something.  Is there an entry in a config file somewhere that I am missing?

It is evident that Ubuntu Needs much better camcorder and Webcam support.

MacPointMan

---

### Post by macpointman on 2008-12-12
Still no help out there I see.  Perhaps I am posting in the wrong forum.

MacPointMan

---

### Post by rhysjones_1 on 2008-12-12
sorry can't help you. . . .

---

### Post by macpointman on 2009-01-05
wow seems that webcam support is quite lacking.

---

### Post by yahs on 2009-03-23
I have a logitech Quickcam STX and I am still using Ubuntu 8.04.2 because 8.04 uses Video for linux driver 1(v4l1) while intrepid uses v4l2.
I have intrepid installed on a separate partition and I can get pictures from camorama  or cheese, but it gives a green screen if I try and use it with skype.
This issue is well documented on the launchpad and there are various fixes suggested, not sure if they all work.
On a separate point when I used the STX webcam in Windows XP it took up a huge amount of resources, often 80% ( under control panel, hardware, devices, usb controller, bandwith) and if it was plugged into a USB1 point, the quality over Skype or MSN was poor.I had to run it through USB2 to get good quality.
In 8.04.2 I get very good quality using Skype. Hope this is useful

---

### Post by hvlugger on 2009-06-05
> **macpointman said:**
> wow seems that webcam support is quite lacking.

I have the same problem, it is due to the USB ports 'swapping' on reboot. I had it in previous version and now again in Jaunty. I had to write a small script for applications to 'see' the webcam, not the best, but all I could do, the script is something like this for my webcam which comes up as:

Bus 002 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam

My script for Skype is like this to detect webcam device number:

# detect moving cam
v4l-info /dev/video1 2>/dev/null | grep -q "zc3xx"
if [ $? -eq 0 ];then
camdev=1
else
camdev=0
fi

# full name of device for 'grep'
port=/dev/video$camdev

---

