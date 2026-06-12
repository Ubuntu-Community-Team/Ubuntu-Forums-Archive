---
title: "not wired, lucid, wireless BCM4311"
date: 2012-01-29
forum: Networking &amp; Wireless
---

### Post by MarianHill on 2012-01-29
Hi,
I trying to get this Compaq Presario v6000 with a p { margin-bottom: 0.08in; }  03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01) wireless going.
All I have is usb access, the cd doesn't work and no wired internet is available.
I'm running ubuntu 10.04 off the usb trial version hoping I can get wireless proven out but its pretty confusing.
I'm very new to linux and have seen lots of others having issues here.
Thx!

---

### Post by MarianHill on 2012-01-29
Okay, I have installed 10.04 on this laptop now and I'm trying to figure how to get the b43-fwcutter file installed.
I now realize that b43-fwcutter is already on the ubuntu thumb drive!
Running the command;
$sudo apt-get install firmware-b43-installer 

results in

Reading package lists...done
Building dependency tree
reading state information...done
E: Couldn't find package  firmware-b43-installer 

What I find on the thumbdrive located @
USB20FD/pool/main/b
is actually named b43-fwcutter_012-1build1_i386.deb

So I guess ...

---

### Post by MarianHill on 2012-01-30
I can't figure out why the package manager can't find it

---

### Post by varunendra on 2012-01-31
Don't bother with the terminal commands. Just double-click the .deb file to install it(**b43-fwcutter.....deb**. The latter part of the filename just tells the version, which should be same as that of the installed kernel, and it IS in your case.). After it is installed, wait a couple of minutes or restart to let it detect available networks.

If it gives any 'dependency' errors during installation, install the 'build-essential' package first from the 'pool/main/b/build-essential' directory on the thumb drive.

Hope it's all you need.

---

### Post by MarianHill on 2012-01-31
Hi,
I really appreciate the help. Indeed I did get errors with processing b43-fwcutter. I made a screen shot of the terminal errors that came up, last few lines (I'm typing this manually)

Installation finished
Failed to install package 'b43-fwcutter_012-1build1_i386.deb'
....
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host adress 'downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--install):
 subprocess installed post-installation script returned error exit status 4
Processing triggers for man-db ...
Errors were encountered while processing:
 b43-fwcutter

So I followed your advise and installed package; build-essential and that resulted in the following;

Package: build-essential
Status: Error: Dependency is not satisfiable: g++ (>= 4:4.3.1)

I don't think I mentioned this computer is running windows xp works fine, security keyed internet works fine, I have a different computer running ubuntu sitting right beside it same wireless  
So, nothing to lose here I marked and then removed b43-cutter and tried build-essential again. Same result
Checked a second time neither b43-fwcutter or build-essential is installed or removable from Package Installer
Same result;
Package: build-essential
Status: Error: Dependency is not satisfiable: g++ (>= 4:4.3.1)

---

### Post by varunendra on 2012-02-01
> **MarianHill said:**
> Status: Error: Dependency is not satisfiable: g++ (>= 4:4.3.1)
All the dependencies should be available in the /pool directory in the USB drive. For example, the missing g++ package is available in /pool/main/g directory. If it further leads to other dependencies (that's the worst thing about installing such packages manually) they should also be available in the /pool directory. You'll have to find and install them manually in correct sequence.

For reference: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

Online repository to download packages manually on XP, then install from within Ubuntu: [http://packages.ubuntu.com/lucid/allpackages](http://packages.ubuntu.com/lucid/allpackages)

---

