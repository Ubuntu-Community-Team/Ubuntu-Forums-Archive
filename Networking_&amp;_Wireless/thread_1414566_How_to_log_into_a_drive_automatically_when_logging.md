---
title: "How to log into a drive automatically when logging into Ubuntu"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by cforput on 2010-02-23
I am sure this is somewhere in the forums but since I don't know any of the buzz words associated with what I am trying to do, I haven't had any luck searching.

Here's the deal:

I have 1 physical drive. On it, I have a partition for XP, a partition for Karmic and a partition for all my data so I can share between XP and Karmic.

When I boot in Karmic, I need to select the data drive (called SHAREDDRIVE) and enter my password before any of my apps can access the data. 

My question is: Is there a way to automatically connect / log onto the SHAREDDRIVE during bootup so I don't have to remember (this is VERY difficult for me!!!) manually log onto it?

---

### Post by dmizer on 2010-02-24
Try this: [http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

---

### Post by cforput on 2010-02-24
After tackling this problem a little further, I discovered that what I really needed to happen was for the drive to automount. I found some info on fstab and put an entry there. It auto mounts now so thanks for your help.

---

