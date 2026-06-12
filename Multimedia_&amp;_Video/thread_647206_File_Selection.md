---
title: "File Selection"
date: 2007-12-22
forum: Multimedia &amp; Video
---

### Post by TheManzine on 2007-12-22
Hi so I am having trouble trying to open my music files with amarok because it only finds my root folder and home directory etc but I have all my music on my other partition which is my C:/ with vista on it. I had my music playing with another player but it wouldn't play mp3 files fine and I heard amarok was better. Do I have to mount my C:/ so that amarok can read into my ACER partition, I think it already is mounted actually but that's all I can come up with.

---

### Post by irwa82 on 2007-12-22
Hi,

The following will talk about restricted formats which should help you understand why the mp3 files are not playing:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

The easiest way would probably be to enable the restricted repositories and search mp3 in synaptic package manager and install any of the mp3 libraries that you see.

With your windows partition for music it will need to be mounted. I am not sure what the mount location will be called but if you do the following in the command line you should see all the mounted partitions. the vista partition will probably be an ntfs or vfat partition.

mount

anyway hope this helps

---

