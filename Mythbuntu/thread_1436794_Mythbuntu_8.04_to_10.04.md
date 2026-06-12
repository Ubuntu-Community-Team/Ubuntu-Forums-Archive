---
title: "Mythbuntu 8.04 to 10.04"
date: 2010-03-23
forum: Mythbuntu
---

### Post by jbman on 2010-03-23
Hi guys,

I have been waiting for 10.04 to become ready to upgrade my 8.04 0.21-fixes mythbuntu box.

If I do it now with the update-manager -d command or wait till 10.04 is officially released, will it be a simple upgrade for mythtv? Will the database from 0.21 be converted over for me during this process or are there other steps I am going to have to take to move from 0.21-fixes to 0.23 via mythbuntu?

Cheers in advance.

---

### Post by ian dobson on 2010-03-23
Hi,

If you upgrade from 8.04 to 10.04 you'll have to upgrade to 9.10 first then 10.4.

The mythtv database should be converted to the new database schema. I say should as it doesn't always work, conversion involves reading/updating all tables in the database and can uncover corruption.

I've done several mythbuntu upgrades on several systems in the last 6 months or so and I only once had problems with the database. In this case the db harddisk was almost dead before I started the upgrade.

Regards
Ian Dobson

---

### Post by nickrout on 2010-03-23
back up your database to somewhere it will not get overwritten.

See this page. [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore) 

Read ALL of it. Do not use other methods. If something goes wrong email the mailing list and undoubtedly Mike will have some tips.

---

### Post by tgm4883 on 2010-03-23
> **ian dobson said:**
> Hi,

If you upgrade from 8.04 to 10.04 you'll have to upgrade to 9.10 first then 10.4.

The mythtv database should be converted to the new database schema. I say should as it doesn't always work, conversion involves reading/updating all tables in the database and can uncover corruption.

I've done several mythbuntu upgrades on several systems in the last 6 months or so and I only once had problems with the database. In this case the db harddisk was almost dead before I started the upgrade.

Regards
Ian Dobson

Has this been tested? There shouldn't be any need to upgrade to 9.10 first then to 10.04 (in fact, that would be not recommended)

---

### Post by nickrout on 2010-03-23
> **tgm4883 said:**
> Has this been tested? There shouldn't be any need to upgrade to 9.10 first then to 10.04 (in fact, that would be not recommended)

I thought you usually had to go through each intermediate version, or is there a dispensation for LTS-->LTS?

That would be sweet as my backend is at 8.04/myth-0.21. A smooth upgrade path straight to 10.04 would be super!

---

### Post by tgm4883 on 2010-03-23
> **nickrout said:**
> I thought you usually had to go through each intermediate version, or is there a dispensation for LTS-->LTS?

That would be sweet as my backend is at 8.04/myth-0.21. A smooth upgrade path straight to 10.04 would be super!

LTS->LTS should work. We are still testing it, but that should be fine. That is a canonical supported upgrade path last I checked.

---

### Post by jbman on 2010-03-23
Cheers for the info.

Not sure how I would go from 8.04 to 9.10 then to 10.04. LTS to LTS was my understanding as well, and this is why i stayed with 8.04.

I think I will do a full HDD image and try the update to 10.04 and see how it goes.

---

### Post by jbman on 2010-04-13
Update:

I took the plunge and upgraded to 10.04 Beta 2 via the update manager

couple of hitches along the way

I had [www.avenard.org](www.avenard.org) 0.21-fixes on my machine, they didn't seem to uninstall correctly after reboot so I had to totally remove mythtv and reinstall. I did so with the auto builds.

I was using WICD for my wifi network as I had troubles with network manager in 8.04, WICD updated ok, however on reboot I had no WIFI. I removed WICD and installed the normal network manager from the CD that I downloaded of mythbuntu 10.04 beta 2 as a backup.

Very happy so far, everything is running well except my Twinhan USB IR.

Before it just plugged in and came up as a USB HID and when I pressed a key on the remote a keyboard key press would come up. Right now, the device shows its installed, but when i press a key I get nothing. I have been reading some new patches were done to the twinhan-hid driver to make the buttons all work, but this might have killed mine or its simply a case that 10.04 is beta so it might get fixed before final release.

So anyone who has been sitting on 8.04 LTS like myself, the update was not too much trouble at all.

---

### Post by newlinux on 2010-04-19
> **jbman said:**
> Update:

I took the plunge and upgraded to 10.04 Beta 2 via the update manager

couple of hitches along the way

I had [www.avenard.org](www.avenard.org) 0.21-fixes on my machine, they didn't seem to uninstall correctly after reboot so I had to totally remove mythtv and reinstall. I did so with the auto builds.

I was using WICD for my wifi network as I had troubles with network manager in 8.04, WICD updated ok, however on reboot I had no WIFI. I removed WICD and installed the normal network manager from the CD that I downloaded of mythbuntu 10.04 beta 2 as a backup.

Very happy so far, everything is running well except my Twinhan USB IR.

Before it just plugged in and came up as a USB HID and when I pressed a key on the remote a keyboard key press would come up. Right now, the device shows its installed, but when i press a key I get nothing. I have been reading some new patches were done to the twinhan-hid driver to make the buttons all work, but this might have killed mine or its simply a case that 10.04 is beta so it might get fixed before final release.

So anyone who has been sitting on 8.04 LTS like myself, the update was not too much trouble at all.

This is good to know, as all of my servers are on 8.04 running myth .21. Don't want to reconfigure all the various server config files if I don't have to. I'll wait until a couple of weeks after official release, but then I'll upgrade master, then slave backends and fileservers, then laptops/frontend only machines (which are on 9.04 so they'll need to go to 9.10 then 10.04).

---

### Post by newlinux on 2010-06-02
for what it's worth, I upgraded my machines. My experiences were somewhat detailed at [avsforum here]("http://www.avsforum.com/avs-vb/showthread.php?p=18715541#post18715541"). For all but one machine it was successful, and probably would have been for all if it weren't for the flashplugin-nonfree I installed in 8.04.  I maybe could have spent more time to figure out how it was screwing up apt, but I it didn't take long to restore my apps from a fresh install.  Upgrading myth was easy.

---

### Post by new_tolinux on 2010-06-02
> **newlinux said:**
> for what it's worth, I upgraded my machines. My experiences were somewhat detailed at [avsforum here]("http://www.avsforum.com/avs-vb/showthread.php?p=18715541#post18715541"). For all but one machine it was successful, and probably would have been for all if it weren't for the flashplugin-nonfree I installed in 8.04.  I maybe could have spent more time to figure out how it was screwing up apt, but I it didn't take long to restore my apps from a fresh install.  Upgrading myth was easy.
Any ideas why you had to remove the mythbuntu desktop?

As I update ubuntu I don't have to remove gnome, I can actually use the graphical update-manager to upgrade the system, so it seems a bit odd to me that I'll have to remove the desktop when I'm going to update mythbuntu.

---

### Post by newlinux on 2010-06-02
A bug in update-manager.
mythbuntu-desktop is just a meta package, it doesn't actually remove the desktop. The error I was getting is a known issue that many others ran into with alternate desktops. I use gnome anyway even if it had removed xfce.

[http://ubuntuforums.org/showthread.php?p=9230993](http://ubuntuforums.org/showthread.php?p=9230993)
[http://swiss.ubuntuforums.org/showthread.php?t=1466387](http://swiss.ubuntuforums.org/showthread.php?t=1466387)

---

### Post by new_tolinux on 2010-06-03
> **newlinux said:**
> A bug in update-manager.
mythbuntu-desktop is just a meta package, it doesn't actually remove the desktop. The error I was getting is a known issue that many others ran into with alternate desktops. I use gnome anyway even if it had removed xfce.

[http://ubuntuforums.org/showthread.php?p=9230993](http://ubuntuforums.org/showthread.php?p=9230993)
[http://swiss.ubuntuforums.org/showthread.php?t=1466387](http://swiss.ubuntuforums.org/showthread.php?t=1466387)
My mistake then.
I assumed that I had to remove the complete graphical interface. I thought mythbuntu-desktop was the same as xcfe (actually I didn't even remember the name of xcfe).

---

