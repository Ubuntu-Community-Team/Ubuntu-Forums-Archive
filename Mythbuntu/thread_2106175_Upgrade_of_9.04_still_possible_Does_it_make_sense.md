---
title: "Upgrade of 9.04 still possible? Does it make sense?"
date: 2013-01-18
forum: Mythbuntu
---

### Post by _Manul_ on 2013-01-18
Hello,

I've been running a combined FE/BE on an EPIA EN12000 board using Mythbuntu 9.04/mythtv 0.22 for roughly three and a half years now. I've basically treated it as an appliance and never upgraded it again once I had it running. The system runs relatively stable with only minor glitches (DVD playback is a bit unreliable, MythArchive with commercial removing sometimes transcodes away the audio, one recent recording will only play back muted).

However, since I just ordered a small SSD to use as a system disk, I thought this might be a good time to try and update the system a little. I can't go beyond mythtv 0.24 since I need Chrome support for the Via board, so I'd aim at upgrading to 10.04 (should be quite mature by now since it was a LTS release) and mythtv 0.24.

The plan is to install the SSD, copy the system over and try the upgrade. If I don't get the system into a stable running state in a reasonable amount of time, I'll just copy the old system from the HD again and continue using that.

Does this plan make sense so far?

If yes, how would I go about the upgrade? I figure, the order of things would be 9.04->9.10->10.04->mythtv0.24. Ist that about right? Or should I upgrade mythtv via 0.23 and possibly even 0.23.1?

I've still found the Mythbuntu 10.04 ISO image, but had no such luck with 9.10. Can I use an Ubuntu alternate CD image to upgrade Mythbuntu to 9.10 or is that missing some packages? Any alternatives? Any chance to still get my hands on a Mythbuntu 9.10 ISO?

A lot of questions, I know - thanks for readings this far. I'll be very grateful for any answers as well as additional hints and thoughts.

All the best,

Manuel

---

### Post by klc5555 on 2013-01-18
Didn't 9.04 just run 0.21, period? I didn't realize they had ever backported 0.22 to it.


Anyway, the important things are your mythconverg database and the recordings themselves. If you have (several) good, reliable backups of your mythconverg database, and if your recordings are safe (for example, on their own storage drive(s)), then my inclination would be to do a clean installation of 10.04. None of the system-slowing cruft that inevitably accumulates after multiple upgrades and endless patching.

Restore your older 0.21 or 0.22 mythconverg from your reliable backups to the new installation, then run mythbackend to allow it to upgrade the older db to the later schema.

---

### Post by _Manul_ on 2013-01-18
Thanks for your answer. Could be that it's indeed 0.21 I'm running, I was going from memory here. According to [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos), 0.22 should have been available for 9.04 though.

I wanted to avoid doing a fresh install since it took me quite a while to get everything running on my first setup - and, fool that I am, I didn't document most of the steps I took. I might try to go that route though, at least I have my old config files around to peek at - and if I don't succeed, I can still go back to my backups and the old system.

---

### Post by _Manul_ on 2013-01-18
If I do a fresh install, should I choose 10.04 (LTS version, possibly quite mature) or 11.10 (newest version that still offers 0.24)? What are people's experiences with these? Or should I start a new thread for this question?

---

### Post by uteck on 2013-01-18
I agree with klc5555, backup your database (which has all your settings) and your recorded shows if they are on the same drive, then do a fresh install on the new disk.  You can then import your database and copy over your recordings and be ready to watch TV.

I would recomend 10.04 since it still has full updates for the next few months before it loses desktop support, but kernel and other areas will be supported till 2015.  11.10 is off support already.

---

### Post by klc5555 on 2013-01-18
I thought 10.04 went over the edge in April; I'd forgotten about later kernel support to 2015. On the other hand, 11.10's 18-month day in the sun ends completely in April.

But the main question, since your hardware is over 3 years old and a bit out of the mainstream, but known to work right with 9.04, is: would the hardware be able to handle the later kernel and later drivers? In particular does your chipset & graphics work right with 3.x kernels in 11.10? For Mythtv 0.24 itself, the OS version won't matter one way or the other.

So since Mythtv 0.24 doesn't care much what it runs on, 10.04 is probably the more responsible choice. And gives you a couple of years of kernel support to shop for newer hardware.

---

### Post by Slim Odds on 2013-01-18
> **uteck said:**
> <cut>
11.10 is off support already.
No, it goes until April 2013

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Ubuntu 11.10 
   [Oneiric Ocelot]("https://wiki.ubuntu.com/OneiricOcelot")
    [Tech]("https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview") / [Rel]("https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes") 
    [October 13, 2011]("https://lists.ubuntu.com/archives/ubuntu-announce/2011-October/000153.html") 
    April 2013
 [(for details)]("https://wiki.ubuntu.com/OneiricOcelot/ReleaseManifest")

---

### Post by _Manul_ on 2013-01-18
Thanks everybody, I'll give 10.04 a try once the SSD arrives and I find a bit of time. It's not so much the mythtv settings I'm worried about but getting all hardware components up and running. I'll post an update here once I get around to trying.

---

### Post by BicyclerBoy on 2013-01-18
Old versions of mythtv did not ship with the dB backup/restore scripts.
[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

I would study this page & confirm the backup script is working before any other step.

You might have problems with via-chrome & the Xorg version in 10.04.

---

### Post by klc5555 on 2013-01-19
Mythtv 0.21 did a weekly backup. These backups should be saved, just in case...

Since 0.21 did precede the "official" backup script, one may do the "up-to-the-minute" backup from a user prompt as follows:```
mysqldump -u mythtv -p[mysql-password] --extended-insert --databases mythconverg > mythdatabase.bak
```

There is no space between -p and the actual password.

Since this command omits the "--no-create-db" and "--add-drop-table" switches, the assumption is that the new, freshly installed but essentially empty Mythtv 0.24 mythconverg will have been dropped before the 0.21 "mythdatabase.bak" is restored into its place. 

The restoration of the saved old database into its new home will be as follows:```
mysql -u mythtv -p[new-mysql-password] mythconverg < mythdatabase.bak
```

Then, of course, starting the backend from a prompt will upgrade the 0.21 db schema to the appropriate point.

---

