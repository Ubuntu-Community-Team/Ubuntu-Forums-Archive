---
title: "Problems in writing external HD from the home network"
date: 2012-09-11
forum: Networking &amp; Wireless
---

### Post by piero1977 on 2012-09-11
Hi!

I have installed Ubuntu 12.04 (Desktop) on an Asus EEE Pc because I want to use it to substitute an home Nas. I would like to store data on an external hd (1TB; formatted in Fat32), connected to the Ubuntu Asus via usb. Data in hd should be read/written by the Asus pc and by another notebook with Vista.

I created on Vista two user accounts: Administrator (with administration permissions) and Normal (with standard permission). My idea is to have on the external Hd three main directories: COmmon Files (that have to be read/written by both users), Administrator files (r/w by Administrator) and Normal Files (r/w by Normal). I would also like that these two useser had a correspondence with two users on Ubuntu Asus with the same name.

To share directories I use Samba.

1) I've created Administrator and Normal also on Ubuntu Asus. I have noticed that shared directories were working on Windows/Administrator (r/w on Common files and Administrator files), but not on Windows/Normal (it says it has no access to the directories Common Files and Normal files).

2) I have noticed that when Ubunbtu starts from Adiministrator and then I open Normal user, Normal user doesn't mount the external hd. I've thought that this was the cause of the problem with Windows (If I disconnect the usb hd and I connect it again when I am on Normal user, Normal mounts it and Windows/Normal can r/w, but Windows/administrator doesn't see the hd anymore).

3) To fix the problem I have modified /etc/fstab file in order to make it automatically mount the external hd (I've set the UIDD, the mount point in /media, r/w parameters and so on).

4) Now the external hd is mounted by both users when Ubuntu starts, but there are two (linked) problems: a) on Ubuntu/administrator I see 2 external drive; b) first external hd can0t be accessed (it says it is already mounted), as for the second I only have reading permission. So, I now see the external drive from both Windows users, but I can't write on it!

How can I fix this problem? Sorry but I am a newbie. 
Thanks!

---

### Post by piero1977 on 2012-09-12
Can anyone help me? Please...

---

