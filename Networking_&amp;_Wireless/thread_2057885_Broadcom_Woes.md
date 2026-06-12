---
title: "Broadcom Woes"
date: 2012-09-14
forum: Networking &amp; Wireless
---

### Post by squeakyfridge on 2012-09-14
Hey all,

I'm running on 10.04 and updated the kernel to 2.6.36. The issue I'm having is with trying to activate the Broadcom drivers via Hardware Devices. The error message I have been receiving is:

```
SystemError: installArchives() failed
```

I've read numerous posts on this issue, some of which suggests removing and reinstalling bcmwl-kernel-source and its dependencies which I have attempted without success. Ethernet works, but it is wireless that I am concerned with at this point.

Trying to install bcmwl results in this error:

```
Selecting previously deselected package dkms.
(Reading database ... 141384 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.1.1.2-2ubuntu1_all.deb) ...
Selecting previously deselected package bcmwl-kernel-source.
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.1.1.2-2ubuntu1) ...

Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.36-cos
Building for architecture i686
Building initial module for 2.6.36-cos
```

Wireless works fine on 2.6.32-38, but I require 2.6.36 instead.

Any suggestions would be greatly appreciated.

---

### Post by Hadaka on 2012-09-14
Hi, lets have a look at what card you have. please post the output of:

```
lspci -nnk | grep -iA3 net 
```

thanks.

---

### Post by squeakyfridge on 2012-09-14
Hi, thanks for the response

```
01:00.0 Ethernet controller [0200]: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter [1969:1062] (rev c0)
    Kernel driver in use: atl1c
    Kernel modules: atl1c
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
```

Quick note: I need to step away for about a few hours in a moment, please leave any other requests for information that you'd like to examine and I will get back to you ASAP. Thanks in advance!

---

### Post by Hadaka on 2012-09-14
Hi, this should get you up and running....read POST #6
[http://ubuntuforums.org/showthread.php?t=1456310](http://ubuntuforums.org/showthread.php?t=1456310)

---

### Post by squeakyfridge on 2012-09-14
Got it. Will try that and report back. Thanks!

---

### Post by squeakyfridge on 2012-09-14
Unfortunately that did not work. Here is the output:

```
(Reading database ... 141449 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.10.91.9+bdcom-0ubuntu4 (using .../bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Preparing to replace dkms 2.1.0.1-0ubuntu1 (using .../dkms_2.1.0.1-0ubuntu1_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace dpkg-dev 1.15.4ubuntu2 (using .../dpkg-dev_1.15.4ubuntu2_all.deb) ...
Unpacking replacement dpkg-dev ...
Preparing to replace fakeroot 1.12.4ubuntu1 (using .../fakeroot_1.12.4ubuntu1_i386.deb) ...
Unpacking replacement fakeroot ...
Preparing to replace g++ 4:4.4.1-1ubuntu2 (using .../g++_4.4.1-1ubuntu2_i386.deb) ...
Unpacking replacement g++ ...
Preparing to replace g++-4.4 4.4.1-4ubuntu8 (using .../g++-4.4_4.4.1-4ubuntu8_i386.deb) ...
Unpacking replacement g++-4.4 ...
Preparing to replace libstdc++6-4.4-dev 4.4.1-4ubuntu8 (using .../libstdc++6-4.4-dev_4.4.1-4ubuntu8_i386.deb) ...
Unpacking replacement libstdc++6-4.4-dev ...
Preparing to replace patch 2.5.9-5 (using .../patch_2.5.9-5_i386.deb) ...
Unpacking replacement patch ...
Setting up dkms (2.1.0.1-0ubuntu1) ...
 * Running DKMS auto installation service for kernel 2.6.36-cos          [ OK ] 

Setting up fakeroot (1.12.4ubuntu1) ...

dpkg: dependency problems prevent configuration of g++-4.4:
 g++-4.4 depends on gcc-4.4-base (= 4.4.1-4ubuntu8); however:
  Version of gcc-4.4-base on system is 4.4.3-4ubuntu5.1.
 g++-4.4 depends on gcc-4.4 (= 4.4.1-4ubuntu8); however:
  Version of gcc-4.4 on system is 4.4.3-4ubuntu5.1.
dpkg: error processing g++-4.4 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libstdc++6-4.4-dev:
 libstdc++6-4.4-dev depends on gcc-4.4-base (= 4.4.1-4ubuntu8); however:
  Version of gcc-4.4-base on system is 4.4.3-4ubuntu5.1.
 libstdc++6-4.4-dev depends on g++-4.4 (= 4.4.1-4ubuntu8); however:
  Package g++-4.4 is not configured yet.
dpkg: error processing libstdc++6-4.4-dev (--install):
 dependency problems - leaving unconfigured
Setting up patch (2.5.9-5) ...
dpkg: dependency problems prevent configuration of g++:
 g++ depends on g++-4.4 (>= 4.4.1-1); however:
  Package g++-4.4 is not configured yet.
dpkg: error processing g++ (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Setting up dpkg-dev (1.15.4ubuntu2) ...
Processing triggers for ureadahead ...
Setting up bcmwl-kernel-source (5.10.91.9+bdcom-0ubuntu4) ...
Adding Module to DKMS build system
Doing initial module build

Error! Bad return status for module build on kernel: 2.6.36-cos (i686)
Consult the make.log in the build directory
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/ for more information.
Installing initial module

Error! Could not locate wl.ko for module bcmwl in the DKMS tree.
You must run a dkms build for kernel 2.6.36-cos (i686) first.
Done.
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-38-generic
Errors were encountered while processing:
 g++-4.4
 libstdc++6-4.4-dev
 g++
The package Broadcom STA Driver should now be installed!

All finished here! Reboot your system and you should have a working WiFi...
```

I have tried rebooting in spite of the error messages and WiFi still does not seem to work.

Additional info. At the end of the script, Synaptic reports **g++-4.4** and** libstdc++6-4.4-dev** to be broken. Repairing via Synaptic installs newer versions which fixes the broken dependencies issue, and running the script reverts them to the older version.

---

### Post by Hadaka on 2012-09-14
Hi, i forgot you were running 10.04, have you tried this

```
sudo apt-get install b43-fwcutter firmware-b43-installer 
```

---

### Post by squeakyfridge on 2012-09-14
Here is the output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
E: Couldn't find package firmware-b43-installer
```

---

### Post by squeakyfridge on 2012-09-15
Additional information: Occasionally when I go through the Hardware Devices to Activate the Broadcom driver (Ethernet works so it is able to detect it), there is also an error message relating to the jockey logs (/var/log/jockey...). I'll post the logs when I get a chance if they are of help.

---

### Post by Hadaka on 2012-09-15
Hi, I doubt b43 is blacklisted,but take a look anyway...

```
grep -i b43  /etc/modprobe.d/blacklist.conf 
```

also,per your last post, are you saying the wireless works if you
play around with the network activation settings...sometimes??

---

### Post by squeakyfridge on 2012-09-15
The output of that is:

```
# replaced by b43 and ssb
```

And no, I meant that there's an error message if I try to activate the Broadcom driver via Hardware Devices. There are actually 2 different messages I get, the most common one is the installArchives() failed one from my first post. The jockey message occurs less often, and I am not sure how to replicate it.

---

### Post by Hadaka on 2012-09-15
Hi, ok, good not blacklisted. I have never used 10.04 so i dont know what it
looks like, Do you have some kind of desktop? and a download directory?
code to check if you have them....

```
cd Desktop 
``````
cd Downloads 
```if both these give you a terminal directory prompt, I have a file to send you
that you can load the b43 dirvers, offline and it should get you going.

** note: both directories are uppercase "D"

---

### Post by squeakyfridge on 2012-09-15
I don't quite understand that question, but I do have both directories.

---

### Post by Hadaka on 2012-09-15
Hi, glad you have those directories, here is the offline how to, so you will
want to unlug your hardwire connection...no internet.
drag the b43.zip file to your Desktop, right click it, and choose open here

[ATTACH]224191[/ATTACH]

then
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
 
```boot and see if that does it for you.
*remember, do this offline

---

### Post by squeakyfridge on 2012-09-15
The b43 directory already exists, should I overwrite its contents with the files you attached?

---

### Post by Hadaka on 2012-09-15
Hi, yeah , overwrite it, i know the zip file works and is clean, yours may
be fine, but it may also not be. so yeah..overwrite it.

---

### Post by squeakyfridge on 2012-09-16
Sorry for the delay-

The rmmod commands returned

```
No such file or directory
```

And the modprobe command does not return any output.

After a reboot, WiFi remains inaccessible.

Thank you very much for the assistance so far though!

---

### Post by Hadaka on 2012-09-16
Hi, it looks like it loaded ok..but doenst like it.
your wireless card is the broadcom 4713 , im attaching a link
with a how to for broadcom cards, hopefully the instructions
for your card will work..

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers)

or maybe someone like chilli55 will read this and jump in, he has
alot more experience with this than i do.

---

### Post by squeakyfridge on 2012-09-16
Got it. I will give this a try once I have a little more free time. 

Thank you very much for the help so far!!

---

### Post by Hadaka on 2012-09-17
Hi, I typed broadcom 4713 card...that is not correct...it is 4313, sorry.

I did more research and think i have the correct solution now if you
want to continue working on this, or close this thread as solved and post a new one
with attn: chili555 in the header.
thanks for being patient.

---

