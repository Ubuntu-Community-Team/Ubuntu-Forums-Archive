---
title: "Missing DVD ROM and a hard drive"
date: 2009-04-01
forum: Mythbuntu
---

### Post by DonMegel on 2009-04-01
So I am still trying to get my Mythbuntu box up and running. One of the things I was looking forward to the most was ripping my DVDs. However, I can't rip or play DVDs. I have activated the extra codecs but when I hit play DVD the screen goes black for a few seconds and then returns to the myth screen. When I hit Rip it says its waiting on the DVD ROM.

Also, I have a second, 160 gig, HD installed but I dont see it any where.

I am a complete n00b with linux as you are prolly beginning to guess.

---

### Post by DonMegel on 2009-04-01
Ok, turns out the DVD problem was coming from the sound card actaully falling out of the PCI slot. Oops. 

I am still having a time finding the files that are on the second 120gig hard drive though. 

Side note: When I rip a DVD, is it as an Mpeg2 file? I saw the ISO option but the others just said Good, Excellent, etc.

---

### Post by Nobodyspeshul on 2009-04-01
Yeah, it gets ripped as a .vob file and stored in your local directory.

My internal player didn't like that at all, it would play the video but not the sound.

I ended up ripping my DVD's with Slysoft's AnyDVD and Clone DVD Mobile on my windows box and then moving those files into my player folder.

Working great so far.

---

### Post by DonMegel on 2009-04-01
Actually it ripped it as an avi file, about 1.6 gigs for a 2 hour movie. The file showed up in the video folder and all my networked PCs can access it. Very Happy.

However, I still cant find my second hard drive.

---

### Post by nickrout on 2009-04-01
> **DonMegel said:**
> Actually it ripped it as an avi file, about 1.6 gigs for a 2 hour movie. The file showed up in the video folder and all my networked PCs can access it. Very Happy.

I think perfect rips as an iso (which is just a copy of whats on the dvd, which contains vob files) and the other settings transcode to something smaller, ie an .avi

> 
However, I still cant find my second hard drive.

Is it being mounted? Perhaps not unles syou set it up to be!

show us the output of the ```
mount
``` command. And of ```
dmesg|grep sd
```

It may be mounted already under /media ?

---

### Post by DonMegel on 2009-04-01
Well I was able to get it mounted but can't seem to figure out how to make it auto mount instead of heaving to do it manually. There was a tutorial, [http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/) but my fstab does not look like his so I am a bit lost.

---

### Post by nickrout on 2009-04-01
> **DonMegel said:**
> Well I was able to get it mounted but can't seem to figure out how to make it auto mount instead of heaving to do it manually. There was a tutorial, [http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/) but my fstab does not look like his so I am a bit lost.

add a line like this to /etc/fstab.

NB each line in fstab needs a line-end character at the end, press enter at the end of the line!

```
/dev/sdb1 /mnt/disk2 ext3 noatime 0 1
```

where /dev/sdb1, /mnt/disk2 and ext3 are system dependent.

in my example /dev/sdb1 is the device (second drive, 1st partition)

/mnt/disk2 is where it is to be mounted, its up to you (you will need to create this directory first)

ext3 is the filesystem on there.

---

### Post by DonMegel on 2009-04-03
so for me, it would be 

/dev/sdb1 /media/160HD FAT32 noatime 0 1

at the bottom of the fstab file?

---

### Post by nickrout on 2009-04-03
I don't think FAT32 is a valid filesystem. I think it should be vfat.

---

### Post by AboveTheLogic on 2009-04-04
I recommend using the GUI mount manager:

sudo apt-get install mountmanager

I like the command prompt just as much as the next guy, but mountmanager makes it very easy.

I was having trouble because sometimes my 1TB HDD would show up as /dev/sda or /dev/sdc... and mount manager uses the serial instead of the device path to mount it, much more reliable. Sometimes after a reboot my drives weren't mounting properly but this is not a problem anymore.

---

### Post by DonMegel on 2009-04-06
So how do I tell mountmanager to mount the drive every time the system boots up?

---

### Post by nickrout on 2009-04-06
put it in fstab!!!

---

