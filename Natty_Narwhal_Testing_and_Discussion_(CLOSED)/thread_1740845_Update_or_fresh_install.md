---
title: "Update or fresh install?"
date: 2011-04-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Rodayo on 2011-04-27
So since the final release is coming out tomorrow I was wondering if it's better to use the update manager or do a fresh install?

I'd prefer the update method of course since I have so many things I would need to back up. And all my configurations and such....

I did some googling and most people recommend reinstalls but not sure what the reason for that is...

---

### Post by madjr on 2011-04-27
i recommend downloading the iso image it lets you do both an upgrade right from it or do a fresh install if needed.

more info:
[http://www.webupd8.org/2011/04/how-to-upgrade-to-ubuntu-1104-natty.html](http://www.webupd8.org/2011/04/how-to-upgrade-to-ubuntu-1104-natty.html)

---

### Post by his221 on 2011-04-27
I would do a backup of the system (I use clonezilla for backups, as it's worked perfectly so far for me) and try both methods. Then you can decide which one fits best for you.

Anyway, I did an update from maverick to the beta and had no problems, so you should be fine with the update.

---

### Post by el_koraco on 2011-04-27
Backup, backup, backup, whatever you do. 

As for the OP - **clean** install is my preferred method.

---

### Post by cariboo on 2011-04-27
I usually do a fresh install, as my system tends to get crufty after the development cycle. That being said, I usually only use the fresh install for a week or so until the toolchain is uploaded, then only revert when the testing version is unusable.

---

### Post by Harry33 on 2011-04-27
> **cariboo907 said:**
> I usually do a fresh install, as my system tends to get crufty after the development cycle. That being said, I usually only use the fresh install for a week or so until the toolchain is uploaded, then only revert when the testing version is unusable.

I have two setups that originate from Lucid clean install and one from Maverick.
These have been updated all through the development cycles through Maverick up to Natty. I haven't even been compelled to chroot, no reinstalls.
I use some kind of minimal amount of packages (only those necessary for me), without any meta packages, without Unity, Compiz; totalling up to 750 packages.

I plan to keep it that way too.
But, I do not use terminal to update nor do I use Update Manager (which is not even installed), I only use Synaptic, taking care to remove all deprecated and old packages and resetting confs when necessary.

---

### Post by seeker5528 on 2011-04-27
I don't do fresh installs unless I am forced to because of hardware failure, disk corruption, etc....

Some system wide settings may differ because of packages that default to using your old settings instead of some different settings a newer version of a package may default to when freshly installed.

Sometimes configuration files in '/etc/' may be replaced leaving 'blah-blah.old' configuration files laying around. Usually not significant in number of files or disk space used and not really a point of confusion either since since it's clear which files are old.

You will probably end up with extra packages installed that would not get installed if you do a clean install, then re-install the additional software/packages you want, but if you view and remove obsolete or locally installed packages, these should not be *that* significant in terms of disk space. 

If you keep your old home directory on a "clean" install, because you keep it on a separate partition or use the upgrade feature on the install disk, this is where the most potential for problems come from in the way of old configuration files that get used, old settings migrated to new formats/directories, old unused configuration stuff left behind, making it more difficult to determine whats actually being used when/if you have a problem. 

I'm sure on the migration front, good efforts are made to insure the end result is good, but it's hard to eliminate every corner case and the more deeply you get into configuration stuff, hand editing, gconf-editor, etc... the more potential for oddities from old configurations that get used or scenarios that were not accounted for in some migration script/utility leading to issues during or after migration.

There are reasons to do clean installs and reasons to do upgrades, but in the end, IMHO, the biggest reason by far is just personal preference, neither really stands out much from the standpoint of one being "better" than the other.

Later, Seeker

---

### Post by Rodayo on 2011-04-27
> **seeker5528 said:**
> I don't do fresh installs unless I am forced to because of hardware failure, disk corruption, etc....

Some system wide settings may differ because of packages that default to using your old settings instead of some different settings a newer version of a package may default to when freshly installed.

Sometimes configuration files in '/etc/' may be replaced leaving 'blah-blah.old' configuration files laying around. Usually not significant in number of files or disk space used and not really a point of confusion either since since it's clear which files are old.

You will probably end up with extra packages installed that would not get installed if you do a clean install, then re-install the additional software/packages you want, but if you view and remove obsolete or locally installed packages, these should not be *that* significant in terms of disk space. 

If you keep your old home directory on a "clean" install, because you keep it on a separate partition or use the upgrade feature on the install disk, this is where the most potential for problems come from in the way of old configuration files that get used, old settings migrated to new formats/directories, old unused configuration stuff left behind, making it more difficult to determine whats actually being used when/if you have a problem. 

I'm sure on the migration front, good efforts are made to insure the end result is good, but it's hard to eliminate every corner case and the more deeply you get into configuration stuff, hand editing, gconf-editor, etc... the more potential for oddities from old configurations that get used or scenarios that were not accounted for in some migration script/utility leading to issues during or after migration.

There are reasons to do clean installs and reasons to do upgrades, but in the end, IMHO, the biggest reason by far is just personal preference, neither really stands out much from the standpoint of one being "better" than the other.

Later, Seeker

Well is there a way to tell the installer to keep my old home folder?

---

### Post by Sina_RJ on 2011-04-27
i've always done update and there were no problems.
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by cgroza on 2011-04-27
Fresh install when possible, upgrades sometimes get weird and result into all sorts of complications (sound problems for me).

---

### Post by Sina_RJ on 2011-04-27
> **cgroza said:**
> Fresh install when possible, upgrades sometimes get weird and result into all sorts of complications (sound problems for me).

of course we will face this kind of problems,we are testers!
no way to think we get the best now
28th is the big day
i'm waiting for updates!!!!
updates will keep so many things like personal settings...

---

### Post by VMC on 2011-04-27
> **Rodayo said:**
> Well is there a way to tell the installer to keep my old home folder?

When I do a "fresh" install, if I uncheck the "format" on the manual install, then my "/home" folder is left intact.

---

### Post by residualbit on 2011-04-27
if I did a fresh install of natty beta 1, would there be any real benefit to doing a fresh install of the final version or should I just install updates as they come through?

---

### Post by seeker5528 on 2011-04-27
> **Rodayo said:**
> Well is there a way to tell the installer to keep my old home folder?

Looking at the options now...

The 'Upgrade Ubuntu XX.XX to XX.XX' option says it will keep programs where possible, so I don't know what that leaves you with when it is done relative to what you would end up with if you run update-manager from within your existing installation.

So unless you planned ahead and actually created a separate home partition, there is no quick and reliable way to preserve home and have it be like a clean install + /home on separate partition.

I have seen other people indicate they have re-installed without reformatting, in which case you run the risk of having stuff spread about that the installer doesn't know about if you choose to do it half-*** (don't delete anything) or manually delete everything not in your home directories after booting the live session and before installation which is time consuming, but an option none the less, maybe. 

I believe when installing Debian formatting your '/' partition is always done, for the rest of your partitions it is optional, so if the underlying stuff that does the actual partitioning in Ubiquity is the same as the stuff that does the actual work for the Debian installer, I don't know if you can rely on the option to not format your '/' partition to always be there. It's not something I do, so not something I check for. 

Personally if I decided I wanted to start using a separate home parition after the fact, I would shrink the existing partition by the amount I wanted my OS partition to be, create a new partition in the free space to be used for the OS, delete any files that exist outside of the old home directory. Mount the old partition again if necessarry. Open a terminal window and type something along the lines of ```
cd /media/your_old_os_partition/home
mv * ../
```

so when you mount the partition at '/home' things will be where they should '/home/*' instead of '/home/home/*'

If you prefer using cut and paste in the file manager, that's probably fine too.

There are other options depending on how many drives/partitions you have and how they are used.

Personally I prefer to keep stuff on other partitions, one for MythTV recordings, one for music, another for everything else for example, have each OS keep it's own home directory in it's own partition, using descriptive labels for the partitions so I have the option of using the label instead of the UUID when mounting. This way there is not much if anything in my home directory to save at any given time, bookmarks, email and some miscellaneous riff raff. 

If you only have one user in each installation and use the same user name, shouldn't be any big thing, unless the distributions disagree about the numerical ID the first user should be given.

If you have multiple users in one installation or use different user names in different installations and want to share files between them, if you create a group with the same name and numerical ID in each Linux installation and chown/chmod the directories/files you want to allow access to```
chown -R :group /some/location/*
chmod -R g=rwxs,o=rX /some/location/*
```if you don't want people other than the owner or group allowed access to the files use 'o=' with no arguments following, I believe if you want people in the group to be able to read all the files, but only allow the person that creates a file to delete it you would use the 't' option ' ```
chmod -R g=rwxst,o= /some/location/*
```

I have to look this stuff up all the time, but between the man pages for chmod and [http://www.dartmouth.edu/~rc/help/faq/permissions.html](http://www.dartmouth.edu/~rc/help/faq/permissions.html) I believe my examples are correct, it's not exactly clear what happens when there are symbolic links, you may have to chmod the targets of the links separately.

Later, Seeker

---

### Post by cgroza on 2011-04-27
> **Sina_RJ said:**
> of course we will face this kind of problems,we are testers!
no way to think we get the best now
28th is the big day
i'm waiting for updates!!!!
updates will keep so many things like personal settings...
That is tomorrow! I bettor get my DVD ready... :):)

---

