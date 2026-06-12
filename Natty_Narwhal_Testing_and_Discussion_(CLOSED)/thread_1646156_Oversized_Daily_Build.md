---
title: "Oversized Daily Build"
date: 2010-12-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2010-12-15
The Natty daily builds have been OVERSIZED since the beginning.  Three of my four test pc's won't boot from USB.  I've tried DVD-r/w before but Ubuntu wouldn't erase my DVD-r/w and I'm not going to burn a bunch of throw-away's.  I can make a separate hard drive partition and put the oversized on that, however several times in the past that would run and the real CD wouldn't.  What I'm trying to do is find bugs in the real process.

Any way to mount the iso, remove something I'm not testing, and rebuild the iso so it will fit on a CD?

Thanks much, Jerry

---

### Post by ronacc on 2010-12-15
try k3b and see if it will erase the dvd-r/w I find it much more capable than anything in gnome . I never tried to erase one because I don't use them .

---

### Post by seeker5528 on 2010-12-15
> **jerrylamos said:**
> I've tried DVD-r/w before but Ubuntu wouldn't erase my DVD-r/w and I'm not going to burn a bunch of throw-away's. 

It wouldn't erase your DVD RW or it wouldn't write the CD image to DVD?

CDs and DVDs use different file systems, so you have to use the correct image for the type of disk you want to burn to.

Outside of that K3B is what I normally would use.

Later, Seeker

---

### Post by cariboo on 2010-12-15
I must be doing something wrong, cause I've been writing the oversized images to DVD and haven't run into any problems yet. :)

I don't have any DVD/RWs, but I do use quite a few CD/RWs and have no problems using Brasero to erase them.

---

### Post by zenarcher on 2010-12-16
> **ronacc said:**
> try k3b and see if it will erase the dvd-r/w I find it much more capable than anything in gnome . I never tried to erase one because I don't use them .

If I recall correctly, K3B doesn't erase a DVD, as it does with a CD.  However, you can put a used DVD R/W in the drive and choose to burn your new image and K3B will automatically overwrite the existing data on the used DVD.  I'm pretty sure that's how it's worked for me.

Cheers,
zenarcher

---

### Post by rondackcpu on 2010-12-16
Same problem here; computer won't boot from USB.  I remastered the ISO, removing openoffice-help-en-us.  That was enough to get it to fit on the CD.  Process is intense, but straight forward.  Google "remaster ubuntu" for instructions from community/LiveCDCustomization.

CRS

---

### Post by rajeev1204 on 2010-12-16
I booted just fine from a USB stick .Make sure you have set correct boot device from bios, but i assume you already done that.

---

### Post by ratcheer on 2010-12-16
> **cariboo907 said:**
> I must be doing something wrong, cause I've been writing the oversized images to DVD and haven't run into any problems yet. :)

I don't have any DVD/RWs, but I do use quite a few CD/RWs and have no problems using Brasero to erase them.

+1

Also, I ***do*** write CD iso's to DVD+RW's. I use the same disks over and over and there is no trouble erasing them.

Tim

---

### Post by psusi on 2010-12-16
Yes, with DVD+/-RW you just overwrite them with new data; there is no need or ability to erase them first.

---

### Post by seeker5528 on 2010-12-16
> **cariboo907 said:**
> I must be doing something wrong, cause I've been writing the oversized images to DVD and haven't run into any problems yet. :)

Hmmm, I thought this was something I had done in the past, but it's been a while since I was able to do it with CD images I have tried. Maybe there are other factors involved.

When I *have* tried it when it didn't work, it was because I only had blank DVDs to write the images to, not because the images were oversized for a CD, maybe *that* factors in somehow. It's not that I started the burn and it failed or resulted in a disc that was not usable, it's that it didn't even lite up the button to start the burn. 

Later, Seeker

---

### Post by cariboo on 2010-12-16
I've had that happen once or twice in the past too, I never took the time to find out why though.

---

