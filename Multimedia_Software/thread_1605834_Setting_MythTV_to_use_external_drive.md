---
title: "Setting MythTV to use external drive"
date: 2010-10-25
forum: Multimedia Software
---

### Post by bluetomgold on 2010-10-25
Possibly a very silly question...

I'd like to use my external USB drive with MythTV. This is an NTFS (windows) volume. Ubuntu mounts it automatically as /dev/sdb1

I've created a folder on it called mythtemp, and tried setting the storage directory in MythTV to: /dev/sdb1/mythtemp/

However MythTV says the path does not exist. What am I doing wrong?

---

### Post by bluetomgold on 2010-10-31
Any ideas where I might be going wrong here?

---

### Post by Brasil on 2010-11-01
Stupid question but can you see the drive from anywhere else (eg Thunar)?

---

### Post by bluetomgold on 2010-11-05
The drive is visible on the desktop and from nautilus etc. No idea what Thunar is I'm afraid!

---

### Post by technoboi on 2010-11-08
> **bluetomgold said:**
> 

However MythTV says the path does not exist. What am I doing wrong?
1. Could it be a permissions/ownership problem? Have you set these accordingly. Check your 'does not exist' path properties against those of say, /var/lib/mythtv/recordings/.
'mythtv' should have ownership with appropriate permissions.

2. I don't have Windows so have never tried linking to such a file system. However, a method I have used in Ubuntu, to link to other locations, is to create a symlink.
First rename the recordings directory (so you can put it back to the original if you so wish). Then create a symlink:-
ln -s targetPath&Directory /var/lib/mythtv/recordings

The symlink itself will be owned by root. Don't worry about that but make sure the target is owned by 'mythtv' (Command: ls -l).

Those are just 2 ideas. Let's know how you go on with those.

---

