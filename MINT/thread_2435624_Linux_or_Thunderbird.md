---
title: "Linux or Thunderbird?"
date: 2020-01-23
forum: MINT
---

### Post by driveyousteadybor on 2020-01-23
Hi, all - my first post here.

Yes the title is intentional - I'm trying to move away from Windows to Linux, and have installed Linux Mint 19.3 as dual-boot with my existing Win7. Both O/S's are on a SSD, and documents and emails stored on a separate HDD. I've got Palemoon working more-or-less as I'm used to, but have hit a brick wall with Thunderbird. My old system still runs v2.0.0.24 (Yes - I know...), but it always worked fine with the non-default directories. However when trying to configure v68.4.1 already installed on Mint I have run into serious problems. I can set up new accounts (all POP3), point each one to the existing locations on the HDD, and all the folders and messages appear as they should. I can send and receive messages between them, shut Thunderbird down, reopen and all is fine. I then re-boot into Win7 and see the new messages - just as I was able to do previously with a XP/Win7 dual-boot set up on my late parents PC. If I then re-boot into Mint, and fire up Thunderbird, when it does open either: 1) the accounts are missing - it's as if they were never created, or 2) If I've loaded the previous working profile with Profile Manager the accounts usually show, but none of the folders & sub-folders until I once more point it to the correct directories when they re-appear, but this only holds until closing Mint.

Searching reveals many similar complaints and this Bugzilla post in particular: [https://bugzilla.mozilla.org/show_bug.cgi?id=1542025](https://bugzilla.mozilla.org/show_bug.cgi?id=1542025)  It seems to be marked as "Fixed" but I didn't see anything which resolves my problem. I can't try an older (v60) version as the Software Manager only lists the latest one, and my efforts to get v60 via the PPA route also installs v68. Considering that once setup Thunderbird 68 DOES work fine with my existing files & folders there doesn't seem to be a problem with "old vs new", it's just the settings not being remembered on shut-down. I've created/tried/deleted many different profiles, in various locations (the default) as well as the HDD and the same thing happens every time. So my question is this: Is this a Linux or a Thunderbird v68 bug? I have installed Sea Monkey (which appears to be based on an earlier Thunderbird) but that doesn't "See" the original folders at all...

Any ideas? -

---

### Post by CatKiller on 2020-01-23
From your description it sounds to me more that you've got your Thunderbird config files on your Windows partition, but that partition isn't being automatically mounted until you manually access it, so as far as Thunderbird is concerned those files simply don't exist.

---

### Post by driveyousteadybor on 2020-01-23
> But that partition isn't being automatically mounted until you manually access it


@ CatKiller - you may have found the answer! It's not the location of the Profile - even when it's in the "Home" folder the problem occurs. What I've found is if I start Mint, access the HDD, ***and play an audio file from it*** (the one I have to announce new emails), THEN start Thunderbird it seems to load up with the accounts and folders visible. If I simply start it without having accessed the HDD then only the accounts show, and no folders are visible. Can you explain more about Linux "Mounting" a volume, and is there a better way to get round this, other than remembering to play the file (I have put a shortcut on the  desktop) before running Thunderbird? It's not a perfect solution, but at least I can now use it without major hassle.

---

### Post by ajgreeny on 2020-01-23
*Thread moved to **MINT**.* which is more appropriate and a better fit.

Mint is based on Ubuntu but is very different in many ways so you could well get better answers from other Mint users here.

---

### Post by CatKiller on 2020-01-23
> **driveyousteadybor said:**
> Can you explain more about Linux "Mounting" a volume

It's how different filesystems get attached to the filesystem tree. The location in the filesystem tree where a filesystem gets attached is called the mount point, and accessing that location shows you the files on that filesystem. The filesystems you attach could be different partitions, or filesystems from another machine through NFS, Samba, or whatever.

The file that controls which filesystems get automatically mounted at boot time, and where they are attached, is **/etc/fstab**. There's quite a lot of information available about it already. From your description I'm guessing that it's an NTFS partition that you want to be mounted automatically.

---

### Post by driveyousteadybor on 2020-01-23
Thanks ajgreeny.

I've now found that first playing the audio file from a desktop shortcut DOES NOT WORK!  However, navigating to it via "Computer" >> "26GB Volume" >> "Email" >> and playing the audio file ***does*** work, and Thunderbird then starts up with everything showing. I presume this because it's not actually a "Shortcut" in the Windows sense, but a copy on the desktop itself - is this correct? If so, is there another method to make the process simpler? A bit of a long winded way to get my emails, but I suppose it's better than going down the Win10 route. I specifically didn't want to move the folders to the Linux partition as I want to keep a fall-back available, via Win7. As I said earlier, this arrangement worked O.K. with 2 Windows O/S's but they shared the same file systems...

---

### Post by driveyousteadybor on 2020-01-23
@ CatKiller - Thanks, and I found this: [https://www.maketecheasier.com/easily-automount-windows-ntfs-partition-in-ubuntu/](https://www.maketecheasier.com/easily-automount-windows-ntfs-partition-in-ubuntu/)  If it's what you are describing, I'll give it a go.

---

### Post by TheFu on 2020-01-23
Be very careful using random google answers with a Linux system. Sometimes those are for the wrong OS, wrong version, or just oversimplify answers hoping that your needs are also the same.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Note the "ubuntu" in the domain name?

There are a few different ways, but a minimal amount of understanding about the difference between system config files and how to safely edit those is required.

---

### Post by driveyousteadybor on 2020-01-23
@ TheFu - Point taken, but the "*ntfs-config" *GUI programme in my link is available from the Software Manager, so I would have thought it was trustworthy? I should have said earlier that the full description of my O/S is "Linux Mint 19.3 Cinnamon" edition. As far as I'm concerned, I either use a GUI based method to select "Automount" or I'll just have to go through the long-winded process of accessing the file manually on each startup. I'm afraid that any post/ answer which involves numerous lines of code running in Terminal immediately makes my eyes glaze over.  Sorry, but that is not for beginners - or even 10+ year MS users, and I've done a little Registry editing and Command Prompt work in that time!

---

### Post by TheFu on 2020-01-23
> **driveyousteadybor said:**
> @ TheFu - Point taken, but the "*ntfs-config" *GUI programme in my link is available from the Software Manager, so I would have thought it was trustworthy? I should have said earlier that the full description of my O/S is "Linux Mint 19.3 Cinnamon" edition. As far as I'm concerned, I either use a GUI based method to select "Automount" or I'll just have to go through the long-winded process of accessing the file manually on each startup. I'm afraid that any post/ answer which involves numerous lines of code running in Terminal immediately makes my eyes glaze over.  Sorry, but that is not for beginners - or even 10+ year MS users, and I've done a little Registry editing and Command Prompt work in that time!

If you aren't willing to modify a simple text config file, you'll be missing out on 80% of the power for any computer, including MS-Windows.  Your choice.  Not all configurations on Linux have a GUI tool to modify them.  Being afraid to enter 6 field seems like worrying over next to nothing.  Just make a copy of the file before starting. If you mess up, you can put that back.

Completely unrelated, but I think the change to registry in Windows was a mistake and where Gnome has followed that technique - I think is also a mistake - talking about dconf. Learn more about it, if you care with **man -s 7 dconf**.

I also think that "Software Manager" is a mistake. It has dumb-ed down software management way, way, way, too far. Synaptic is the GUI for software management if you must have a mouse.  Aptitude if you don't need a mouse or there is always apt and apt-get if you don't want to waste time.

I'm sorta surprised that NTFS can be used for any thunderbird profile data.  Permissions on files and directories matter in Linux, so using a file system that doesn't support permissions just doesn't make sense.  I would just rsync the data back and forth automatically, but that's me.

---

### Post by coffeecat on 2020-01-23
> **driveyousteadybor said:**
> @ TheFu - Point taken, but the "*ntfs-config" *GUI programme in my link is available from the Software Manager, so I would have thought it was trustworthy? 

A few years ago, I used to regularly help users who got into a pickle with that particular GUI app. My main advice then: don't use it! I don't think there has ever been a GUI app for helping with mounting ntfs filesystems that hasn't exhibited serious problems. I agree with TheFu. There is no substitute for learning to manually configure /etc/fstab. It's not actually that hard.

A more general point. The howto you linked to is almost 7 years old. That is old. Linux-based operating systems develop fast, and there have been many important changes in the last few years. If you must surf the internet for howtos and tutorials be wary of ones that are not recent, and please be aware that there is a lot of stuff out there which is just plain bad. Just because it sounds good and is well presented visually does not necessary mean it is technically trustworthy.

Last point - you are welcome to post your questions here, but our main focus is Ubuntu and the official flavours. Mint is derived from Ubuntu, but is not Ubuntu, nor one of the official flavours. Mint has their own forum, here: [https://forums.linuxmint.com/](https://forums.linuxmint.com/) It's an excellent forum. You might find it useful. Some of our regulars here are also regulars there. 

> **TheFu said:**
> 
I'm sorta surprised that NTFS can be used for any thunderbird profile data.  Permissions on files and directories matter in Linux, so using a file system that doesn't support permissions just doesn't make sense.

Yes it is surprising, but it does work. Or, at least it did when I last tried what I think the OP is trying to achieve. I had a dual-boot with Windows and Ubuntu, and a shared Data partition formatted ntfs. I put my thunderbird config files in a ".thunderbird" folder inside a "home-configs" folder on the ntfs Data partition, and then simply created a "~/.thunderbird" symlink to the hidden folder in the ntfs partition. If I upgraded Ubuntu by making a fresh installation instead of do-release-upgrade, I simply had to create the ~/.thunderbird symlink in the new installation and carry on as before.

Once, in a fit of masochistic enthusiasm, I found where the Windows equivalent of ~/.thunderbird was and created whatever Windows calls their equivalent of a symlink to .thunderbird in the ntfs partition. Gratifyingly, it worked, and I was able to alternate between Windows and Ubuntu, open thunderbird in whichever OS I was working and update my thunderbird data ad lib, and then find the new data in the "other" OS.

Those days are gone. I have abandoned Windows, and you'll be glad to hear that my Data partition is now formatted ext4. :)

---

### Post by driveyousteadybor on 2020-01-24
O.K. - I'm suitably chastised! Now that I know NTFS partitions aren't automatically mounted on startup - and having discovered there's a "Mount/Unmount" option in the right click menu under "Computer" - I have just tried booting first into Windows, then re-booting into Mint and mounting both those volumes first. Thunderbird then started up fine. It's not the best solution, but for now, I'm happy with it. I also noticed that an SD card I always have inserted in the laptop WAS mounted on startup - is this because FAT32 is a common format used by all systems? Maybe I'll revisit the posts about editing the config file at a later date, and I'll check out the Mint forum as well.

---

### Post by TheFu on 2020-01-24
FAT32 is a foreign file system, like NTFS and exFAT.  The drivers run in userland and are slow due to the extra layers necessary to access the storage. 
Native Linux storage has kernel-level drivers and are much faster.

We all have to make compromises to access non-native storage.

---

