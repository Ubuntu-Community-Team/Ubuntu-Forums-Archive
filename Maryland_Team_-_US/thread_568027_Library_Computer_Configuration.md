---
title: "Library Computer Configuration"
date: 2007-10-05
forum: Maryland Team - US
---

### Post by phr0ze on 2007-10-05
I have picked up the library computers and started the install to build an image. I realise we are close to a new release but I feel we should push forward to learn as much as we can now.

I am asking for input on packages, and other configuration settings that should be done prior to making the image.

What I have so far is:

Mondo - Use this for making the image. Considered Linux-Ghost but Mondo seems to be better.

Medibuntu - Added these repositories

Flash - They'll need it.

All updates through update manager.


What I still plan to add is:

MP3, DVD, Quicktime, DIVX, XVID, and WMV codecs.

Anything else?


These are for basic users. They don't care about free/non-free. They just want it to work.

---

### Post by ChuckFrain on 2007-10-06
I realize that the end users 'just want it to work' but we do have to worry about the licencing of what is pre-installed. Mainly because we are accepting/creating a legal agreement for someone else. 

A better option I think would be to include a bookmark or homepage pointing to EasyUbuntu or other links to the licenced products that would be found useful. I would steer clear of AutoMatix as that tends to have [more than EasyUbuntu] problems. Perhaps some instructions as well.

---

### Post by phr0ze on 2007-10-09
I have setup the medibunti links, but did not install any codecs. When the user tries to play that type of file, it should then offer to download it.

---

### Post by phr0ze on 2007-10-09
I've tried to image the library computers about a dozen different ways and I'm not having any luck. 

Seems like Mondo, although the easiest of them all currently has a compatability problem with Ubuntu. I can create the disks fine, but I can't restore from them because of the way it handles device labels. (HDA,SDA, etc)

Ghost 4 Linux seemed like the next best choice but it appears to be crude and it attempts to backup the empty space on the partition too. Because the actual bytes weren't zeroed, the file size is huge and I don't think it'll like it at all if the new drive is different in size. If anyone knows a way to easily zero the free space on a journaled file system, let me know.

Downloaded Norton Ghost 11 and it turned out to be a waste.

Downloaded the ultimate boot CD and I'm going to try the tools in there.

Any other suggestions???

Thanks.

---

### Post by phr0ze on 2007-10-17
Ok, after all the work I ended up using gparted + clonezilla boot CD. Gparted is used to reduce the partition sizes. Then clonezilla clones the drives to a USB hard drive. Then I use gparted on the new machine to make 2 partitions. Then Use clonezilla to restore.

Believe it or not, this was the only thing I could get to actually work end to end. I can't wait to try Mondo in Gutsy, that, by far, is the solution I really want.

---

