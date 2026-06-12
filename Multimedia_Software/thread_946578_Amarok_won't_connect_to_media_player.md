---
title: "Amarok won't connect to media player"
date: 2008-10-13
forum: Multimedia Software
---

### Post by outdoorsman14 on 2008-10-13
So I have a 8gb Sansa Fuze and I am trying to connect to Amarok via MTP. I have gotten it to connect in MSC Mode, but I want to make playlists. I know I can make a file with the names of the songs and such and I can manually get it to show up on my player, but it is blank. At any rate when I try auto detect, it says that no media has been found, but when I run mtp-detect in root, I find and can connect to my Sansa. When trying to auto detect Amarok asks to run 'dcop kded mediamanager fullList'. So I put that in the console and it prints this out:

greg@greg-laptop:~$ dcop kded mediamanager fullList
/org/freedesktop/Hal/devices/volume_uuid_cea71409_3052_43cf_b277_1b5c236485c0
sda5
36G Media

true
/dev/sda5
/
ext3
true

media/hdd_mounted

false

---
/org/freedesktop/Hal/devices/volume_uuid_32EA277EEA273D8B
sda3
Linux

true
/dev/sda3

ntfs
false

media/hdd_unmounted

false

---
/org/freedesktop/Hal/devices/volume_uuid_9C1092C31092A3B4
sda2
ACER

true
/dev/sda2

ntfs
false

media/hdd_unmounted

false

---

I was having trouble at first with the DCOP server not running, but all of a sudden it works, but only under my username, not root. I thought that was kind of weird. I don't know what to do from here. Also if I try to setup a manual configuration, it brings up a Malformed Url error. Any help would be great.

---

