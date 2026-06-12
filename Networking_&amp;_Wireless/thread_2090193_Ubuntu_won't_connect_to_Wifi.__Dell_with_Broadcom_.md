---
title: "Ubuntu won't connect to Wifi.  Dell with Broadcom BCM4311"
date: 2012-12-01
forum: Networking &amp; Wireless
---

### Post by chuckcrj on 2012-12-01
Ubuntu beginner here!  I searched for this problem and tried everything I could find.  I got wifi to work just fine, then after I booted up again it won't connect.  Wifi light is on and the network shows up as "connect automatically" but it doesn't.

I have Ubuntu 12.04

In the Network menu it has an option to "enable wireless" but it is gray and doesn't let me click it.  If I try plugging in wireless ethernet it won't connect to that either, but then the "enable wireless" is white and I can click it on and a check appears but it still won't connect.

---

### Post by haqking on 2012-12-01
> **chuckcrj said:**
> Ubuntu beginner here!  I searched for this problem and tried everything I could find.  I got wifi to work just fine, then after I booted up again it won't connect.  Wifi light is on and the network shows up as "connect automatically" but it doesn't.

I have Ubuntu 12.04

In the Network menu it has an option to "enable wireless" but it is gray and doesn't let me click it.

[http://ubuntuforums.org/showthread.php?t=2072887](http://ubuntuforums.org/showthread.php?t=2072887)

basically

```
sudo apt-get remove bcmwl-kernel-source
sudo apt-get install firmware-b43-installer b43-fwcutter 			 		
```

---

### Post by chuckcrj on 2012-12-01
> **haqking said:**
> [http://ubuntuforums.org/showthread.php?t=2072887](http://ubuntuforums.org/showthread.php?t=2072887)

basically

```
sudo apt-get remove bcmwl-kernel-source
sudo apt-get install firmware-b43-installer b43-fwcutter                      
```
Many thanks for the quick reply!

Here is what I got;

```
 chuckcrj@chuck-laptop:~$ sudo apt-get remove bcmwl-kernel-source  
 [sudo] password for chuckcrj:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 Package bcmwl-kernel-source is not installed, so not removed  
 The following packages were automatically installed and are no longer required:  
   fakeroot dkms  
 Use 'apt-get autoremove' to remove them.  
 0 upgraded, 0 newly installed, 0 to remove and 222 not upgraded.  
 chuckcrj@chuck-laptop:~$ sudo apt-get install firmware-b43-installer b43-fwcutter  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following packages were automatically installed and are no longer required:  
   fakeroot dkms  
 Use 'apt-get autoremove' to remove them.  
 The following NEW packages will be installed:  
   b43-fwcutter firmware-b43-installer  
 0 upgraded, 2 newly installed, 0 to remove and 222 not upgraded.  
 Need to get 22.4 kB of archives.  
 After this operation, 111 kB of additional disk space will be used.  
 Err http://us.archive.ubuntu.com/ubuntu/ precise/main b43-fwcutter i386 1:015-9  
   Could not resolve 'us.archive.ubuntu.com'  
 Err http://us.archive.ubuntu.com/ubuntu/ precise/multiverse firmware-b43-installer all 1:015-9  
   Could not resolve 'us.archive.ubuntu.com'  
 Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_015-9_i386.deb  Could not resolve 'us.archive.ubuntu.com'  
 Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/multiverse/b/b43-fwcutter/firmware-b43-installer_015-9_all.deb  Could not resolve 'us.archive.ubuntu.com'  
 E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?  
 chuckcrj@chuck-laptop:~$  
 
```

---

### Post by chuckcrj on 2012-12-01
I found the following thread; [http://ubuntuforums.org/showthread.php?t=1957419](http://ubuntuforums.org/showthread.php?t=1957419)

I used the unblock all command and now wireless is up and working.

---

