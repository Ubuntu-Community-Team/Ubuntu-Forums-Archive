---
title: "My plan for going from 9.10 to 10.04, comments?"
date: 2010-06-11
forum: Mythbuntu
---

### Post by dborn on 2010-06-11
Hi all,

I have two machines in my Mythtv setup: a BE/FE and a separate FE both running Mythbuntu 9.10 quite successfully after many months of fine-tuning.

My plan is to split my OS disks in two partitions (250GB on the BE/FE and 160GB on the FE) and then I will install a fresh Mythbuntu 10.04 on each second partition. Then, I'll need to migrate the 9.10 database onto 10.04 so that I can continue using all my recordings/DVD rips from my other two separate data HDDs (1TB each).

This way, I figure I don't have to deal with the upgrade pitfalls and will have a fallback 9.10 system to use in case of major problems or while I finish setting everything up.

Any thoughts, suggestions, warnings, etc?

Thanks in advance,
Daniel Born

---

### Post by klc5555 on 2010-06-11
> **dborn said:**
> Hi all,

I have two machines in my Mythtv setup: a BE/FE and a separate FE both running Mythbuntu 9.10 quite successfully after many months of fine-tuning.

My plan is to split my OS disks in two partitions (250GB on the BE/FE and 160GB on the FE) and then I will install a fresh Mythbuntu 10.04 on each second partition. Then, I'll need to migrate the 9.10 database onto 10.04 so that I can continue using all my recordings/DVD rips from my other two separate data HDDs (1TB each).

This way, I figure I don't have to deal with the upgrade pitfalls and will have a fallback 9.10 system to use in case of major problems or while I finish setting everything up.

Any thoughts, suggestions, warnings, etc?

Thanks in advance,
Daniel Born

Just the usual question: If your system, fine-tuned "after many months" is running "quite successfully", why upgrade at all? Unless there is a new feature that you need (or really want) in the later version, or a critical bug that is fixed, or improved hardware support that would make your life easier, there is no intrinsic reason to stop running your current version until the wheels fall off the hardware. Because there's always some breakage in upgrading. The danger of perpetual beta code.

That said, your method of upgrading is quite conservative and should work fine. I'd make a couple of backups of the database as described [http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance)
And keep them safe to have on hand in case the database gets nuked in the migration, or if gparted blows up your OS partition when you try the partition splitting process. 

Not that these sorts of things ever happen ...

---

### Post by utar on 2010-06-11
Just to add, if you want to update solely for Myth 0.23 why don't you just use autobuilds:

[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

That way you can have the advantages of using the latest version of Myth without risking something breaking with the OS.

If you want to upgrade for another reason I would be tempted to backup your drives to an external drive given that your system drives are small.  That way you won't need to bother with repartition your drives.



Utar

---

### Post by dborn on 2010-06-11
I guess I want to upgrade so that I don't get left behind on all the great upcoming features of Mythtv. I could use the storage groups for the videos (.iso copies of my DVDs), I now have it setup with an NFS mount for my remote FE. I could use the better handling of different movies by the internal player as I have a few movies right now that don't want to play properly (A/V sync or just plain "weirdness" like each frame alternates between the movie and the main menu screen!?). I could use the built-in handling of my nVidia GT220 HDMI sound so that I don't need to recompile alsa after each kernel upgrade.

I figure once I get on the LTS version of Mythbuntu, I should be good for quite a while before I need to upgrade the O/S again.

I am using the auto builds but am staying on .22 for fear of ending up with a non-functional system.

As I am a software developer by trade and have done some IT work in the past, I've had my share of "why did I have to go and fix that unbroken thing!?" ;)

This is why I am contemplating using a two partition approach with each containing the current and previous versions of Myth so that I can move forward with minimal risks. Our Mythtv system has become quite essential to our TV watching so I'd hate to have to go back to regular "live" TV watching.

I'm already having problems trying to find some "down time" on the backend to perform routine maintenance so going without it for a while is close to unthinkable.

Thanks,
Daniel

---

### Post by tgm4883 on 2010-06-11
> **dborn said:**
> I guess I want to upgrade so that I don't get left behind on all the great upcoming features of Mythtv.** I could use the storage groups for the videos (.iso copies of my DVDs)**, I now have it setup with an NFS mount for my remote FE. I could use the better handling of different movies by the internal player as I have a few movies right now that don't want to play properly (A/V sync or just plain "weirdness" like each frame alternates between the movie and the main menu screen!?). I could use the built-in handling of my nVidia GT220 HDMI sound so that I don't need to recompile alsa after each kernel upgrade.

**I figure once I get on the LTS version of Mythbuntu, I should be good for quite a while before I need to upgrade the O/S again.**

I am using the auto builds but am staying on .22 for fear of ending up with a non-functional system.

As I am a software developer by trade and have done some IT work in the past, I've had my share of "why did I have to go and fix that unbroken thing!?" ;)

This is why I am contemplating using a two partition approach with each containing the current and previous versions of Myth so that I can move forward with minimal risks. Our Mythtv system has become quite essential to our TV watching so I'd hate to have to go back to regular "live" TV watching.

I'm already having problems trying to find some "down time" on the backend to perform routine maintenance so going without it for a while is close to unthinkable.

Thanks,
Daniel

ISO's don't work with storage groups.

Mythbuntu 10.04 will only give you MythTV 0.23 and when released 0.24. No more.

---

### Post by dborn on 2010-06-12
Ah, I thought I read that this would work in 10.04...
Oh well, fortunately NFS works pretty well!

Thanks,
Daniel

---

