---
title: "mediatomb premissions cant acess media drive"
date: 2009-12-08
forum: Multimedia Software
---

### Post by burntresistor on 2009-12-08
I keep all my media on a different drive. When I try to add that drive in media tomb it says I dont have permissions to do so. I tried  chmod 777 pointed to the selected drive which didn't work. Its annoying I'm having to log into windows to use tversity to stream anything

drwx------ 1 burntresistor burntresistor 28672 2009-12-11 11:28 411C80AC517E1FE9
lrwxrwxrwx 1 root          root              6 2009-10-26 17:47 cdrom -> cdrom0
drwxr-xr-x 2 root          root           4096 2009-10-26 17:47 cdrom0
drwx------ 1 burntresistor burntresistor 16384 2009-12-13 11:43 New Volume

---

### Post by burntresistor on 2009-12-13
bump  I was doing some reading chmod 777 is used for read write and executable and the reason it could not be working is cause you can't set a drive as executable? Just trying to go into the drive in question from terminal cd (drive name) its bashing the command. I can enter it fine in computer,
I am using the name shown after doing the ls command in media.

---

