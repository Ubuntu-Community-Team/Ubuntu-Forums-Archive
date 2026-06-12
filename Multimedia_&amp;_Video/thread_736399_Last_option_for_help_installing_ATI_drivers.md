---
title: "Last option for help installing ATI drivers"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by Nickohyzer on 2008-03-26
First I just want to say that I have checked all of the guides and for one reason or another they don't seem to work for me.

My story:  I installed Ubuntu 7.10 last night (Gutsy I think) and everything went ok with the installation.  The problem is that once I boot in Ubuntu I get up to 
> * Running local boot scripts (/etc/rc.local)

From there I press Ctrl+Alt+F2 and log in.

After my password it says
> Linux <myusername> 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64

Now I'm able to use sudo commands and such.

I follow the guide from [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

I use the following sudo command
> sudo apt-get update

It finishes and reads
> Reading package lists . . . Done

I enter the next command in the guide
> sudo apt-get install linux-restricted-modules-generic restricted-manager

It says this after that command is done
> Reading package lists . . . Done
Building dependency tree
Reading state information . . . Done
linux-restricted-modules-generic is already the newest version.
restricted-manager is already the newest version.
The following packages were automatical installed and are no longer required:  dpkg-dev patch
Use ' apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 201 not upgraded.

So far so good from what I understand.  Now that I'm sure I have the latest updates I go on to the next step of the guide and use the command
> sudo apt-get install linux-restricted-modules-generic restricted-manager-kde

It tells me that 
> After unpacking 188MB of additional disk space will be used.
Do you want to continue [Y/n]?

I hit Y for yes and press enter

It now says
> Get: 1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libartsc0 1.5.8-0ubuntu1 [17.0kB]
Get: 2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libaudio2 1.9-2 [81.1kB]
Get: 3 http//us.archive.ubuntu.com gutsy-updates/main libqt3-mt 3:3.3.8really3.3.7-0ubuntu11.1 [3646kB]
Get 4.... and so on until it says
(Reading database . . . 93572 files and directories currently installed.)
Upacking restricted-manager-kde (from . . ./restricted-manager-kde_0.33.1_amd64.deb)
Setting up python2.5 (2.5.1-5ubuntu5.1) . . 

Setting up libxapian15 (1.0.1-1ubuntu1) . . 

Setting up libept0 (0.5.10ubuntu2) . . .

Setting up debtags (1.7.3ubuntu2) . . .

Setting up adept-common (2.1.3ubuntu17.1) . . .

Setting up adept-manager (2.1.3ubuntu 17.1) . . .

Setting up adept-batch (2.1.3ubuntu17.1) . . .
Setting up python2.5-dev (2.5.1-5ubuntu5.1) . . .
Setting up libpythonize0 (0.4.0-4ubuntu4) . . .

Setting up restricted-manager-kde (0.33.1) . . .

Processing riggers for libc6 . . .
ldconfig deferred processing now taking place

After that I reboot and choose to boot into Ubuntu and I'm back to square one pretty much it loads to
> * Running local boot scripts (/etc/rc.local)



One thing that I didn notice was my monitor said "Out of range"

The Horizontal frequency was 90 and Vertical was 60.

Please post any thoughts you may have or anything that will help at all.  For now I'm going to look for a guide to change your resolution and video settings through the command prompt.


Thaks for any help in advance!

---

### Post by Nickohyzer on 2008-03-27
Well it seems that I got it under control somewhat.  Now I have to hit Ctrl+alt+F2 and log in that way and it will boot into my desktop.  But it won't go into the log in screen anymore.  Any idea what I did?  And just a last request for anyone that can get me a quick link to some info on WINE and how to use it, that would be great!

---

### Post by Sidewinder1 on 2008-03-27
Hi Nick,
can't really help with the ATI driver issues but there is a special forum for wine:
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)
HTH

---

