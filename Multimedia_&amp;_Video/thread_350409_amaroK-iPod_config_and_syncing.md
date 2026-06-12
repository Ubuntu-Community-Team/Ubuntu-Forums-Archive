---
title: "amaroK-iPod config and syncing"
date: 2007-01-31
forum: Multimedia &amp; Video
---

### Post by djangomike on 2007-01-31
ok so i have just built the latest version of amaroK, along with libgpod(every package that i could find), so when i run amarok and then attach my ipod it shows up in my media devices section, but not as an "Apple iPod Device" as i have seen other people say in other threads, it shows up at a "Generic MP3 Player", and shows me the file structure of the ipod which im pretty sure that i dont want to be seeing if i just want to sync my songs over there

any ideas on configuring amarok to actually recognize my ipod correctly

if it is of any importance i can sync with gtkpod but i would like to use amarok for album art and it is a 20gig iPod Color

---

### Post by Maxtorm on 2007-02-01
I installed Amarok the old fashioned way (i.e. via Add/Remove) and it worked as soon as I configured the connection to the iPod via Settings -> Configure Amarok -> Media Devices -> Add Device.  I then just specified the mount point : /media/ipod and it saw the iPod correctly.  It is a 60GB video iPod.

---

### Post by enigma_0Z on 2007-02-02
OK, I'm also wanting to put album art on my iPod with Amarok.

However, for putting music onto an iPod through Amarok, what you need to do is go into Settings>Configure Amarok>Media Devices, and change the "Generic MP3 Player" to "Apple iPod" or similar. I am not quite sure how to get the album art over there yet.

** IF anyone else knows how to get album art onto an iPod from Linux (preferably through amarok), please post... bump **

---

### Post by Maxtorm on 2007-02-02
The album art I had in my Amarok collection automatically came over to the iPod when I transferred files (I think).  

Two things: (1) Do you have your covers updated in your collection?  Go to Tools menu and select Cover Manager.  Are there any missing?  You should be able to fetch missing covers from Amazon.  (2) Have you used the Repair iPod -> Refresh Cover Images command?  With the iPod contents open in the Media Device menu, right-click anywhere in the contents listing and choose Repair iPod -> Refresh Cover Images.

Does that help?

---

### Post by enigma_0Z on 2007-02-04
--edit-- Possibly important, I've got a 2nd gen iPod nano... --edit--

I've got my covers in amarok (well, the ones that have covers, anyway).

I've also tried the Fix iPod>Refresh Covers thing, didn't work.

All of the music on my iPod I copied w/ amarok. What version of amarok are you running?

I put the covers in with iTunes from the other side of my PC (I dualboot for games in Windows), but this is slightly unacceptable, considering all of my music is in Linux.

---

### Post by enigma_0Z on 2007-02-04
aha!!! It *was* important...

After ALOT of digging on the internet, I came up with these sites:

[http://www.makezine.com/blog/archive/2005/09/how_to_ipod_nan.html](http://www.makezine.com/blog/archive/2005/09/how_to_ipod_nan.html)
[http://www.ipodlinux.org/SysInfo](http://www.ipodlinux.org/SysInfo)
[http://www.mediamonkey.com/forum/viewtopic.php?t=10994](http://www.mediamonkey.com/forum/viewtopic.php?t=10994)
[http://www.ipodwizard.net/showthread.php?t=14932](http://www.ipodwizard.net/showthread.php?t=14932)

I almost immedately dismissed them because I have a *2nd* gen nano... HOWEVER: the 2nd gen nano also is missing the "/iPod_Control/Device/SysInfo" file. This would not be a problem, but libgpod uses this file to determine what kind of iPod you have, and consequentially how to transfer the pictures.

More digging found me these links:

[http://ubuntuforums.org/showthread.php?t=293406&highlight=gtkpod+sysinfo+amarok](http://ubuntuforums.org/showthread.php?t=293406&highlight=gtkpod+sysinfo+amarok)
[http://amarok.kde.org/wiki/Media_Device:IPod#Artwork_not_working](http://amarok.kde.org/wiki/Media_Device:IPod#Artwork_not_working)

This article recommends that you use a recent (the most recent, actually) version of libgpod and gtkpod to reset the sysinfo file. However, ubuntu edgy ships with libgpod < 0.4.0, and gtkpod < 0.99.8, which are required for this to work...

After downloading compiling these things (and their deps), I ran gtkpod, and lo and behold, when I hit "Load iPods", it asked me for the generation and type of iPod I had!!!!

After "Loading" my iPod twice, the sysinfo was properly populated.

A quick jaunt over to amarok to "Refresh cover images" and guess what--it works too!!!!

I'm gonna post an article on my blog to help others out...

---

### Post by DianeOfTheMoon on 2007-02-05
Hi, I'm also having a problem with Amarok and my iPod.  I've installed the latest version of Amarok and suddenly, it cannot find my iPod.

I checked the media settings, and it sees the device, but there is no option for 'Apple iPod' or anything similar to select as the device type.

Does anyone know what is going on?

---

### Post by Maxtorm on 2007-02-06
When you go to Settings -> Configure Amarok -> Media Devices -> Add Device, does it not list Apple iPod in the list of device types?

---

### Post by ruhar on 2007-02-06
> **DianeOfTheMoon said:**
> Hi, I'm also having a problem with Amarok and my iPod.  I've installed the latest version of Amarok and suddenly, it cannot find my iPod.

I checked the media settings, and it sees the device, but there is no option for 'Apple iPod' or anything similar to select as the device type.

Does anyone know what is going on?

I can second this.  I installed the latest amarok 1.4.5 from source and there is no longer an option to choose an 'Apple iPod' under the Media Device Section of the Amarok Settings manager.  In the last version (1.4.4) this was not an issue.

---

### Post by ruhar on 2007-02-06
I came across another post on this forum which points to this link:
[http://dot.kde.org/1170628159/1170640766/1170668738/1170673828/1170688921/](http://dot.kde.org/1170628159/1170640766/1170668738/1170673828/1170688921/)

Looks like 1.4.5 needs libgpod 0.4.2.  I'll try upgrading my libgpod and post back if that solved the problem.

---

### Post by ruhar on 2007-02-06
Ok, once I upgraded my libgpod to v0.4.4 and recompiled amarok 1.4.5, all is well with iPod support once again :)

---

