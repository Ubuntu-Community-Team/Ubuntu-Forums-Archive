---
title: "Rythmbox (Sansa Fuze)"
date: 2010-04-29
forum: Multimedia Software
---

### Post by n2o-Gr55 on 2010-04-29
I got a Sansa Fuze today, and i wanted to load my music on it, using Rythmbox.

I transfered over 221 songs, 29 of which did NOT transfer, and returned the error

Unable to send file to MTP device: PTP Layer error 200f: send_file_object_info(): Could not send object info.

There was no relation to the files, different artists and albums. Anyone know of a way to fix this? Any help would be appreciated.

Also, running Lucid Lynx

-n2o-Gr55

---

### Post by HyperFlexed on 2010-05-31
Don't know of a fix myself, but I have the same player, same problem.

---

### Post by Guitar John on 2010-05-31
You can just drag files/folders into the Fuze.  Change the mode on the Sanza from MTP to MSC.  Much easier.

---

### Post by HyperFlexed on 2010-05-31
Found a fix. At first I was getting error messages, but then rhythmbox was crashing and my fuze was acting funny. Ended up here:

[https://bugs.launchpad.net/ubuntu/lucid/+source/rhythmbox/+bug/569380](https://bugs.launchpad.net/ubuntu/lucid/+source/rhythmbox/+bug/569380)

They recommend upgrading to the lucid-proposed versions of rhythmbox.

```
sudo apt-get upgrade rhythmbox/lucid-proposed
```

It worked for me. If it works for you, sign in and leave a comment letting them know that it worked. Happy fuze-ing :)

---

### Post by HyperFlexed on 2010-05-31
> **Guitar John said:**
> You can just drag files/folders into the Fuze.  Change the mode on the Sanza from MTP to MSC.  Much easier.

Fine if you don't have an SD card. I, however, have an SD card, and it's annoying that the player shows up in rhythmbox as 2 separate devices. MTP is the way to go in this regard. Also, in MSC mode, deleting files leaves behind a .trash-xxx folder, which has caused this device to crash. Either way, I outlined a working solution in my previous post.

Edit: I know now that you can reconfigure nautilus to create a proper delete action (getting rid of the .trash issue). I still prefer to have rhythmbox see my device as a single unit.

---

### Post by HyperFlexed on 2010-05-31
spoke too soon. This bug seems to be very intermittent. &(^#)&($^()&^#^*$#

MSC mode it is. It'd be nice if a plugin could be written so that rhythmbox consolidates the two volumes under a single device. Even better if it could be intelligent enough to put podcasts in the podcast folder, music in the music folder etc.

---

### Post by denlord on 2010-07-25
Had the same problem. Upgrading the firmware on the view solved the issues. 

Firmware version - 01.03.02
Rhythmbox version - 0.12.8

Hope that helps.

---

### Post by HyperFlexed on 2010-07-26
> **denlord said:**
> Had the same problem. Upgrading the firmware on the view solved the issues. 

Firmware version - 01.03.02
Rhythmbox version - 0.12.8

Hope that helps.

I'm guessing you have a Fuze V1.

My firmware: 2.03.33A

Rhythmbox doesn't seem available in stable form for my version of the fuze :(

---

### Post by scottmuz on 2010-08-04
Been battling with a similar issue with my Sansa Clip.

Was detected in Nautilus but not Rhythmbox.

I fixed by following instructions here [http://wiki.birth-online.de/know-how/hardware/sandisk-sansa-fuze/rhythmbox](http://wiki.birth-online.de/know-how/hardware/sandisk-sansa-fuze/rhythmbox)

---

### Post by cdated on 2011-01-29
> **scottmuz said:**
> Been battling with a similar issue with my Sansa Clip.

Was detected in Nautilus but not Rhythmbox.

I fixed by following instructions here [http://wiki.birth-online.de/know-how/hardware/sandisk-sansa-fuze/rhythmbox](http://wiki.birth-online.de/know-how/hardware/sandisk-sansa-fuze/rhythmbox)

Worked great for me.  My Sansa Clip+ also has a microSD slot where most of my music lies.  So I added a .is_audio_player file there too and sync in MSC mode.

---

