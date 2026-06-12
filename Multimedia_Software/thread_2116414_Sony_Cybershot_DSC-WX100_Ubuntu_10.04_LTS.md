---
title: "Sony Cybershot DSC-WX100 Ubuntu 10.04 LTS"
date: 2013-02-15
forum: Multimedia Software
---

### Post by The Chef on 2013-02-15
Recently bought a very nice little camera, Sony Cyber-shot DSC-WX100 , but when it was plugged into the USB port Ubuntu would only mount and display 2 drives neither of which were the size of the memory card and neither of which contained the photos - the image JPG files (even when displaying hidden files).

The image files could however be accessed as if on a mass storage device under Windows 7 using whatever native device reader it uses.  I could find nothing on the Internet on this except to discover that the camera itself ran under Linux, which was only doubly maddening.

Reading around the subject I discovered a 95% solution though.  Set the camera's USB mode to MTP (Media Transfer Protocol), some Microsoft abomination.  Do not set it to Auto nor to Mass Storage.

Then install the following using Ubuntu's software centre (I am not really one for resorting to grep / make / install / off a deprecated library mirrored on somebody's blog site just to use a camera :D ):

mtpfs (Fuse Filesystem for MTP devices)
mtp-tools
libmtp8
python-pymtp

Now when you plug in the camera to a USB you will get one drive mounted and it will contain folders with your image files as you might be forgiven for expecting in the first place.  These files can be copied; however, you cannot write to the card or delete the files.  That still has to be done using the camera's menu system, which is annoying.

Although the big issue of not being able to access photos taken on my camera is solved.  I would value an explanation of what's going on, just as a matter of interest, and any thoughts on how to get 'root' type access to the card also to do mass deletions.  As a further technical note: when the 64GB Mini SD XC I card is formatted by the camera, then removed and inserted into my PC card reader, Ubuntu does not even recognize that a card has been inserted.  It usually auto-mounts the card.

Thanks!

---

