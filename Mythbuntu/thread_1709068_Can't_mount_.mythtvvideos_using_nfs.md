---
title: "Can't mount ./mythtv/videos using nfs"
date: 2011-03-17
forum: Mythbuntu
---

### Post by nhtrader on 2011-03-17
PC1:
Mythbuntu 10.10 (32bit)
xfce 4.8.1
MythTV v0.24-222

/etc/hosts.deny - empty
/etc/hosts.allow - empty
/etc/exports
/home/mythtv/recordings    *(ro,async,no_root_squash,no_subtree_check)
[INDENT]file permissions: *.mpg (video)  -rw-r--r--   owner: mythtv   group: mythtv[/INDENT]

/home/mythtv/videos    *(ro,async,no_root_squash,no_subtree_check)
[INDENT]file permissions: *.m4v (video) -rw-r--r--   owner: bob (jay)  group: mythtv[/INDENT]

PC2:
kubuntu 10.04 (64bit)
kde 4.4.5



command used on PC2 as User: bob
sudo su
mount -t nfs myth:/home/mythtv/videos  /mnt/mtv-vid
(no error messages)

/mnt/mtv-vid  owner: root   group: root

cd /mnt/mtv-vid is empty. No videos appear. but File Manager shows 11 files.



What's wrong with my implementation of mounting MythTV's directories onto another ubuntu-box using NFS?

---

### Post by LowSky on 2011-03-17
just install mythtv frontend on the other PC.

make sure it uses the same info as your main box and the videos will be seen.

---

### Post by nhtrader on 2011-03-17
> **LowSky said:**
> just install mythtv frontend on the other PC.

make sure it uses the same info as your main box and the videos will be seen.

I realize that this is the most expedient solution, but due to other factors, this is not currently an option. 

The kubuntu PC is currently being used to test various web browsers and how they handle different media formats. So all I'm trying to do is transfer/access a *.m4v video file for the purposes of testing.

Basically, I'm having problems trying to play *.m4v on chromium 10.06 when accessing mythweb. So I'm conducting a test. I'm trying to play a *.m4v from this kubuntu PC to see it if Kaffeine, VLC, etc. can play it. Then I'll move on to other tests to figure out why Chromium(Chrome) can't play this video.

I also realize that "sneakerware" would also be easy, but again, I'm trying to learn new things. So I'm interested in getting NFS to play nice between MythBox and kubuntu.

---

### Post by nhtrader on 2011-03-17
I found the solution.

All that I needed to do is edit the file:  /etc/exports

I only had to change "no_root_squash" to root_squash". That's it.

Now I have access to these media files on the kubuntu PC.


Original Entries:
/etc/exports
/home/mythtv/recordings *(ro,async,no_root_squash,no_subtree_check)
/home/mythtv/videos *(ro,async,no_root_squash,no_subtree_check)

Modified Entries:
/etc/exports
/home/mythtv/recordings *(ro,async,root_squash,no_subtree_check)
/home/mythtv/videos *(ro,async,root_squash,no_subtree_check)

---

### Post by tgm4883 on 2011-03-18
> **nhtrader said:**
> I found the solution.

All that I needed to do is edit the file:  /etc/exports

I only had to change "no_root_squash" to root_squash". That's it.

Now I have access to these media files on the kubuntu PC.


Original Entries:
/etc/exports
/home/mythtv/recordings *(ro,async,no_root_squash,no_subtree_check)
/home/mythtv/videos *(ro,async,no_root_squash,no_subtree_check)

Modified Entries:
/etc/exports
/home/mythtv/recordings *(ro,async,root_squash,no_subtree_check)
/home/mythtv/videos *(ro,async,root_squash,no_subtree_check)

root_squash is actually the NFS default, so you could actually remove it completely

---

