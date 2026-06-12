---
title: "unable to install any programs in ubuntu 8.10"
date: 2009-03-31
forum: Multimedia Software
---

### Post by balajijagadesh on 2009-03-31
I installed ubuntu 8.10 using wubi installer in my windows xp.... i dont have an interner connection... i could not play any mp3 files in ubunto.. i tried to install mplayer it is asking libhal-dev and libdbus-dev and zlib... i dont have internet connection... then i tried to install smplayer.. vlc player.. but every thing is showing that  some thing is missing.. it says "need to install libxine a-ffmpeg manually"... i am unable to install gtk++ is it not possible to use ubuntu without internet??? i want to switch to ubuntu... but i am worried that i am unable to do any thing with out internet connection.. is there any solution

---

### Post by stumbleUpon on 2009-03-31
Most packages in ubuntu that you mention have to be downloaded which means an internet connection is necessary. If you dont have an internet connection on the machine in which you have installed ubuntu, you can either make your own local repository by downloading the full ubuntu repositories (using some other machine with a working internet connection). See here for info on this

[http://ubuntuforums.org/showthread.php?t=352460](http://ubuntuforums.org/showthread.php?t=352460)

If you cannot go for such a large download, then you can consider purchasing ubuntu repos on DVDs. See the above link for this as well.

---

### Post by 3rdalbum on 2009-03-31
How are you getting the programs to use on Ubuntu? You should be getting them from [http://packages.ubuntu.com](http://packages.ubuntu.com). On the page where it describes the package that you are about to download, it will also list the "dependencies", that is, the packages that are required in order to install the main package. You need to install those dependencies first.

Some of the dependencies will have dependencies of their own.

Linux is really meant to be used with an internet connection. But you can manually download packages using the method I mentioned, before transferring those packages to your Ubuntu machine and installing them there by double-clicking them. You must install the dependencies FIRST.

---

