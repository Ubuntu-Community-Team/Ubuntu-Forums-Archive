---
title: "Share music library between Windows and Linux"
date: 2008-09-11
forum: Multimedia Software
---

### Post by sporkubus on 2008-09-11
So I use Linux for just about everything now even though I have a dual boot system. I'm thinking about getting an iPod touch, which I'd want to manage using Windows, but I still want to use Linux to play my music, as well. Soooo... is there some way I can share my music library between Windows and Linux? I am thinking the best way would be to create a new partition that Windows can recognize and put my whole music folder into there, then force it to mount automatically whenever I boot into Ubuntu. Anybody know how I might go about doing this?

---

### Post by lackoblacko on 2008-09-11
there are multiple ways to do this.
1. just leave your music on the windows partition and access it on linux by mounting the windows partition
2. create a new partition to share between windows and linux
3. leave your music on linux and access it in windows

i suggest number 1 because no additional configuration is required.

---

### Post by SuperSonic4 on 2008-09-11
> **lackoblacko said:**
> there are multiple ways to do this.
1. just leave your music on the windows partition and access it on linux by mounting the windows partition
2. create a new partition to share between windows and linux
3. leave your music on linux and access it in windows

i suggest number 1 because no additional configuration is required.

I agree with option 1, it would be easiest to put them on an ntfs partition although you can force windows to recognise ext3 it's not worth it.

I have my music on an ntfs drive with no OS, just storage media on it and can access it in both linux (/media/Music) and windows (G:\).

---

### Post by sporkubus on 2008-09-11
Great, thanks guys :)

Now... how do I get Linux to automatically mount the partition?

---

### Post by ad_267 on 2008-09-11
It should already be mounted automatically. It's probably in /media somewhere. You can create a symbolic link from ~/My Music to point to /media/windows/My Documents/My Music or something like that.

---

