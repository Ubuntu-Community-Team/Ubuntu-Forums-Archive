---
title: "how do I import single photo with fpot?"
date: 2009-12-11
forum: Multimedia Software
---

### Post by ahood on 2009-12-11
Hello,

I have a netbook running UNR 9.10 and I want to import a 10-20 photos from my digital camera that has 700+ photos. I am finding that fspot doesn't have the feature that will allow me to manually select a few photos after clicking on the the "Import" button in fspot. The only thing I am able to do with fspot is import all 700+ photos. 

The thought of importing all of the photos and then manually deleting 600+ photos isn't too appealing.

Because I am using UNR, dragging and dropping between application windows (nautilis and fpot) doesn't appear to be a workable option.

Manually copying select photos into a temporary folder in the /home/username directory and then importing them into fspot seems inefficient.

I am looking for the simplest way to manually select a few photos from a memory card and import them into spot.

Any suggestion will be greatly appreciated.

---

### Post by gordintoronto on 2009-12-11
Ctrl-click will select a file in addition to the files which were selected previously.

---

### Post by ahood on 2009-12-11
> **gordintoronto said:**
> Ctrl-click will select a file in addition to the files which were selected previously.

Thanks for suggestion. Sometimes the most simplest is the answer. 

Unfortunately, the above suggestion isn't the solution. F-Spot insists on importing all photos even after ctrl+clicking. 

I have determined the following.

(1) The problem occurs when placing a SD Card in the media slot of the machine.

(2) Fspot might allow importing of a few photos after ctrl+clicking when the SD card is in the camera and the camera is connected to the machine via usb.

Unfortunately, fspot displays an I/O error when it tries to import from the camera connected via USB. This problem is reported for many other cameras.

---

### Post by gordintoronto on 2009-12-11
That's interesting.  Over the months, I've connected three cameras to three computers, using three versions of Ubuntu.  Never had a problem such as you described.

---

### Post by ahood on 2009-12-12
> **gordintoronto said:**
> That's interesting.  Over the months, I've connected three cameras to three computers, using three versions of Ubuntu.  Never had a problem such as you described.

Thanks for replying.

There are several posts in Launchpad bug system reporting similar disfunctionality with the F-Spot import tool. 

I contributed and reported the error to [[COLOR="Blue"]Bug #258083[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/258083").

A more recent bug with similar error message is reported in Launchpad [[COLOR="Blue"]Bug #191316[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/191316").

This issue with F-Spot is also reported for other Linux distributions.

[[COLOR="Blue"]F-Spot "Could not lock decive error in GNOME[/COLOR]]("http://forums.opensuse.org/applications/414188-f-spot-could-not-lock-decive-error-gnome.html") 

[[COLOR="Blue"]Bug 485037 -  f-spot-import fails with error dialogue: Error connecting to camera; Received error "Could not lock the device" while connecting to camera  [/COLOR]]("https://bugzilla.redhat.com/show_bug.cgi?id=485037")

I am giving up on F-Spot. This bug is a show stopper for me.

Thanks again.

---

### Post by leandromartinez98 on 2009-12-12
Part of the problem for me is that F-Spot starts to import the photos
before I have the chance to choose between them, just to show thumbnails. 

If I have a folder with 700 photos and I just want to import 5 of them, I have to wait 5 minutes for the loading to be complete. 

This is horrible from my point of view (and I have the impression that Picassa does the same thing). 

I don't understand why importing folders had become the standard procedure, I don't like this kind of restrictive decision, particularly when considering that this is a photo organizer, that is, a software to organize one of the most personal records.

---

### Post by ahood on 2009-12-13
FYI - 

I proposed importing of a single/few photos F-Spot be addressed in Ubuntu Brainstorm. If you think importing of a single/few photos into F-Spot can be improved, please click on the link below and consider voting for the proposed solution or suggest an even better solution.

[[COLOR="Blue"]Quickly add a single photo to F-Spot catalog and Photos Folde[/COLOR] ]("http://brainstorm.ubuntu.com/idea/22944/")

With kind regards,

---

