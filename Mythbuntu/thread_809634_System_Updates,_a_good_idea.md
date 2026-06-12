---
title: "System Updates, a good idea?"
date: 2008-05-27
forum: Mythbuntu
---

### Post by Steve Goodey on 2008-05-27
Hello,

Do people recommend doing system updates? I've just done a clean install of 8.04, did the updates as suggested then, today I noticed quite a few updates, amongst them it looks like a kernel update. Am I asking for trouble updating when it ain't broke.

Regards, Steve.

---

### Post by freymann on 2008-05-27
> **Steve Goodey said:**
> Hello,

Do people recommend doing system updates? I've just done a clean install of 8.04, did the updates as suggested then, today I noticed quite a few updates, amongst them it looks like a kernel update. Am I asking for trouble updating when it ain't broke.


 I've been letting the updates go through since 7.10 and since upgrading to 8.04. Today's kernel updates didn't cause any grief on all 4 of my machines, or any of the other updates...

 'cept maybe the update in mythbuntu 7.10 when MythTV went to 0.21... but the fix(es) for that were quickly addressed in the forums.

---

### Post by ttlarsen on 2008-05-27
I have just made to days update to kernel to 2.16.24-17 generic. Unfortunately the new kernel will not boot. It stops with the message:
 
ALERT! /host/ubuntu/disks/root.dsk does not exist. Dropping to a shell
BusyBox ...Built-in shell(ash)
(initramfs)

Fortunately the old kernel still works. I will try to uninstall the kernel update

br 
TTL

---

### Post by superm1 on 2008-05-27
Particularly this kernel update has some fixes in the scheduler.  People who were struggling with playing back HD on hardy may have more luck here.

---

### Post by agamotto on 2008-05-27
Depending on how tolerant you are of things hiccuping and other bits, I would have to say no to updates in general with Mythbuntu.  I had a perfectly running system with 7.10, no updates.  I could burn DVDs, recording from multiple channels worked quite well, save for digital telly, and stuff worked well other than MythNews.  I upgraded to 8.04, as I had nothing important for recordings and thought what the hell.  8.04 installed and most of it worked without messing up anything that I had before.  MythArchive refused to work, no matter what options I changed.  It had something to do with not seeing/recognizing my dvd drive.  I assume that it has something to do with the .21 libraries, as everything worked under 7.10 stock install, no updates.  Unfortunately, I don't have the patience to wait weeks or months for the issue to be fixed.  I burn DVDs quite often for when I travel, allowing me to catch up with my  shows while away.  

This is not to take anything away from Mythbuntu, but more a statement of my not being willing to experiment anymore.

---

### Post by laga on 2008-05-28
Well, there's a difference between installing Stable Release Updates and upgrading to the next major release of Mythbuntu (which includes a new release of MythTV, too).

There are more problems bound to happen when upgrading to another release. Stable Release Updates on the other hand should be much safer.

---

### Post by Bubba64 on 2008-05-28
I have all repositories ticked on in software sources except source and medibuntu and two different launchpad there as well and have never had even a hiccup, but I have ancient computers that run off pretty generic drivers nothing cutting edge, this seems to be where the problem generally are.

---

### Post by ptipton on 2008-05-28
The recent update to 2.16.24-17 broke lirc for my PVR150 ir blaster

---

### Post by ozybushwalker on 2008-05-28
I had Mythbuntu 7.10 working fine. I haven't been able to get 8.04 working on either of two systems. One of them doesn't have a necessary instruction and on the other Mythbuntu 8.04 boots up until about when the Mythbuntu screen should display and hangs, only known recovery technique is a power cycle. On and off for about two months (counting the time with the 8.04 betas) I've been trying to figure out where it goes wrong without success. I've gone back to 7.04.

I'm now very cautious about applying upgrades.

---

### Post by koskos on 2008-05-28
Recent kernel update broke my graphics that I devoted so much time to setting up. Obviously poorly tested by the dev team, highly un-recommended.

---

### Post by Juppers on 2008-05-28
Add me to that list as well. 

Check root= bootarg cat/proc/cmdline or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/5be37d33-72c1-4dcd-966c-2f838757f266 does not exist. Dropping to a shell!

---

