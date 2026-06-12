---
title: "Video problem in Wine"
date: 2009-03-17
forum: Multimedia Software
---

### Post by rasmith1959 on 2009-03-17
Hi, I'm trying to get a program to work in Wine and am having some problems.  For the most part it runs just fine, but it also plays a wmv format video on occasion.  When it tries to show the video a window pops up with the title of MCI ERROR across the top and the following text:

The specified device is not installed on the system.  Use the Driver option in Control Panel to install the device.

I have to codecs installed for wmv video as I can open and play them in Movie Player.  So what do I have to do to get this working?  Or is this something that won't work?  If it can't it's something that I can deal with by removing the wmv files from the program folder and it won't try to play them.

---

### Post by gandaran on 2009-03-17
> **rasmith1959 said:**
> Hi, I'm trying to get a program to work in Wine and am having some problems.  For the most part it runs just fine, but it also plays a wmv format video on occasion.  When it tries to show the video a window pops up with the title of MCI ERROR across the top and the following text:

The specified device is not installed on the system.  Use the Driver option in Control Panel to install the device.

I have to codecs installed for wmv video as I can open and play them in Movie Player.  So what do I have to do to get this working?  Or is this something that won't work?  If it can't it's something that I can deal with by removing the wmv files from the program folder and it won't try to play them.
wine programs don't use ubuntu/linux codecs, for a wine player install the windows k-lite codecs package.

---

