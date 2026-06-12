---
title: "Mounting external hard drive(mint) as root to windows host"
date: 2020-03-09
forum: MINT
---

### Post by Creenome on 2020-03-09
I'm having a problem with accessing root files on my mounted Mint hard drive and can't seem to find an answer. It's starting to give me a headache and I feel like I'm getting further away the longer I research.

I'm using a 32 bit version of Win8.1

I'm using EXT2 to mount my Mint Hard drive as read only. I can access the standard files fine. The only problem is that the HD isn't mounting as root. It's my understanding that I can root my HD with EXT2 using the UID and GID but I can't access those files through EXT2 as they're located on a SWAP partition. 

Is there a way to pull User Info from a SWAP partition externally? 

And it this even the correct process for doing this?

I feel like I'm probably making this harder than it is, but then again, I'm tired and have been working on this for a good part of the day.

Any help would be greatly appreciated. 

Thanks

EDIT: I can't boot from my HD and recover files the easy way because the older laptop that I have access too doesn't support USB 3.0 boot.

---

### Post by yancek on 2020-03-09
I am having a really difficult time making sense of your post??  Where is Mint?  Is it an actual, full install of Linux Mint on an internal or external hard drive (which one please).  How does windows 8 fit in?  A default windows installation is incapable of reading or writing to/from any Linux filesystem.  What does 'accessing root files' mean in your case?  A standard user on Linux systems cannot access root owned files by design.  Why are you trying to access those files in this manner?  Why don't you just boot Mint to access them?  Or is that the problem, that your boot has been messed up and you can't boot Mint?  Is this your problem actually, you need to accesss/save file from Mint and are unable to boot it?

---

### Post by Creenome on 2020-03-09
> **yancek said:**
> I am having a really difficult time making sense of your post??  Where is Mint?  Is it an actual, full install of Linux Mint on an internal or external hard drive (which one please).
It's a full install of Mint Cinnamon on an INTERNAL HDD. My mistake.

> **yancek said:**
> How does windows 8 fit in?
Windows 8.1 is the OS on the Host machine attempting to access the files on the Mint System.

> **yancek said:**
> A default windows installation is incapable of reading or writing to/from any Linux filesystem.
If this was true I wouldn't be able to use EXT2 to pull any files from my Linux install. Which I can. I just can't access ROOT folders such as .gnupg

> **yancek said:**
> What does 'accessing root files' mean in your case?
By accessing ROOT files I mean, reading them. To recover info.

> **yancek said:**
> Why are you trying to access those files in this manner?  Why don't you just boot Mint to access them?  Or is that the problem, that your boot has been messed up and you can't boot Mint?  Is this your problem actually, you need to accesss/save file from Mint and are unable to boot it?
I need to pull my ~/.gnupg folder. I would boot from the HDD, but I cannot. My laptop does NOT support booting from USB 3.0 which my external HDD Dock uses. The install has zero issues.

Futhermore, since GNUPG requires ROOT permissions(a login), I cannot access this information using EXT2.

---

### Post by CelticWarrior on 2020-03-09
Perhaps we should start by clarifying the "EXT2" reference... I think you don't mean the EXT2 file system (old, pretty much everything uses EXT4 nowadays) but the [ext2fs]("http://e2fsprogs.sourceforge.net/ext2.html") software, isn't it? This is a third-party (it means non-native) software/driver for the EXT2/3/4 file systems in Windows.

If you want to recover data from an EXT4 partition you would be much better doing it from a live session (e.g. Mint installation USB) with the drive you want to retrieve data from also connected. Trying to do it from Windows with a tool that is known for occasionally corrupt partitions is absurd (can't think of a better word).

And this smells a lot like a X-Y problem...

---

### Post by coffeecat on 2020-03-09
As this doesn't appear to involve Ubuntu or any of the official Ubuntu flavours, I've moved this to the Mint sub-forum. 

A few comments, and then I'll step back.

What do you mean by "using EXT2". Ext2 is a non-journalled filesystem. Your Mint partition will probably have the ext4 filesystem. Have you got some sort of ext2 driver on Windows? That's the last thing I would try - probably not try it at all. If you need to recover files from a Linux system, use a Linux system. Either plug the Mint HD into a running Linux system, or boot a live session of any distro you prefer, and mount the Mint HD from that.

I think you're confused about the ./gnupg folder. If it's in your home as ~/.gnupg, then it is owned by your Mint user. If it's owned by root, then your Mint install is significantly damaged.

**Edit:** second part of post ninja'd by CelticWarrior, who's phrased it better than I. I shall step back now and watch with interest.

---

### Post by QIII on 2020-03-09
@Creenome

The "XY Problem" is asking about your solution (or perhaps why it hasn't worked), rather than asking about the problem itself.

It is far easier for people to help if you "start from the start".  That is: What were the symptoms of the problem that compelled you to seek a solution?  I'm not sure that you have asked an XY question.  That was just by way of explanation.

Also, to the best of your ability, use terminology appropriately and carefully.  If you don't know it, of course, just do your best.

Cheers!

---

### Post by Creenome on 2020-03-09
> **CelticWarrior said:**
> Perhaps we should start by clarifying the "EXT2" reference... I think you don't mean the EXT2 file system (old, pretty much everything uses EXT4 nowadays) but the [ext2fs]("http://e2fsprogs.sourceforge.net/ext2.html") software, isn't it? This is a third-party (it means non-native) software/driver for the EXT2/3/4 file systems in Windows.

If you want to recover data from an EXT4 partition you would be much better doing it from a live session (e.g. Mint installation USB) with the drive you want to retrieve data from also connected. Trying to do it from Windows with a tool that is known for occasionally corrupt partitions is absurd (can't think of a better word).

And this smells a lot like a X-Y problem...

I'm only trying to pull the .gnupg folder. Which is not showing up.

To clarify, the EXT2 reference is pointing towards the program ext2fs. I realize this program can corrupt files, as to why I am only using it in read only mode. I'm not using it to write any info the the disk.

I am running an ASUS x205ta, 64-bit processor but 32-bit UEFI firmware. This is stock. This is a backup PC and the only one I have access too.

The only way I've been able to get Mint booted is through Virtual Box. And at that, I can't get my HDD to show up via USB with guest additions installed.

---

### Post by CelticWarrior on 2020-03-09
.gnupg is an hidden folder, hence the period.
If ext2fs supports and respects this attributes it should keep the folder hidden also in Windows explorer. Not sure it works but perhaps you should try this: [https://support.microsoft.com/en-us/help/14201/windows-show-hidden-files](https://support.microsoft.com/en-us/help/14201/windows-show-hidden-files)

---

### Post by Creenome on 2020-03-09
> **CelticWarrior said:**
> .gnupg is an hidden folder, hence the period.
If ext2fs supports and respects this attributes it should keep the folder hidden also in Windows explorer. Not sure it works but perhaps you should try this: [https://support.microsoft.com/en-us/help/14201/windows-show-hidden-files](https://support.microsoft.com/en-us/help/14201/windows-show-hidden-files)

Sometimes just talking to people helps me remember certain things, however this one is still stumping me. 

I realize the (.) in .gnupg means hidden, however its appearing the folder is completely gone. I have the other hidden files shown without any problems.

Is there possibly something wrong with the .gnupg folder that isn't letting it be seen?

---

### Post by CelticWarrior on 2020-03-09
Not sure how it works, whether that folder is part of a standard installation or created on demand... If this is a new installation that never booted then maybe the folder doesn't exist? Really, don't know. And I wonder why are you looking for that folder, what do you expect to do with it...

---

### Post by Creenome on 2020-03-09
> **CelticWarrior said:**
> Not sure how it works, whether that folder is part of a standard installation or created on demand... If this is a new installation that never booted then maybe the folder doesn't exist? Really, don't know. And I wonder why are you looking for that folder, what do you expect to do with it...

The hard drive containing Mint 17(the hard drive in question) used to be booted and used daily. That specific folder has the GNUPG keys I need to transact BTC with an old buddy on a P2P site. They rely heavily on community feedback. Bitcoin-OTC.

---

### Post by TheFu on 2020-03-09
I only skimmed the thread. Sorry if this has been covered.

Don't do things the hard way. Please.

Don't use Windows to fix Linux issues.  Use a "Try Ubuntu" flash USB stick. I don't use mint, but suspect their installation ISO placed onto a flash drive and booted will work just as well.  After booting from teh flash storage, choose the "Try {whatever Linux OS}" option, point-n-click any file manager at the disk and follow it down into the user's HOME/.gpg/ directory.  Insert a different flash storage/usb storage device and copy/paste the entire folder over to it.

If the directory isn't in the HOME directory for the userid you expect, my expectation would be that the Windows computer screwed it up OR there is a HW fault with the storage.  Check the SMART data.

swap files don't have users.  They are just used to extend RAM as needed.  There's nothing useful for anyone but crackers in a swap file and most of it will be garbage after a shutdown.

Anything you consider critical needs to have at least 3 copies in at least 2 different locations, with the 2nd location being at least 500 miles away from the 1st location to avoid regional disasters.  Anything less is a total failure.

---

### Post by SeijiSensei on 2020-03-10
The concept of a dot file doesn't exist in Windows filesystems, so if you're trying to copy ~/.gnupg to Windows I can imagine you might have problems.

I rarely back up to Windows, but when I do, I first create tar archives of the files I want to preserve, then copy the archives to windows.  E.g.,

```

cd /
tar czvpf myhomedirectory.tar.gz /home/myusername 

```

You might look into reversing the process by exporting a directory in Windows and mounting it in Linux.

---

