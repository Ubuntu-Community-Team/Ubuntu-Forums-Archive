---
title: "Need Help with WiFi"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by mrossi711 on 2011-01-09
I have a Linksys USB300N wifi adapter which I use for my windows system,  however I recently loaded Ubuntu 10.10 as a dual boot. It fails to  recognize the adapter and I cant seem to fix this error that I get when I  try to install the driver using ndiswrapper. I'm a complete newbie with  Linux but I'm pretty sure that all of the drivers and software I  downloaded are compatible. 

Hence I'm not sure where on earth this is coming from:

# sudo dmesg |grep ndis
[   11.515065] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   12.362534] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   12.362538] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netmw245'
[   12.362736] ndiswrapper (load_wrap_driver:108): couldn't load driver  netmw245; check system log for messages from 'loadndisdriver'
[   12.363870] usbcore: registered new interface driver ndiswrapper
[  278.816371] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  278.816375] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netmw245'
[  278.816699] ndiswrapper (load_wrap_driver:108): couldn't load driver  netmw245; check system log for messages from 'loadndisdriver'

I tried following the instructions here: [http://ubuntuforums.org/showthread.php?t=873027](http://ubuntuforums.org/showthread.php?t=873027)

Any help would be greatly appreciated, even just a push in the right direction.

---

### Post by walt.smith1960 on 2011-01-09
Which version of Windows are you using? NdisWrapper works with XP windows drivers, not Vista or Win7.  It looks like Linksys drivers don't differentiate between 32 & 64 bit, there's only 1 XP driver file available for download.  Have you looked through this thread?

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

Here's something else--doesn't look promising for 64 bit  [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Linksys_WUSB300N](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Linksys_WUSB300N)

If you haven't done so, you might take a look at NDISGTK in Synaptic package manager.

EDIT:  Just for grins, I might uninstall NdisWrapper, restart then install Maverick wireless backports, restart and see if your device is found.  If that doesn't work, you could install NDISGTK and try again.

---

### Post by mrossi711 on 2011-01-10
I'm using Windows XP Home Edition, and I don't believe that either OS is 64 bit. Hence my confusion. I used Wubi to install it, so unless something strange happened there, it should be 32.

I did browse around the other threads and I have tried uninstalling and reinstalling the OS and following their instructions exactly, and it still spits out the same error. Its kind of a pain though because I don't have convenient access to a hard connection so I kept having to run a flash drive between my two computers in order to get the required software. 

I might just be doing something foolish that I haven't recognized yet, but I'm a complete newbie when it comes to Linux.  Is there any info I could provide that could be useful in resolving this?

I'll give the things you suggested a shot.

---

### Post by mrossi711 on 2011-01-11
So I tried reinstalling everything to no avail.  I tried it off of a cd this time and now it fails to install.

(initramfs) /scripts/casper-premount/20iso_scan: line 46 cant open /dev/sr0: No medium found

Perhaps this is closer to the reason the wifi won't work. Do you think there is a problem with my whole installation?

---

### Post by bcbc on 2011-01-11
> **mrossi711 said:**
> I'm using Windows XP Home Edition, and I don't believe that either OS is 64 bit. Hence my confusion. I used Wubi to install it, so unless something strange happened there, it should be 32.

I did browse around the other threads and I have tried uninstalling and reinstalling the OS and following their instructions exactly, and it still spits out the same error. Its kind of a pain though because I don't have convenient access to a hard connection so I kept having to run a flash drive between my two computers in order to get the required software. 

I might just be doing something foolish that I haven't recognized yet, but I'm a complete newbie when it comes to Linux.  Is there any info I could provide that could be useful in resolving this?

I'll give the things you suggested a shot.

wubi will always select 64-bit if your machine is capable. You can force it to use 32-bit.
Also if you installed wubi.exe from [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer) it's actually 10.04.1, not 10.10.

If you want to install with wubi do the following... download the .iso yourself and the wubi.exe into the same folder and run it from there. 

For 10.04.1 download from here: [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)
For 10.10 download from here: [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

Other notes: you can't install netbook edition using wubi.exe 10.04.1. You need 10.04. Netbook edition is always 32-bit

Important:
once you get wubi installed, do not update packages grub-pc and grub-common as they are breaking wubi installs at the moment.

---

### Post by mrossi711 on 2011-01-12
Well put a folder on my desktop called 'New Folder' with wubi.exe and ubuntu-10.10-desktop-i386.iso.  It didn't download anything so I'm assuming it's now the correct version installed.  The error I'm having still persists. What Now?

---

### Post by bcbc on 2011-01-12
> **mrossi711 said:**
> Well put a folder on my desktop called 'New Folder' with wubi.exe and ubuntu-10.10-desktop-i386.iso.  It didn't download anything so I'm assuming it's now the correct version installed.  The error I'm having still persists. What Now?

It still says the windows driver is not 64-bit?
> [ 12.362534] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B

what is the output of "uname -m" and "file /sbin/init"

---

### Post by mrossi711 on 2011-01-12
Oops, I meant this error:

(initramfs) /scripts/casper-premount/20iso_scan: line 46 cant open /dev/sr0: No medium found

The installation won't complete after I reboot

---

### Post by bcbc on 2011-01-12
> **mrossi711 said:**
> Oops, I meant this error:

(initramfs) /scripts/casper-premount/20iso_scan: line 46 cant open /dev/sr0: No medium found

The installation won't complete after I reboot

That's puzzling. Is anything else different between when you successfully installed before and now (apart from 32vs64bit). i.e. some hardware attached that wasn't there before?

Before you also likely had 10.04.1 (that's the wubi version on [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)), not 10.10. But I can't see why you'd be getting this error...

---

### Post by mrossi711 on 2011-01-12
There shouldn't be. Might I try downloading 10.04 instead, and upgrading later?

---

### Post by bcbc on 2011-01-12
> **mrossi711 said:**
> There shouldn't be. Might I try downloading 10.04 instead, and upgrading later?

It's worth a try. I might skip upgrading to 10.10 unless there's something specific on it you want. There's not a whole lot different between it and 10.04 - personally I prefer 10.04. And Wubi upgrades to 10.10 are known to fail - you can fix them, but ideally you shouldn't be doing it.

---

### Post by mrossi711 on 2011-01-13
Well I finally got everything to work. I wish I had known to use 10.04 in the first place because trying to install 10.10 was a nightmare.  Wifi works fine, installed with no errors.  Thanks for helping me out with this (the thing about wubi was very helpful) I appreciate it. 

:P

---

### Post by bcbc on 2011-01-13
> **mrossi711 said:**
> Well I finally got everything to work. I wish I had known to use 10.04 in the first place because trying to install 10.10 was a nightmare.  Wifi works fine, installed with no errors.  Thanks for helping me out with this (the thing about wubi was very helpful) I appreciate it. 

:P

Great - you're welcome. That is very puzzling, that 10.10 failed like that. Anyway... I'm going to caution again (because I see so many broken wubi installs): don't update packages grub-pc and grub-common.

For insurance, you can backup the root.disk prior to a major update/upgrade for added security, and regular backups are a good idea. If, at a later date, you decide you want more stability than Wubi offers, then you can always [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") a wubi install to partition without losing anything.

---

