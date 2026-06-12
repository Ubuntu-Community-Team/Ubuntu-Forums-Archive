---
title: "Media from USB"
date: 2008-06-04
forum: Mythbuntu
---

### Post by deadlydes on 2008-06-04
Sorry if this is a stupid question but i cant seem to find the answer.

I have recently installed Mythbuntu and am still getting to grips with it.
One thing i would like to do and havent managed yet is to play media (Videos, music and  pictures perhaps) from a USB key.

Is there a way i can plug in a USB key then navigate to it through the Mythbuntu menu system?

Much appreciated
Des

---

### Post by Weidbrewer on 2008-06-04
I can't say for 100% certain, but you might be able to add "/home/media/USBDRIVE" or whatever it mounts as to your videos and music sections to have it look there for files.

---

### Post by majoridiot on 2008-06-04
> **deadlydes said:**
> Sorry if this is a stupid question but i cant seem to find the answer.

I have recently installed Mythbuntu and am still getting to grips with it.
One thing i would like to do and havent managed yet is to play media (Videos, music and  pictures perhaps) from a USB key.

Is there a way i can plug in a USB key then navigate to it through the Mythbuntu menu system?

Much appreciated
Des

once you determine the mount point, you will need to add this location in both music and video
setups, and then use the respective manager to locate and add them to the database.  

you will need to use the media mangers to search for new media every time you add 
new media to the usb stick, or it will not show up in mythmusic or mythvideo.

---

### Post by isaidi on 2008-06-05
I couldn't find how to do that neither.

you will have to either create a sym-link to the /media/usb-key mount point inside the music and movies folders.. i believe default is /var/lib/mythtv/music ?

I configured my mythtv to have music and movies stored in /storage

so i just did
```

 ln -s /media/USB-KEY /storage/music/usb-key
 ln -s /media/USB-KEY /storage/videos/usb-key

```

I am not sure how this would work when re-plugging different USB keys in, that will result with different mount-points... I don't know how to get around it, but for now i would just manually go into terminal and delete/create sym links accordingly...

---

