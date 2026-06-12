---
title: "Rhythymbox Pseudo-syncing (iPod Touch 4g iOS4.2 w/ Maverick x86 64-Bit)"
date: 2011-02-26
forum: Multimedia Software
---

### Post by cdeli on 2011-02-26
I don't know if the title helped to explain what my computer is doing,  but it is the best way I can put it. I just BARELY got around to  installing the ppa for my iPod (I am very new to ubuntu), and was very  excited to see Rhythmbox finally detect it. This excitement faded away  as I proceeded to put two albums on my iPod, shown on my iPod as  'SYNCING IN PROCESS' and Rhythmbox even displaying the proof that it  transferred to my iPod; but, for some reason, I cannot find the artists  or their albums or songs on my iPod. I even used the search bar on the  home screen, and nothing.

I don't understand, did I forget something? Is there a certain way to do it?

Here is the link to the PPA I installed: [https://launchpad.net/~pmcenery/+archive/ppa/+index?field.series_filter=maverick]("https://launchpad.net/%7Epmcenery/+archive/ppa/+index?field.series_filter=maverick")

Thanks guys.

---

### Post by Kimos on 2011-02-26
I came here to post this same question. I have an iPod touch running 4.2.1 and I am trying to get it to sync with Ubuntu 10.04.2 with no luck.

I have most of my libs all up to date:

```

libimobiledevice-utils/lucid uptodate 1.0.4-1ubuntu1~lucid1
libimobiledevice1/lucid uptodate 1.0.4-1ubuntu1~lucid1
gvfs/lucid uptodate 1.6.2-1ubuntu1~ppa1
libgpod-common/lucid uptodate 0.8.0-1ubuntu1~lucid1
libgpod4/lucid uptodate 0.8.0-1ubuntu1~lucid1
```

I have done pairing and unpairing several times:

```

idevicepair unpair
idevicepair pair
idevicepair validate
```

The device mounts in ~/.gvfs and I created the Device folder has has been specified. I synced some music on a Mac to get the DB all setup on the device. I even generated a HashInfo file on [http://ihash.marcansoft.com/](http://ihash.marcansoft.com/) and dropped it in the folder since it didn't exist from the Mac:

```

$ ls ~/.gvfs/Guide/iTunes_Control/Device/
HashInfo*  SysInfo*  SysInfoExtended*  Trainer/
```

The device detects and mounts and GTKPod and Rhythmbox both will transfer music. The iPod says "Sync in progress" on the screen but it looks like the actual music DB never gets updated. When I unplug it the new music is not detected.

From the [http://www.libimobiledevice.org/](http://www.libimobiledevice.org/) website:

[B]Music/Video Synchronization
Done
4.2.1
Rhythmbox, gtkpod and Amarok sync with latest libgpod >= 0.7.90. The iPhone 4, iPad and Apple TV do NOT work.
[/B]
I had assumed that that means that iPods DO work, but maybe they are implicitly included in with iPhone 4s. I tried this same setup with my wife's iPod Nano 5G and got the exact same result of the music transferring but not appearing in the DB on the device.

---

### Post by cdeli on 2011-02-26
> **Kimos said:**
> [B]Music/Video Synchronization
Done
4.2.1
Rhythmbox, gtkpod and Amarok sync with latest libgpod >= 0.7.90. The iPhone 4, iPad and Apple TV do NOT work.
[/B]
I had assumed that that means that iPods DO work, but maybe they are implicitly included in with iPhone 4s. I tried this same setup with my wife's iPod Nano 5G and got the exact same result of the music transferring but not appearing in the DB on the device.

Agh, crikey. iPhone 4 usually means a unanimous anything that's running iOS; notice the iPad was stated too. 

Another thing I found extremely peculiar, when my Pod is docked and I hit properties on it, it says there is no memory being taken up. Yet when I disconnect it, I have all my apps, pics, and all my songs. Could that help in the diagnosis?

---

### Post by djolk on 2011-03-10
> **cdeli said:**
> Another thing I found extremely peculiar, when my Pod is docked and I hit properties on it, it says there is no memory being taken up. Yet when I disconnect it, I have all my apps, pics, and all my songs. Could that help in the diagnosis?

That interesting - Gnome tells me I have 285mb free on my iPod, yet the iPod says 125mb are free. 

I've also noticed that when I try to sync files from Rhythmbox to my iPod (touch 4g) it goes through the whole pseudo-syncing process (ie files are not visible on iPod afterwards) but disk space on the iPod is used up.

So the files ARE being synced, I imagine the iPod has all these tracks listed in a database, and rythmbox is not updating this.

Ugh.

I was so excited, I thought it was going to work.

---

### Post by JacobVengeance on 2011-03-23
> **djolk said:**
> That interesting - Gnome tells me I have 285mb free on my iPod, yet the iPod says 125mb are free. 

I've also noticed that when I try to sync files from Rhythmbox to my iPod (touch 4g) it goes through the whole pseudo-syncing process (ie files are not visible on iPod afterwards) but disk space on the iPod is used up.

So the files ARE being synced, I imagine the iPod has all these tracks listed in a database, and rythmbox is not updating this.

Ugh.

I was so excited, I thought it was going to work.

Chances are it is saying on the entire memory, including the System partition which is not included from the About screen on your iPod.

---

