---
title: "Installing a Philips webcam SPC715NC/27"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by gluonman on 2007-12-14
Hi. I just bought a Philips USB webcam. On the front cover, it says it needs SPC715NC/27, but on the installation manual it says it needs both SPC710NC and SPC715NC. In any case, I have no idea where to even begin making this cam work with my Linux Ubuntu 7.10 laptop. I spent a bit of time looking for a decent tutorial or how-to, but none were specific to this cam. Any help please?

---

### Post by charroch on 2007-12-30
Have you tried:

cat /dev/video0?

Or andy videoX value that is available.

It should give you some rubish to the console but at least it means it is working. Alternatively you can install camorama.

---

### Post by Pastit on 2007-12-30
Hi, I have just got this webcam working in Kubuntu 7.10
It doesn't (as yet) give a quality picture and the only resolution is at 320.
I downloaded the latest GSPCA [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)
copied the file to /usr/src, tar(ed) the file and followed the instructions in the Readme file.
Now when I connect the webcam to the usb socket it loads the appropriate modules, it can be found with lsusb and there is the file /dev/video0 present when it is connected.
The output can be seen with camorama, ekiga and kopete.
The webcam is identified as spc710 and not as spc715 so I guess we will have to wait for a later version of GSPCA.
Good luck

---

### Post by stevenrnelson on 2008-01-05
I'm using this same camera, and have not been able to get it working with the suggestions given. Would any one mind posting more specific directions? Is there any better way to pinpoint the trouble than checking for /dev/video0 or running camorama?

---

### Post by stevenrnelson on 2008-01-06
I've done some digging in the logs and found something possibly worthwhile in /var/log/messages
When I attach a webcam that does work, I get a message like this:
```
Jan  6 00:10:21 TheItalian kernel: [18421.348000] usb 2-4: new full speed USB device using ohci_hcd and address 16
Jan  6 00:10:22 TheItalian kernel: [18421.552000] usb 2-4: configuration #1 chosen from 1 choice
Jan  6 00:10:22 TheItalian kernel: [18421.556000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(SPCA561A)
```
When I attach the spc715nc, I get something similar, but lacking the last line:
```

Jan  6 00:10:25 TheItalian kernel: [18424.784000] usb 1-4: new full speed USB device using ohci_hcd and address 12
Jan  6 00:10:25 TheItalian kernel: [18424.988000] usb 1-4: configuration #1 chosen from 1 choice

```
I don't think the issue depends on any hardware problems because both are recognized, but the philips one doesn't get a driver assigned to it.
I also found the usb id in the source code for the gspca driver, so I know it should support it, but for some reason it isn't getting attached.
I'll keep digging around and see if I discover anything. I'm by no means an expert, but I'll give it a shot.

---

### Post by stevenrnelson on 2008-01-06
Hah, I have it working!
Okay, I will try to explain it carefully, though I apologize if any of this is incorrect.
After downloading and installing the newest gspca like the poster above me suggested, I removed the package version of gspca-source I had installed through synaptic.
Still I was afraid that the correct kernel module was not getting installed. Using `locate gspca.ko` I discovered I had two versions of the file in two different places. One was in /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/gspca.ko and the other was in /lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1/gspca.ko
I had a hunch the one I had compiled was not the one that was getting loaded into the kernel. I made a backup of both file versions just in case, and then copied the bigger version (because bigger is better, right?) over top of the smaller version with this command:
sudo cp /lib/modules/2.6.22-14-generic/kernel/drivers/usb/media/gspca.ko /lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1/gspca.ko
After that I used modprobe to remove the previous module and load the new one. 
modprobe -r gspca
modprobe -a gspca
I plugged in the webcam and checked /var/log/messages and sure enough, it worked!! I've tried a couple of different programs like camorama and ekiga and all recognize the camera and push video. I got a working camera and learned a thing or two. 
Good luck.

---

### Post by Pastit on 2008-01-06
Glad you now have it working - does it show as a 715 or as a 710 and can you get better than 320 resolution.?

---

### Post by stevenrnelson on 2008-01-06
It reports as a 710nc. In the driver, that's the model number that corresponds to the usb id. I am able to get 640x480, but only after viewing the stream in ekiga. The only reason I know it's 640x480 is that I'm running a little piece of software I've written with opencv, a library for computer vision. I don't yet know how to make the program demand the maximum resolution, but even the last message in /var/log/messages specifically states that the maximum resolution is 640x480 and the minimum is 160x120. So the camera and driver are capable of VGA, I just don't know how to demand it from it yet, other than running Ekiga.
Another quick note. Whatever I did with modprobe didn't load the module again after I booted the computer this morning. I'll have to look into that. I think that will be better documented.

---

### Post by stevenrnelson on 2008-01-06
okay. I'm not sure this is the "right" way to do this, but by adding gspca to the end of /etc/modules the module is loaded at boot time, detected the cameras and just worked.

---

### Post by tvor on 2008-01-20
This camera does not work out of the box. Please follow this instructions for GSPCA driver using this tutorial. > [http://ubuntuforums.org/showthread.php?t=322218](http://ubuntuforums.org/showthread.php?t=322218) it worked as dream. For me, the camera was not recognized in skype at first, but worked with Ekiga, Camorama and XawTV.  This command > sudo usermod -a -G video username added me as user and video showed in skype. Enjoy

---

