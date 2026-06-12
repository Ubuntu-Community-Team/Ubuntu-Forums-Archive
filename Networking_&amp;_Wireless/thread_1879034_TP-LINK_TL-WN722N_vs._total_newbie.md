---
title: "TP-LINK TL-WN722N vs. total newbie"
date: 2011-11-10
forum: Networking &amp; Wireless
---

### Post by big.d on 2011-11-10
I have just installed Ubuntu 10.04LTS on an old eMachine. I was using XP Pro, and getting online via a TP-LINK TL-WN722N usb wireless adapter. This is my only way to get online on this machine.

This adapter won't work with linux out of the box, and I have found out that there is supposed to be a driver for it. (ath9k_htc is its name)

I was able to download a folder called 'compat-wireless-3.1-rc8-1.tar.bz2' on a windows netbook and transfer it to the ubuntu machine via a thumbdrive. I extracted it to the desktop, and now I have no idea what to do from here.

What do I need to do now to get the darn thing online?

---

### Post by rosencrantz on 2011-11-10
The standard way to install a tarball is:
-open a terminal
-navigate to the tar.bz2 file
-unpack with tar -jxf <filename>.tar.bz2
-cd into the unpacked folder
-run ./configure
-run make
-run sudo make install
However, the standard way doesn't always work and afterwards the package is not administered (i.e. periodically updated etc.) by your software manager.
I'd suggest looking for a debian package.
Here's the Lucid package list:
[http://packages.ubuntu.com/lucid/allpackages](http://packages.ubuntu.com/lucid/allpackages)
There's a number of compat-wireless backports for different kernel versions, so could you post the output of uname -a (in a terminal) so we can figure out what's applicable?

---

### Post by big.d on 2011-11-10
I have just installed Ubuntu 10.04LTS on an old eMachine. I was using XP  Pro, and getting online via a TP-LINK TL-WN722N usb wireless adapter.  This is my only way to get online on this machine.

This adapter won't work with linux out of the box, and I have found out  that there is supposed to be a driver for it. (ath9k_htc is its name)

I was able to download a folder called  'compat-wireless-3.1-rc8-1.tar.bz2' on a windows netbook and transfer it  to the ubuntu machine via a thumbdrive. I extracted it to the desktop,  and now I have no idea what to do from here.

What do I need to do now to get the darn thing online?

edit: Whoops I missed a click, that was supposed to be regular ubuntu, not xubuntu.

---

### Post by big.d on 2011-11-10
typing uname -a in the terminal gives me
'Linux dustin-desktop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 201
1 i686 GNU/Linux'

---

### Post by big.d on 2011-11-10
Also please bear in mind I haven't the slightest clue how to do basically anything with any flavor of linux.

---

### Post by rosencrantz on 2011-11-10
> **big.d said:**
> Also please bear in mind I haven't the slightest clue how to do basically anything with any flavor of linux.
That's why I recommended the .deb package. No need to torture yourself with tarballs.
I think this should be the right package for you:
[http://packages.ubuntu.com/lucid/linux-backports-modules-compat-wireless-2.6.34-2.6.32-33-generic](http://packages.ubuntu.com/lucid/linux-backports-modules-compat-wireless-2.6.34-2.6.32-33-generic)
Here's the package location:
[http://security.ubuntu.com/ubuntu/pool/universe/l/linux-backports-modules-2.6.32/linux-backports-modules-compat-wireless-2.6.34-2.6.32-33-generic_2.6.32-33.33_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/l/linux-backports-modules-2.6.32/linux-backports-modules-compat-wireless-2.6.34-2.6.32-33-generic_2.6.32-33.33_i386.deb)
It depends only on the kernel and dpkg, so I don't think you need to get extra packages. 
Double clicking on the .deb file should get you to an installer interface. Alternatively, you can always open a terminal where the package is and do
dpkg -l linux-backports-modules-compat-wireless-2.6.34-2.6.32-33-generic_2.6.32-33.33_i386.deb

If this works, restart linux and see what's happening.

---

### Post by big.d on 2011-11-10
Alright. Installing the deb package. Wish me luck lol.

---

### Post by big.d on 2011-11-10
No joy. I installed the deb package and rebooted the machine, but there's no change with the wireless adapter.

---

### Post by wildmanne39 on 2011-11-10
Hi, I am not sure if I can help or not but here goes.

Install linux-headers and build-essential: I think they're on the CD or DVD. Extract the driver and do:
```
cd Desktop/compat
```
```
./scripts/driver-select ath9k_htc
make
sudo make install
sudo modprobe ath9k_htc
```
Run the commands one line at a time.
Thank you

---

### Post by wildmanne39 on 2011-11-10
Hi, I also answered you over here:
[http://ubuntuforums.org/showthread.php?p=11445370#post11445370](http://ubuntuforums.org/showthread.php?p=11445370#post11445370)
Thank you

---

### Post by big.d on 2011-11-10
Thanks for the help guys. I'm still working on it, and I'm preparing a final solution in case I can't get it to work: starting over and installing 11.10, since reviews on the adapter say it works out of the box in that version.

---

### Post by wildmanne39 on 2011-11-10
My directions are copy and paste, since you say you already have the driver you should be on line in about ten minutes if you have not installed any other drivers.
Thank you

---

### Post by big.d on 2011-11-10
OK there is no 'linux-headers' on the cd, but 'build-essentials' is there

---

### Post by cariboo on 2011-11-10
Please don't create multiple threads on the same subject. I have merged your two threads.

---

### Post by wildmanne39 on 2011-11-10
Hi, the kernel header should be installed I just include it just in case, open synaptic and see if headers and build-essentials are installed if so then you do not need to worry about them, if not in put the livecd in your drive then in synaptic click  settings, repositories, put a check by install from cdrom under ubuntu software and reload the repositories and see if you see the kernel headers and build-essentials.

---

### Post by wildmanne39 on 2011-11-10
Hi, sorry I thought you were talking to me.

I am going to back out and let rosencrantz handles it, if you want my help with your question from network just ask and I will try to help.
Bye

---

### Post by R. Hunter on 2011-12-09
There's a simple way to solve the problem.

I'm using the same wireless adapter: bought it for an old Pentium III laptop with Xubuntu 10.04. It didn't work at first, but then, as a friend of mine suggested, we simply installed the new (latest) kernel (I think it's 2.6.38-13-generic) along with all the updates. That's it. It's working.

Oh, and there's a firmware file (I think it's ar9271.fw).

I believe other more experienced members would explain how all this is done.

---

