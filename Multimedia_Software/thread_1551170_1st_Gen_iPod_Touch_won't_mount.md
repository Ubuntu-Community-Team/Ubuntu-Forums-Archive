---
title: "1st Gen iPod Touch won't mount"
date: 2010-08-11
forum: Multimedia Software
---

### Post by iamnotloggedon on 2010-08-11
I'm running (K)ubuntu 10.04 side-by-side with Windows 7 (Wubi install) and have been having trouble from the word go trying to get my ipod working with it. I've already managed to jailbreak it with Spirit in Windows in hopes that it would get the iPod libs to work but to no avail.

I've downloaded just about every result I could find by searching for "ipod" in Synaptic as well as a few other libraries that I've found while searching the forums for a solution to my problem. I have both Banshee and RhythmBox on my machine and Bash can detect the device but it won't mount and to the best of my knowledge not a single program can see anything other than a folder labeled "iPod" in my "media" drive and even this only recently occurred.

For what it's worth, I've downloaded the ipod-convenience package and this is the code that resulted when I tried to mount via Konsole:
> jack@ubuntu:~$ sudo ipod-touch-mount
[sudo] password for jack: 
Please add yourself to the fuse group, logout/in and try again.
jack@ubuntu:~$ sudo adduser jack fuse
The user `jack' is already a member of `fuse'.
Keep in mind this is after I've added myself to the 'fuse' group and rebooted the computer.

---

### Post by denham2010 on 2010-08-12
Hi,

I had a similar problem, except I was using Xfce.

I found it works out of the box with Gnome, so while that may not be helpful, as I'm sure you use KDE for similar reasons I use Xfce, I found using gvfs along with libimobiledevice works, my 1st gen iPod Touch is now detected in Rhythmbox.

Then again, installing gvfs may well drag in the entire Gnome desktop.

I am sure there is a KDE solution that someone is aware of..

---

### Post by iamnotloggedon on 2010-08-12
> **denham2010 said:**
> Hi,

I had a similar problem, except I was using Xfce.

I found it works out of the box with Gnome, so while that may not be helpful, as I'm sure you use KDE for similar reasons I use Xfce, I found using gvfs along with libimobiledevice works, my 1st gen iPod Touch is now detected in Rhythmbox.

Then again, installing gvfs may well drag in the entire Gnome desktop.

I am sure there is a KDE solution that someone is aware of..

Well I haven't had any problems installing anything made for Gnome, in fact if you take a look at my first post you'll see I'm actually using Synaptic instead of KPackageKit.

Unfortunately, I already have gvfs installed it would seem.

---

