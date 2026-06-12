---
title: "Advice on a major upgrade/reinstall - 0.21 on Gentoo to Mythbuntu 9.10 w/ 0.22"
date: 2009-11-08
forum: Mythbuntu
---

### Post by Entropy512 on 2009-11-08
OK, as implied in my other post asking about 0.21 frontend packages to let my desktop setup "limp along" until I can upgrade my backend machine:

I am going to be embarking on a MAJOR backend upgrade in the next 1-2 weeks.

Does anyone have any advice on what "gotchas" I might encounter during this upgrade - Gentoo with a 0.21 backend with mythstore on an LVM + RAID array to Ubuntu Server 9.10/Mythbuntu 9.10?

Specifics of the system:
Long ago, for flexibility I split each 250GB hard drive in the array into 50GB partitions.  I then took one 50GB partition from each drive and RAID 5ed them together.  I did this for all but one of the 50GB partitions on each drive and LVMed the arrays together in one big volume group.

The remaining 50GB partition on each drive is used for:
OS on first hard drive
RAID 0 "fast temporary scratch space" (used for compiles in Gentoo) array made from the partitions on the other drives

The short of it is:
I have my Myth storage volume on a RAID + LVM array that I THINK can survive an OS reinstall.  (I intend to fully back it up anyway!)
The OS partition of the backend machine is on a standard non-RAID/LVM partition

Now, I figure my upgrade/migration process is going to be:
Do an SQL dump of my mythconverg database
Back up the RAID partitions to a 1TB hard drive on order from Newegg
Nuke the Gentoo OS partition with Ubuntu 9.10 server
Get the server basics (Samba, etc) tweaked and configured
Add Mythbuntu to the server
Restore the SQL dump from the first step
Start the backend and pray

Should I restore the SQL dump before adding Mythbuntu to the server machine instead of after?

Any "gotchas" I should be aware of?

Tuner configuration on the backend is as follows:
1 dual-tuner Happauge PVR-500 for analog
1 dual-tuner Silicon Dust HDHomeRun for digital

---

### Post by nickrout on 2009-11-08
for database issues see here:

[http://ubuntuforums.org/showthread.php?t=1313159](http://ubuntuforums.org/showthread.php?t=1313159)

I would use mythbuntu CD rather than server+mythbuntu packages, just cos I see less problems with this. However maybe your raid/lvm requires a server or alternate install? (It shouldn't if your root partition isn't on raid/lvm).

As a former gentoo fanboy, who moved to knoppmyth then mythbuntu, I say "welcome". Gentoo was fun, but required waaaay too much fiddling to get myth going successfully (for me).

---

### Post by yonkiman on 2009-11-08
> Nuke the Gentoo OS partition with Ubuntu 9.10 server

If you can avoid it, I'd recommend *not* nuking your original system.  I'd resolved to spend a weekend upgrading my 8.04/0.21 system several times over the last 18 months.  I'd get a day or two into it but something wouldn't work or I'd hose something, so at the end of the weekend I just went back to my original, working, reliable install and continued to enjoy MythTV uninterrupted.

I finally did successfully upgrade to 9.10/0.22 a week or two ago and am very happy.  However I still occasionally need to look at some random config files or grab something I forgot from the 8.04 system to remind myself of something I'd tweaked.  

And if you do that, it doesn't matter whether or not you forgot anything on your list - you can always fix it later!

Good luck!

---

### Post by Entropy512 on 2009-11-09
I'll see if I can sanely do a full backup of the OS partition.

Problem is that as the other machines on my network go through upgrades, the 0.21 backend becomes less and less useful.  I now cannot watch from the desktop or the laptop (both are 9.10), and the HTPC (which still has 0.21) has been a little ornery lately.

Gentoo still is a very flexible distro, but it used to also be "cutting edge", but not any more. KDE 4.x has been a part of stable Kubuntu releases for over a year now, while in Gentoo they somehow have decided that it's OK to have a note saying "unsupported by upstream" for 3.5 without unmasking anything from 4.x.  Since moving to 4.x on Gentoo, upgrading my system has been a nightmare every time, even for minor upgrades.

The flexibility and (in theory) small performance increases are offset by the massive amount of time invested.  It used to only take a few hours to do an "emerge -uDNv world" even with a majorly neglected system, now even a minor upgrade often turns into a weekend project.

In my case my Myth setup is pretty basic - just recordings with one backend and one storage location, no MythVideo archives, etc.

---

