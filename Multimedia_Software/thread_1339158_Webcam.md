---
title: "Webcam"
date: 2009-11-27
forum: Multimedia Software
---

### Post by Robbyx on 2009-11-27
I do not know how to test if my new webcam is working but I suspect it is not because the following:


rob@rob-desktop:~$ dmesg | grep -i video
[    1.058914] pci 0000:01:00.0: Boot video device
rob@rob-desktop:~$ 


The webcam is designed as a PC camera and came with a windows driver, which I have ignored. I would be grateful for some trouble shooting help.

I am using intrepid an a desktop.

---

### Post by Lars Noodén on 2009-11-27
> **Robbyx said:**
> I do not know how to test if my new webcam is working but I suspect it is not because the following:


rob@rob-desktop:~$ dmesg | grep -i video
[    1.058914] pci 0000:01:00.0: Boot video device
rob@rob-desktop:~$ 


The webcam is designed as a PC camera and came with a windows driver, which I have ignored. I would be grateful for some trouble shooting help.

I am using intrepid an a desktop.

Try a more general search of dmesg.  

```

# unplug the camera, then
dmesg > /tmp/without

# plug the camera in, then
dmesg > /tmp/with

# see if it's recognized
diff /tmp/with /tmp/without

```

---

### Post by Robbyx on 2009-11-27
That was clever. Thanks. Here is the result:

> rob@rob-desktop:~$ diff /tmp/with /tmp/without
747,748d746
< [ 5107.120013] usb 4-6: new high speed USB device using ehci_hcd and address 7
< [ 5107.255341] usb 4-6: configuration #1 chosen from 1 choice


So it seems that the camera is being recognised. Can you please suggest how I test it and can see it working?

---

### Post by Lars Noodén on 2009-11-27
Regarding diff, the computer is supposed to do the work for the human not the other way around.  ;)

The camera is recognized as being plugged in but as far as I can tell not recognized as a camera.  The two lines recognizing that *something* has been plugged in should be followed by two more lines about where it is attached (as a device) to the system.  

Can you provide a detailed model name and number?

---

### Post by Robbyx on 2009-11-27
Smarteye 1.3 Megapixel Webcam
USB 2.00 PC camera

---

### Post by Robbyx on 2009-11-27
Here is the relevant line from lsusb:

Bus 004 Device 007: ID 0c45:627b Microdia PC Camera (SN9C201)

I also tried 

lsusb -d 0c45:627b -v | grep "14 Video"

and it did not produce any output so it is not a UVC device.

Currently I am looking at
[http://ubuntuforums.org/showthread.php?t=982471&page=1](http://ubuntuforums.org/showthread.php?t=982471&page=1)
It is a bit complex but I am trying to follow the advice.

---

### Post by Lars Noodén on 2009-11-29
Hmm.  

I see a possible candidate [jojo's list of Microdia webcams](http://groups.google.com/group/microdia/web/list-of-known-microdia-webcams).  From there it is a matter of finding or making the driver, if UVC does not work.  

The vendor really should have a linux driver available and there [is no excuse for missing linux drivers](http://www.kroah.com/log/2007/01/29/#free_drivers) these days, so lean on the vendor a little.  


[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

and an old page

[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

---

### Post by Robbyx on 2009-11-29
Thank you for the reference. I have it working because yesterday I upgraded to Jaunty and realised from your post that the driver might be in the new kernel. I have even installed the latest driver from the instructions below, but it did not seem to improve the quality, but at least it is not broken.

My friend is on MSN. Currently I am using ebuddy for IM to MSN. The picture is good on Cheese but poorer on ebuddy. On ebuddy it lacks definition and is rather dark. Do you have any advice to improve the picture quality over MSN? Is there a better way of connecting?

The camera is 1.3m pixel, VGA (640*480)

Robin



> 		
testing-microdia-driver-draft   	 
		

NOTE: This driver has been deprecated in favor of the sn9c20x sub-driver that is now included in the mainline kernel (2.6.31 or higher).

The latest source can be obtained from [http://linuxtv.org/hg/v4l-dvb/](http://linuxtv.org/hg/v4l-dvb/)


After you get information of your webcam and figure out it's a Microdia cam (List of Known Microdia Webcams),

you probably want to download and test the latest experimental microdia driver version from our source repository. This page will help you do it.

 

The Microdia drivers are stored in the following Git repository: [http://repo.or.cz/w/microdia.git](http://repo.or.cz/w/microdia.git)

Note: To download it you must have installed Git in your system. If you don't, take a look here : [Link] 

---

### Post by Lars Noodén on 2009-11-30
> **Robbyx said:**
> 
My friend is on MSN. Currently I am using ebuddy for IM to MSN. The picture is good on Cheese but poorer on ebuddy. On ebuddy it lacks definition and is rather dark. Do you have any advice to improve the picture quality over MSN? Is there a better way of connecting?
n

AMSN is one tool I've seen people use with specifically the dinosaur network.  There are some general purpose chat clients that work with that one and, more importantly, the others.  Telepathy and Pidgin are two.

[http://www.pidgin.im/](http://www.pidgin.im/)
[http://telepathy.freedesktop.org/wiki/](http://telepathy.freedesktop.org/wiki/)

Last I checked, which was a year ago, AMSN worked best with the legacy chat service named above, but otherwise Pidgin was 'Best in Test'

If you want to read about a really protocol that's useful in other areas beyond chat, look at Jabber/XMPP.  Friends don't let friends use MS protocols.  ;)

---

### Post by Robbyx on 2009-11-30
> **Lars Noodén said:**
> AMSN is one tool I've seen people use with specifically the dinosaur network.  There are some general purpose chat clients that work with that one and, more importantly, the others.  Telepathy and Pidgin are two.



Thank you for your help. I installed pidgin from synaptic only to fail to get the video to work. I therefore used ebuddy.

---

