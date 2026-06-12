---
title: "Problem with digital camera"
date: 2009-06-21
forum: Multimedia Software
---

### Post by evlutn on 2009-06-21
Hi all,

I'm using Ubuntu 9.04 and have a Canon Powershot G2 camera.  Whenever I plug the camera into the USB port, it says "the folder contents cannot be displayed", but I can download the pictures using F-Spot.  The problem is I didn't have this problem when I was using Ubuntu 8.10 since I could plug in the camera and browse through the folder to see which photos I'd keep or trash.

Has anyone else experienced the same problem?  I want to be able to just open the folder and see what's in it.  Can this be done?

Thanks,

Ainge

---

### Post by Luke3026 on 2009-07-06
I'm having the same issue with my Powershot A520 since upgrading to 9.04 from 8.10.  I have yet to find a solution.  If I stumble across a fix, I'll post back.

---

### Post by jynyl on 2009-07-18
Similar problem here, running Kubuntu 9.04.
When I plug in Sony DSC-P71 camera via USB, it is not recognised as a device by Kubuntu, so can't mount it.  Previous versions of Kubuntu worked ok, and I used Dolphin or Konqueror to copy images off the camera.

Any fixes to this?

TIA

---

### Post by socialidiocy on 2009-07-22
I have a canon A520 and a canon rebel xt. 

1.  Accessing the A520 through the folder view, an error message states that:

"Sorry, could not display all the contents of "Canon, Inc. Digital IXUS 50 (normal mode) / IXY Digital 55 (normal mode) / PowerShot A520 (PTP mode) / PowerShot SD400 (normal mode)": Failed to get folder list: -111: Invalid filename"

I am however able to access the camera with f-spot however.


2.  The Rebel XT takes a very long time to lock the device (at least a minute) During that time I only get: 
"Error initializing camera: -60: Could not lock the device"

After it finally establishes a connection to the device, I can browse the folders directly.

Any help with this would definitely be appreciated.

---

### Post by socialidiocy on 2009-07-22
Sorry, forgot to mention I'm running ubuntu 9.04, 2.6.28-13-generic

---

### Post by mustang on 2009-08-03
> **socialidiocy said:**
> 

2.  The Rebel XT takes a very long time to lock the device (at least a minute) During that time I only get: 
"Error initializing camera: -60: Could not lock the device"

After it finally establishes a connection to the device, I can browse the folders directly.

Any help with this would definitely be appreciated.

I have this same problem. Would updating to the latest firmware make any difference? Any help would be greatly appreciated.

---

### Post by Miggles on 2009-08-06
I may be having the same problem here: I have a Nikon D40 and am running 9.04.  I can browse the photos using FSpot but I'd like to use libgphoto2 to script up the camera controls and am unable to. 

Any attempt to control the camera from outside of FSpot (including GTKam) results in errors like this one:

```
gphoto2 --summary
                                                                               
*** Error ***              
An error occurred in the io-library ('Could not lock the device'): Camera is already in use.
*** Error (-60: 'Could not lock the device') ***
```

I suspect this is because Ubuntu is mounting the camera as a storage device. Any advice on how to stop this behaviour?

Edit: Sorry, bad choice of words. I know Ubuntu is not mounting it as a storage device. It is running PTP. The problem seems to be that Ubuntu is locking the device or something similar.

Edit: I found what I was looking for here: [http://ubuntuforums.org/showpost.php?p=7205851&postcount=4](http://ubuntuforums.org/showpost.php?p=7205851&postcount=4)

The problem I had was Ubuntu was mounting the camera using gvfs and locking it for anything I wanted to do.

---

### Post by wgrube on 2009-08-13
Same problem with Canon Powershot SX200 IS after upgrading to 9.04, it was working perfectly under previous version and I need it urgently. I hope someone will find out what's wrong soon. If this happens to be me, I'll let you know...

---

### Post by wgrube on 2009-08-13
Even this haven't solved the problem... :(

---

### Post by szczym on 2009-08-15
mee to have problem with gphoto and canon powershot S2 IS when starting a series of images - it makes only one picture in gphoto and than exits with error. with single images its also very unstable.

here is link to long log file after running command:
gphoto2 --capture-image --interval 20
[http://dl.getdropbox.com/u/433776/gphoto2-jaunty-problem.txt](http://dl.getdropbox.com/u/433776/gphoto2-jaunty-problem.txt)
Its 14 mb in size, but maybe there is the bug info.

---

### Post by Jack Harkness on 2009-08-16
I get the same error with my Kodak EasyShare Z1012IS, but then I can still open gThumb or F-Spot and d/l the pictures.  Actually, this happens both when I plug the camera in and when I pull the SD card and put in the laptop's reader.

---

### Post by rheupeiti on 2009-12-11
try unmounting the camera before you run gphoto2.

Start > Places > Computer
Right-click on your camera item > Unmount volume.

Now over to gphoto2.

---

### Post by lukem on 2009-12-20
Tried the solution posted by Miggles and gthumb finally worked.  It did not automatically launch though.  Had to launch it from menu and do a File>Import.  From there on, it worked as it used to.  Little reluctant to try the permanent fix.  Maybe there will be a bug fix soon to take care of it.  Ubuntu 9.10 with a Sony DSC W70

---

### Post by orbisonitrum on 2010-01-02
I got the same problem with my IXUS 950 IS and my PowerShot Sx200IS. It was as if Ubuntu automatically tried to mount the camera twice, thus locking the camera so that no application could be used to download the photos.

There seems to be multiple ways of telling Ubuntu to handle the camera, and these seem to cause a clash:

1. System->Preferences-Removable Drives & Media
- I unchecked the checkbox for Digital Camera, basically telling Ubuntu to "do nothing"

2. In Nautilus (the file browser) Edit->Preferences->Media
- Here I chose "Ask what to do".

I suppose it would work disabling either one of these configurations, since the general problem seems to be that both "Ubuntu" and "Nautilus" tries to access the camera at the same time.

Now importing photos works perfectly for me, just the way it used to do.

---

### Post by hyde0429 on 2010-02-12
This is definitely the fix:

1. Open terminal. 

2. Issue this command: sudo killall gvfs-gphoto2-volume-monitor 			 		

3. Issue this command: sudo chmod -x /usr/lib/gvfs/gvfs-gphoto2-volume-monitor

4. Close Terminal. Restart for good measure. 

Then feel free to connect the camera and get back to F-Spot/Picasa goodness. Bear in mind, this kills GNOME auto-launch of the camera icon, but who cares. You probably use a photo manager to import your photos anyway, right?

Have fun.

---

