---
title: "Quite the mess .... help with Source files.. ubuntu"
date: 2019-07-01
forum: MINT
---

### Post by steezy on 2019-07-01
Hello Uber Noob Here been at this problem for about a week now .... It started out with trying to implement wine and winetricks to my system. Basically just wanted to be able to play spades on sareharborgames.net while i immersed my self in the adventure that is Linux.So here is the problem at some point i edited /etc/apt/sources.list files ... any direction would be much appreciated thank you. this is the output i recivce when i try to pretty much do anything through the termal application.



jay@Jays:~$ sudo apt-get update
[sudo] password for jay:         
Reading package lists... Done
W: Unable to read /etc/apt/apt.conf.d/ - DirectoryExists (2: No such file or directory)
W: Unable to read /etc/apt/sources.list.d/ - DirectoryExists (2: No such file or directory)
W: Unable to read /etc/apt/sources.list - RealFileExists (2: No such file or directory)


obviously It woud seem that these dir are deleted but here they are :

[IMG]https://i.imgur.com/vuLA0tG.png[/IMG]



[IMG]https://i.imgur.com/4VAS3nQ.png?1[/IMG]

---

### Post by cruzer001 on 2019-07-01
You can generate a new sources list here.
[https://repogen.simplylinux.ch/](https://repogen.simplylinux.ch/)

But whats in this /ect/apt/sources.list folder?  Please post this.

Also post sources.list.bak
```
cat /etc/apt/sources.list.bak
```
and 
```
uname -r && lsb_release -a
```

And welcome to the forums :)

---

### Post by Impavidus on 2019-07-01
> **steezy said:**
> 
W: Unable to read /etc/apt/apt.conf.d/ - DirectoryExists (2: No such file or directory)
W: Unable to read /etc/apt/sources.list.d/ - DirectoryExists (2: No such file or directory)
W: Unable to read /etc/apt/sources.list - RealFileExists (2: No such file or directory)


obviously It woud seem that these dir are deleted but here they are :

No, they're not there. There's no directory named apt.conf.d (instead there's a directory named apt.conf); there's no directory named sources.list.d (instead there's a directory named sources.list); there's no regular file named sources.list (instead there's a directory named sources.list).

It seems that you renamed a few directories by stripping the .d from their name and you moved some files around. There also appear to be three backups of sources.list. Let's see if the contents of the directories seem intact. Use the terminal and post the output in your next post in [noparse]```
code tags
```[/noparse]. That will make it easier to read on the forum. Also check the contents of what seem to be backup files.```
ls /etc/apt/apt.conf
ls /etc/apt/auth.conf
ls /etc/apt/preferences
cat sources.list.bak
diff sources.list.{save,bak}
diff sources.list.save{,.1}
```Some of these commands may give no output at all. Chances are you can fix your problem by just renaming a few directories and restoring some backups.

Can you also show the contents of those files in /etc/apt/sources.list?

---

### Post by coffeecat on 2019-07-01
*Thread moved to the **Mint** sub-forum.*

---

### Post by cruzer001 on 2019-07-01
PS

About posting pics and code.

[https://ubuntuforums.org/showthread.php?t=1006656](https://ubuntuforums.org/showthread.php?t=1006656)

---

### Post by steezy on 2019-07-01
> **cruzer001 said:**
> You can generate a new sources list here.
[https://repogen.simplylinux.ch/](https://repogen.simplylinux.ch/)

But whats in this /ect/apt/sources.list folder?  Please post this.

Also post sources.list.bak
```
cat /etc/apt/sources.list.bak
```
and 
```
uname -r && lsb_release -a
```

And welcome to the forums :)



jay@Jays:~$ uname -r && lsb_release -a
4.15.0-54-generic
No LSB modules are available.
Distributor ID:    LinuxMint
Description:    Linux Mint 19.1 Tessa
Release:    19.1
Codename:    tessa




Y Thank you very much.

---

### Post by steezy on 2019-07-01
> **Impavidus said:**
> No, they're not there. There's no directory named apt.conf.d (instead there's a directory named apt.conf); there's no directory named sources.list.d (instead there's a directory named sources.list); there's no regular file named sources.list (instead there's a directory named sources.list).

It seems that you renamed a few directories by stripping the .d from their name and you moved some files around. There also appear to be three backups of sources.list. Let's see if the contents of the directories seem intact. Use the terminal and post the output in your next post in [noparse]```
code tags
```[/noparse]. That will make it easier to read on the forum. Also check the contents of what seem to be backup files.```
ls /etc/apt/apt.conf
ls /etc/apt/auth.conf
ls /etc/apt/preferences
cat sources.list.bak
diff sources.list.{save,bak}
diff sources.list.save{,.1}
```Some of these commands may give no output at all. Chances are you can fix your problem by just renaming a few directories and restoring some backups.

Can you also show the contents of those files in /etc/apt/sources.list?

jay@Jays:~$ ls /etc/apt/apt.conf
00aptitude    00trustcdrom          20dbus               70debconf
00cdrom       01autoremove          20packagekit         90mintsystem
00mint        01autoremove-kernels  50appstream          99synaptic
00recommends  01-vendor-ubuntu      50command-not-found
jay@Jays:~$  ls /etc/apt/auth.conf
jay@Jays:~$ 
jay@Jays:~$ /etc/apt/preferences
-bash: /etc/apt/preferences: Is a directory
jay@Jays:~$ cat sources.list.bak
cat: sources.list.bak: No such file or directory
jay@Jays:~$ diff sources.list.{save,bak}
diff: sources.list.save: No such file or directory
diff: sources.list.bak: No such file or directory
jay@Jays:~$ diff sources.list.save{,.1}
diff: sources.list.save: No such file or directory
diff: sources.list.save.1: No such file or directory
jay@Jays:~$





4 flies 
 /etc/apt/sources.list
-1
/etc/apt/sources.list/official-dbgsym-repositories.list
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) bionic main restricted universe multiverse
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) bionic-updates main restricted universe multiverse
-2
/etc/apt/sources.list/official-package-repositories.list
deb [http://mirrors.evowise.com/linuxmint/packages](http://mirrors.evowise.com/linuxmint/packages) tessa main upstream import backport romeo

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) bionic-security main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) bionic partner
-3
/etc/apt/sources.list/official-source-repositories.list
deb-src [http://mirrors.evowise.com/linuxmint/packages](http://mirrors.evowise.com/linuxmint/packages) tessa main upstream import backport romeo

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) bionic-security main restricted universe multiverse
deb-src [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) bionic partner
-4
/etc/apt/sources.list/opera-stable.list
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades
# deb [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free #Opera Browser (final releases)

---

### Post by cruzer001 on 2019-07-01
Ok thats a start, please answer my other inquires.

---

### Post by cruzer001 on 2019-07-01
Lets do this, ready :)
/etc/apt/sources.list; rename it to "old" with this command.
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
```
Then create a file (not a folder) in your home directory and name it **sources.list** and enter the URLs below into your newly created sources.list file.
```
deb http://archive.ubuntu.com/ubuntu/ bionic main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ bionic-security main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ bionic-updates main restricted universe multiverse
```
I left out dbgsym-repositories and can be added if needed.
Now transfer that file to /etc/apt/
```
sudo mv ~/sources.list /etc/apt/
```
Then please verify that new sources.list is moved to /etc/apt/ and code/url is in place.

Were not done yet, but do an update and post the results.  Apt-get is being replaced with just apt.
```
sudo apt update
```
to upgrade
```
sudo apt full-upgrade
```
```
man apt
```

---

### Post by steezy on 2019-07-01
> **cruzer001 said:**
> Ok thats a start, please answer my other inquires.


Can you please be more specific? 

exact code would help a lot .

---

### Post by cruzer001 on 2019-07-01
Our timing is amazing.  Check post #9

---

