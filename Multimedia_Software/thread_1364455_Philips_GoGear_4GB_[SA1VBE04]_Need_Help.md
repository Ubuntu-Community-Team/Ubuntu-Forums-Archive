---
title: "Philips GoGear 4GB [SA1VBE04] Need Help"
date: 2009-12-25
forum: Multimedia Software
---

### Post by dalesomers on 2009-12-25
I am trying to get my daughter's Philips GoGear 4GB SA1VBE04/17 to mount as either a usb mass storage device or MTP and manage through banshee or RythmBox...but I just cant seem to get it... I've upgraded to libmtp 1.0.1 and still no avail... here is the output of lsusb:

```
dale@ORION:/usr/lib$ lsusb
Bus 001 Device 011: ID 0471:207b Philips 
```

and the output of mtp-detect:

```

dale@ORION:/usr/lib$ sudo mtp-detect
libmtp version: 1.0.1

Listing raw device(s)
Potential MTP Device with VendorID:0471 and ProductID:207b responded to control message 2 with a response that was too short. Problems may arrise but continuing
Device 0 (VID=0471 and PID=207b) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
   Found 1 device(s):
   0471:207b @ bus 0, dev 11
Attempting to connect device(s)
usb_claim_interface(): Device or resource busy
LIBMTP PANIC: Unable to initialize device
Unable to open raw device 0
OK.

```

Any help would be GREATLY appreciated.

---

### Post by bdoe on 2009-12-27
I'm having pretty much the same problem. It doesn't seem to matter whether or not I set the player to MTP or MSC modes. As soon as I plug in my player, Ubuntu immediately grabs control of it and mounts it. Unfortunately, this means that none of my media managers (Exaile, Rhythmbox, Banshee) can see or work with the device. It also means that the Philips Device Manager (installed via Wine) can't see it either.

I've tried unmounting the device, and ejecting the device, and although this removes Ubuntu's mount on the device, my media managers still can't see the player. "Safely Remove Device" makes the device completely unavailable to the computer, until I unplug the player and plug it back in again - and then we're back at square one.

---

### Post by PGScooter on 2010-02-13
Have you guys managed to solve these problems?
I am interested in a gogear.

---

### Post by dalesomers on 2010-02-13
I have been able to use the device... ill have to look at the steps i used to get it working... i believe that i had to set the device to a certain mode but im not sure... ill post back with my solution tomorrow

---

### Post by Ka Fish on 2010-02-13
I have the device too. It was mounting & unmounting by itself, until yesterday. I got it to tell me it had a problem with the volume control. after installing the program to fix that, it no longer recognizes the mp3 player. I get a file error on the mp3 player itself.

---

### Post by Anton32828 on 2010-06-24
I just bought one of these on sale at Walmart. It will be going back unopened since there seems no chance it will ever support ogg.
 
I found this thread in my research. I hope it helps:
 
[http://ubuntuforums.org/showthread.php?t=1484262&highlight=philips+mp3](http://ubuntuforums.org/showthread.php?t=1484262&highlight=philips+mp3)

---

### Post by Ka Fish on 2010-09-18
oops

---

### Post by MattressVon on 2011-05-04
You need to create a blank file in your root directory on your GoGear player. :P

1.) Open your player via nautilus file browser.

2.) Once you are in the root directory of your player right click > create document > empty file

3.) Select the document and hit F2 or right click and select rename.

4.) Rename the document .is_audio_player

(include the "." and all "_")

5.) Unmount your player

6.) Open Banshee or Rhythmbox and connect your player.

7.) Wait until you see your player in the side bar.

You can edit the .is_audio_player file to control how your player is interacted with by Banshee and Rhythmbox. Mine says:

audio_folders=Music/
video_folders=Video/
output_formats=audio/flac,audio/mpeg

It tells the player to put my music collection in /Music and my video in /Video.

Output_formats tells the player what file types my player supports. I told it only mpeg and flac (by mime type which is why it's audio/...) because those are the only formats I use anymore.

Enjoy!

:popcorn:

---

