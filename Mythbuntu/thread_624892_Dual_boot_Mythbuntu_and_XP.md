---
title: "Dual boot Mythbuntu and XP"
date: 2007-11-27
forum: Mythbuntu
---

### Post by Abrupto on 2007-11-27
Hi

I'm a newbie on Linux so pardon me for my question. Is it possible to install Mythbuntu on a different partion of a disk that already have XP runnig, and dual boot ? Should I install first Ubuntu in a dual boot configuration and after install Mythbuntu?

Do you know any tutorial to help me on this?

Tanks! 

Regards
Abrupto

---

### Post by Cryophallion on 2007-11-27
> **Abrupto said:**
> Hi

I'm a newbie on Linux so pardon me for my question. Is it possible to install Mythbuntu on a different partion of a disk that already have XP runnig, and dual boot ? Should I install first Ubuntu in a dual boot configuration and after install Mythbuntu?

Do you know any tutorial to help me on this?

Tanks! 

Regards
Abrupto

It should be possible with the livecd. Otherwise, you could use the gparted livecd to partition for you first, then install mythbuntu. Just make sure that you run xp first after resizing the partition, otherwise you won't see the windows partition at first (weird thing with windows having to allocate - same problem happens when you dump out of windows instead of shutting it down properly).

However, there are other things to consider. When you have xp running, your myth backend can't be running, and therefore you can't be using it, whether for timed recording or watching. Second, you want all the disk space you can get, and you probably are going to want to leave some head room in your xp partition.

A friend of mine had a vmware server running xp on his myth box so he could run Quicken. He made sure he had 2 gigs of ram, so it flew pretty well (this is an older athlon 2800 box). That way, the backend can still be running, and you can do the things you want. 

If you plan on using your myth box sparingly, and want to play games when not recording/watching, I guess it will work. However, I am sure there will be a frustrating day when you are recording and want to play. I would go vmware for flexibility (plus you can have the xp partition take up drive space as it needs it, instead of taking up a huge chunk of the drive it doesn't need). 

Best of luck.

PS - One other note - decide if you want to take the risk of lvm now. If you have a separate drive/drives to record to, it is probably best to leave the boot part normal, and use only the extra drive as lvm, in case something crashes. You want to be able to recover. DO NOT try and lvm your windows part.

---

### Post by NickGray on 2007-11-29
First time MythTV user, and I got Mythbuntu booted up in VMWare Workstation (XP) within thirty minutes. Just having some problems with full screen resolution now.

I am only loading it on my XP machine for testing purposes. But the whole process was very simple and quick.

---

### Post by superm1 on 2007-11-29
You won't really be able to test much unless you have network tuners or remote backends setup elsewhere.

Ubuntu has a bug with vmware that it by default chooses a much higher resolution by default.

---

### Post by road2elysium on 2007-11-29
You might also want to try out VirtualBox - I have a XP VM running in that.

---

