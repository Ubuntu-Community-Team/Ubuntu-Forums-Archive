---
title: "Cannot install Natty Alpha 3"
date: 2011-03-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Yahoé on 2011-03-04
Bonjour,

This is a follow up of thread [http://ubuntuforums.org/showthread.php?t=1692326&highlight=yaho%E9&page=5](http://ubuntuforums.org/showthread.php?t=1692326&highlight=yaho%E9&page=5) which has been marked as solved.

Recapitulation:

I posted on 2nd March : "I've been using btrfs on / for months now and it's working very nicely.
I  also have a running system with a btrfs /boot partition, and btrfs /,  so btrfs shouldn't be the issue. The last installable daily is 18th  February for me.  Ubiquity just got updated to 2.5.22, will give it a  try and see if installation completes. Well that did not change  anything. Just downloaded and tried a fresh install with the latest Natty daily  2nd march 2011, and Ubiquity still gets stuck at about 75% of the system  installation process. So this is definitely not working with my setup."

Now with Alpha 3, I really experience the same issue. I'm also setting a /home encrypted on it's own btrfs partition.
Formatting of the btrfs partitions and swap goes well, hardware configuration completes, downloading mostly completes but now gets stuck at around 5 minutes left (sometimes 3) I tried to install many times, first with my three HDs connected, then only the one. Same problem, get stuck at around 75 %.
So finally decide to let Ubiquity take over the full disk, accept the proposed 1 ext4 partition but then the installation process doesn't get any further than the 75 % mark.

Any input would be appreciated.

Regards.

Alain-Olivier, Montréal

---

### Post by dino99 on 2011-03-04
report a bug about ubuntu, as the real problem is not clearly identified

---

### Post by VMC on 2011-03-04
> **Yahoé said:**
> Bonjour,

This is a follow up of thread [http://ubuntuforums.org/showthread.php?t=1692326&highlight=yaho%E9&page=5](http://ubuntuforums.org/showthread.php?t=1692326&highlight=yaho%E9&page=5) which has been marked as solved.

...
Now with Alpha 3, I really experience the same issue. I'm also setting a /home encrypted on it's own btrfs partition.
Formatting of the btrfs partitions and swap goes well, hardware configuration completes, downloading mostly completes but now gets stuck at around 5 minutes left (sometimes 3) I tried to install many times, first with my three HDs connected, then only the one. Same problem, get stuck at around 75 %.
So finally decide to let Ubiquity take over the full disk, accept the proposed 1 ext4 partition but then the installation process doesn't get any further than the 75 % mark.

What your decsribing is not the same issue as the link you referred to. That topic was when the installer stopped at  installing ubuntu section.

As dino suggested, I would create a new bug report.

---

### Post by Yahoé on 2011-03-08
Was able to install with no problem using Natty daily live dated 5th March 2011.

---

### Post by grubler on 2011-03-08
Same problem here around 75%, but not if I had the network disconnected.

---

### Post by Kirk M on 2011-03-08
I had the same problem installing 11.04 alpha 3 to a test partition on my hard drive where alpha 2 installed without any problem at all. Ubiquity crashed about 75% through the install. I filed a bug report that ended up being a duplicate of [Bug #652916]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652916/") on which I added the contents of my original bug report. The bottom line is that after 2 different downloads/burns (md5 checksums all correct) and 3 install attempts "Natty-desktop-amd64 (alpha 3)" would simply not install. I reinstalled alpha 2 the exact same way to the same partition as a "stupid" check and again, it installed fine. 

I'm posting my contents of my initial bug report here just for information sake.

*************

This ubiquity crash also happened to me while attempting to install 11.04 alpha 3 64 bit (desktop) to a test partition on my hard drive. Please note that 11.04 alpha 2 installed without a problem. I'm reposting my comments and bug report from Bug #730220.

***************

Binary package hint: ubiquity

Ubiquity crashed during install of Ubuntu 11.04 (Natty Narwhal) alpha 3. Manual partitioning setup to sda2 single partition set as "/" with grub2 installed to sda2 as well (triple boot system with Linux Mint 10's grub2 installed in MBR). This type of install worked with 11.04 alpha 2--no installer crashes. Am not able to install alpha 3 due to Ubiquity crashing during install.

ProblemType: Crash
DistroRelease: Ubuntu 11.04
Package: ubiquity 2.5.22
ProcVersionSignature: Ubuntu 2.6.38-5.32-generic 2.6.38-rc6
Uname: Linux 2.6.38-5-generic x86_64
Architecture: amd64
Date: Sun Mar 6 12:31:41 2011
ExecutablePath: /usr/bin/ubiquity-dm
InterpreterPath: /usr/bin/python2.7
LiveMediaBuild: Ubuntu 11.04 "Natty Narwhal" - Alpha amd64 (20110302)
ProcCmdline: /usr/bin/python /usr/bin/ubiquity-dm vt7 :0 hostname /usr/bin/ubiquity --greeter --only
ProcEnviron:
 LANGUAGE=
 PATH=(custom, no user)
 LANG=en_US.UTF-8
PythonArgs: ['/usr/bin/ubiquity-dm', 'vt7', ':0', 'hostname', '/usr/bin/ubiquity', '--greeter', '--only']
SourcePackage: ubiquity
Title: ubiquity-dm crashed with ValueError in command(): invalid literal for int() with base 10: ''
UpgradeStatus: No upgrade log present (probably fresh install)
UserGroups:

****************

Additional information to initial report: (All 3 install attempts were clean installs)

Attempted installation of 11.04 alpha 3 was to an already created test partition (sda2) which I initially install 11.04 alpha 2 (and other past distros as well). During install of alpha 3 I chose to specify partitions manually and pointed the alpha 3 install to sda2, mounted as "/" and formatted as ext4. The installer (Ubiquity) crashed in the same place during 3 different install attempts; approx. half-way through "Installing system" after all files were copied and all packages were downloaded.

The first install attempt was set to download upgrades and install 3rd party software and not to transfer any data from the 2 other distros I have installed on the same hard drive. Installer crashed.

The 2nd and 3rd install attempt was set to not download any upgrades but to install 3rd party software and to not transfer any data from my other OSs. These are the same settings as I used when I successfully installed alpha 2. Installer crashed the same way each attempt as well.

***************

Update: Downloaded another 11.04 alpha 3 64-bit (desktop) .iso from the main link on the Natty alpha 3 page and burned to CD, md5 checksums match. Installer crashed as initially described in this bug report. Cannot install alpha 3.

***************

As a redundancy check I re-installed alpha 2 using the exact same parameters as I used for alpha 3 above and alpha 2 installed successfully the first time. For both alpha 2 and 3 installation was started when prompted to "Try Ubuntu" or "Install", choosing to install rather than letting the Live session desktop fully load. One difference I noticed right off was when the "Try" or "Install"prompt came up the upper "panel" was fully loaded in alpha 2 and was not loaded at all in alpha 3.

I've downloaded alpha 3 .iso twice now from the second link from the top of the "Ubuntu 11.04 (Natty Narwhal) Alpha 3" page under the "Desktop CD" section: [http://cdimage.ubuntu.com/releases/natty/alpha-3/](http://cdimage.ubuntu.com/releases/natty/alpha-3/)

Note: I had attempted to post the /var/crash/"ubiquity crash log" with the initial bug report but the live session wouldn't submit it and the log was no longer there when I checked the above directory from one of my other installed distros (Linux Mint Debian).

***************

---

### Post by Kirk M on 2011-03-08
I'm wondering, why is this thread marked [solved] when it's not? The problem still exists as it still exists for that previous thread that was also marked as [solved] when it really wasn't. There's obviously a problem with installing alpha 3 and disconnecting the Internet connection while installing is a work-around, not a solution.

Just wondering. :)

---

