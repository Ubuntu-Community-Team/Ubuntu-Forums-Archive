---
title: "Has your usb printer stopped working?"
date: 2007-07-21
forum: Multimedia &amp; Video
---

### Post by rvergara on 2007-07-21
I bought a multifunctional printer Canon MP530 four months ago. I installed the printer function with the turboprint drivers and worked very well, i installed the open source drivers for the scanner and worked as well.

A month ago the printer stopped working all of a sudden, checking the turboprint control panel, it  kept promting that there was no connection with the printer, however the scanner kept working.

After a few hours checking logs I found that the printer device, in my case /dev/usblp0 had as owner group "scanner" and the device for the scanner, in my case /dev/usblp1, had the same group. This sounded wrong after reading about it using google. I changed the group owner to lp and... voila, the printer started working immediately. However in the next reboot the owner was changed back to scanner, after a bit of more reading I added cupsys user to the scanner group, restarted cups and now the printer is back working without any problem.

My assumption is that one of the upgrades from Ubuntu caused the problem.

This may have happened to other multifunctional usb printers out there.

Hope it helps.

Ramiro

---

### Post by callan79 on 2007-07-25
> **rvergara said:**
> 
After a few hours checking logs I found that the printer device, in my case /dev/usblp0 had as owner group "scanner" and the device for the scanner, in my case /dev/usblp1, had the same group.


Hi,

I have Ubuntu Feisty installed on a computer 700Km away, running a Canon Pixma iP1300 printer via USB, using Turboprint. I cannot tell you an exact date, but the owner tells me it stopped printing. I couldn't really find much in the logs, and the turboprint setup program (xtpsetup) was getting an error "Unable to lookup host 'usb'-Unknown host". After reading some forums, I found a few things.

First, the USB device permissions seem OK :
crw-rw---- 1 root lp   180,  0 2007-07-25 22:21 /dev/usblp0

Secondly, from [HERE]("http://www.turboprint.info/support/viewtopic.php?t=122") I found that the cupsys user was supposed to be part of my plugdev group. It wasn't.

I added it but it did not fix the problem.

Then in the xtpsetup program for turboprint, I changed the printer from CUPS ipp://usb://Canon/iP1300, to usb://Canon/iP1300.

This still did not fix it properly, but after stopping and starting the printer, I think it's fixed!

So I really don't know what I did, but I hope this helps someone!!!

Thanks
Callan

---

