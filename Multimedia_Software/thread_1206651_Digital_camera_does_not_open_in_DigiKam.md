---
title: "Digital camera does not open in DigiKam"
date: 2009-07-07
forum: Multimedia Software
---

### Post by plo on 2009-07-07
How simple it could be. I unmounted the camera in Nautilus and then it worked like a charm in DigiKam.  


On my quest for a good photo and video managing software I found DigiKam (others only support photos, from what I have found).

My camera Fuji Finepix 30 opens fine i Ubuntu 9.04 desktop (gnome) and photos import to F-spot. DigiKam autodetects the camera correctly but when I try import media the device is not accessible (wrong path to device). DigiKam suggests  "/" (root). 

I have tried 
* selecting it as a USB mass device
* as the Fuji Finepix 30 camera
* USB PTP Class Camera (as suggested in DigiKam)

In desktop (gnome) it connects as "gphoto2://[usb:001,002]/".
Tried that as a path in DigiKam but no luck.

Anyone ....

/Palle

---

### Post by squee on 2009-07-08
> **plo said:**
> How simple it could be. I unmounted the camera in Nautilus and then it worked like a charm in DigiKam.  


On my quest for a good photo and video managing software I found DigiKam (others only support photos, from what I have found).

My camera Fuji Finepix 30 opens fine i Ubuntu 9.04 desktop (gnome) and photos import to F-spot. DigiKam autodetects the camera correctly but when I try import media the device is not accessible (wrong path to device). DigiKam suggests  "/" (root). 

I have tried 
* selecting it as a USB mass device
* as the Fuji Finepix 30 camera
* USB PTP Class Camera (as suggested in DigiKam)

In desktop (gnome) it connects as "gphoto2://[usb:001,002]/".
Tried that as a path in DigiKam but no luck.

Anyone ....

/Palle


Could you please post how you solved it so others can benefit? Others like me! :-)

---

### Post by xc3RnbFO8P on 2009-07-08
Like he said:
> How simple it could be. I unmounted the camera in Nautilus and then it worked like a charm in DigiKam. 

---

### Post by philip5 on 2009-07-08
I think Fuji Finepix F30 use PTP for communication with the camera and that is taken care of by the libgphoto2 library that among other apps Digikam uses. I'm not sure of the version of the package libgphoto2-2 that comes with jaunty supports your camera as you like but with the latest version of it I think it will (even though you seam to have solved it). I have a updated package of it on my repo (info about it below in my signature).

If you like to try the cutting edge version of Digikam then you could use the packages on my repo for (k)ubuntu 9.04 (jaunty) that holds packages of Digikam 1.0.0 beta 2 (for the moment) among a bunch of other updated packages. (Not sure how well the latest version of Digikam works in Gnome though)

I love what's going on with Digikam and it surely gives i.e Adobe Lightroom and Bibble a run for their buck! I almost can't wait for Digikam to be in final version even though the beta works pretty well so far and have a bunch of new features and look than the old 0.10.x-version.

The url and instructions on how to use my repo are found below in my signature.

Have fun!

---

