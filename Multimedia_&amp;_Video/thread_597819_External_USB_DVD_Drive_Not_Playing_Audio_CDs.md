---
title: "External USB DVD Drive Not Playing Audio CDs"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by steve_b on 2007-10-30
Hello. New Xubuntu user here, but have been using Linux for 2 years. I'm having an issue playing Audio CDs via my External DVD Drive, an HP dvd 940. I'm able to play Video DVDs and access data from DVDs and some CD-Rs, but for some reason I cannot play normal Audio CDs.

I'm getting the following error after inserting an Audio CD and double clicking on the "Audio CD" icon on the desktop:

'Unable to mount "Audio CD": Unknown Error'

When I attempt to mount the volume via the left click menu, I get the same error message.

Any idea how to fix this? I had no issues with using this drive for Audio CDs previously with 2 other distros. Thanks.

---

### Post by steve_b on 2007-10-31
Just some more info...

If I put in a Data DVD into this drive and do a 'mount' from the command line, I can see that it is mounted. For example:

**/dev/scd1 on /media/Led Zeppelin Live - Vol. 4 type iso9660 (ro,nosuid,nodev,uid=1000,utf8)**


If an Audio CD is placed in the drive, 'mount' lists nothing for /dev/scd1. When attempting to 'mount /dev/scd1' when an Audio CD is present, I get:

**mount: can't find /dev/scd1 in /etc/fstab or /etc/mtab**


And it doesn't seem to be just "Audio CDs"...it is for CDs in general. Even when attempting to burn data to a CD-R, I get this:

'The disc in "DVD Writer 940d" is not writable: replace the disc with a recordable CD or DVD.'

This CD-R is fine. I can burn to DVD with no problem.


Any ideas? Do I have an issue with fstab? WHy is it just CDs are causing the issue and not DVDs?

---

### Post by steve_b on 2007-10-31
Yet another update...

1) I am able to rip the contents of an Audio CD to .flac using K3B and this device with no problem. But still can't play the CDs from the device using any CD player app.

2) I am able to play Audio CDs from the PC's internal CD drive (although the music skips at times).

3) Amarok opens up as sson as I insert a CD in this device, then says "Could Not Read AudioCD" after Engage --> Play Audio CD is selected. When trying to select the Audio CD with Engage --> Play Media --> Storage Media --> Audio CD (under media:/), the following Amorok error occurs:

Could not start process Unable to create io-slave: klauncher said: Unknown protocol 'audiocd'.


Does this help identify the issue?

---

### Post by t2000kw on 2007-11-04
I saw your post and thought I'd pass along my experience. 

I've had intermittent problems writing DVDs and CDs to my Sony DVD+/- R/RW drive (one of the first dual drives available) and it quit working altogether before I upgraded to Gutsy. I was hoping it was something Gutsy could fix but it is still not burning after the upgrade to Gutsy.

I took out an old high speed CD burner from a computer I have in the garage and it works just fine. SO I"m going to use it until I need to burn a DVD.

The point of the matter is that these things sometimes do stop working, even partly working. My DVD writer reads discs but won't write to them anymore. 

What I'd like to find out is if USB DVD/CD +/- R/RW drives in general are a problem with Ubuntu so I'll post that question in a separate post. 

If you can borrow a similar drive you might be able to figure out if it's the USB thing or if your drive is defective now. However, since you can write DVDs it seems the burner part IS working.

---

