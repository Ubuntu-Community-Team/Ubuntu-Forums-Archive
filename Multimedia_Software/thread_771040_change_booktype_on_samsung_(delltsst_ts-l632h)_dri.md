---
title: "change booktype on samsung (dell/tsst ts-l632h) drives"
date: 2008-04-27
forum: Multimedia Software
---

### Post by misha680 on 2008-04-27
Hi,

Very simple question, how do I change booktype from DVD+RL DL to DVD-ROM before burning on a Samsung (Dell Latitude D630 drive, TSSTcorp TS-L632H which per one forum I found is a Samsung drive)? 

Dvd+rw tools does not work for samsungs, and ImgBurn on Windows will do it but running it on wine I can burn perfectly but on changing booktype it gives the an unknown error with Reason: Access Denied.

Any suggestions would be greatly appreciated.

Thanks
Misha

---

### Post by mc4man on 2008-04-27
i use imgburn all the time (best iso creator/burner) but with plextor, benQ drives. Most drives will autoset dvd+r dl to dvd-rom, have you checked a burned dl  - open it in imgburn, will show last last recorded info

---

### Post by mc4man on 2008-04-27
A quick test shows you can't change booktype settings from imgburn thru wine but if you make or have made a change in windows then the setting will be used in linux.(if the change was successful) It appears the setting is made to the drive itself. It wouldn't hurt to make sure in imgburn tools>settings>write that auto 'change booktype' is checked

---

### Post by misha680 on 2008-04-27
> **mc4man said:**
> A quick test shows you can't change booktype settings from imgburn thru wine but if you make or have made a change in windows then the setting will be used in linux.(if the change was successful) It appears the setting is made to the drive itself. It wouldn't hurt to make sure in imgburn tools>settings>write that auto 'change booktype' is checked

Hey thanks for the suggestion. Yes I've tried burning (twice) and my disks come out as dvd+r dl which unfortunately works great in the computer but is a coaster in my DVD player (well it does some weird stuff but basically doesn't work, and certainly I can't watch the movie).

I was trying to avoid going into Windows but I guess if I have to change it once I'll do it (I actually left a very small Windows partition on this computer after I wisened up after trying to flash the firmware on my DVD burner on the old computer without Windows installed).

Btw if anyone knows an all-Linux solution let me know.

Thanks
Misha

---

### Post by mc4man on 2008-04-27
Not all drives can be set - hopefully yours can, if so while in windows set dvd+r to dvd-rom also.
Worst case if can't be set see if there is an updated firmware - must do in windows I believe and must be for your exact drive (best from your pc maker )

---

