---
title: "Maverick Meerkat Alpha 1 Released - Read Before Testing"
date: 2010-06-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-06-03
Alpha 1, the first milestone release of the Maverick Meerkat development cycle leading to Ubuntu 10.10.10, has been released. Refer to the links below for more information:

[list] [*] [Release announcement]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2010-June/000721.html") on the [ubuntu-announce mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce")
[*] [Technical Overview]("http://www.ubuntu.com/testing/Maverick/Alpha1")[/list]

If you're new to testing Ubuntu, and are running Maverick for the first time with Alpha 1, the tips below will be especially useful for you. Please take time to read them.

[list]

[*] If you're having a problem with this preliminary milestone release, or are curious about a certain feature, change or malfunction, you're most likely not alone. Please do a forum search before starting new threads. This is very simple with the "Search this Forum" function on the upper right side of the forum index.


[IMG]http://img62.imageshack.us/img62/6821/screenshotxsx.png[/IMG]

Click it, type some keywords related to what you're looking for, and if you see relevant threads come up, please post to those threads instead of starting a new thread. Remember that the best way to provide feedback and help improve Ubuntu is to **file bug reports on the issues you're experiencing**, and improve existing reports if they've been filed. 

**Please don't post your feedback straight to this forum**. Forums are not a good way to keep track of issues, and your post will not be read by the relevant people who can fix your problems. Instead, do a search to find if there's a thread related to your issue(s), and if not, start a new thread, check if others are experiencing the same issue(s), and make sure a bug report is filed (doing a forum search, and/or [a search on the bug tracker]("https://bugs.launchpad.net/ubuntu/") is a good idea). If not, and you need help with [filing a bug report]("https://help.ubuntu.com/community/ReportingBugs"), don't hesitate to ask for help!


[*] **If you install a milestone release once it's released, you can upgrade to the final release without having to do a fresh install**. But there may be some drawbacks in certain scenarios; refer to [the sticky thread on common problems and frequently asked questions]("http://ubuntuforums.org/showthread.php?t=1500648") for details.


[*] The milestone releases (alphas, the beta and the RC) are snapshots of the package archive at their pre-decided release dates. **If you have the latest updates installed on your testing installation, you don't have to remove your current testing installation and install the latest milestone**, unless you want to test installation-specific components (the installer, bootloader etc.), or your installation is affected by potential corner cases that may arise during the development cycle that require a reinstall to fix. Refer to [the sticky thread on common problems and frequently asked questions]("http://ubuntuforums.org/showthread.php?t=1500648") for further details.


[*] If you're just starting to test Maverick, please read the [technical overview]("http://www.ubuntu.com/testing/maverick/alpha1") and see if you're affected by any of the known bugs, take a look at [this wiki page]("https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases"), and [the sticky thread on common problems and frequently asked questions]("http://ubuntuforums.org/showthread.php?t=1500648") for information on various testing methods and good practices. 


[*] Once you've started testing, **exercise caution when upgrading packages** - in special, avoid partial upgrades offered by Update Manager unless you know precisely why it's offering a partial upgrade. Regardless of which tool (APT, Update Manager, Synaptic, Aptitude) you're using to upgrade your packages, **always check the list of packages to be removed, upgraded and installed before each upgrade**. If in doubt, check the changelogs ("Package > Download Changelog" in Synaptic, or "aptitude changelog package_name", or at [packages.ubuntu.com]("http://packages.ubuntu.com")) to see why a package may be being removed. If packages are held back, wait until they're installable again. Refer to [the sticky thread on partial upgrades]("http://ubuntuforums.org/showthread.php?t=1479146") for further information.
[/list]


**Downloads**

(Please prefer torrents, and [using rsync / zsync]("https://help.ubuntu.com/community/RsyncCdImage")).

[http://uec-images.ubuntu.com/releases/maverick/alpha-1/](http://uec-images.ubuntu.com/releases/maverick/alpha-1/)  (Ubuntu Server for UEC and EC2)
[http://cdimage.ubuntu.com/kubuntu/releases/maverick/alpha-1/](http://cdimage.ubuntu.com/kubuntu/releases/maverick/alpha-1/) (Kubuntu Desktop and Netbook)
[http://cdimage.ubuntu.com/xubuntu/releases/maverick/alpha-1/](http://cdimage.ubuntu.com/xubuntu/releases/maverick/alpha-1/) (Xubuntu)
[http://cdimage.ubuntu.com/ubuntustudio/releases/maverick/alpha-1/](http://cdimage.ubuntu.com/ubuntustudio/releases/maverick/alpha-1/) (Ubuntu Studio)
[http://cdimage.ubuntu.com/releases/maverick/alpha-1/](http://cdimage.ubuntu.com/releases/maverick/alpha-1/) (Ubuntu Desktop, Server, and Netbook)

---

### Post by rhlee on 2010-06-07
Hi 23meg,

Is there any way in which I can perform an upgrade to Maverick Alpha1 from Lucid?

Regards,

Richard

---

### Post by ranch hand on 2010-06-07
You should be able to upgrade through Update Mangler if you want to use the "supported" method.

Or you could edit your sources list to read maverick anyplace it now reads lucid and do a "dist-upgrade" in apt.

You can do this is aptitude too but I am not sure of the command in it.

You could also get a CD and, if you are on 2 partitions just install formating your / partition and not your /home partition.  Not sure that is that great an idea because of the config files in the /home partition.  There may be conflicts at this stage of the game but that can be fixed (if they exist at all).

---

### Post by eyelessfade on 2010-06-07
> **rhlee said:**
> Hi 23meg,

Is there any way in which I can perform an upgrade to Maverick Alpha1 from Lucid?

try update-manager -d
or just replace lucid with maverick in sources.list

---

