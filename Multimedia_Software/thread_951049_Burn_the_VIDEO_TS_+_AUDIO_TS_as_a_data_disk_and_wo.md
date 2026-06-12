---
title: "Burn the VIDEO_TS + AUDIO_TS as a data disk and work?"
date: 2008-10-17
forum: Multimedia Software
---

### Post by Squish on 2008-10-17
Hey just a question of curiosity, I have a bunch of VIDEO_TS/AUDIO_TS files laying about from some former projects of mine, and I was wondering if you could just take those files, and burn them to a dvd as a data disk, and have it work.

Otherwise, could someone point out to me the method that you would burn them to a disk in linux? If possible, having not to convert them to ISO files would be nice.

---

### Post by mc4man on 2008-10-17
> burn them to a dvd as a data disk, and have it work.
Yes and no. You'll be able to play them back on your pc in the same manner as you can when they're stored on your hdd, in other words as a directory. (ex. - right click on the VIDEO_TS - 'open with vlc' or in vlc - file -> open directory.
As far as being a playable dvd video disk, no, you'll need it properly burned as such.
 
> If possible, having not to convert them to ISO files would be nice. 
Not sure if any linux apps can do that in regards to taking a VIDEO_TS folder and directly burning to disk as a proper dvd video disk. ( myself I don't bother with linux iso creating or burning apps for dvd video - too unreliable

Imgburn can do that by choosing the option 'device' in 'set build mode' (vs. 'image file'

---

### Post by berarma on 2008-12-06
You can make a good video dvd with genisoimage with this command:
# genisoimage -dvd-video -o dvd.iso sourcedir

An ISO image will be created in the file "dvd.iso", "sourcedir" is where your dvd directories are. All directories and files in "sourcedir" must be uppercase. You can then burn the ISO image to a DVD.

Similarly, you could burn directly to a DVD without using an ISO image with the growisofs command.

Maybe graphical frontends like K3B could do the same, I don't know.

---

