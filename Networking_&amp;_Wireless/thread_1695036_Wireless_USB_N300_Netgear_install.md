---
title: "Wireless USB N300 Netgear install"
date: 2011-02-25
forum: Networking &amp; Wireless
---

### Post by jazzsax93 on 2011-02-25
Hi all. I'm quite new to Ubuntu and have been running it off the memory stick trial for a while around a windows crash. It's great and I have been getting used to some programs such as Wine and some use of ndiswrapper.
Unfortunately, my laptops wireless card is incompatible with Linux (typical :-( ) and so I've purchased a wireless Usb device by Netgear (N300) in the hope that if this works I can install fully.

I followed the instructions on a previous thread: [http://ubuntuforums.org/showthread.php?t=885520](http://ubuntuforums.org/showthread.php?t=885520)

and installed the drivers recommended. All it says however is that the hardware is not present. Am I missing a step somewhere? or is there an issue with running it off the memory stick (the only reason I haven't yet installed is the wireless issue).

Any help would be most appreciated, and am happy to post screenshots/terminal results that will help.

---

### Post by chili555 on 2011-02-25
> my laptops wireless card is incompatible with Linux Are you quite sure? How about letting an old timer have a look at a terminal command:```
lspci -nn
```Feel free to strip away everything that is not your wireless device; if in doubt, post it all.> I've purchased a wireless Usb device by Netgear (N300)There are several models that have the N300 designation, according to Google. Please let us see:```
lsusb
ndiswrapper -l
```> it says however is that the hardware is not present.That often, not always, means you have installed the Windows .inf for the wrong device.

---

### Post by jazzsax93 on 2011-02-26
> 
ubuntu@ubuntu:~$ lspci -nn
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

I had previously checked whether it would work against a list of drivers using the instructions on 

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

The wireless card it came out with was a Dell wireless 1395 (Laptop is a Dell Inspiron 1525) which is in red on the chipset complete list.

> 
ubuntu@ubuntu:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0846:9020 NetGear, Inc. 
Bus 002 Device 002: ID 0781:5530 SanDisk Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@ubuntu:~$ ndiswrapper -l
arusb_xp : driver installed
bcmwlhigh5 : driver installed

Sorry about not being specific on the wireless USB, the box says: "Netgear N300 wireless Usb adapter, WNA3100" If that is any clearer.

Thanks :)

---

### Post by chili555 on 2011-02-26
> Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01) If you can carry the laptop over to the router and get an internet connection, please do:```
sudo apt-get install bcmwl-kernel-source
```Remove the USB device, reboot and the built-in should be working.

After that, we can fix up the Netgear, too, if you wish.

---

### Post by jazzsax93 on 2011-02-26
I typed that into the terminal but on the reboot the wireless settings still say Firmware missing and it was unable to detect the network.

The code output was:
> 
ubuntu@ubuntu:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms
The following NEW packages will be installed:
  bcmwl-kernel-source dkms
0 upgraded, 2 newly installed, 0 to remove and 270 not upgraded.
Need to get 71.3kB/967kB of archives.
After this operation, 3,084kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main dkms all 2.1.1.2-3ubuntu1.1 [71.3kB]
Fetched 71.3kB in 18s (3,898B/s)                                               
Selecting previously deselected package dkms.
(Reading database ... 129249 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.1.1.2-3ubuntu1.1_all.deb) ...
Selecting previously deselected package bcmwl-kernel-source.
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.1.1.2-3ubuntu1.1) ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu5) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-22-generic
Building for architecture i686
Building initial module for 2.6.35-22-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.35-22-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
cp: cannot stat `/vmlinuz': No such file or directory
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
cp: cannot stat `/vmlinuz': No such file or directory
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 bcmwl-kernel-source
 initramfs-tools
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick-updates_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by chili555 on 2011-02-26
> W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1) Let's do just that:```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```Any time a process ends in an error:> Errors were encountered while processing: it will not magically yield success. We have to fix the error first.

We're almost there!

---

### Post by jazzsax93 on 2011-02-26
Sorry, should've realised that would be needed :\

Ran it, but came up with: 
> 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
ubuntu@ubuntu:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

Should I have run the previous command again before these two?

---

### Post by chili555 on 2011-02-26
Please see: [http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```After fixing this, Update Manager will probably want to install 11 million updates, so set aside some free time!

---

### Post by jazzsax93 on 2011-02-26
> Err cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Fetched 9,050kB in 1min 13s (124kB/s)
W: Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.


And then proceeded to give the same error as before.
Just looked at the other thread and followed some of that. Come up with files missing or denied, Wonder if this is because i've not fully installed and it refuses to work?

---

### Post by chili555 on 2011-02-26
> Wonder if this is because i've not fully installed and it refuses to work?Meaning what? Are you running from the live CD? Please try:```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```

---

### Post by jazzsax93 on 2011-02-26
Yes I am running it off a Memory Stick at the moment.

> ubuntu@ubuntu:~$ sudo apt-cdrom add
Using CD-ROM mount point /media/apt/
Identifying.. [2ca80175b6d14c8645f46f38c8987732-2]
Scanning disc for index files..
Found 0 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
W: Failed to mount '/dev/sr0' to '/media/apt/'
E: Unable to locate any package files, perhaps this is not a Debian Disc or the wrong architecture?


---

### Post by chili555 on 2011-02-26
I have no clue what's going wrong. Would you mind rebooting into the Ubuntu USB memory stick? Remove the Netgear. Then get a wired ethernet connection and do:```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
iwconfig
```Note any errors and post back.

---

### Post by jazzsax93 on 2011-02-26
Code:
>  Sudo apt-get update... {no errors till here:}

Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en_US
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en_US
Reading package lists... Error!
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick-updates_universe_binary-i386_Packages)
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


ubuntu@ubuntu:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


ubuntu@ubuntu:~$ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module wl not found.

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


---

### Post by chili555 on 2011-02-26
I suggest you remove the CDROM as a software source.```
sudo gedit /etc/apt/sources.list
```Find the line similar to this:> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Beta amd64 (20070925)]/ gutsy main restrictedIt may not look exactly like that, but it will start with "deb cdrom:" Comment it out by adding the pound sign at the beginning:```
[COLOR="Red"]**#**[/COLOR]deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Beta amd64 (20070925)]/ gutsy main restricted
```Proofread, save and close gedit.

We are doing this because you do not have a CDROM with software on it, you have a USB memory stick. There may be a more elegant way to do this, but I am unaware of what it may be.

Next, do:```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
iwconfig
```Note any errors and...well, you know the rest.

---

### Post by jazzsax93 on 2011-02-27
Commented out the first part then:

> 
sudo rm /var/lib/apt/lists/* -vf {no errors}

sudo apt-get update

Fetched 9,050kB in 16s (564kB/s)                                               
Reading package lists... Error!
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick-updates_universe_binary-i386_Packages)
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

ubuntu@ubuntu:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off 


---

### Post by chili555 on 2011-02-27
Man, oh man! You have a sticky problem there!

Please try:```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-RENAMED
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update 
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
iwconfig
```We're going to solve this if I have to wear out every key on my laptop!

---

### Post by jazzsax93 on 2011-02-27
I think this is all the errors:

> ubuntu@ubuntu:~$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-RENAMED
mv: cannot move `/var/lib/dpkg/status' to `/var/lib/dpkg/status-RENAMED': Input/output error
ubuntu@ubuntu:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
cp: reading `/var/lib/dpkg/status-old': Input/output error


> Reading package lists... Done
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick-updates_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
ubuntu@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

> Fetched 121MB in 2min 46s (725kB/s)                                            
E: Could not perform immediate configuration on 'libbz2-1.0'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
ubuntu@ubuntu:~$ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module wl not found.
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


Tricky one then? :/

---

### Post by chili555 on 2011-02-27
> ubuntu@ubuntu:~$ [COLOR="Red"]apt-get update[/COLOR]
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root? It should be:```
[COLOR="Red"]sudo[/COLOR] apt-get update
```Please try again:```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
iwconfig
```> Tricky one then? :/ Yes, indeed! We'll fix it; I have a plasma cutter and a pry bar, if needed.

---

### Post by jazzsax93 on 2011-02-27
oops! my mistake.
Hasn't come up with "Reading package lists... Error!" this time:

> Reading package lists... Done
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_maverick-updates_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

ran the update again and no errors.

next line:
> After this operation, 444MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
E: Could not perform immediate configuration on 'libbz2-1.0'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

and
> ubuntu@ubuntu:~$ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module wl not found.
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off 


---

### Post by chili555 on 2011-02-27
I suspect there are multiple things wrong with your Apt configuration, the basis of the package management system. I am not terribly experienced in this area, it simply works for me without fiddling. You may want to post in General Help and specifically refer to "Could not perform immediate configuration on 'libbz2-1.0"

[http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

I do know that the module wl supports your device:> 0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [[COLOR="Red"]14e4:4315[/COLOR]] (rev 01) ```
$ modinfo wl | grep 4315
alias:          pci:v0000[COLOR="Red"]14E4[/COLOR]d0000[COLOR="Red"]4315[/COLOR]sv*sd*bc*sc*i*
```If you could get it properly installed, your wireless would go to work.

I am not sure I can be of more help, but don't hesitate to post back if you have a question.

---

### Post by jazzsax93 on 2011-03-01
Thanks for you help anyway. I'll try installing fully when i have some time to see if that works. Else I'll try the Netgear device. :)

---

### Post by jazzsax93 on 2011-03-21
Hi all,
Although did not manage to get the Dell wireless card working, I did find a solution for the Netgear device.

You need to download ndiswrapper for windows wireless drivers to work. Once installed find the system driver for your device (if you've already installed on Windows/Mac, these will be in your driver folder, else on the CD. I also include the driver files i used for anyone who wants them)

Install the drivers you need through ndiswrapper, restart your system if necessary then plug in the netgear device. It should then come up with "Hardware present" in ndiswrapper if you go check. And a message should come up on screen sayng that wireless connection is now available. Then just connect as normal and it should detect your network.


I hope this can be of use to someone, and worked for me in both Ubuntu 10.10 and Linux Mint v10 (both 32 bit). Else try the links at the start of this thread for further instruction until you get the right drivers.

---

### Post by forestwalkerjoe on 2011-03-31
Ok.. I don't know how your SOLVE is a SOLVE on the NetGear Card.. you gave me a ZIP file that had nothing in it.. someone want to help a fella out and find how to get this NETGEAR CARD to work.  Wireless N-300 adapter WNA3100. The same one as above where it says SOLVED. 
WHAT solve? 
thanks for the help. If it is plain to every one else.. then help the DIM <--- Me out.

---

### Post by jazzsax93 on 2011-04-16
Apologies, I am useless with .zip and .rar files. Tried a different extension, Let me know if it's gone wrong!
I hope this one contains the files (2 x .sys, 2 x .inf).

---

### Post by TheAdvenger777 on 2011-08-30
I have the same usb card and I downloaded the file you attached and I used wireless network drivers and I got it to say that the usb was connected. I'm new to Linux and i'm using zorin 5. Any help would be appreciated.

---

### Post by Maud Dib on 2012-01-15
Hi, 

I am also having problems using a Netgear n-300 wireless USB adapter with Ubuntu. 

I am a new Linux/Ubuntu user and don't know any terminal commands, or special Linux OS administration commands/procedures.  

 Is there a simple "download-and-click" solution for this (getting Netgear N300 wireless USB to work with Ubuntu)?  Or if terminal use is required, I would need the most simple fix possible (due to my being a beginner).   
  
I have to move my computer back into my own office and so I have to have wireless. 

Sincere thanks in advance for any help. :D

---

### Post by chili555 on 2012-01-15
> **Maud Dib said:**
> Hi, 

I am also having problems using a Netgear n-300 wireless USB adapter with Ubuntu. 

I am a new Linux/Ubuntu user and don't know any terminal commands, or special Linux OS administration commands/procedures.  

 Is there a simple "download-and-click" solution for this (getting Netgear N300 wireless USB to work with Ubuntu)?  Or if terminal use is required, I would need the most simple fix possible (due to my being a beginner).   
  
I have to move my computer back into my own office and so I have to have wireless. 

Sincere thanks in advance for any help. :DIn this case, download and click is the hard way and the terminal is the easy way; easier by far!

Please open a terminal and type in:```
lsusb
```Press Enter. Some data will appear. Since there are several versions of N300 and, I suspect, several different chipsets, we need to know the data before we can proceed. Post the result here. Thanks.

---

### Post by franklink1829 on 2012-01-20
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 002: ID 1058:1123 Western Digital Technologies, Inc. 
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 006: ID 0bb4:0ffe High Tech Computer Corp. 
Bus 001 Device 005: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer

---

### Post by chili555 on 2012-01-20
> Bus 001 Device 005: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]The best way to install the driver for your device is with ndiswrapper; a system that uses the Windows driver. First, please verify that ndiswrapper is installed by default. Please open a terminal and run:```
sudo dpkg -s ndiswrapper-common
```We hope we see:> Package: ndiswrapper-common
Status: install ok *installed*Next, download the attached file to your desktop. Right-click it and select *Extract Here*. Now back in the terminal, do:```
cd Desktop/wna3100-drivers
sudo su
ndiswrapper -i bcmwlhigh5.inf
modprobe ndiswrapper
echo ndiswrapper >> /etc/modules
exit
```Now is it working? If not, post back:```
ndiswrapper -l
```

---

### Post by acdiboss on 2012-02-24
Hey guys am new to this i have a dell vostro 200 desktop. am running windows vista and ubuntu 11.10 lastest 32bit/64bit fully installed. i have a netgear wireless n-300 usb adapter wna3100 i downloaded the drivers you guys posted above and about to go try it on my computer though am not sure wat/how to do it.

---

### Post by chili555 on 2012-02-24
> **acdiboss said:**
> Hey guys am new to this i have a dell vostro 200 desktop. am running windows vista and ubuntu 11.10 lastest 32bit/64bit fully installed. i have a netgear wireless n-300 usb adapter wna3100 i downloaded the drivers you guys posted above and about to go try it on my computer though am not sure wat/how to do it.The post right above, post #29, seems pretty clear. What can I clarify for you?

---

### Post by acdiboss on 2012-02-24
yup i been trying out the terminal for the past 4 hours i knw most of the basic commands now. I dont have ndiswrapper installed and i dnt have internet on to install it. so thats where we need to start, i have the files now wat?

thank you

****lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:0805 Logitech, Inc. Webcam C300
Bus 002 Device 012: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 005 Device 002: ID 1130:1620 Tenx Technology, Inc. 
Bus 005 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 013: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Bus 001 Device 006: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]

---

### Post by chili555 on 2012-02-25
> I dont have ndiswrapper installed and i dnt have internet on to install it. so thats where we need to start, i have the files now wat?
I thought it was installed by default. What does this tell us?```
ndiswrapper -v
```If you get a version number, it is installed. If not, use the Ubuntu install CD and add it as a software source. With the CD *not* in the tray, please do:```
sudo apt-cdrom add
```It will prompt for a disk to be inserted and then proceed to scan it and copy the index files. Then you may do:```
sudo apt-get install ndiswrapper-utils ndiswrapper-1.9
```It will try and fail to reach the internet but will get the files from the CD.

Then proceed as above.

---

### Post by Skullxbagel on 2012-03-03
Yess!!!! It worked I installed common and utils so now what do I do.

What I was doing wrong was that I tried installing the folder, not the files inside of the folder

---

### Post by Skullxbagel on 2012-03-03
Oops wrong thread

---

### Post by woodbrick on 2012-03-09
Hi there I have followed these instructions and now I have achieved this: 

woody@captain-coach:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
	device (0846:9020) present

But I don't know how to proceed to "get connected." Nothing is happening. No "Wireless network detected"or anything:


woody@captain-coach:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

Can anyone help? 

This is with 10.04 LTS. Any suggestions appreciated.

---

### Post by chili555 on 2012-03-09
> **woodbrick said:**
> Hi there I have followed these instructions and now I have achieved this: 

woody@captain-coach:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
	device (0846:9020) present

But I don't know how to proceed to "get connected." Nothing is happening. No "Wireless network detected"or anything:


woody@captain-coach:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

Can anyone help? 

This is with 10.04 LTS. Any suggestions appreciated.Let's see:```
lsusb
dmesg | grep ndis
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by woodbrick on 2012-03-09
Hi thanks for getting back. 

lsusb:
```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:7e11 Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 003: ID 0846:9020 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

dmesg | grep ndis:
```

[   14.359057] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   15.104834] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[   15.104952] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh5'
[   15.105357] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'
[   15.107644] usbcore: registered new interface driver ndiswrapper

```
rfkill list all:

(nothing)

Hope this helps. Thanks again.

---

### Post by chili555 on 2012-03-09
> ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'There are three possibilities: First, that we compile ndiswrapper from source code and make a change to one file: [http://sourceforge.net/tracker/index.php?func=detail&aid=3093376&group_id=93482&atid=604452](http://sourceforge.net/tracker/index.php?func=detail&aid=3093376&group_id=93482&atid=604452)

Second, that we check the bcmwlhigh5.inf and make sure it's an XP, not Vista, 7, etc. file and correct as needed.

Third, that you upgrade from 10.04 to 11.10 and your troubles will be over!

What would you like to do? I'll be happy to help in any event.

---

### Post by woodbrick on 2012-03-09
Chili 555, thanks so much for your help.

> **chili555 said:**
> we check the bcmwlhigh5.inf and make sure it's an XP, not Vista, 7, etc. file and correct as needed.What would you like to do? I'll be happy to help in any event.
The driver should be XP. It was downloaded from this thread. 

> **chili555 said:**
> upgrade from 10.04 to 11.10 and your troubles will be over!
I will be upgrading to 12.04 in a little over a month, but I usually do my upgrades from clean install.

My wife wants me out in the bungalow (beyond the ethernet cable zone) ASAP, so I guess that means I try option 1:

> **chili555 said:**
> we compile ndiswrapper from source code and make a change to one file: [http://sourceforge.net/tracker/index.php?func=detail&aid=3093376&group_id=93482&atid=604452](http://sourceforge.net/tracker/index.php?func=detail&aid=3093376&group_id=93482&atid=604452) 

Can you let me know whats involved here? I've been using ubuntu for quite a while now, but I'm still a noob when it comes to really getting 'under the hood'. 

Thanks again.

---

### Post by chili555 on 2012-03-09
> Can you let me know whats involved here?It involves downloading ndiswrapper source code here: [http://sourceforge.net/projects/ndiswrapper/files/stable/](http://sourceforge.net/projects/ndiswrapper/files/stable/)

I'd suggest you download 1.56. It may be fixed! Notice your version is currently 1.55:> [   14.359057] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)You'd then need to have build-essential and linux-headers:```
sudo apt-get install build-essential linux-headers-generic
```Download 1.56 to your desktop. Right-click it and select *Extract Here*. Open a terminal and do:```
sudo su
apt-get remove --purge ndiswrapper*
cd Desktop/ndiswrapper-1.56
make
make install
ndiswrapper -i /path/to/bcmwlhigh5.inf
modprobe -rv ndiswrapper
modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndis
exit
```I tried to compile this older version but was unsuccessful in 11.10. I'll be interested in your report.

If we still get the ntoskrnl.exe error, we'll change the file and re-compile.

PS - 1.57 makes perfectly for me in 11.10.

---

### Post by woodbrick on 2012-03-09
> **chili555 said:**
> It involves downloading ndiswrapper source code here: [http://sourceforge.net/projects/ndiswrapper/files/stable/](http://sourceforge.net/projects/ndiswrapper/files/stable/)

I'd suggest you download 1.56. It may be fixed! Notice your version is currently 1.55:You'd then need to have build-essential and linux-headers:```
sudo apt-get install build-essential linux-headers-generic
```Download 1.56 to your desktop. Right-click it and select *Extract Here*. Open a terminal and do:```
sudo su
apt-get remove --purge ndiswrapper*
cd Desktop/ndiswrapper-1.56
make
make install
ndiswrapper -i /path/to/bcmwlhigh5.inf
modprobe -rv ndiswrapper
modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndis
exit
```I tried to compile this older version but was unsuccessful in 11.10. I'll be interested in your report.

If we still get the ntoskrnl.exe error, we'll change the file and re-compile.

PS - 1.57 makes perfectly for me in 11.10.

Success!!!!

I had to add one more line. Due to this message after 'make install' code:

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.

I ran this instruction before re-installing the driver: 

```
/Desktop# ndiswrapper -e bcmwlhigh5 
```

Immediately after ```
modprobe ndiswrapper
```, my wireless connection came up. 

Thank you very much, Chili555. For a moment there I thought I was staring into the abyss of Windows Computing again!

---

### Post by chili555 on 2012-03-09
Awesome! Glad it's working! Have fun and tell your wife, as you pack up and leave for the bungalow, Chili said, "You're welcome!"

---

### Post by Introspektor on 2012-03-16
Hello Chili
I am trying to activate the netgear as well
I tried so ;any things tonight from your different posts that I got lost
I will be back on sunday for help
Hope you are still willign to provide it
I am a complete beginer with ubuntu
installed it few hours ago

---

### Post by chili555 on 2012-03-16
> I will be back on sunday for help
Hope you are still willign to provide itI'll be here and I'll be glad to help.

---

### Post by scottrasmussen on 2012-04-05
chili,
i've been reading these forums trying to get my n600 usb to be recognized by new ubuntu computer.

after typing : ndiswrapper -i /path/to/bcmwlhigh5.inf

i get:

driver bcmwlhigh5 is already installed
root@skat:/home/massolit/Desktop/ndiswrapper-1.57# modprobe -rv ndiswrapper
rmmod /lib/modules/3.0.0-12-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
root@skat:/home/massolit/Desktop/ndiswrapper-1.57# modprobe ndiswrapper
root@skat:/home/massolit/Desktop/ndiswrapper-1.57# ndiswrapper -l
autorun :** invalid driver!**
bcmwlhigh5 : driver installed

is this causing a problem?

computer is running ubuntu 11.10. 

thx!

---

### Post by chili555 on 2012-04-05
> autorun : invalid driver!
bcmwlhigh5 : driver installed

is this causing a problem?Maybe. Does your wireless work? If so, no worries. You can get rid of the error by looking in /etc/ndiswrapper for an 'autorun' file and removing it entirely.```
cd /etc/ndiswrapper && ls
```If there is an autorun file or folder in there, delete it:```
sudo rm -rf autorun
```Now check again:```
ndiswrapper -l
```Is all OK now?> after typing : ndiswrapper -i /path/to/bcmwlhigh5.inf

i get:

driver bcmwlhigh5 is already installedThere is no reason to keep installing what's already installed.

---

### Post by scottrasmussen on 2012-04-05
chili thx for the reply,

i've gotten rid of the autrun.inf (i had tried to use the steps listed above on the installation cd).  i've been able to install both b-high5, and b-high6 (didn't know if using both would help or create a conflict, but b-high5 wasn't working). n-wrapper -l lists both drivers as installed but does not detect the device (though it is detected when i type: lsusb) .  running ubuntu (11.10 32 bit) on asus m5a97 mobo with phenom II cpu.

should i try a different adapter?

question...what wireless adapter (if any) do you use?

thx
-s

---

### Post by chili555 on 2012-04-05
Isn't it a little premature to ditch your wireless adapter? You haven't, as far as I can see, done any troubleshooting or diagnosis.> didn't know if using both would help or create a conflictI'd certainly think it would conflict.

Let's take a look at:```
lsusb
arch
dmesg | grep ndis
```Thanks.

---

### Post by scottrasmussen on 2012-04-05
chili,
here you go:

massolit@skat:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100(v2) 802.11n [Broadcom BCM4323]
Bus 005 Device 002: ID 046d:c52e Logitech, Inc. 
massolit@skat:~$ arch
i686
massolit@skat:~$ dmesg | grep ndis
[   13.377288] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   13.544973] usbcore: registered new interface driver ndiswrapper

again thx for your help...i know that i'm jumping into this thread so if there's any etiquette that i'm not following let me know....

---

### Post by chili555 on 2012-04-05
Please do:```
sudo gedit /etc/ndiswrapper/bcmwlhigh5/bcmwlhigh5.inf
```You are looking for XP and your device ID. Is it there?```
;-----------------------------------------------------------------
; x86 - Win9x, Win2K, [COLOR="Red"]WinXP[/COLOR]
;
[BROADCOM]
	%BCM430ND_DeviceDesc% = BCM43XNMD, USB\VID_[COLOR="Red"]0846[/COLOR]&PID_[COLOR="Red"]9011[/COLOR]
        
```If not, you have the wrong .inf file. Where did you get it?

Close gedit _*without*_ saving any changes.

---

### Post by Ale3mend0 on 2012-04-05
when i do modprobe ndiswrapper nothing happend...what can i do, i can stop it with CTRL+C

---

### Post by Ale3mend0 on 2012-04-05
i download your attacament, i have a wna3100(v1), can you help me please chili?

lsusb output
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 005: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Bus 005 Device 002: ID 04fc:05da Sunplus Technology Co., Ltd 
Bus 008 Device 002: ID 045e:028e Microsoft Corp. Xbox360 Controller
ale@Pc:~$ 

```

---

### Post by chili555 on 2012-04-05
> i download your attacament, i have a wna3100(v1), can you help me please chili?Did you follow the steps I outlined in post #29? It's exactly what I suggest you do.

---

### Post by Ale3mend0 on 2012-04-05
yes i do this ```
root@Pc:/home/ale/Scrivania# ndiswrapper -i bcmwlhigh5.inf
installing bcmwlhigh5 ...
root@Pc:/home/ale/Scrivania# modprobe ndiswrapper


```but the last command doesen't end... what can i do?
i have a white rectangle

---

### Post by chili555 on 2012-04-05
Remove the device from the USB slot. See if you can end the process with Ctrl+c. Then look for errors or warnings:```
dmesg | grep ndis
arch
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by Ale3mend0 on 2012-04-06
> **chili555 said:**
> Remove the device from the USB slot. See if you can end the process with Ctrl+c. Then look for errors or warnings:```
dmesg | grep ndis
arch
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

i'm newbie at linux please help me
My Output : 

```
root@Pc:/home/ale# dmesg | grep ndis
[    7.314522] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[    8.422047] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[    8.422053] ndiswrapper (load_sys_files:199): couldn't prepare driver 'bcmwlhigh5'
[    8.422153] ndiswrapper (load_wrap_driver:121): couldn't load driver 'bcmwlhigh5'
[    8.427828] usbcore: registered new interface driver ndiswrapper

root@Pc:/home/ale# arch
x86_64
root@Pc:/home/ale# 






```

---

### Post by chili555 on 2012-04-06
> kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010BI have a set of 64-bit .inf files. I'll attach them in a moment. In the meantime, let's get rid of the incorrect files you have now:```
sudo modprobe -r ndiswrapper
sudo rm -rf /etc/ndiswrapper/*
```I'll be back in a few minutes with 64-bit files.

---

### Post by Ale3mend0 on 2012-04-06
> **chili555 said:**
> I have a set of 64-bit .inf files. I'll attach them in a moment. In the meantime, let's get rid of the incorrect files you have now:```
sudo modprobe -r ndiswrapper
sudo rm -rf /etc/ndiswrapper/*
```I'll be back in a few minutes with 64-bit files.

I do a fresh install of ubuntu 11.10 32 bit bcz the 12.04 64 bit give me some problem...what can i do now?

i only download ndiswrapper by software center, i am connected by ethernet it's ok?

EDIT: i do this 
```

[B]root@Pc:/home/ale/Scrivania/wna3100-drivers# ndiswrapper -i bcmwlhigh5.inf
installing bcmwlhigh5 ...
root@Pc:/home/ale/Scrivania/wna3100-drivers# modprobe ndiswrapper
root@Pc:/home/ale/Scrivania/wna3100-drivers# echo ndiswrapper >> /etc/modules
root@Pc:/home/ale/Scrivania/wna3100-drivers# exit
exit
ale@Pc:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
    device (0846:9020) present
[/B]
```


Here other output:
```

ale@Pc:~$ dmesg | grep ndis
[  479.941276] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  480.195586] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[  480.195833] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[  480.492207] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[  480.492212] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[  480.492218] ndiswrapper (mp_halt:262): device f26c8480 is not initialized - not halting
[  480.492221] ndiswrapper: device eth%d removed
[  480.492236] ndiswrapper: probe of 1-2:1.0 failed with error -22
[  480.496116] usbcore: registered new interface driver ndiswrapper
ale@Pc:~$ 

```

---

### Post by chili555 on 2012-04-06
Try these files instead. Follow the instructions in post #29 above but, using the files I've attached, install bcmn43x**x64**.inf.

I'm off to shop with Mrs. Chili; I'll check in later. Good luck.

---

### Post by Ale3mend0 on 2012-04-06
> **chili555 said:**
> Try these files instead. Follow the instructions in post #29 above but, using the files I've attached, install bcmn43x**x64**.inf.

I'm off to shop with Mrs. Chili; I'll check in later. Good luck.

Read #59 please...

---

### Post by chili555 on 2012-04-06
> **Ale3mend0 said:**
> Read #59 please...Soory about that! I guess our posts crossed. Please remove the bcmwlhigh5.inf and try the bcmn43x**x32**.inf from the file I attached.```
sudo modprobe -r ndiswrapper
sudo ndiswraper -e bcmwlhigh5
sudo rm -rf /etc/ndiswrapper/*
cd ~/Scrivania/ndis_bcmwl
sudo ndiswrapper -i bcmn43x**x32**.inf
sudo modprobe ndiswrapper
dmesg | grep ndis
```Now I'm *really* leaving!

---

### Post by Ale3mend0 on 2012-04-06
Thnaks! i reboot and all works perfect! you're my god!:lolflag:

---

### Post by chili555 on 2012-04-06
> all works perfect! Awesome! Glad I could help you. Have fun and thanks for your kind words.

---

### Post by scottrasmussen on 2012-04-06
chili,

hope you had fun at the shop....

when i type: sudo gedit /etc/ndiswrapper/bcmwlhigh5/bcmwlhigh5.inf

i get: ** (gedit:2101): WARNING **: Hit unhandled case 1 (Invalid byte sequence in conversion input) in parse_error.

and i downloaded the drivers from this forum.

thx

-s

---

### Post by chili555 on 2012-04-06
Please try:```
cat /etc/ndiswrapper/bcmwlhigh5/bcmwlhigh5.inf | less
```Or maybe:```
cat /etc/ndiswrapper/bcmwlhigh5/bcmwlhigh5.inf 
```Some of the .inf files are a bit tricky. Where did you get the .inf file you're examining? Not from me, I hope!

---

### Post by scottrasmussen on 2012-04-06
chili,

when i type:  cat /etc/ndiswrapper/bcmwlhigh5/bcmwlhigh5.inf 
i get:

```
    HKR,    Ndi\params\IBSSGProtection,default,,"2"

    HKR,    Ndi\params\Rate, ParamDesc,    0,    %Rate%
    HKR,    Ndi\params\Rate, type,        0,    "enum"
    HKR,    Ndi\params\Rate\enum, "0",    0,    %Usebestrate%
    HKR,    Ndi\params\Rate\enum, "2",    0,    " 1"
    HKR,    Ndi\params\Rate\enum, "4",    0,    " 2"
    HKR,    Ndi\params\Rate\enum, "11",    0,    " 5.5"
    HKR,    Ndi\params\Rate\enum, "12",    0,    " 6"
    HKR,    Ndi\params\Rate\enum, "18",    0,    " 9"
    HKR,    Ndi\params\Rate\enum, "22",    0,    "11"
    HKR,    Ndi\params\Rate\enum, "24",    0,    "12"
    HKR,    Ndi\params\Rate\enum, "36",    0,    "18"
    HKR,    Ndi\params\Rate\enum, "48",    0,    "24"
    HKR,    Ndi\params\Rate\enum, "72",    0,    "36"
    HKR,    Ndi\params\Rate\enum, "96",    0,    "48"
    HKR,    Ndi\params\Rate\enum, "108",0,    "54"
    HKR,    Ndi\params\Rate,default,,"0"

    HKR,    Ndi\params\Afterburner, ParamDesc,    0,      %Afterburner%
    HKR,    Ndi\params\Afterburner, type,       0,      "enum"
    HKR,    Ndi\params\Afterburner\enum, "0",   0,      %Disabled%
    HKR,    Ndi\params\Afterburner\enum, "1",   0,      %Enabled%
    HKR,    Ndi\params\Afterburner,default,,"0"
        
    HKR,    Ndi\params\Intolerant, ParamDesc,    0,      %Intolerant%
    HKR,    Ndi\params\Intolerant, type,         0,      "enum"
    HKR,    Ndi\params\Intolerant\enum, "0",     0,      %Disabled%
    HKR,    Ndi\params\Intolerant\enum, "1",     0,      %Enabled%
    HKR,    Ndi\params\Intolerant,default,,"0"

    HKR,    Ndi\params\BandwidthCap, ParamDesc,     0,      "Bandwidth Capability"
    HKR,    Ndi\params\BandwidthCap, type,          0,      "enum"
    HKR,    Ndi\params\BandwidthCap\enum, "0",      0,      "11b/g/n:20MHz"
    HKR,    Ndi\params\BandwidthCap\enum, "1",      0,      "11b/g/n:20/40MHz"
    HKR,    Ndi\params\BandwidthCap,default,,"0"

    ; option to override antenna selection, -1: no override, 0: no selection
    HKR,                    ,"mimo_antsel",    0,    "-1"

; options common to both b and g
[bg.options.reg]
    HKR,    Ndi\params\Chanspec, ParamDesc, 0, %IBSSChannelNumber%
    HKR,    Ndi\params\Chanspec, type,      0, "enum"
    HKR,    Ndi\params\Chanspec, default,   0, "11"
      
    HKR,    Ndi\params\ApCompatMode, ParamDesc,    0,    %ApCompatibilityMode%
    HKR,    Ndi\params\ApCompatMode, type,        0,    "enum"
    HKR,    Ndi\params\ApCompatMode\enum, "1",    0,    %BroaderCompat%
    HKR,    Ndi\params\ApCompatMode\enum, "0",    0,    %HigherPerf%
    HKR,    Ndi\params\ApCompatMode,default,,"0"


[a.options.reg]
    HKR,    Ndi\params\Afterburner, ParamDesc,    0,      %Afterburner%
    HKR,    Ndi\params\Afterburner, type,       0,      "enum"
    HKR,    Ndi\params\Afterburner\enum, "0",   0,      %Disabled%
    HKR,    Ndi\params\Afterburner\enum, "1",   0,      %Enabled%
    HKR,    Ndi\params\Afterburner,default,,"0"

    HKR,    Ndi\params\RateA, ParamDesc,    0,    %Rate_802_11a%
    HKR,    Ndi\params\RateA, type,        0,    "enum"
    HKR,    Ndi\params\RateA\enum, "0",    0,    %Usebestrate%
    HKR,    Ndi\params\RateA\enum, "12",    0,    " 6"
    HKR,    Ndi\params\RateA\enum, "18",    0,    " 9"
    HKR,    Ndi\params\RateA\enum, "24",    0,    "12"
    HKR,    Ndi\params\RateA\enum, "36",    0,    "18"
    HKR,    Ndi\params\RateA\enum, "48",    0,    "24"
    HKR,    Ndi\params\RateA\enum, "72",    0,    "36"
    HKR,    Ndi\params\RateA\enum, "96",    0,    "48"
    HKR,    Ndi\params\RateA\enum, "108",0,    "54"
    HKR,    Ndi\params\RateA,default,,"0"

    HKR,    Ndi\params\Chanspec, ParamDesc, 0, %IBSSChannelNumber%
    HKR,    Ndi\params\Chanspec, type,      0, "enum"
    HKR,    Ndi\params\Chanspec, default,   0, "36"

[bag.options.reg]
    HKR,    Ndi\params\Afterburner, ParamDesc,    0,      %Afterburner%
    HKR,    Ndi\params\Afterburner, type,       0,      "enum"
    HKR,    Ndi\params\Afterburner\enum, "0",   0,      %Disabled%
    HKR,    Ndi\params\Afterburner\enum, "1",   0,      %Enabled%
    HKR,    Ndi\params\Afterburner,default,,"0"

    HKR,     Ndi\params\11HNetworks, ParamDesc, 0,     "802.11h+d"
    HKR,     Ndi\params\11HNetworks, type,         0, "enum"
    HKR,     Ndi\params\11HNetworks\enum, "1",     0, %Loose_11h%
    HKR,     Ndi\params\11HNetworks\enum, "2",     0, %Strict_11h%
    HKR,     Ndi\params\11HNetworks\enum, "4",     0, %Loose_11h_and_11d%
    HKR,     Ndi\params\11HNetworks,default,,"1"

    HKR,    Ndi\params\RoamTrigger, ParamDesc,    0,    %RoamingDecision%
    HKR,    Ndi\params\RoamTrigger, type,        0,    "enum"
    HKR,    Ndi\params\RoamTrigger\enum, "3",    0,    %Auto%
    HKR,    Ndi\params\RoamTrigger\enum, "1",    0,    %OptimizeBandwidth%
    HKR,    Ndi\params\RoamTrigger\enum, "0",    0,    %Default%
    HKR,    Ndi\params\RoamTrigger\enum, "2",    0,    %OptimizeDistance%
    HKR,    Ndi\params\RoamTrigger,default,,"3"
    
    HKR,    Ndi\params\PLCPHeader, ParamDesc,    0,    %BSSPLCPHeader%
    HKR,    Ndi\params\PLCPHeader, type,        0,    "enum"
    HKR,    Ndi\params\PLCPHeader\enum, "-1",    0,    %Long%
    HKR,    Ndi\params\PLCPHeader\enum, "0",    0,    %AutoShortLong%
    HKR,    Ndi\params\PLCPHeader,default,,"0"

    HKR,    Ndi\params\band, ParamDesc,    0,    %DisableBands%
    HKR,    Ndi\params\band, type,        0,    "enum"
    HKR,    Ndi\params\band\enum, "0",    0,    %None%
    HKR,    Ndi\params\band\enum, "1",    0,    %Disable80211gb%
    HKR,    Ndi\params\band\enum, "2",    0,    %Disable80211a%
    HKR,    Ndi\params\band,default,,"0"

    HKR,    Ndi\params\BandPref, ParamDesc,    0,    %BandPreference%
    HKR,    Ndi\params\BandPref, type,        0,    "enum"
    HKR,    Ndi\params\BandPref\enum, "0",    0,    %None%
    HKR,    Ndi\params\BandPref\enum, "1",    0,    %Prefer80211a%
    HKR,    Ndi\params\BandPref\enum, "2",    0,    %Prefer80211gb%
    HKR,    Ndi\params\BandPref,default,,"0"
        
    HKR,    Ndi\params\AssocRoamPref, ParamDesc,    0,    %AssociationRoamPreference%
    HKR,    Ndi\params\AssocRoamPref, type,        0,    "enum"
    HKR,    Ndi\params\AssocRoamPref\enum, "0",    0,    %Disabled%
    HKR,    Ndi\params\AssocRoamPref\enum, "1",    0,    %Enabled%
    HKR,    Ndi\params\AssocRoamPref,default,,"0"

    HKR,    Ndi\params\IBSSMode, ParamDesc,       0,      %IBSS54gtmMode%
    HKR,    Ndi\params\IBSSMode, type,         0,      "enum"
    HKR,    Ndi\params\IBSSMode\enum, "0",     0,      %80211bOnly%
    HKR,    Ndi\params\IBSSMode\enum, "2",     0,      %54gAuto%
    HKR,    Ndi\params\IBSSMode\enum, "4",     0,      %54gPerformance%
    ;default from bcmwl5[ei].inf

    HKR,    Ndi\params\IBSSGProtection, ParamDesc,    0,      %IBSS54gtmProtectionMode%
    HKR,    Ndi\params\IBSSGProtection, type,       0,      "enum"
    HKR,    Ndi\params\IBSSGProtection\enum, "0",   0,      %Disabled%
    HKR,    Ndi\params\IBSSGProtection\enum, "2",   0,      %Auto%
    HKR,    Ndi\params\IBSSGProtection,default,,"2"


    HKR,    Ndi\params\RateA, ParamDesc,    0,    %Rate_802_11a%
    HKR,    Ndi\params\RateA, type,        0,    "enum"
    HKR,    Ndi\params\RateA\enum, "0",    0,    %Usebestrate%
    HKR,    Ndi\params\RateA\enum, "12",    0,    " 6"
    HKR,    Ndi\params\RateA\enum, "18",    0,    " 9"
    HKR,    Ndi\params\RateA\enum, "24",    0,    "12"
    HKR,    Ndi\params\RateA\enum, "36",    0,    "18"
    HKR,    Ndi\params\RateA\enum, "48",    0,    "24"
    HKR,    Ndi\params\RateA\enum, "72",    0,    "36"
    HKR,    Ndi\params\RateA\enum, "96",    0,    "48"
    HKR,    Ndi\params\RateA\enum, "108",0,    "54"
    HKR,    Ndi\params\RateA,default,,"0"


    HKR,    Ndi\params\Rate, ParamDesc,    0,    %Rate_802_11bg%
    HKR,    Ndi\params\Rate, type,        0,    "enum"
    HKR,    Ndi\params\Rate\enum, "0",    0,    %Usebestrate%
    HKR,    Ndi\params\Rate\enum, "2",    0,    " 1"
    HKR,    Ndi\params\Rate\enum, "4",    0,    " 2"
    HKR,    Ndi\params\Rate\enum, "11",    0,    " 5.5"
    HKR,    Ndi\params\Rate\enum, "12",    0,    " 6"
    HKR,    Ndi\params\Rate\enum, "18",    0,    " 9"
    HKR,    Ndi\params\Rate\enum, "22",    0,    "11"
    HKR,    Ndi\params\Rate\enum, "24",    0,    "12"
    HKR,    Ndi\params\Rate\enum, "36",    0,    "18"
    HKR,    Ndi\params\Rate\enum, "48",    0,    "24"
    HKR,    Ndi\params\Rate\enum, "72",    0,    "36"
    HKR,    Ndi\params\Rate\enum, "96",    0,    "48"
    HKR,    Ndi\params\Rate\enum, "108",0,    "54"
    HKR,    Ndi\params\Rate,default,,"0"

    HKR,    Ndi\params\Chanspec, ParamDesc, 0, %IBSSChannelNumber%
    HKR,    Ndi\params\Chanspec, type,      0, "enum"
    HKR,    Ndi\params\Chanspec, default,   0, "11"

    HKR,    Ndi\params\ApCompatMode, ParamDesc,    0,    %ApCompatibilityMode%
    HKR,    Ndi\params\ApCompatMode, type,        0,    "enum"
    HKR,    Ndi\params\ApCompatMode\enum, "1",    0,    %BroaderCompat%
    HKR,    Ndi\params\ApCompatMode\enum, "0",    0,    %HigherPerf%
    HKR,    Ndi\params\ApCompatMode,default,,"0"

[bagn.options.reg]
    HKR,    Ndi\params\Afterburner, ParamDesc,    0,      %Afterburner%
    HKR,    Ndi\params\Afterburner, type,       0,      "enum"
    HKR,    Ndi\params\Afterburner\enum, "0",   0,      %Disabled%
    HKR,    Ndi\params\Afterburner\enum, "1",   0,      %Enabled%
    HKR,    Ndi\params\Afterburner,default,,"0"

    HKR,     Ndi\params\11HNetworks, ParamDesc, 0,     "802.11h+d"
    HKR,     Ndi\params\11HNetworks, type,         0, "enum"
    HKR,     Ndi\params\11HNetworks\enum, "1",     0, %Loose_11h%
    HKR,     Ndi\params\11HNetworks\enum, "2",     0, %Strict_11h%
    HKR,     Ndi\params\11HNetworks\enum, "4",     0, %Loose_11h_and_11d%
    HKR,     Ndi\params\11HNetworks,default,,"1"

    HKR,    Ndi\params\RoamTrigger, ParamDesc,    0,    %RoamingDecision%
    HKR,    Ndi\params\RoamTrigger, type,        0,    "enum"
    HKR,    Ndi\params\RoamTrigger\enum, "3",    0,    %Auto%
    HKR,    Ndi\params\RoamTrigger\enum, "1",    0,    %OptimizeBandwidth%
    HKR,    Ndi\params\RoamTrigger\enum, "0",    0,    %Default%
    HKR,    Ndi\params\RoamTrigger\enum, "2",    0,    %OptimizeDistance%
    HKR,    Ndi\params\RoamTrigger,default,,"3"

    HKR,    Ndi\params\PLCPHeader, ParamDesc,    0,    %BSSPLCPHeader%
    HKR,    Ndi\params\PLCPHeader, type,        0,    "enum"
    HKR,    Ndi\params\PLCPHeader\enum, "-1",    0,    %Long%
    HKR,    Ndi\params\PLCPHeader\enum, "0",    0,    %AutoShortLong%
    HKR,    Ndi\params\PLCPHeader,default,,"0"

    HKR,    Ndi\params\band, ParamDesc,    0,    %DisableBands%
    HKR,    Ndi\params\band, type,        0,    "enum"
    HKR,    Ndi\params\band\enum, "0",    0,    %None%
    HKR,    Ndi\params\band\enum, "1",    0,    %Disable80211gb%
    HKR,    Ndi\params\band\enum, "2",    0,    %Disable80211a%
    HKR,    Ndi\params\band,default,,"0"

    HKR,    Ndi\params\BandPref, ParamDesc,    0,    %BandPreference%
    HKR,    Ndi\params\BandPref, type,        0,    "enum"
    HKR,    Ndi\params\BandPref\enum, "0",    0,    %None%
    HKR,    Ndi\params\BandPref\enum, "1",    0,    %Prefer80211a%
    HKR,    Ndi\params\BandPref\enum, "2",    0,    %Prefer80211gb%
    HKR,    Ndi\params\BandPref,default,,"0"
        
    HKR,    Ndi\params\AssocRoamPref, ParamDesc,    0,    %AssociationRoamPreference%
    HKR,    Ndi\params\AssocRoamPref, type,        0,    "enum"
    HKR,    Ndi\params\AssocRoamPref\enum, "0",    0,    %Disabled%
    HKR,    Ndi\params\AssocRoamPref\enum, "1",    0,    %Enabled%
    HKR,    Ndi\params\AssocRoamPref,default,,"0"

    HKR,    Ndi\params\IBSSMode, ParamDesc,    0,      %IBSSMode%
    HKR,    Ndi\params\IBSSMode, type,         0,      "enum"
    HKR,    Ndi\params\IBSSMode\enum, "0",     0,      %80211abOnly%
    HKR,    Ndi\params\IBSSMode\enum, "2",     0,      %80211abgAuto%
    HKR,    Ndi\params\IBSSMode\enum, "4",     0,      %80211abgPerf%
    HKR,    Ndi\params\IBSSMode\enum, "5",     0,      %80211abgnAuto%
    HKR,    Ndi\params\IBSSMode,default,,"0"

    HKR,    Ndi\params\IBSSGProtection, ParamDesc,    0,      %IBSS54gtmProtectionMode%
    HKR,    Ndi\params\IBSSGProtection, type,       0,      "enum"
    HKR,    Ndi\params\IBSSGProtection\enum, "0",   0,      %Disabled%
    HKR,    Ndi\params\IBSSGProtection\enum, "2",   0,      %Auto%
    HKR,    Ndi\params\IBSSGProtection,default,,"2"

    HKR,    Ndi\params\RateA, ParamDesc,    0,    %Rate_802_11a%
    HKR,    Ndi\params\RateA, type,        0,    "enum"
    HKR,    Ndi\params\RateA\enum, "0",    0,    %Usebestrate%
    HKR,    Ndi\params\RateA\enum, "12",    0,    " 6"
    HKR,    Ndi\params\RateA\enum, "18",    0,    " 9"
    HKR,    Ndi\params\RateA\enum, "24",    0,    "12"
    HKR,    Ndi\params\RateA\enum, "36",    0,    "18"
    HKR,    Ndi\params\RateA\enum, "48",    0,    "24"
    HKR,    Ndi\params\RateA\enum, "72",    0,    "36"
    HKR,    Ndi\params\RateA\enum, "96",    0,    "48"
    HKR,    Ndi\params\RateA\enum, "108",0,    "54"
    HKR,    Ndi\params\RateA,default,,"0"

    HKR,    Ndi\params\Rate, ParamDesc,    0,    %Rate_802_11bg%
    HKR,    Ndi\params\Rate, type,        0,    "enum"
    HKR,    Ndi\params\Rate\enum, "0",    0,    %Usebestrate%
    HKR,    Ndi\params\Rate\enum, "2",    0,    " 1"
    HKR,    Ndi\params\Rate\enum, "4",    0,    " 2"
    HKR,    Ndi\params\Rate\enum, "11",    0,    " 5.5"
    HKR,    Ndi\params\Rate\enum, "12",    0,    " 6"
    HKR,    Ndi\params\Rate\enum, "18",    0,    " 9"
    HKR,    Ndi\params\Rate\enum, "22",    0,    "11"
    HKR,    Ndi\params\Rate\enum, "24",    0,    "12"
    HKR,    Ndi\params\Rate\enum, "36",    0,    "18"
    HKR,    Ndi\params\Rate\enum, "48",    0,    "24"
    HKR,    Ndi\params\Rate\enum, "72",    0,    "36"
    HKR,    Ndi\params\Rate\enum, "96",    0,    "48"
    HKR,    Ndi\params\Rate\enum, "108",0,    "54"
    HKR,    Ndi\params\Rate,default,,"0"

    HKR,    Ndi\params\Chanspec, ParamDesc, 0, %IBSSChannelNumber%
    HKR,    Ndi\params\Chanspec, type,      0, "enum"
    HKR,    Ndi\params\Chanspec, default,   0, "11"

    HKR,    Ndi\params\ApCompatMode, ParamDesc,    0,    %ApCompatibilityMode%
    HKR,    Ndi\params\ApCompatMode, type,        0,    "enum"
    HKR,    Ndi\params\ApCompatMode\enum, "1",    0,    %BroaderCompat%
    HKR,    Ndi\params\ApCompatMode\enum, "0",    0,    %HigherPerf%
    HKR,    Ndi\params\ApCompatMode,default,,"0"

    HKR,    Ndi\params\Intolerant, ParamDesc,    0,      %Intolerant%
    HKR,    Ndi\params\Intolerant, type,         0,      "enum"
    HKR,    Ndi\params\Intolerant\enum, "0",     0,      %Disabled%
    HKR,    Ndi\params\Intolerant\enum, "1",     0,      %Enabled%
    HKR,    Ndi\params\Intolerant,default,,"0"

    HKR,     Ndi\params\11NPreamble, ParamDesc,  0,     "802.11n Preamble"
    HKR,     Ndi\params\11NPreamble, type,         0, "enum"
    HKR,     Ndi\params\11NPreamble\enum, "-1",     0, %Auto%
    HKR,     Ndi\params\11NPreamble\enum, "0",     0, %Mixed_Mode%
    HKR,     Ndi\params\11NPreamble,default,,"-1"

    HKR,     Ndi\params\ShortGI, ParamDesc,  0,     "Short GI"
    HKR,     Ndi\params\ShortGI, type,         0, "enum"
    HKR,     Ndi\params\ShortGI\enum, "-1",     0,     %Auto%
    HKR,     Ndi\params\ShortGI\enum, "0",     0,    %Disabled%
    HKR,     Ndi\params\ShortGI,default,,"-1"

    HKR,    Ndi\params\BandwidthCap, ParamDesc,     0,      "Bandwidth Capability"
    HKR,    Ndi\params\BandwidthCap, type,          0,      "enum"
    HKR,    Ndi\params\BandwidthCap\enum, "0",      0,      "11a/b/g:20MHz"
    HKR,    Ndi\params\BandwidthCap\enum, "1",      0,      "11a/b/g:20/40MHz"
    HKR,    Ndi\params\BandwidthCap\enum, "2",      0,      "11a:20/40;11bg:20MHz"
    HKR,    Ndi\params\BandwidthCap,default,,"1"

[strings]
V_BCM="Netgear"
BCM43XX_HELP="The Broadcom 802.11 Network Adapter provides wireless local area networking."
BCM43XX_Service_DispName="Broadcom 802.11 Network Adapter Driver"
BCM43XX_DiskName="802.11 Network Adapter Install Disk"
BCM430ND_DeviceDesc="Wireless N-300 USB Adapter WNA3100"
BCMH43XX_Service_DispName="Broadcom 802.11 USB Network Adapter Driver"
54gAuto="54g - Auto"
54gPerformance="54g - Performance"
80211bOnly="802.11b Only"
AntennaDiversity="Antenna Diversity"
Auto="Auto"
AutoShortLong="Auto (Short/Long)"
BSSPLCPHeader="BSS PLCP Header"
BlueToothCollaboration="Bluetooth Collaboration"
Default="Default"
Disable="Disable"
Disable80211a="Disable 802.11a"
Disable80211gb="Disable 802.11g/b"
DisableBands="Disable Bands"
Disabled="Disabled"
Enable="Enable"
Enabled="Enabled"
FragmentationThreshold="Fragmentation Threshold"
IBSS54gtmMode="IBSS 54g(tm) Mode"
IBSS54gtmProtectionMode="IBSS 54g(tm) Protection Mode"
IBSSMode="IBSS Mode"
LocallyAdministeredMACAddress="Locally Administered MAC Address"
Long="Long"
None="None"
OptimizeBandwidth="Optimize Bandwidth"
OptimizeDistance="Optimize Distance"
PLCPHeader="PLCP Header"
PowerOutput="Power Output"
PowerSaveMode="Power Save Mode"
Prefer80211a="Prefer 802.11a"
Prefer80211gb="Prefer 802.11g/b"
RTSThreshold="RTS Threshold"
RadioEnableDisable="Radio Enable/Disable"
Rate="Rate"
RoamingDecision="Roaming Decision"
XPress_Technology="XPress (TM) Technology"
Fast="Fast"
MinimumPowerConsumption="Minimum Power Consumption"
AssociationRoamPreference="Association Roam Preference"
BandPreference="Band Preference"
RoamingTendency="Roam Tendency"
Aggressive="Aggressive"
Moderate="Moderate"
Conservative="Conservative"
ApCompatibilityMode="AP Compatibility Mode"
BroaderCompat="Broader Compatibility"
HigherPerf="Higher Performance"
WME="WMM"
Afterburner="Afterburner"
Rate_802_11a="Rate (802.11a)"
Rate_802_11bg="Rate (802.11b/g)"
WZC_Managed_Ethernet="WZC Managed Ethernet"
Legacy="Legacy"
IBSS_Link_Indication="IBSS Link Indication"
Manage_Wireless_Settings="Manage Wireless Settings"
DisableRadioUponWiredConnection="Disable Upon Wired Connect"
SSIDAutoPromote="SSID Autopromote"
IBSSChannelNumber="WZC IBSS Channel Number"
IbssAllowed="IBSS Allowed"
Loose_11h_and_11d="Loose 11h+d"
Loose_11h="Loose 11h"
Strict_11h="Strict 11h"
MixedCell="Mixed Cell Support"
vlan_mode="VLAN Priority Support"
80211abOnly="802.11a/b Only"
80211abgAuto="802.11a/b/g Auto"
80211abgPerf="802.11a/b/g Performance"
80211abgnAuto="802.11a/b/g/n Auto"
PriorityVLANTag="Priority & VLAN"
PriorityAndVLANDisabled="Priority & VLAN Disabled"
PriorityAndVLANEnabled="Priority & VLAN Enabled"
PriorityEnabled="Priority Enabled"
VLANEnabled="VLAN Enabled"
Lock_Wireless_Settings="Lock Wireless Settings"
Usebestrate="Best Rate"
WakeUpCapabilities="Wake-Up Mode"
MagicPacket="Magic Packet"
NetPattern="Wake Up Frame"
Intolerant="40MHz Intolerant"
All="All"
MagicNet="Magic & WakeUp Frame"
LossofAP="LossOfLink"
Mixed_Mode="Mixed Mode"
LossMagic="MagicPkt & LinkLoss"
LossNet="WakeUpPkt & LinkLoss"


[strings.0407] 
V_BCM="Netgear"
BCM43XX_HELP="Der Broadcom 802.11-Netzwerkadapter erm&#65533;glicht drahtlosen Local Area Netzwerkbetrieb."
BCM43XX_Service_DispName="Treiber f&#65533;r Broadcom 802.11-Netzwerkadapter"
BCM43XX_DiskName="Installationsdisk f&#65533;r 802.11-Netzwerkadapter"
BCM430ND_DeviceDesc="Wireless N-300 USB Adapter WNA3100"
BCMH43XX_Service_DispName="Treiber f&#65533;r Broadcom 802.11-USB-Netzwerkadapter"
54gAuto="54g Auto"
54gPerformance="54g - Leistung"
80211bOnly="Nur 802.11b"
AntennaDiversity="Antennendiversit&#65533;t"
Auto="Automatisch"
AutoShortLong="Auto (Kurz/Lang)"
BSSPLCPHeader="BSS-PLCP-Header"
BlueToothCollaboration="Bluetooth-Kompatibilit&#65533;t"
Default="Standard"
Disable="Deaktivieren"
Disable80211a="802.11a deaktivieren"
Disable80211gb="802.11g/b deaktivieren"
DisableBands="Frequenzbereiche deaktivieren"
Disabled="Deaktiviert"
Enable="Aktivieren"
Enabled="Aktiviert"
FragmentationThreshold="Fragmentierungsschwelle"
IBSS54gtmMode="IBSS-54g(tm)-Modus"
IBSS54gtmProtectionMode="IBSS-54g(tm)-Schutzmodus"
IBSSMode="IBSS-Modus"
LocallyAdministeredMACAddress="Lokal verwaltete MAC-Adresse"
Long="Lang"
None="Keine"
OptimizeBandwidth="Bandbreite optimieren"
OptimizeDistance="Entfernung optimieren"
PLCPHeader="PLCP-Header"
PowerOutput="Ausgangsleistung"
PowerSaveMode="Stromsparmodus"
Prefer80211a="802.11a bevorzugt"
Prefer80211gb="802.11g/b bevorzugt"
RTSThreshold="RTS-Schwelle"
RadioEnableDisable="Funkger&#65533;t aktiviert/deaktiviert"
Rate="Geschwindigkeit"
RoamingDecision="Roamingentscheidung"
XPress_Technology="XPress(TM)-Technologie"
Fast="Schnell"
MinimumPowerConsumption="Mindeststromverbrauch"
AssociationRoamPreference="Bevorzugte Roaming-Zuordnung"
BandPreference="Bevorzugtes Band"
RoamingTendency="Roaming-Tendenz"
Aggressive="Hoch"
Moderate="Mittel"
Conservative="Traditionell"
ApCompatibilityMode="Modus ""AP-Kompatibilit&#65533;t"""
BroaderCompat="Gr&#65533;&#65533;ere Kompatibilit&#65533;t"
HigherPerf="H&#65533;here Leistung"
WME="WMM"
Afterburner="Afterburner"
Rate_802_11a="Geschwindigkeit (802.11a)"
Rate_802_11bg="Geschwindigkeit (802.11b/g)"
WZC_Managed_Ethernet="WZC verwaltetes Ethernet"
Legacy="&#65533;ltere Ger&#65533;te"
IBSS_Link_Indication="IBSS-Verbindungsindikator"
Manage_Wireless_Settings="Drahtlose Einstellungen verwalten"
DisableRadioUponWiredConnection="Funkger&#65533;t bei Kabel deaktivieren"
SSIDAutoPromote="SSID Autopromote"
IBSSChannelNumber="WZC IBSS-Kanalnummer"
IbssAllowed="IBSS zugelassen"
Loose_11h_and_11d="Locker 11h+d"
Loose_11h="Locker 11h"
Strict_11h="Streng 11h"
MixedCell="Unterst&#65533;tzung gemischter Zellen"
vlan_mode="VLAN-Priorit&#65533;tunterst&#65533;tzung"
80211abOnly="Nur 802.11a/b"
80211abgAuto="802.11a/b/g   Auto"
80211abgPerf="802.11a/b/g   Performance"
80211abgnAuto="802.11a/b/g/n   Auto"
PriorityVLANTag="Priorit&#65533;t & VLAN"
PriorityAndVLANDisabled="Priorit&#65533;t & VLAN deaktiviert"
PriorityAndVLANEnabled="Priorit&#65533;t & VLAN aktiviert"
PriorityEnabled="Priorit&#65533;t aktiviert"
VLANEnabled="VLAN aktiviert"
Lock_Wireless_Settings="Wireless-Einstellungen sperren"
Usebestrate="Beste Geschwindigkeit"
WakeUpCapabilities="Reaktivierungsmodus"
MagicPacket="Magic Packet"
NetPattern="Wake Up Frame"
Intolerant="40 MHz intolerant"
All="Alle"
MagicNet="Magic und WakeUp Frame"
LossofAP="Verbindungsverlust"
Mixed_Mode="Mixed Mode"
LossMagic="MagicPkt u. LinkLoss"
LossNet="WakeUpPkt u. LinkLoss"

```i did try to install bcmn43xx32 but received an error message so deleted it.

and again ndiswrapper -l lists the driver as installed but does not list the device, but lsusb does list the adapter as present

all files have been downloaded from this forum

thx

---

### Post by clinteas on 2012-04-07
The .exe seems to only install the driver for the particular OS it is being run on, so trying to get an XP 64bit driver for this by installing it on Vista 32bit and search the installation directory will fail. I'm getting the same error as the person above, I can install the driver you provided with ndiswrapper, but when running the -l command, the device isn't listed, and no wlan0 interface seems available.

---

### Post by chili555 on 2012-04-07
> I'm getting the same error as the person above, I can install the driver you provided with ndiswrapper, but when running the -l command, the device isn't listed, and no wlan0 interface seems available.Do you have exactly the same device according to lsmod?

---

### Post by chili555 on 2012-04-07
> **scottrasmussen said:**
> chili,

when i type:  cat /etc/ndiswrapper/bcmwlhigh5/bcmwlhigh5.inf 
i get:

```
    HKR,    Ndi\params\IBSSGProtection,default,,"2"

    HKR,    Ndi\params\Rate, ParamDesc,    0,    %Rate%
    HKR,    Ndi\params\Rate, type,        0,    "enum"

    <snip>
    
    
LossNet="WakeUpPkt u. LinkLoss"

```i did try to install bcmn43xx32 but received an error message so deleted it.

and again ndiswrapper -l lists the driver as installed but does not list the device, but lsusb does list the adapter as present

all files have been downloaded from this forum

thxHmmm. I think the terminal showed you only the last lines; We actually need to see the *first* 20 or so lines. Please try this:```
cat /etc/ndiswrapper/bcmwlhigh5/bcmwlhigh5.inf > bcmwl.txt
head -n20 bcmwl.txt > bcmwl_head.txt
```Now copy and paste the bcmwl_head.txt file into your reply.> i did try to install bcmn43xx32 but received an error message so deleted it.It always helps diagnose the problem if we know the exact error!

You may have needed to remove bcmwlhigh5 first.

---

### Post by skabople on 2012-04-07
Hello,

I did not see a post about this in the thread and please correct me if I'm wrong.

Personally I have had the same problem with my Sabrent NT-H802N wireless usb dongle. My solution was to install linux-backports-modules-wireless-* there are many packages with that title but just have to find the one that works.

I hope this helps!

Regards,
Kyle

---

### Post by chili555 on 2012-04-07
> **skabople said:**
> Hello,

I did not see a post about this in the thread and please correct me if I'm wrong.

Personally I have had the same problem with my Sabrent NT-H802N wireless usb dongle. My solution was to install linux-backports-modules-wireless-* there are many packages with that title but just have to find the one that works.

I hope this helps!

Regards,
KyleYou are generally quite correct; however, the Broadcom bcmwlhigh devices are not supported in Linux at all and not in backports at all. If it were that easy, I'd schedule a vacation, take the afternoon off and have time to clean my house!

---

### Post by scottrasmussen on 2012-04-09
hi chili...hope you had a nice weekend...

so i entered the code as directed in post 70, but nothing happened.   i just received a new command prompt line

---

### Post by chili555 on 2012-04-09
Did you miss this step?> Now copy and paste the bcmwl_head.txt file into your reply.

---

### Post by scottrasmussen on 2012-04-09
chili,

i'm getting an error message saying the file has invalid characters ..

```
\FE;\00;\00 \00
\00;\00;\00 \00b\00c\00m\00w\00l\00h\00i\00g\00h\005\00.\00i\00n\00f\00 \00
\00;\00;\00 \00
\00;\00;\00 \00C\00o\00p\00y\00r\00i\00g\00h\00t\00 \001\009\009\008\00-\002\000\000\009\00,\00 \00B\00r\00o\00a\00d\00c\00o\00m\00 \00C\00o\00r\00p\00o\00r\00a\00t\00i\00o\00n\00.\00 \00
\00;\00;\00 \00A\00l\00l\00 \00R\00i\00g\00h\00t\00s\00 \00R\00e\00s\00e\00r\00v\00e\00d\00.\00 \00
\00;\00;\00 \00
\00;\00;\00 \00T\00h\00i\00s\00 \00i\00s\00 \00U\00N\00P\00U\00B\00L\00I\00S\00H\00E\00D\00 \00P\00R\00O\00P\00R\00I\00E\00T\00A\00R\00Y\00 \00S\00O\00U\00R\00C\00E\00 \00C\00O\00D\00E\00 \00o\00f\00 \00B\00r\00o\00a\00d\00c\00o\00m\00 \00C\00o\00r\00p\00o\00r\00a\00t\00i\00o\00n\00;\00 \00
\00;\00;\00 \00t\00h\00e\00 \00c\00o\00n\00t\00e\00n\00t\00s\00 \00o\00f\00 \00t\00h\00i\00s\00 \00f\00i\00l\00e\00 \00m\00a\00y\00 \00n\00o\00t\00 \00b\00e\00 \00d\00i\00s\00c\00l\00o\00s\00e\00d\00 \00t\00o\00 \00t\00h\00i\00r\00d\00 \00p\00a\00r\00t\00i\00e\00s\00,\00 \00c\00o\00p\00i\00e\00d\00 \00o\00r\00 \00
\00;\00;\00 \00d\00u\00p\00l\00i\00c\00a\00t\00e\00d\00 \00i\00n\00 \00a\00n\00y\00 \00f\00o\00r\00m\00,\00 \00i\00n\00 \00w\00h\00o\00l\00e\00 \00o\00r\00 \00i\00n\00 \00p\00a\00r\00t\00,\00 \00w\00i\00t\00h\00o\00u\00t\00 \00t\00h\00e\00 \00p\00r\00i\00o\00r\00 \00w\00r\00i\00t\00t\00e\00n\00 \00
\00;\00;\00 \00p\00e\00r\00m\00i\00s\00s\00i\00o\00n\00 \00o\00f\00 \00B\00r\00o\00a\00d\00c\00o\00m\00 \00C\00o\00r\00p\00o\00r\00a\00t\00i\00o\00n\00.\00 \00
\00;\00;\00 \00
\00 \00
\00[\00v\00e\00r\00s\00i\00o\00n\00]\00 \00
\00    \00S\00i\00g\00n\00a\00t\00u\00r\00e\00    \00=\00 \00"\00$\00W\00i\00n\00d\00o\00w\00s\00 \00N\00T\00$\00"\00    \00    \00;\00 \00C\00o\00m\00b\00i\00n\00e\00d\00 \00W\00i\00n\00X\00P\00/\00V\00i\00s\00t\00a\00 \00i\00n\00f\00 \00
\00    \00C\00l\00a\00s\00s\00 \00 \00 \00 \00 \00 \00 \00 \00 \00 \00 \00=\00 \00N\00e\00t\00 \00
\00    \00C\00l\00a\00s\00s\00G\00U\00I\00D\00    \00=\00 \00{\004\00d\003\006\00e\009\007\002\00-\00e\003\002\005\00-\001\001\00c\00e\00-\00b\00f\00c\001\00-\000\008\000\000\002\00b\00e\001\000\003\001\008\00}\00 \00
\00    \00P\00r\00o\00v\00i\00d\00e\00r\00    \00=\00 \00%\00V\00_\00B\00C\00M\00%\00 \00
\00    \00C\00o\00m\00p\00a\00t\00i\00b\00l\00e\00    \00=\00 \001\00 \00
\00D\00r\00i\00v\00e\00r\00V\00e\00r\00=\001\001\00/\000\005\00/\002\000\000\009\00,\00 \005\00.\006\000\00.\001\008\000\00.\001\001\00 \00
\00    \00C\00a\00t\00a\00l\00o\00g\00F\00i\00l\00e\00    \00=\00 \00b\00c\00m\00h\004\003\00x\00x\00.\00c\00a\00t\00 \00
```

---

### Post by chili555 on 2012-04-09
I was afraid of that. I'm sorry, I'm a bit lost since the thread is so long and has several different customers at the window. Scott, please confirm for me your actual device:```
lsusb
```32- or 64-bit?```
arch
```Where did you get the bcmwlhigh5.inf and .sys you installed? From me as an attachment? As you have seen by now, there are several floating around and not all work in all circumstances. Once we know your particulars, I'll see if I have a better file for you.

---------

Note to searchers: Let me repeat and please note well: there are several bcmwlhigh5.inf files floating around and ***not all work in all circumstances. *** We must actually read the .inf file (vim does it) and it must be for Windows XP, mention your usb.id exactly and match your architecture; 32- or 64-bit.

---

### Post by scottrasmussen on 2012-04-09
chili,

```
massolit@skat:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100(v2) 802.11n [Broadcom BCM4323]
Bus 005 Device 002: ID 046d:c52e Logitech, Inc. 
massolit@skat:~$ 
``````
massolit@skat:~$ arch
i686

```yeah i downloaded the driver from one of the earlier posts.  thought it would work.  

thx!

---

### Post by chili555 on 2012-04-09
This is my best shot. Download the attachment to your desktop. Right-click it and select *extract here*. Remove your old file:```
sudo modprobe -r ndiswrapper
sudo ndiswrapper -e bcmwlhigh5
sudo rm -rf /etc/ndiswrapper/*
```Now install the new one:```
sudo ndiswrapper -i Desktop/WinXP2000/bcmwlhigh5.inf
```See if the driver and the device are recognized:```
ndiswrapper -l
```It ought to mention your usb.id: 0846:9011. Load the module:```
sudo modprobe ndiswrapper
```Any improvement? If not, please post:```
dmesg | grep ndis
```Fingers crossed.

---

### Post by scottrasmussen on 2012-04-09
chili.....

you are awesome!!!

works!!!

[CODE][/massolit@skat:~$ dmesg | grep ndis
[   10.438443] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   10.542152] usbcore: registered new interface driver ndiswrapper
[20119.624261] usbcore: deregistering interface driver ndiswrapper
[20249.205081] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[20249.479603] ndiswrapper: driver bcmwlhigh5 (Netgear,05/05/2009, 5.10.79.30) loaded
[20250.030216] usbcore: registered new interface driver ndiswrapper
CODE]

posted this using my new wireless connection!

---

### Post by chili555 on 2012-04-09
Awesome indeed. You have helped some searchers and helped our understanding of the mysterious bcmwlhigh5 series. Have fun!

---

### Post by Ale3mend0 on 2012-04-10
Hi,i'm here another time :D i install ubuntu 12.04 64 bit and i download the archive that u provide me for 64 bit but there aren't any bcmh43xx64.inf inside :l

---

### Post by chili555 on 2012-04-10
Please try this.

---

### Post by Ale3mend0 on 2012-04-11
ok i'll try in 20 min w8 me ;)

EDIT: i try the 64 bit, when i install show this 
```
root@Pc:/home/noname/Scrivania/Driver/Broadcom_bcm43xx_USB_32_64bit_v2# ndiswrapper -i bcmn43xx64.inf
couldn't find SourceDisksFiles section - continuing anyway...
installing bcmn43xx64 ...
couldn't find install section "BCM43XXN32" -
installation may be incomplete
root@Pc:/home/noname/Scrivania/Driver/Broadcom_bcm43xx_USB_32_64bit_v2# 

```then if i do modprobe ndiswrapper with the WNA3100 plug in appear a fullscreen black screen with some white text and i can only reboot, if i do modprobe ndiswrapper without it plug in all works fine but if i do echo >> /etc/modules and i reboot ndiswrapper -l show this but in the connections i can't see nothing

```
bcmn43xx64 : driver installed
    device (0846:9020) present

```

---

### Post by Ale3mend0 on 2012-04-11
if i reboot i can't see nothing wi-fi network..

---

### Post by chili555 on 2012-04-11
Let's check the message file:```
dmesg | grep ndis
```

---

### Post by Ale3mend0 on 2012-04-11
Nothink happend
```
 root@Pc:/home/noname# dmesg | grep ndis
root@Pc:/home/noname# ndiswrapper -l
bcmn43xx64 : driver installed
    device (0846:9020) present
root@Pc:/home/noname# 


```

---

### Post by chili555 on 2012-04-11
Please try:```
sudo modprobe ndiswrapper
dmesg | grep ndis
iwconfig
```Off to lunch; see you this afternoon.

---

### Post by Ale3mend0 on 2012-04-11
Here the output
```

root@Pc:/home/noname# sudo modprobe ndiswrapper
root@Pc:/home/noname# dmesg | grep ndis
[ 1044.192042] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[ 1044.215060] usbcore: registered new interface driver ndiswrapper
root@Pc:/home/noname# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@Pc:/home/noname# 

```

what can i do now?

---

### Post by chili555 on 2012-04-12
Please try this instead after you remove the old files. Delete the folder on your desktop or Scrivania. Then do:```
sudo modprobe -r ndiswrapper
sudo ndiswrapper -e bcmn43xx64
sudo rm -rf /etc/ndiswrapper/*
```Now install these files as you've done before.

This is highly experimental. The system is looking for a 32-bit piece:> couldn't find install section "BCM43XXN[COLOR="Red"]32[/COLOR]" -
installation may be incompleteHowever, this is supposed to be a 64-bit file. I've changed the line (that doesn't refer to your device anyway) and let's see if it works.

We might as well try it, we have very little else to try, frankly. I am sorry it took me so long to reply, this is a very tough problem.

---

### Post by jpmayhew on 2012-04-19
Hi, 

I've been following this thread and have now got my new N300 to detect my wireless (using bcmn43xx32 in ndisgtk) - thanks for all the great help. But the funny thing is that although it can see and detect the network, it cannot connect to it. It asks for my password, and even when I enter this it  just pops up again and again asking for authentication. I tried disabling all encryption and it still wouldn't connect, so it isn't a case me getting the password wrong. 

Does anyone have any idea what why it might not be able to connect, despite being able to detect the network?

Many thanks in advance.

---

### Post by namedan on 2012-04-29
> **chili555 said:**
> Try these files instead. Follow the instructions in post #29 above but, using the files I've attached, install bcmn43x**x64**.inf.

I'm off to shop with Mrs. Chili; I'll check in later. Good luck.
Chilli, your the best, I was having similar troubles to ale3mend0, followed a number of the posts and now I don't have to annoy/trip up my house mates with my super long ethernet cable. Thanks for all the hard work.

---

### Post by MyrllynEmrys on 2012-05-06
To Mr Chili. I'm running Ubuntu 12.04/32 bit on a dual booting gateway netbook. By following your instructions in Post number 29, and then following up with post 41, I was able to get my Netgear wna3100 running perfectly. Thank you so much! Btw, I just started using linux like 3 days ago. :-]

---

### Post by 477145 on 2012-05-14
hi i'm having similar problems with my wlan but i can't get ndiswrapper to work.

ndiswrapper -l tells me that a driver is installed and some device is present but modprobe ndiswrapper doesn't do anything; the message reads: "FATAL: module ndiswrapper not found. can somebody please tell me what i'm doing wrong?

i'm using ubuntu 12.04 and a netgear wireless usb n300 adapter.

---

### Post by chili555 on 2012-05-14
You might try:```
sudo apt-get install --reinstall ndiswrapper-common ndiwrapper-utils-1.9
```Then proceed as before.

---

### Post by bdukes11 on 2012-08-25
Looking for some help from the experts (chili) I am brand new to Linux, using Linux Mint 13 with the Cinnamon Desktop and enjoying my Linux experience thus far, but I am having issues with this device as well read through the blog, but thought i would start here with the list command

hasina@hasina-HP-Z400-Workstation ~ $ ndiswrapper -l
bcmwlhigh5 : invalid driver!

---

### Post by dkim53 on 2012-08-26
Hi All,
I'm a newbie and have the same exact  Wireless USB N300 Netgear to install. I'm currently running off the internet  with a Linksys Wireless  G PCI Adapter and want to get the Netgear to work. Will someone walk me through it?

chili555 can you help?

---

### Post by chili555 on 2012-08-26
> **bdukes11 said:**
> Looking for some help from the experts (chili) I am brand new to Linux, using Linux Mint 13 with the Cinnamon Desktop and enjoying my Linux experience thus far, but I am having issues with this device as well read through the blog, but thought i would start here with the list command

hasina@hasina-HP-Z400-Workstation ~ $ ndiswrapper -l
bcmwlhigh5 : invalid driver!Where did the driver come from? Please post:```
lsusb
```Thanks.

---

### Post by bdukes11 on 2012-08-29
Sorry for the late reply. Nearly 50, and I have never been more than an end user, Mac OS at home, Windows at work. I love them, but Mac has just gotten too expensive and not big on Windows so Linux is entirely new to me. Took home two old machines with "wiped" hard drives and installed Linux Mint 64 bit on one and 32 bit on the other.  I spent nearly 3 hours on the 64 bit machine zeroing in on posts 29 and 41 of this thread. No luck, so I gave up and we through the Cat 5 across the floor to the next room where the router is.  
I moved on to the older machine with 32 bit OS. (BTW the terminal can be dangerous for someone who does not know exactly what they are doing :)) I left myself with a quite a mess after playing with terminal commands, but must admit it was a beneficial Linux learning experience. After several hours I am back to square one on this machine as well.

  	 	 	 	 	 	   shae@brian-HP-xw6400-Workstation ~ $ lsusb  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse  
 Bus 004 Device 003: ID 049f:0051 Compaq Computer Corp. KU-0133 Easy Access Interner Keyboard  
 Bus 001 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]  
 shae@brian-HP-xw6400-Workstation ~ $ ndiswrapper -l  
 arusb_xp : driver installed  
 bcmwlhigh5 : driver installed  
 shae@brian-HP-xw6400-Workstation ~ $  
  
Still no luck. When Wireless Network Drivers is opened, bcmwlhigh5 is shown but states "Device Not Detected"

My daughter who's machine this will be wants to install Windows, but I'm not ready to give up just yet. Running a cable to this machine is not an option. 

I am even  willing to buy another wireless adapter that works out of the box.

---

### Post by chili555 on 2012-08-30
> [COLOR="Red"]0846:9020[/COLOR] NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231] For your 32-bit machine, you need a 32-bit Windows XP .inf and .sys file that specifically mention your device vendor and product ids; in this case, 0846:9020. Failing that, ndiswrapper will assert it has properly installed a driver but doesn't see a corresponding device:> When Wireless Network Drivers is opened, bcmwlhigh5 is shown but states "Device Not Detected"Let's start by erasing the incorrect drivers:```
sudo ndiswrapper -e bcmwlhigh5
```I don't quite know what the other driver arusb_xp is for. If was another attempt to get your Netgear going, erase it, too.```
sudo ndiswrapper -e arusb_xp
```I have been studying the intricacies of bcmwlhigh5 for so long that I have about every version made. Please try the file I'v attached. Download it to your desktop and right-click it and select Extract Here. Then open the terminal and do:```
sudo ndiswrapper -i Desktop/wna3100-drivers/bcmwlhigh5.inf
sudo ndiswrapper -l
```Now does it report the driver is installed *AND* the device is present? If so, please do:```
sudo modprobe ndiswrapper
iwconfig
```Do you have a wireless interface? Can you connect?

---

### Post by bdukes11 on 2012-08-30
Still not working, but this is the closest I've been,

The wireless network drivers bcmwlhigh5, hardware present: yes
click on Configure network, click on wireless tab, click add,
nothing is available, everything is greyed out except for cancel on all tabs. The Linux Mint laptop I am using to type this is right next to the desktop and indicates good signal from my wireless.
 
shae@brian-HP-xw6400-Workstation ~ $ sudo ndiswrapper -e bcmwlhigh5 
[sudo] password for shae: 
shae@brian-HP-xw6400-Workstation ~ $ sudo ndiswrapper -e arusb_xp 
shae@brian-HP-xw6400-Workstation ~ $ sudo ndiswrapper -i Desktop/wna3100-drivers/bcmwlhigh5.inf 
installing bcmwlhigh5 ... 
shae@brian-HP-xw6400-Workstation ~ $ sudo ndiswrapper -l 
bcmwlhigh5 : driver installed 
	device (0846:9020) present 
shae@brian-HP-xw6400-Workstation ~ $ sudo modprobe ndiswrapper 
shae@brian-HP-xw6400-Workstation ~ $ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

shae@brian-HP-xw6400-Workstation ~ $

---

### Post by chili555 on 2012-08-30
Any interesting clues here?```
sudo modprobe ndiswrapper
dmesg | grep ndis
```Thanks.

---

### Post by bdukes11 on 2012-08-30
Sorry for the delay I wasn't allowed to walk past the grandchildrens room until they were asleep :)

shae@brian-HP-xw6400-Workstation ~ $ sudo modprobe ndiswrapper 
[sudo] password for shae: 
shae@brian-HP-xw6400-Workstation ~ $ dmesg | grep ndis 
[   11.150187] ndiswrapper version 1.57 loaded (smp=yes, preempt=no) 
[   12.335285] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded 
[   12.634521] usbcore: registered new interface driver ndiswrapper 
shae@brian-HP-xw6400-Workstation ~ $

Now I have to do some homework to try and figure out what you just had me do!

---

### Post by chili555 on 2012-08-30
Looks perfect so far! Now how about:```
iwconfig 
sudo iwlist wlan0 scan
```

---

### Post by dkim53 on 2012-08-30
Chilli, Bdukes. I was able to get mine running. I'm running Ubuntu 12.04 LTS. 
1. Went to Ubuntu Software Center.
2. Type ndiswrapper in the search box and click enter.
3. Click on windows wireless drivers (ndiswrapper)
4. This I had installed but not any add ons.
5. Click the add on for ndiswrapper-dkms.
6 Apply.
This woke up the usb n300 netgear.
Then I did the sudo modprobe stuff in the tewrminal and entered the connection info.
Maybe this will help, but not familiar with Mint.
Good luck.

---

### Post by bdukes11 on 2012-09-01
Thanks chili, you just taught me a new useful terminal command.
10 networks were detected but I have chosen to list my network only.

shae@brian-HP-xw6400-Workstation ~ $ iwconfig 
lo        no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

eth0      no wireless extensions. 
shae@brian-HP-xw6400-Workstation ~ $ sudo iwlist wlan0 scan 
[sudo] password for shae: 
wlan0     Scan completed : 
          Cell 01 - Address: 90:84:0D:D7:13:EF 
                    ESSID:"Dukesnet" 
                    Protocol:IEEE 802.11g 
                    Mode:Master 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
                    IE: Unknown: 000844756B65736E6574 
                    IE: Unknown: 010882848B960C121824 
                    IE: Unknown: 03010B 
                    IE: Unknown: 0706555320010B1E 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 32043048606C 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 2D1AAC4117FFFFFF0000000000000000000000000000000000000000 
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00 
                    IE: Unknown: DD0700039301720320 
                    IE: Unknown: DD070017F203020180 
                    IE: Unknown: DD0E0017F2070001010690840DD713EF 
          Cell 02 - Address: 96:84:0D:D7:13:EF 
                    ESSID:"Dukesnet Guest" 
                    Protocol:IEEE 802.11g 
                    Mode:Master 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality:58/100  Signal level:-59 dBm  Noise level:-96 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
                    IE: Unknown: 000E44756B65736E6574204775657374 
                    IE: Unknown: 010882848B960C121824 
                    IE: Unknown: 03010B 
                    IE: Unknown: 0706555320010B1E 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 32043048606C 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 2D1AAC4117FFFFFF0000000000000000000000000000000000000000 
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00 
                    IE: Unknown: DD0700039301720208 
                    IE: Unknown: DD070017F203020180 
                    IE: Unknown: DD0E0017F2070001010690840DD713EF 
          Cell 03 - 
          Cell 04 -
          Cell 05 - 
          Cell 06 - 
          Cell 07 - 
          Cell 09 - 
          Cell 10 - 
           
shae@brian-HP-xw6400-Workstation ~ $

---

### Post by bdukes11 on 2012-09-01
> **dkim53 said:**
> Chilli, Bdukes. I was able to get mine running. I'm running Ubuntu 12.04 LTS. 
1. Went to Ubuntu Software Center.
2. Type ndiswrapper in the search box and click enter.
3. Click on windows wireless drivers (ndiswrapper)
4. This I had installed but not any add ons.
5. Click the add on for ndiswrapper-dkms.
6 Apply.
This woke up the usb n300 netgear.
Then I did the sudo modprobe stuff in the tewrminal and entered the connection info.
Maybe this will help, but not familiar with Mint.
Good luck.

I am new to Linux, but from what I understand Mint is an Ubuntu derivative.

I go to the Mint Software Manager and search ndiswrapper and it lists and also indicates as already installed
mintwifi, ndisgtk, ndiswrapper-common, ndiswrapper-dkms, ndiswrapper-source, ndiswrapper-utils-1.9

---

### Post by chili555 on 2012-09-02
> **bdukes11 said:**
> Thanks chili, you just taught me a new useful terminal command.
10 networks were detected but I have chosen to list my network only.

shae@brian-HP-xw6400-Workstation ~ $ iwconfig 
lo        no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

<snip>In both of the networks listed, the encryption is set to mixed mode WPA *AND* WPA2 mode. You may have better luck if you can reset the router to WPA2 only.

---

### Post by adamboy on 2013-01-04
> **chili555 said:**
> It involves downloading ndiswrapper source code here: [http://sourceforge.net/projects/ndiswrapper/files/stable/](http://sourceforge.net/projects/ndiswrapper/files/stable/)

I'd suggest you download 1.56. It may be fixed! Notice your version is currently 1.55:You'd then need to have build-essential and linux-headers:```
sudo apt-get install build-essential linux-headers-generic
```Download 1.56 to your desktop. Right-click it and select *Extract Here*. Open a terminal and do:```
sudo su
apt-get remove --purge ndiswrapper*
cd Desktop/ndiswrapper-1.56
make
make install
ndiswrapper -i /path/to/bcmwlhigh5.inf
modprobe -rv ndiswrapper
modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndis
exit
```I tried to compile this older version but was unsuccessful in 11.10. I'll be interested in your report.

If we still get the ntoskrnl.exe error, we'll change the file and re-compile.

PS - 1.57 makes perfectly for me in 11.10.

Holy cow! Thank you so much!! I just followed these instructions, using ndiswrapper 1.58, and it worked perfectly!!! Thank you so much!!!!!!:guitar:

---

### Post by BeckFree79 on 2013-02-01
Ok, Chili555... 
I'm a total Ubuntu noob, but fairly intelligent, but I think that I must have missed it... Which # in this thread tells me what it should look like when fixed?  I think that your instructions fixed it, but how do I know for sure?  And how do I connect to the wifi?  The modem is my landlord's (free wifi incl in rent).
Thanks for your help.  You are literally a God-send!!!  :O)

---

### Post by chili555 on 2013-02-02
If it's fixed, you should get a wireless interface, ideally wlan0 here:```
iwconfig
```To connect, click the Network Manager icon, see your network and connect. Please see attached. In this example, I clicked 'GBR1' and was asked for the WPA password. I filled it in and connected.

Post back if you need more assistance.

The forum is actually a God-send to me! I love learning new things and then sharing with you all.

---

### Post by heikkios on 2013-02-18
manaattimasiina heikki # cd Desktop/wna3100-drivers
bash: cd: Desktop/wna3100-drivers: No such file or directory
manaattimasiina heikki # sudo su
manaattimasiina heikki # ndiswrapper -i bcmwlhigh5.inf
couldn't open bcmwlhigh5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
manaattimasiina heikki # modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
manaattimasiina heikki # echo ndiswrapper >> /etc/modules
manaattimasiina heikki # exit

i try to follow you advice, but i get only this message. whats wrong. please somebody wil help.

---

### Post by chili555 on 2013-02-18
Let's try to solve this one step at a time.> manaattimasiina heikki # cd Desktop/wna3100-drivers
bash: cd: Desktop/wna3100-drivers: No such file or directoryWhere did you download the driver files? To your desktop? You are running as super-user, similar to root; please see the little # in your command prompt. Please try navigating to your own desktop, not root:> cd ~/DesktopNow list the contents of the desktop:```
ls
```Now do you see the wna3100-drivers file? Now you are ready to install the driver, except that ndiswrapper is not installed correctly:> manaattimasiina heikki # modprobe ndiswrapper
FATAL: Module ndiswrapper not found.How did you install ndiswrapper? From the Ubuntu repositories with apt-get? Were there any errors as you did so? We need to fix it first before we can proceed.

---

### Post by heikkios on 2013-02-18
i dont have a even clue how can i navigate my own desktop. please.

---

### Post by chili555 on 2013-02-18
> **heikkios said:**
> i dont have a even clue how can i navigate my own desktop. please.Please try this instead of above; first, drop out of super-user:```
exit
```Next, navigate to your user directory:```
cd
```Now change directories to your desktop. Warning, 'Desktop' will be something different in your language. Is it Finnish? Then it will be something like:```
cd pöytä-
```Now list the contents of the directory:```
ls
```Now do you see the wna3100-drivers folder?

---

### Post by Marcd225 on 2013-02-24
Hi chili i have also just DL Ubuntu.  Also did a lot of updates.  I did get your file for this driver and it is currently showing in my windows wireless drivers, but, where it says hardware present I am getting a "no"

When i do my lsusb i can clearly see my device there.  I know I did your steps a couple of times but then again it was later last night.  still learning some things but think i can get around the terminal ok.  let me know what you need to see and i will get it to you.   


thanks in advance.

---

### Post by chili555 on 2013-02-24
Let's have a look:```
ndiswrapper -l
lsusb
```Thanks.

---

### Post by Marcd225 on 2013-02-24
marcus@ubuntu:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
marcus@ubuntu:~$ lsusb
Bus 001 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 002: ID 045e:00dd Microsoft Corp. Comfort Curve Keyboard 2000 V1.0
Bus 003 Device 002: ID 1532:0015 Razer USA, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
marcus@ubuntu:~$

---

### Post by chili555 on 2013-02-24
> bcmwlhigh5 : driver installedFor ndiswrapper to work, the .inf file must match the usb.id of your device:>  ID [COLOR="Red"]0846:9020[/COLOR] NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]It also needs to be appropriate for your architecture; either 32- or 64-bit:```
arch
```So does it? Find the .inf file on your desktop or wherever it was when you installed it and open it with gedit text editor, if you can. Does it have your device listed?> ;-----------------------------------------------------------------
; x64 (AMD64, Intel EM64T) - WinXP
;
[BROADCOM.NTamd64]
        %BCM430ND_DeviceDesc% = BCM43XNMD, USB\VID_0846&PID_9020

;-----------------------------------------------------------------
; x86 - Win9x, Win2K, WinXP
;
[BROADCOM]
        %BCM430ND_DeviceDesc% = BCM43XNMD, USB\VID_[COLOR="Red"]0846[/COLOR]&PID_[COLOR="Red"]9020
[/COLOR]
;-----------------------------------------------------------------
If not, where did you get the files? Did you use Windows XP files? 95, Vista, 7 or 3.1 will not work. Finally, are there any clues here?```
sudo modprobe ndiswrapper
dmesg | grep ndis
```

---

### Post by Marcd225 on 2013-02-24
I got the file for the 64 a couple of post back that you put in there.  here is what i get from the codes you provided which may be a good answer.

```
marcus@ubuntu:~$ arch
x86_64
marcus@ubuntu:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
marcus@ubuntu:~$ dmesg | grep ndis
marcus@ubuntu:~$ 

```

I did not see anything in the .inf that said windows 7.... maybe i missed it.

---

### Post by chili555 on 2013-02-24
> $ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.That can't be good! Let's try the easy way first:```
sudo apt-get remove --purge ndiswrapper-dkms
sudo apt-get install --reinstall ndiswrapper-common
sudo apt-get install --reinstall ndiswrapper-utils-1.9
sudo modprobe ndiswrapper
dmesg | grep ndis
```

---

### Post by Marcd225 on 2013-02-24
still seeing the FATAL after sudo modprobe ndiswrapper

---

### Post by chili555 on 2013-02-24
Alrighty then. Now we try the hard way:```
sudo apt-get install linux-headers-generic build-essential
```Download this file: [http://sourceforge.net/projects/ndiswrapper/files/stable/ndiswrapper-1.58.tar.gz/download](http://sourceforge.net/projects/ndiswrapper/files/stable/ndiswrapper-1.58.tar.gz/download) 

Drag and drop it to your desktop. Right-click it and select 'Extract Here.' Then do:```
cd Desktop/ndiswrapper-1.58
make
sudo make install
modprobe ndiswrapper
dmesg | grep ndis
```

---

### Post by Marcd225 on 2013-02-24
all right this is now what it is showing

```
marcus@ubuntu:~/Desktop/ndiswrapper-1.58$ modprobe ndiswrapper
marcus@ubuntu:~/Desktop/ndiswrapper-1.58$ dmesg | grep ndis
[ 3011.414484] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[ 3011.435211] usbcore: registered new interface driver ndiswrapper
marcus@ubuntu:~/Desktop/ndiswrapper-1.58$ 

```

---

### Post by chili555 on 2013-02-24
> **Marcd225 said:**
> all right this is now what it is showing

```
marcus@ubuntu:~/Desktop/ndiswrapper-1.58$ modprobe ndiswrapper
marcus@ubuntu:~/Desktop/ndiswrapper-1.58$ dmesg | grep ndis
[ 3011.414484] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[ 3011.435211] usbcore: registered new interface driver ndiswrapper
marcus@ubuntu:~/Desktop/ndiswrapper-1.58$ 

```Well, sir or madam, now we're getting somewhere! Now let's check:```
ndiswrapper -l
iwconfig
```

---

### Post by Marcd225 on 2013-02-24
at least we are making some progress


```
marcus@ubuntu:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
marcus@ubuntu:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

marcus@ubuntu:~$ 

```

---

### Post by chili555 on 2013-02-24
From which post did you get the files? Linky??

---

### Post by Marcd225 on 2013-02-24
> **chili555 said:**
> Try these files instead. Follow the instructions in post #29 above but, using the files I've attached, install bcmn43x**x64**.inf.

I'm off to shop with Mrs. Chili; I'll check in later. Good luck.

it was post number 60. maybe i should try the files from post 82?

---

### Post by chili555 on 2013-02-24
> ;-----------------------------------------------------------------
; x64 (AMD64, Intel EM64T) - WinXP
;
[BROADCOM.NTamd64]
        %BCM430ND_DeviceDesc% = BCM43XNMD, USB\VID_0846&PID_[COLOR="Red"]9011
[/COLOR]
;-----------------------------------------------------------------
; x86 - Win9x, Win2K, WinXP
;
[BROADCOM]
        %BCM430ND_DeviceDesc% = BCM43XNMD, USB\VID_0846&PID_9011

;-----------------------------------------------------------------
That's from post #60. As I suspected, not correct for your 9020 device. Checking #82...

EDIT: Yes, please. Do:```
sudo ndiswrapper -e bcmwlhigh5
sudo rm -rf /etc/ndiswrapper/*
sudo ndiswrapper -i Desktop/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
iwconfig
```

---

### Post by Marcd225 on 2013-02-24
like the people in the post before... you are awesome.  Thank you so much for your help.  I can't wait to learn more about Ubuntu.  I hope there are others that can be just as helpful within the community, as I am sure they are out there.:KS

---

### Post by chili555 on 2013-02-24
> **Marcd225 said:**
> like the people in the post before... you are awesome.  Thank you so much for your help.  I can't wait to learn more about Ubuntu.  I hope there are others that can be just as helpful within the community, as I am sure they are out there.:KSThere are many that are just as or more helpful. I was happy to help. Have fun!

---

### Post by wscrivens1 on 2013-03-07
Hi, everyone!
I have read the thread fairly thoroughly and have followed the installation instructions therein.  I've tried installing ndiswrapper 1.55 from the package, and also installing 1.58 from source.  I'm using the wna3100-drivers.zip package downloaded from here.

I'm running a 32-bit version of Ubuntu 10.04, and can't upgrade this particular box since its reason for existence is to run some software to drive a milling machine, which won't run on later versions.

Despite all my attempts, the interface is just not recognized by linux (does not show up in iwconfig).

Here are the diagnostic messages I've gotten most recently:
```
root@Linux-CNC:/home/walts/wna3100-drivers# lsusb
Bus 002 Device 004: ID 08e6:0432 Gemplus GemPC432 SmartCard Reader
Bus 002 Device 003: ID 049f:000e Compaq Computer Corp. Internet Keyboard
Bus 002 Device 002: ID 0451:2036 Texas Instruments, Inc. TUSB2036 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0781:5576 SanDisk Corp. 
Bus 001 Device 002: ID 0846:9020 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@Linux-CNC:/home/walts/wna3100-drivers# ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/emc2, it will be ignored in a future release.
bcmwlhigh5 : driver installed
    device (0846:9020) present
root@Linux-CNC:/home/walts/wna3100-drivers# dmesg | grep ndis
[ 1524.863239] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 1525.114988] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[ 1525.115108] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh5'
[ 1525.115418] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'
[ 1525.115976] usbcore: registered new interface driver ndiswrapper
root@Linux-CNC:/home/walts/wna3100-drivers# ^C

```

As I read this, the physical device is present, ndiswrapper has bcmwlhigh5 and sees the device - but the kernel can't load the driver because of teh unknown symbol.
I have tried googling for 'IoUnregisterPlugPlayNotification' but could not find any help.

I have a lot more experience with Windows than with linux and I may not be interpreting the messages correctly, but regardless, I need some help here, please.


Walt

P.S. the interface works, on this box, when booted with Windows.

---

### Post by chili555 on 2013-03-07
My admiration and respect for a well-researched and well-written post. It's a refreshing departure from the all too common, "what's up my wireless wotn werk whadda I do??"

As you correctly surmise, this is the problem:> (import:242): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'However, when you searched:> I have tried googling for 'IoUnregisterPlugPlayNotification' but could not find any help....you would have had a better result searching for 'unknown symbol: ntoskrnl.exe' and I am fairly sure the answer is that ndiswrapper 1.55 is incompatible with some later kernels. I am surprised it is incompatible with 10.04.

You said you compiled 1.58 and yet 1.55 loads:> ndiswrapper version 1.55 loaded (smp=yes, preempt=no)What was the outcome of your compile? Errors, warnings, smoke, sparks??? That's the first thing I'd try, compiling and installing 1.58.

EDIT: If 1.58 errors out, please see here and try 1.57: [http://sourceforge.net/projects/ndiswrapper/files/stable/](http://sourceforge.net/projects/ndiswrapper/files/stable/)

As for this little gem:> ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh5'I think it goes hand in hand with ntoskrnl.exe and I suspect it will resolve with a newer, better ndiswrapper.

I am anxious to help you; as an old friend once told me, with a milling machine, you can make horsepower *and* money!

---

### Post by wscrivens1 on 2013-03-08
Thanks, Chili!

Thank you for your kind words.  I've been around Internet forums long enough to know that you need to provide all possible information so folks can understand your problem :)

I don't know why ndiswrapper was reporting version 1.55 - the last thing I had done was to compile 1.58!

I think part of the problem was too much cruft left over from previous attempts.  I did use modprobe to remove the module and apt-get to remove ndiswrapper* but it missed one file, /kernel/ubuntu/ndiswrapper/ndiswrapper.ko which I removed by hand.  Then I recompiled 1.58 and installed bcmwlhigh5.inf - but it told me it was already installed, so I must have missed  something more!

Anyway, I modprobe'd ndiswrapper, and this time it worked.

Then, summoning all of my courage, I did a software update with Update Manager.  I was down this road before - I had gotten the Netgear adapter working, ran an update, and it quit.  This time, though, it seems to have survived.

The one remaining curiosity is to understand the method of COMPLETELY removing something like ndiswrapper.  

Thanks for your help!

Walt

---

### Post by chili555 on 2013-03-08
> The one remaining curiosity is to understand the method of COMPLETELY removing something like ndiswrapper. It should remove completely with:```
sudo modprobe -r ndiswrapper
sudo apt-get remove [COLOR="#FF0000"]--purge[/COLOR] ndiswrapper*
```A note on updates. You have compiled 1.58 against your current kernel only. When Update Manager installs a newer kernel version, known in Ubuntu World as linux-image, you will need to compile 1.58 against the newer kernel after you reboot into it:```
cd ndiswrapper-1.58
make clean
make
sudo make install
sudo modprobe ndiswrapper
```The bcmwlhigh5 is already installed permanently so your wireless should fire right up. Please retain your 1.58 files and these instructions for that day.

Glad it's working! Have fun!

---

### Post by wscrivens on 2013-03-09
Thanks for all your help.  The networking is working OK now!

Walt

---

### Post by jimbo.slice on 2013-03-25
Hi Chilli, I've gone through all these pages but I am still having problems getting my wireless to work. Currently I'm reading of my broken laptop, unplugging the VGA cable to go back to the desktop im trying to set up. I'm so frustrated -.-'

jimbo@Demian ~ $ lsusb
Bus 002 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]

jimbo@Demian ~ $ ndiswrapper -l
bcmwlhigh5 : driver installed

When I type dmesg | grep ndis ... I get nothing, just back to a clean command line...?

I'm sorry, im quite new to Terminal, and linux in general. I played around a bit with the command options but I'm just not sure exactly what I'm supposed to be looking for. I am under the impression I have the archive wna3100-drivers.zip installed(the correct version for my 32bit system, i think), but I have installed like 4 other drivers previous to this that may be conflicting? If you could help me that would be so great. I'm trying to do my university work on a broken netbook its just too difficult I need to get my desktop figured out.

---

### Post by jimbo.slice on 2013-03-25
woohoo just got it. My first major terminal success with mint.

for anyone with a similar problem, I got it from another thread chili commented on. [here]("http://ubuntuforums.org/showthread.php?t=1923143").

Edit. lol. 3rd times a charm? whenever I restart the computer the wireless stops working. This is how i get it working again.

jimbo@Demian ~ $ sudo modprobe ndiswrapper
jimbo@Demian ~ $ ndiswrapper -l
bcmwlhigh5 : driver installed
    device (0846:9020) present
jimbo@Demian ~ $ dmesg | grep ndis
[  143.153597] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[  143.454206] ndiswrapper: driver bcmwlhigh5 (Netgear,05/05/2009, 5.10.79.30) loaded
[  143.713136] usbcore: registered new interface driver ndiswrapper
jimbo@Demian ~ $ 

The wireless switches on when I ask for the kernal message. Any ideas on how to have it configured correctly for when I boot the computer up?

---

### Post by chili555 on 2013-03-25
> **jimbo.slice said:**
> 
Any ideas on how to have it configured correctly for when I boot the computer up?Please try this:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```

---

### Post by crazy_23_1999_04290 on 2013-03-25
So major problems here NEED HELP. I was running windows 8 i hated it so i desided to switch over to ubuntu as I had it in the past version 10 i think. But i just downloaded 12.10 and I bought myself a NETGEAR N300 usb adapter. Nothing i really came across looks like it works out of the box but this was really only easy post i could find. After playing around for several hours im still not connected to the internet and kinda getting pissed. Also i have no sound coming out of my HDMI output 

specs on my computer AMD A8-5500 APU with Radeon(tm) HD Graphics × 4  Realtek ALC892 


PLEASE HELP ASAP!!!!

---

### Post by chili555 on 2013-03-25
> **crazy_23_1999_04290 said:**
> So major problems here NEED HELP. I was running windows 8 i hated it so i desided to switch over to ubuntu as I had it in the past version 10 i think. But i just downloaded 12.10 and I bought myself a NETGEAR N300 usb adapter. Nothing i really came across looks like it works out of the box but this was really only easy post i could find. After playing around for several hours im still not connected to the internet and kinda getting pissed. Also i have no sound coming out of my HDMI output 

specs on my computer AMD A8-5500 APU with Radeon(tm) HD Graphics × 4  Realtek ALC892 


PLEASE HELP ASAP!!!!May we see the usual suspects? Open a terminal and run and post:```
ndiswrapper -l
sudo modprobe ndiswrapper
dmesg | grep ndis
```

---

### Post by crazy_23_1999_04290 on 2013-03-25
FATAL: Module ndiswrapper not found.

---

### Post by crazy_23_1999_04290 on 2013-03-25
danny@danny-CM1745:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

---

### Post by chili555 on 2013-03-25
> **crazy_23_1999_04290 said:**
> FATAL: Module ndiswrapper not found.Not too surprising...Which Ubuntu version did you install?```
lsb_release -d
```If it is 12.10, you will probably need to compile ndiswrapper from scratch. Fun!

--------

Reference to chili:  Post #132 above.

---

### Post by crazy_23_1999_04290 on 2013-03-25
chilli 

12.10 but if its to much trouble i can back track to 12.04?

---

### Post by chili555 on 2013-03-25
Nothing is too much trouble for me; my wireless works!

Please get a temporary ethernet connection and do:```
sudo apt-get install linux-headers-generic build-essential

```Go here and download the 1.58 tar.gz and drag and drop it to your desktop so we can find it. Right-click it and select 'Extract Here.' Now back to the terminal:```
cd Desktop/ndiswrapper-1.58
sudo su
make
make install
modprobe ndiswrapper
exit
```Any improvement?

[http://sourceforge.net/projects/ndiswrapper/files/stable/](http://sourceforge.net/projects/ndiswrapper/files/stable/)

---

### Post by crazy_23_1999_04290 on 2013-03-25
danny@danny-CM1745:~$ cd ndiswrapper-1.58
bash: cd: ndiswrapper-1.58: No such file or directory
danny@danny-CM1745:~$ sudo su
root@danny-CM1745:/home/danny# make
make: *** No targets specified and no makefile found.  Stop.
root@danny-CM1745:/home/danny# make install
make: *** No rule to make target `install'.  Stop.
root@danny-CM1745:/home/danny# modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
root@danny-CM1745:/home/danny# exit

---

### Post by chili555 on 2013-03-25
> danny@danny-CM1745:~$ cd ndiswrapper-1.58
bash: cd: ndiswrapper-1.58: No such file or directoryOops! That's my mistake; sorry. Please try:```
cd [COLOR="#FF0000"]Desktop/[/COLOR]ndiswrapper-1.58
sudo su
make
make install
modprobe ndiswrapper
exit
```"Put it on the desktop so we can find it, old Chili."

---

### Post by crazy_23_1999_04290 on 2013-03-25
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 302 not upgraded.
danny@danny-CM1745:~$ cd ndiswrapper-1.58
bash: cd: ndiswrapper-1.58: No such file or directory
danny@danny-CM1745:~$ cd Desktop/ndiswrapper-1.58
danny@danny-CM1745:~/Desktop/ndiswrapper-1.58$ sudo su
root@danny-CM1745:/home/danny/Desktop/ndiswrapper-1.58# make
make -C utils
make[1]: Entering directory `/home/danny/Desktop/ndiswrapper-1.58/utils'
gcc -g -Wall -I../driver  -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/danny/Desktop/ndiswrapper-1.58/utils'
make -C driver
make[1]: Entering directory `/home/danny/Desktop/ndiswrapper-1.58/driver'
make -C /usr/src/linux-headers-3.5.0-17-generic M=/home/danny/Desktop/ndiswrapper-1.58/driver
make[2]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
  LD      /home/danny/Desktop/ndiswrapper-1.58/driver/built-in.o
  MKEXPORT /home/danny/Desktop/ndiswrapper-1.58/driver/crt_exports.h
  MKEXPORT /home/danny/Desktop/ndiswrapper-1.58/driver/hal_exports.h
  MKEXPORT /home/danny/Desktop/ndiswrapper-1.58/driver/ndis_exports.h
  MKEXPORT /home/danny/Desktop/ndiswrapper-1.58/driver/ntoskernel_exports.h
  MKEXPORT /home/danny/Desktop/ndiswrapper-1.58/driver/ntoskernel_io_exports.h
  MKEXPORT /home/danny/Desktop/ndiswrapper-1.58/driver/rtl_exports.h
  MKEXPORT /home/danny/Desktop/ndiswrapper-1.58/driver/usb_exports.h
  CC [M]  /home/danny/Desktop/ndiswrapper-1.58/driver/crt.o
  CC [M]  /home/danny/Desktop/ndiswrapper-1.58/driver/hal.o
  CC [M]  /home/danny/Desktop/ndiswrapper-1.58/driver/iw_ndis.o
  CC [M]  /home/danny/Desktop/ndiswrapper-1.58/driver/loader.o
  CC [M]  /home/danny/Desktop/ndiswrapper-1.58/driver/ndis.o
  CC [M]  /home/danny/Desktop/ndiswrapper-1.58/driver/ntoskernel.o
  CC [M]  /home/danny/Desktop/ndiswrapper-1.58/driver/ntoskernel_io.o
  CC [M]  /home/danny/Desktop/ndiswrapper-1.58/driver/pe_linker.o
  CC [M]  /home/danny/Desktop/ndiswrapper-1.58/driver/pnp.o
  CC [M]  /home/danny/Desktop/ndiswrapper-1.58/driver/proc.o
  CC [M]  /home/danny/Desktop/ndiswrapper-1.58/driver/rtl.o
  CC [M]  /home/danny/Desktop/ndiswrapper-1.58/driver/wrapmem.o
  CC [M]  /home/danny/Desktop/ndiswrapper-1.58/driver/wrapndis.o
  CC [M]  /home/danny/Desktop/ndiswrapper-1.58/driver/wrapper.o
  CC [M]  /home/danny/Desktop/ndiswrapper-1.58/driver/usb.o
  CC [M]  /home/danny/Desktop/ndiswrapper-1.58/driver/divdi3.o
  LD [M]  /home/danny/Desktop/ndiswrapper-1.58/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/danny/Desktop/ndiswrapper-1.58/driver/ndiswrapper.mod.o
  LD [M]  /home/danny/Desktop/ndiswrapper-1.58/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
make[1]: Leaving directory `/home/danny/Desktop/ndiswrapper-1.58/driver'
root@danny-CM1745:/home/danny/Desktop/ndiswrapper-1.58# make install
make -C driver install
make[1]: Entering directory `/home/danny/Desktop/ndiswrapper-1.58/driver'
mkdir -p -m 755 /lib/modules/3.5.0-17-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/3.5.0-17-generic/misc
/sbin/depmod -a 3.5.0-17-generic
make[1]: Leaving directory `/home/danny/Desktop/ndiswrapper-1.58/driver'
make -C utils install
make[1]: Entering directory `/home/danny/Desktop/ndiswrapper-1.58/utils'
mkdir -p -m 755 /sbin
mkdir -p -m 755 /usr/sbin
install -m 755 loadndisdriver /sbin
install -m 755 ndiswrapper /usr/sbin
install -m 755 ndiswrapper-buginfo /usr/sbin
make[1]: Leaving directory `/home/danny/Desktop/ndiswrapper-1.58/utils'
mkdir -p -m 755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
root@danny-CM1745:/home/danny/Desktop/ndiswrapper-1.58# modprobe ndiswrapper
root@danny-CM1745:/home/danny/Desktop/ndiswrapper-1.58# exit

---

### Post by chili555 on 2013-03-25
> root@danny-CM1745:/home/danny/Desktop/ndiswrapper-1.58# modprobe ndiswrapper
root@danny-CM1745:/home/danny/Desktop/ndiswrapper-1.58# exit So now ndiswrapper loaded cleanly. What does this tell us?```
ndiswrapper -l
dmesg | grep ndis
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by crazy_23_1999_04290 on 2013-03-25
root@danny-CM1745:/home/danny/Desktop/ndiswrapper-1.58# ndiswrapper -l
root@danny-CM1745:/home/danny/Desktop/ndiswrapper-1.58# dmesg | grep ndis
[ 8365.012055] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[ 8365.022528] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2013-03-25
> # ndiswrapper -lIt should have produced some output. Did you install the .inf and .sys files? Do you have the files? Or did you just come here without doing your homework?

EDIT: If yours is a 32-bit system (i686) I suggest you get the files in post #29. If it's 64-bit (x86_64) then try post #60 above. Confirm:```
arch
```

---

### Post by crazy_23_1999_04290 on 2013-03-25
Not sure

---

### Post by chili555 on 2013-03-25
> **crazy_23_1999_04290 said:**
> Not sureLet's check:```
ls /etc/ndiswrapper
```

---

### Post by crazy_23_1999_04290 on 2013-03-25
alright sorry about that finished post 29 as per i686 for a 32 bit system then 

ls /etc/ndiswrapper 

bcmwlhigh5

---

### Post by chili555 on 2013-03-25
> **crazy_23_1999_04290 said:**
> alright sorry about that finished post 29 as per i686 for a 32 bit system then 

ls /etc/ndiswrapper 

bcmwlhigh5So you did, just now,install the .inf file. Is there any change here?```
ndiswrapper -l
iwconfig
```If not, please post:```
lsusb
```

---

### Post by crazy_23_1999_04290 on 2013-03-25
bcmwlhigh5 : driver installed
    device (0846:9020) present
danny@danny-CM1745:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

danny@danny-CM1745:~$ lsusb
Bus 001 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231

---

### Post by jimbo.slice on 2013-03-25
> **chili555 said:**
> Please try this:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```

that did the trick. thank you chilli!!

---

### Post by chili555 on 2013-03-25
> **crazy_23_1999_04290 said:**
> bcmwlhigh5 : driver installed
    device (0846:9020) present
danny@danny-CM1745:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

danny@danny-CM1745:~$ lsusb
Bus 001 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231You seem to have the right driver for the right device. Let's see if there is any error or warning in the message logs:```
dmesg | grep ndis
```

---

### Post by chili555 on 2013-03-25
It worked? Are you all set?

---

### Post by crazy_23_1999_04290 on 2013-03-25
Yes it worked chili but I restarted my computer cause been trying to fix my audio problem. Now I can't seem to get connected again. I read some where in the post someone else had the problem. I looked at lsusb still bus 1. Driver installed device present everything looks good but no connect

---

### Post by chili555 on 2013-03-26
> I read some where in the post someone else had the problem. And did you do what I suggested they do? See posts #137 and 138.

---

### Post by crazy_23_1999_04290 on 2013-04-11
modprobe ndiswrapper terminal doesnt respond
dmesg | grep ndis

] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[80867.065161]  [<f9819531>] load_wrap_device+0x181/0x1d0 [ndiswrapper]
[80867.065184]  [<f98267f4>] wrap_pnp_start_pci_device+0x44/0x70 [ndiswrapper]
[80867.065331]  [<f98196aa>] loader_init+0x8a/0x140 [ndiswrapper]
[80867.065351]  [<f9828007>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[80867.065368]  [<f98450a7>] wrapper_init+0xa7/0x1000 [ndiswrapper]
[80986.690120]  [<f9819531>] load_wrap_device+0x181/0x1d0 [ndiswrapper]
[80986.690142]  [<f98267f4>] wrap_pnp_start_pci_device+0x44/0x70 [ndiswrapper]
[80986.690290]  [<f98196aa>] loader_init+0x8a/0x140 [ndiswrapper]
[80986.690310]  [<f9828007>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[80986.690326]  [<f98450a7>] wrapper_init+0xa7/0x1000 [ndiswrapper]
[81106.315069]  [<f9819531>] load_wrap_device+0x181/0x1d0 [ndiswrapper]
[81106.315092]  [<f98267f4>] wrap_pnp_start_pci_device+0x44/0x70 [ndiswrapper]
[81106.315240]  [<f98196aa>] loader_init+0x8a/0x140 [ndiswrapper]
[81106.315260]  [<f9828007>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[81106.315276]  [<f98450a7>] wrapper_init+0xa7/0x1000 [ndiswrapper]
[81225.940022]  [<f9819531>] load_wrap_device+0x181/0x1d0 [ndiswrapper]
[81225.940046]  [<f98267f4>] wrap_pnp_start_pci_device+0x44/0x70 [ndiswrapper]
[81225.940193]  [<f98196aa>] loader_init+0x8a/0x140 [ndiswrapper]
[81225.940214]  [<f9828007>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[81225.940230]  [<f98450a7>] wrapper_init+0xa7/0x1000 [ndiswrapper]
[81345.564982]  [<f9819531>] load_wrap_device+0x181/0x1d0 [ndiswrapper]
[81345.565005]  [<f98267f4>] wrap_pnp_start_pci_device+0x44/0x70 [ndiswrapper]
[81345.565152]  [<f98196aa>] loader_init+0x8a/0x140 [ndiswrapper]
[81345.565173]  [<f9828007>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[81345.565189]  [<f98450a7>] wrapper_init+0xa7/0x1000 [ndiswrapper]
[81465.189924]  [<f9819531>] load_wrap_device+0x181/0x1d0 [ndiswrapper]
[81465.189947]  [<f98267f4>] wrap_pnp_start_pci_device+0x44/0x70 [ndiswrapper]
[81465.190095]  [<f98196aa>] loader_init+0x8a/0x140 [ndiswrapper]
[81465.190115]  [<f9828007>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[81465.190132]  [<f98450a7>] wrapper_init+0xa7/0x1000 [ndiswrapper]
[81584.814908]  [<f9819531>] load_wrap_device+0x181/0x1d0 [ndiswrapper]
[81584.814935]  [<f98267f4>] wrap_pnp_start_pci_device+0x44/0x70 [ndiswrapper]
[81584.815117]  [<f98196aa>] loader_init+0x8a/0x140 [ndiswrapper]
[81584.815142]  [<f9828007>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[81584.815162]  [<f98450a7>] wrapper_init+0xa7/0x1000 [ndiswrapper]
[81704.439844]  [<f9819531>] load_wrap_device+0x181/0x1d0 [ndiswrapper]
[81704.439866]  [<f98267f4>] wrap_pnp_start_pci_device+0x44/0x70 [ndiswrapper]
[81704.440015]  [<f98196aa>] loader_init+0x8a/0x140 [ndiswrapper]
[81704.440035]  [<f9828007>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[81704.440052]  [<f98450a7>] wrapper_init+0xa7/0x1000 [ndiswrapper]
[81824.064794]  [<f9819531>] load_wrap_device+0x181/0x1d0 [ndiswrapper]
[81824.064817]  [<f98267f4>] wrap_pnp_start_pci_device+0x44/0x70 [ndiswrapper]
[81824.064965]  [<f98196aa>] loader_init+0x8a/0x140 [ndiswrapper]
[81824.064985]  [<f9828007>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[81824.065002]  [<f98450a7>] wrapper_init+0xa7/0x1000 [ndiswrapper]
[81943.689763]  [<f9819531>] load_wrap_device+0x181/0x1d0 [ndiswrapper]
[81943.689789]  [<f98267f4>] wrap_pnp_start_pci_device+0x44/0x70 [ndiswrapper]
[81943.689969]  [<f98196aa>] loader_init+0x8a/0x140 [ndiswrapper]
[81943.689993]  [<f9828007>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[81943.690013]  [<f98450a7>] wrapper_init+0xa7/0x1000 [ndiswrapper]

---

### Post by DylanCh82 on 2013-05-03
Hello.  I installed ubuntu on my laptop a few months ago and found that I liked it, installed it on my old Dimension 4300 and tried to get this device to work, failed, and gave up.  Now recently I purchased a Dell Vostro 200 to use as a HTPC/PVR which came with Windows 7 installed.  I set it up to dual boot with Ubuntu 12.04 64 bit and would really like to get this wireless adapter working under Ubuntu, as even though using win7 as a OS will be easier for me to set up, I really would like to use Ubuntu.  I have tried to follow the steps listed here on the various posts and have not succeded.  I followed Chili's advice on building ndiswrapper from source.

Here is the most common asked info:
dylan@htpc-Vostro-200:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
dylan@htpc-Vostro-200:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
dylan@htpc-Vostro-200:~$ dmesg | grep ndis
[   33.420402] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   33.547677] usbcore: registered new interface driver ndiswrapper
dylan@htpc-Vostro-200:~$ lsusb
Bus 001 Device 003: ID 1058:1140 Western Digital Technologies, Inc. 
Bus 002 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Is this able to be used on a 64 bit system?  Or am I just going to either have to tether or buy a new card?
Any help would be greatly appreciated.

---

### Post by chili555 on 2013-05-05
> Is this able to be used on a 64 bit system? Or am I just going to either have to tether or buy a new card?It's tricky, but you'll need 64-bit .inf files. Is that what you have? 

It all depends on whether you'd like to persevere despite all odds and probably succeed and maybe not; or if you'd like to spend US$12 for a new known working device and be done. I'll be happy to help in either case.

---

### Post by DylanCh82 on 2013-05-08
I am stubborn so I will try to get it going :-) I have not had time to play with it the last few days and will have a busy week but very much appreciate your quick response. if you would point me to some specific posts to double check and make sure I did everything properly that may be the best place to start. again thanks

---

### Post by DylanCh82 on 2013-05-08
sorry for the duplicate phone service spotty

---

### Post by chili555 on 2013-05-08
> dylan@htpc-Vostro-200:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.First, let's fix this. Instead of just removing it or re-naming it, let's see what's in it and do it correctly:```
cat /etc/modprobe.d/options 
```Next, this implies you have the wrong .inf file:> dylan@htpc-Vostro-200:~$ ndiswrapper -l
bcmwlhigh5 : driver installedIt ought to include *device present* indicating that the .inf file and the hardware see and recognize each other; they don't. Where did you get the files? Are they specifically labelled for 64-bit?

You might erase what you have now:```
sudo ndiswrapper -e bcmwlhigh5
sudo rm -rf /etc/ndiswrapper/*
```...And then install these. Download the file to your desktop. Right-click it and select 'Extract Here.' Open the terminal and do:```
sudo modprobe -r ndiswrapper
sudo ndiswrapper -i Desktop/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf
```Note is specifically claims to be for 64-bit. Also, the .inf file claims your device; here is a snip:> ; inf-File for Broadcom bcm43xx based WLAN Devices
; [COLOR="#FF0000"]64bit[/COLOR]

[version]
        Signature       = "$CHICAGO$"
        Class           = Net
        ClassGUID       = {4d36e972-e325-11ce-bfc1-08002be10318}
        Provider        = %Broadcom%
        Compatible      = 1
        DriverVer=08/26/2009, 5.10.79.30

[Manufacturer]
%Broadcom% = Broadcom

[Broadcom]
%BCM4xx01_DeviceDesc% = BCM43XXN64, USB\VID_050D&PID_825C
%BCM4xx02_DeviceDesc% = BCM43XXN64, USB\VID_050D&PID_6050
%BCM4xx04_DeviceDesc% = BCM43XXN64, USB\VID_050D&PID_615A
%BCM4xx03_DeviceDesc% = BCM43XXN64, USB\VID_0846&PID_9011
%BCM4xx03_DeviceDesc% = BCM43XXN64, USB\VID_[COLOR="#FF0000"]0846[/COLOR]&PID_[COLOR="#FF0000"]9020[/COLOR]
Now, reload ndiswrapper:```
sudo modprobe ndiswrapper
```And check:```
ndiswrapper -l
iwconfig
dmesg | grep ndis
```I have explained quite a bit here because I hope you and a lot of searchers will be interested in a greater understanding of the process.

---

### Post by DylanCh82 on 2013-05-08
Thanks a lot I will try this when I get home and post the results.

---

### Post by DylanCh82 on 2013-05-08
Okay here we go:

I ran through this and then accidentally closed my terminal (I am connecting to the computer via SSH from my laptop) here is what it gave me before I did anything:

cat/etc/modprobe.d/options:  told me no file exists

So then I did the code posted to erase what I had, downloaded the files and:

> dylan@htpc-Vostro-200:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ sudo modprobe -r ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
dylan@htpc-Vostro-200:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ sudo ndiswrapper -i ~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2/bcm43xx64.inf
couldn't open /home/dylan/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2/bcm43xx64.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.

> 
dylan@htpc-Vostro-200:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
dylan@htpc-Vostro-200:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ ndiswrapper -l
dylan@htpc-Vostro-200:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

dylan@htpc-Vostro-200:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ dmesg | grep ndis
[   20.429137] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   36.223024] usbcore: registered new interface driver ndiswrapper
[13510.988300] usbcore: deregistering interface driver ndiswrapper
[13752.489441] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[13752.500686] usbcore: registered new interface driver ndiswrapper
[14041.451297] usbcore: deregistering interface driver ndiswrapper
[14435.795092] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[14435.808690] usbcore: registered new interface driver ndiswrapper
dylan@htpc-Vostro-200:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ cat /etc/modprobe.d/optionsoptions saa7164 card=7

Hope this gives some clues.

---

### Post by chili555 on 2013-05-09
Let's take one thing at a time. First:> $ cat /etc/modprobe.d/options
options saa7164 card=7 You probably do need this file. Let's rename it so the system stops complaining:```
sudo  mv  /etc/modprobe.d/options  /etc/modprobe.d/options.conf
```Next, this:> couldn't open /home/dylan/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2/bcm43xx64.inf: No such file or directory I believe it is bcm[COLOR="#FF0000"]n[/COLOR]43xx64.inf.

---

### Post by DylanCh82 on 2013-05-09
Boy I feel stoopid missing the "n", I have to laugh because I checked it like 10 times... oh well it was a long night! I started from memory before the thread opened so I hope I didn't mess anything up doing it out of order, anyway:

> dylan@htpc-Vostro-200:~$ sudo ndiswrapper -i ~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf
[sudo] password for dylan: 
couldn't find SourceDisksFiles section - continuing anyway...
installing bcmn43xx64 ...
couldn't find install section "BCM43XXN32" -
installation may be incomplete
dylan@htpc-Vostro-200:~$ sudo mv /etc/modprobe.d/options /etc/modprobe.d/options.conf
dylan@htpc-Vostro-200:~$ sudo ndiswrapper -i ~/Deskop/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf
driver bcmn43xx64 is already installed

dylan@htpc-Vostro-200:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

dylan@htpc-Vostro-200:~$ ndiswrapper -l
bcmn43xx64 : driver installed
    device (0846:9020) present
dylan@htpc-Vostro-200:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

dylan@htpc-Vostro-200:~$ dmesg | grep ndis
[   20.129000] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   20.210878] usbcore: registered new interface driver ndiswrapper
dylan@htpc-Vostro-200:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

---

### Post by chili555 on 2013-05-10
> Boy I feel stoopid missing the "n", I have to laugh because I checked it like 10 times... oh well it was a long night!No worries. I've done worse myself. I've done worse today!!> couldn't find install section "BCM43XXN32" -
installation may be incompletePlease see here. This is the same problem and I propose the same experimental fix.

[http://ubuntuforums.org/showthread.php?t=1695036&page=9&p=11838453#post11838453](http://ubuntuforums.org/showthread.php?t=1695036&page=9&p=11838453#post11838453)

Especially note:> We might as well try it, we have very little else to try, frankly. I am sorry it took me so long to reply, this is a very tough problem. 

---

### Post by DylanCh82 on 2013-05-10
I took a quick look at the link and will try that tomorrow currently I am installing a fresh 3tb drive in this pc and don't want to mess it up I will post the results. again I will say that I am stubborn so I aim to get this working. thanks again for your help, not trying to get sappy but it reminds me why I want to use ubuntu rather than Windows... community support rocks!

---

### Post by intrloper on 2013-05-11
So I am brand new to linux and really want to not be pushed away but this network thing is annoying me to no end.

I read through several different forums and post to try and get this to work.

As it stands right now I somehow was about to get Ubuntu 13.04 to see the wireless WNA3100 USB adapter and says it is connected to my wireless router. It will even connect to sites for about 90 seconds then it just times out constantly. Can restart and surf before it times out. I do use WPA2 encryption but it seems to still cause issues even if open network. 

I am really sorry to be so new at this platform but I really dont want to give up and move back to Win7. Any help would be great, thank you.

---

### Post by asan42 on 2013-06-05
> **intrloper said:**
> So I am brand new to linux and really want to not be pushed away but this network thing is annoying me to no end.

I read through several different forums and post to try and get this to work.

As it stands right now I somehow was about to get Ubuntu 13.04 to see the wireless WNA3100 USB adapter and says it is connected to my wireless router. It will even connect to sites for about 90 seconds then it just times out constantly. Can restart and surf before it times out. I do use WPA2 encryption but it seems to still cause issues even if open network. 

I am really sorry to be so new at this platform but I really dont want to give up and move back to Win7. Any help would be great, thank you.


I have the same exact problem where you able to fix the issue?  Im running ubuntu 12.04

---

### Post by chili555 on 2013-06-06
> **asan42 said:**
> I have the same exact problem where you able to fix the issue?  Im running ubuntu 12.04Doe the logs have any clues?```
dmesg | grep -e wlan -e ndis -e 80211
cat /var/log/syslog | grep -e wlan -e ndis -e 80211 | tail -n20
```

---

### Post by DaMcNugGet on 2013-06-06
> **chili555 said:**
> spend US$12 for a new known working device and be done.

can you recomend an adapter for a 64bit ubuntu desktop (ubuntu is 12.04) I would prefer to be able to go to a store and buy it but if thats not possible that is all right.

---

### Post by chili555 on 2013-06-06
> **DaMcNugGet said:**
> can you recomend an adapter for a 64bit ubuntu desktop (ubuntu is 12.04) I would prefer to be able to go to a store and buy it but if thats not possible that is all right.There are many threads here about the same question. Please search.

Here is one to get started:  [http://ubuntuforums.org/showthread.php?t=1072694](http://ubuntuforums.org/showthread.php?t=1072694)


[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by DaMcNugGet on 2013-06-06
thanks

---

### Post by asan42 on 2013-06-06
asan@minepc:~$ dmesg | grep -e wlan -e ndis -e 80211
[   14.158946] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   15.534408] ndiswrapper: driver bcmwlhigh5 (Netgear,05/05/2009, 5.10.79.30) loaded
[   16.068545] wlan0: ethernet device 10:0d:7f:38:8f:9e using NDIS driver: bcmwlhigh5, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[   16.070741] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   16.071446] usbcore: registered new interface driver ndiswrapper
[   16.236610] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.237607] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.436372] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
asan@minepc:~$ cat /var/log/syslog | grep -e wlan -e ndis -e 80211 | tail -n20 
Jun  6 12:04:32 minepc NetworkManager[916]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun  6 12:04:32 minepc NetworkManager[916]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jun  6 12:04:32 minepc NetworkManager[916]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun  6 12:04:32 minepc NetworkManager[916]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jun  6 12:04:32 minepc dhclient: Listening on LPF/wlan0/10:0d:7f:38:8f:9e
Jun  6 12:04:32 minepc dhclient: Sending on   LPF/wlan0/10:0d:7f:38:8f:9e
Jun  6 12:04:32 minepc dhclient: DHCPREQUEST of 192.168.2.13 on wlan0 to 255.255.255.255 port 67
Jun  6 12:04:35 minepc dhclient: DHCPREQUEST of 192.168.2.13 on wlan0 to 255.255.255.255 port 67
Jun  6 12:04:35 minepc NetworkManager[916]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jun  6 12:04:35 minepc NetworkManager[916]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun  6 12:04:35 minepc NetworkManager[916]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jun  6 12:04:36 minepc NetworkManager[916]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jun  6 12:04:36 minepc NetworkManager[916]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun  6 12:04:36 minepc NetworkManager[916]: <info> Policy set 'belkin.991' (wlan0) as default for IPv4 routing and DNS.
Jun  6 12:04:36 minepc NetworkManager[916]: <info> Activation (wlan0) successful, device activated.
Jun  6 12:04:36 minepc NetworkManager[916]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jun  6 12:04:52 minepc NetworkManager[916]: <info> (wlan0): IP6 addrconf timed out or failed.
Jun  6 12:04:52 minepc NetworkManager[916]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun  6 12:04:52 minepc NetworkManager[916]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun  6 12:04:52 minepc NetworkManager[916]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
asan@minepc:~$ ^C
asan@minepc:~$



asan@minepc:~$ lsusb
Bus 001 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 002 Device 004: ID 0781:5561 SanDisk Corp. 
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
asan@minepc:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
	device (0846:9011) present
asan@minepc:~$ modprobe ndiswrapper
asan@minepc:~$ /desktop# ndiswrapper -e bcmwlhigh5
bash: /desktop#: No such file or directory
asan@minepc:~$ dmesg | grep ndis
[   14.334313] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   15.743295] ndiswrapper: driver bcmwlhigh5 (Netgear,05/05/2009, 5.10.79.30) loaded
[   15.998441] usbcore: registered new interface driver ndiswrapper
asan@minepc:~$ arch
x86_64
asan@minepc:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11g  ESSID:"belkin.991"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 08:86:3B:D4:19:91   
          Bit Rate=117 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:40  Invalid misc:28310   Missed beacon:0


asan@minepc:~$ 


i don't see any red flags but then again im no expert at this. any ideas would be very appreciated.

---

### Post by asan42 on 2013-06-06
> **chili555 said:**
> Doe the logs have any clues?```
dmesg | grep -e wlan -e ndis -e 80211
cat /var/log/syslog | grep -e wlan -e ndis -e 80211 | tail -n20
```

code:[COLOR=#000000][INDENT]asan@minepc:~$ dmesg | grep -e wlan -e ndis -e 80211
[ 14.158946] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[ 15.534408] ndiswrapper: driver bcmwlhigh5 (Netgear,05/05/2009, 5.10.79.30) loaded
[ 16.068545] wlan0: ethernet device 10:0d:7f:38:8f:9e using NDIS driver: bcmwlhigh5, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf
[ 16.070741] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[ 16.071446] usbcore: registered new interface driver ndiswrapper
[ 16.236610] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 16.237607] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 27.436372] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
asan@minepc:~$ cat /var/log/syslog | grep -e wlan -e ndis -e 80211 | tail -n20 
Jun 6 12:04:32 minepc NetworkManager[916]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 6 12:04:32 minepc NetworkManager[916]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jun 6 12:04:32 minepc NetworkManager[916]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun 6 12:04:32 minepc NetworkManager[916]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jun 6 12:04:32 minepc dhclient: Listening on LPF/wlan0/10:0d:7f:38:8f:9e
Jun 6 12:04:32 minepc dhclient: Sending on LPF/wlan0/10:0d:7f:38:8f:9e
Jun 6 12:04:32 minepc dhclient: DHCPREQUEST of 192.168.2.13 on wlan0 to 255.255.255.255 port 67
Jun 6 12:04:35 minepc dhclient: DHCPREQUEST of 192.168.2.13 on wlan0 to 255.255.255.255 port 67
Jun 6 12:04:35 minepc NetworkManager[916]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jun 6 12:04:35 minepc NetworkManager[916]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 6 12:04:35 minepc NetworkManager[916]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jun 6 12:04:36 minepc NetworkManager[916]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jun 6 12:04:36 minepc NetworkManager[916]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun 6 12:04:36 minepc NetworkManager[916]: <info> Policy set 'belkin.991' (wlan0) as default for IPv4 routing and DNS.
Jun 6 12:04:36 minepc NetworkManager[916]: <info> Activation (wlan0) successful, device activated.
Jun 6 12:04:36 minepc NetworkManager[916]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jun 6 12:04:52 minepc NetworkManager[916]: <info> (wlan0): IP6 addrconf timed out or failed.
Jun 6 12:04:52 minepc NetworkManager[916]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun 6 12:04:52 minepc NetworkManager[916]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun 6 12:04:52 minepc NetworkManager[916]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
asan@minepc:~$ ^C
asan@minepc:~$



asan@minepc:~$ lsusb
Bus 001 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 002 Device 004: ID 0781:5561 SanDisk Corp. 
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
asan@minepc:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
device (0846:9011) present
asan@minepc:~$ modprobe ndiswrapper
asan@minepc:~$ /desktop# ndiswrapper -e bcmwlhigh5
bash: /desktop#: No such file or directory
asan@minepc:~$ dmesg | grep ndis
[ 14.334313] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[ 15.743295] ndiswrapper: driver bcmwlhigh5 (Netgear,05/05/2009, 5.10.79.30) loaded
[ 15.998441] usbcore: registered new interface driver ndiswrapper
asan@minepc:~$ arch
x86_64
asan@minepc:~$ iwconfig
eth0 no wireless extensions.


lo no wireless extensions.


wlan0 IEEE 802.11g ESSID:"belkin.991" 
Mode:Managed Frequency:2.437 GHz Access Point: 08:86:3B:grin:4:19:91 
Bit Rate=117 Mb/s Tx-Power:32 dBm 
RTS thr:2347 B Fragment thr:2346 B 
Power Management:eek:ff
Link Quality:67/100 Signal level:-53 dBm Noise level:-96 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:40 Invalid misc:28310 Missed beacon:0


asan@minepc:~$ 


i don't see any red flags but then again im no expert at this. any ideas would be very appreciated.[/INDENT]
[/COLOR]
[INDENT][Last edited by asan42]("http://ubuntuforums.org/posthistory.php?p=12680440"); 3 Hours Ago at [COLOR=#3E3E3E]07:31 PM[/COLOR].[/INDENT]

---

### Post by sivart111 on 2013-07-07
Its working for me now.  Thank you!

> **Marcd225 said:**
> at least we are making some progress


```
marcus@ubuntu:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
marcus@ubuntu:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

marcus@ubuntu:~$ 

```

---

### Post by cyril.godart on 2013-09-19
Hi,

I have installed apparently a 32 bits Lubuntu 13.04 on a 64 bits processor:
```

cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~$ grep --color=always -iw lm /proc/cpuinfo
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx [COLOR=#ff0000]lm[/COLOR] constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~$ arch
i686
cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring



```
I am trying to use a Netgear N300 USB wifi dongle:
```

cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~$ lsusb
Bus 001 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I have downloaded and installed the latest version of ndiswrapper:
```

cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/3.8.0-30-generic/misc/ndiswrapper.ko
version:        1.58
vermagic:       3.8.0-30-generic SMP mod_unload modversions 686 

```
I have downloaded 2 of Chilli s folders:
```

cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~$ ls Desktop/Broadcom_bcm43xx_USB_32_64bit_v2/ Desktop/wna3100-drivers/
Desktop/Broadcom_bcm43xx_USB_32_64bit_v2/:
bcmn43xx32.inf  bcmn43xx32.sys  bcmn43xx64.inf  bcmn43xx64.sys
Desktop/wna3100-drivers/:
bcmh43xx64.cat  bcmh43xx.cat  bcmwlhigh5.inf  bcmwlhigh5.sys

```
I have tried with several version of the driver but to no avail:
```

cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~$ iwconfig
wlan10    IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.


eth0      no wireless extensions.
cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~$ sudo dmesg | grep ndis
[   23.149175] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   23.909183] usbcore: registered new interface driver ndiswrapper


```


Could someone help ?

Thanks and best,

Cyril

---

### Post by chili555 on 2013-10-13
> **cyril.godart said:**
> Hi,

I have installed apparently a 32 bits Lubuntu 13.04 on a 64 bits processor:
<snip>

Could someone help ?

Thanks and best,

CyrilLet's see some additional diagnostics:```
ndiswrapper -l
arch
```

---

### Post by cyril.godart on 2013-10-13
Great to have you back, Chilli55.

So 

```

cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~$ arch
i686
cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~$ ndiswrapper -l
cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~$ 


```
hum...
It has been 3 weeks since my post. I am not sure what I tried in the meantime.

---

### Post by chili555 on 2013-10-13
I suggest you try:```
cd Desktop/Broadcom_bcm43xx_USB_32_64bit_v2/
sudo ndiswrapper -i bcmn43xx32.inf
sudo modprobe -r ndiswrapper && sudo modprobe ndiswrapper
```Now check for messages, errors, clues, etc.:```
iwconfig
dmesg | grep ndis
```

---

### Post by cyril.godart on 2013-10-13
Ok. So you tracked down a first issue. My version of ndiswrapper was not
the latest on. I just downloaded 1.58, make uninstall, make, make install in the directory. 
Now:
```
 
cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~$ iwconfig
wlan10    IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
wlan11    IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.


cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~$ dmesg | grep ndis
[   19.863949] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   21.541626] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[   21.800754] usbcore: registered new interface driver ndiswrapper
[   22.219435] ndiswrapper: changing interface name from 'wlan0' to 'wlan11'
cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~$ pwd
/home/cyrilgodart
cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~$ cd Desktop/
cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~/Desktop$ cd Broadcom_bcm43xx_USB_32_64bit_v2/
cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ 
cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ sudo ndiswrapper -i bcmn43xx32.inf
[sudo] password for cyrilgodart: 
driver bcmn43xx32 is already installed
cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ sudo ndiswrapper -i bcmn43xx32.inf
driver bcmn43xx32 is already installed
cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ sudo modprobe -r ndiswrapper && sudo modprobe ndiswrapper
cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ iwconfig
wlan10    IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
wlan11    IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.
cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ dmesg | grep ndis
[   19.863949] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   21.541626] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[   21.800754] usbcore: registered new interface driver ndiswrapper
[   22.219435] ndiswrapper: changing interface name from 'wlan0' to 'wlan11'
[  470.980730] usbcore: deregistering interface driver ndiswrapper
[  471.004997] ndiswrapper: device wlan11 removed
[  471.034935] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[  471.298603] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[  471.562318] usbco: registered new interface driver ndiswrapper
[  471.576446] ndiswrapper: changing interface name from 'wlan0' to 'wlan11'
cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ 

```
Trying to reboot.

---

### Post by cyril.godart on 2013-10-13
and just so that there is no ambiguity: still not working after reboot.

---

### Post by chili555 on 2013-10-13
Why do you have two wireless interfaces; the enigmatic wlan10 and wlan11?? Is there an internal device that isn't performing as expected? We ought to troubleshoot it and if all else fails, blacklist its driver so it can't interfere.

Actually, it looks pretty solid:> wlan11    IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   We see no obvious errors, warnings, smoke, sparks, etc.

---

### Post by cyril.godart on 2013-10-14
You are exactly right. I found the computer in a flat and the former tenant confirmed he was not interested without explaining why. 
I charged it, switched it on and it was working except for the wifi. I assumed that was the reason why it had been discarded. 
I needed a laptop. So I installed Lubuntu and purchased a series of dongles, of which none performed in a satisfactory way. 
Then I got the Netgear 300 that looked like an upgrade on the previous ones, if only because it is larger piece of equipment and it can be
attached to a cable. 

Now, it is not unlikely that the original card works after all: I had simply not contemplated the possibility. There is a hardware
button with the wifi sign on it that strangely enough is always on, even when pressed insistantely. 

Let me know how you want to proceed.

---

### Post by chili555 on 2013-10-14
Please run and post:```
lspci -nn | grep 0280
sudo lshw -C network
```

---

### Post by cyril.godart on 2013-10-15
Here you are...
```

cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~$ lspci -nn | grep 0280
01:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
cyrilgodart@cyrilgodart-Presario-C700-Notebook-PC:~$ sudo lshw -C network
[sudo] password for cyrilgodart: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:91300000-91303fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:82:fb:5c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.4 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:1000(size=256) memory:91200000-912000ff
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan10
       serial: 00:1a:73:af:8c:b0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.8.0-31-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan11
       serial: 10:0d:7f:40:f7:de
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmn43xx32 driverversion=1.58+,08/26/2009, 5.10.79.30 link=no multicast=yes wireless=IEEE 802.11g

```

---

### Post by chili555 on 2013-10-15
Why don't we get the pretty easy Broadcom 4311 going and show the Netgear the door? I suggest you detach the Netgear, get a temporary wired ethernet connection and do:```
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet, reboot and let us have your report.

---

### Post by cyril.godart on 2013-10-16
Why does it have to look so embarassingly simple ?

You were right all along Chili555. The internal card is working now. 

It looks as though I cannot reach the main Wifi hub but I believe 
because I changed the frequency and the internal card must be somewhat old. 

On a standard Wifi hub, the card is running fine. As a matter of fact, this answer
is written while on a wireless connection.

What can I say ? Thanks for serving the Linux and Ubuntu community with dedication
and knowledge. And thanks for helping on this specific issue which has been dragging
on for weeks.

Best

---

### Post by chili555 on 2013-10-17
It is my pleasure. I'm glad it's working!

---

### Post by nlorenzo40 on 2013-10-31
hey im having trouble contecting my netgear wireless adapter are you on to help?

---

### Post by chili555 on 2013-11-01
> **nlorenzo40 said:**
> hey im having trouble contecting my netgear wireless adapter are you on to help?Sure. Please post:```
lsusb
lsb_release -d
```Thanks.

---

### Post by nlorenzo40 on 2013-11-01
nick@nick-MacBookPro:~$ lsusb
Bus 002 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 002 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD Camera
Bus 001 Device 005: ID 05ac:0252 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 001 Device 008: ID 05ac:821a Apple, Inc. Bluetooth Host Controller
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
nick@nick-MacBookPro:~$ lsb_release -d
Description:	Ubuntu 13.10
nick@nick-MacBookPro:~$

---

### Post by chili555 on 2013-11-01
>  0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]I have grown, in hundreds of posts, to hate this device. If yours is a 64-bit machine, as most are today, it may never work. What have you tried so far?

I'd rather try to get the wireless device in your MacBook working. Did you try that?

---

### Post by nlorenzo40 on 2013-11-02
yes my wireless in my mac book works but i want to get wireless in my vm virtual box but i read it only works if you get a usb wireless adapter. liek shown in here i dont have a wlan0 so it doesnt work in vm virtual box

nick@nick-MacBookPro:~$ sudo airmon-ng




Interface	Chipset		Driver


eth1		Unknown 	wl - [phy0]

---

### Post by chili555 on 2013-11-03
I know nothing about airmon and I don't want to know. If you are trying to do packet corruption or whatever, then I highly doubt you will ever get it going with ndiswrapper. Sorry I can't be of further assistance.

---

### Post by loaba on 2014-04-20
Resurecting an old thread...

I've got a wna3100 on a desktop running Kubuntu 14.04. I have DL'd the proper win drivers and installed  NDISWRAPPER via package manner. Where I do I go from here?

---

### Post by loaba on 2014-04-20
More infoe
```
root@Mercury:/home/*******/Desktop/ndiswrapper-1.59# dmesg | grep ndis
[  555.875783] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[  555.882723] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  555.973167] usbcore: registered new interface driver ndiswrapper
[ 2249.140306] usbcore: deregistering interface driver ndiswrapper
[ 2262.113069] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 2262.373907] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'
[ 2262.373994] usbcore: registered new interface driver ndiswrapper
```

---

### Post by chili555 on 2014-04-20
> **loaba said:**
> More infoe
```
root@Mercury:/home/*******/Desktop/ndiswrapper-1.59# dmesg | grep ndis
[  555.875783] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[  555.882723] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  555.973167] usbcore: registered new interface driver ndiswrapper
[ 2249.140306] usbcore: deregistering interface driver ndiswrapper
[ 2262.113069] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 2262.373907] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'
[ 2262.373994] usbcore: registered new interface driver ndiswrapper
```You probably have the wrong inf file for your device. What does this tell us?```
cat /var/log/syslog | grep ndis
```Check your device here:```
lsusb
```Then search this thread for the same usb.id. Here is a post that describes the general process: [http://ubuntuforums.org/showthread.php?t=1695036&page=13&p=12528053#post12528053](http://ubuntuforums.org/showthread.php?t=1695036&page=13&p=12528053#post12528053) 

Now I have no idea if yours is a 0846:9011 or a 0846:9020 or a whatever, but you need an inf file that enumerates your device exactly, for Windows ***XP*** and for your architecture, either 32- or 64-bit. Find out with:```
arch
```If you find that you do have the wrong file, I've attached various files numerous places in this thread.

Now I could try to fix each and every N300 case one-by-one and this could be a 1200 post thread. I prefer to describe the process and let self-reliant Ubuntuans find the solution. Of course, I am always willing to help if you or anyone is really stuck.

---

### Post by sidewalkcynic on 2014-04-25
Mr. Chilli, help me. I have gone through the thread, and have completed several makes and installs and this seems to be the best I can do.

```
lunaphiles@acer-pacer:~$ ndiswrapper -l
bcmwlhigh6 : driver installed
	device (0846:9020) present
lunaphiles@acer-pacer:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

lunaphiles@acer-pacer:~$ 
```
I do not have a wired connection to the PC that I am trying to fix, but I do have a wireless connection to the laptop that I am using to trouble shoot from. is there any possibility of hooking them up to use the wireless?

I'll be leaving the computer for the day, shortly - so don't expect an immediate reply. Will be able to spend all day tomorrow on the project.

---

### Post by chili555 on 2014-04-25
> **sidewalkcynic said:**
> Mr. Chilli, help me. I have gone through the thread, and have completed several makes and installs and this seems to be the best I can do.

```
lunaphiles@acer-pacer:~$ ndiswrapper -l
bcmwlhigh6 : driver installed
	device (0846:9020) present
lunaphiles@acer-pacer:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

lunaphiles@acer-pacer:~$ 
```
I do not have a wired connection to the PC that I am trying to fix, but I do have a wireless connection to the laptop that I am using to trouble shoot from. is there any possibility of hooking them up to use the wireless?

I'll be leaving the computer for the day, shortly - so don't expect an immediate reply. Will be able to spend all day tomorrow on the project.Are there any interesting messages here?```
sudo modprobe ndiswrapper > wifi.txt
dmesg | grep ndis  >>  wifi.txt
```Find the file wifi.txt in your user directory, transfer it on a USB drive or similar and post it here.

Until I change my avatar again, it's Señor Chili.

---

### Post by sidewalkcynic on 2014-04-25
this looks like it has some problems that can be fixed
```
lunaphiles@acer-pacer:~$ sudo modprobe ndiswrapper
[sudo] password for lunaphiles: 
lunaphiles@acer-pacer:~$ dmesg | grep ndis
[    9.446482] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[    9.447299] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[    9.970312] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[    9.970322] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[    9.970328] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[    9.970335] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[    9.970340] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[    9.970345] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[    9.970350] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[    9.970355] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[    9.970360] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[    9.970367] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[    9.970374] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[    9.970379] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[    9.970384] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[    9.970390] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[    9.970395] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[    9.970401] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[    9.970406] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[    9.970412] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[    9.970417] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[    9.970423] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[    9.970429] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[    9.970435] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[    9.970441] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[    9.970450] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[    9.970456] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[    9.970461] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[    9.970467] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[    9.970476] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[    9.970488] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[    9.970492] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[    9.970497] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[    9.970502] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[    9.970507] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[    9.970510] ndiswrapper (load_sys_files:200): couldn't prepare driver 'bcmwlhigh6'
[    9.970977] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
[    9.971024] usbcore: registered new interface driver ndiswrapper
[   41.519501] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   41.519510] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   41.519515] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   41.519521] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   41.519525] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   41.519529] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   41.519533] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   41.519538] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   41.519542] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   41.519548] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   41.519554] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   41.519558] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   41.519563] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   41.519567] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[   41.519571] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   41.519575] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   41.519579] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[   41.519583] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   41.519587] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[   41.519592] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[   41.519597] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[   41.519601] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   41.519605] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   41.519614] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   41.519618] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   41.519622] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   41.519626] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   41.519634] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   41.519644] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   41.519648] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   41.519651] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[   41.519655] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[   41.519658] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   41.519660] ndiswrapper (load_sys_files:200): couldn't prepare driver 'bcmwlhigh6'
[   41.520154] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
```

There was nothing on the wifi.txt document

thanks for your help, Senior Chili.

---

### Post by chili555 on 2014-04-25
> [    9.970510] ndiswrapper (load_sys_files:200): couldn't prepare driver 'bcmwlhigh6'
[    9.970977] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'Bingo! Where did you get the files you used? It is doubtful that bcmwlhigh6 is correct. 

I suggest you try the files I attached in post #89. If you need additional guidance to undo bcmwlhigh6 and redo with those files, please post back.

---

### Post by sidewalkcynic on 2014-04-26
> **chili555 said:**
> Bingo! Where did you get the files you used? It is doubtful that bcmwlhigh6 is correct. I recovered the files from the Windows installation, which I got from the Netgear website for drivers. The WiFi for the Windows partition works

> **chili555 said:**
> I suggest you try the files I attached in post #89. If you need additional guidance to undo bcmwlhigh6 and redo with those files, please post back.I reinsalled ndiswrapper, thinking that was how to remove the high6 file, but that did not work. I installed the 64 bit first and it did not work, and so, I tried the 32.

```
lunaphiles@acer-pacer:/media/lunaphiles/1G/broadcom$ sudo ndiswrapper -i bcmn43xx32.inf
[sudo] password for lunaphiles: 
couldn't find SourceDisksFiles section - continuing anyway...
installing bcmn43xx32 ...
lunaphiles@acer-pacer:/media/lunaphiles/1G/broadcom$ ndiswrapper -l
bcmn43xx32 : driver installed
	device (0846:9020) present
bcmn43xx64 : driver installed
	device (0846:9020) present
bcmwlhigh6 : driver installed
	device (0846:9020) present
lunaphiles@acer-pacer:/media/lunaphiles/1G/broadcom$ sudo modprobe ndiswrapper
lunaphiles@acer-pacer:/media/lunaphiles/1G/broadcom$ 

lunaphiles@acer-pacer:~$ dmesg | grep ndis
[   10.012923] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   10.013730] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   10.944327] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   10.944338] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   10.944344] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   10.944351] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   10.944356] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   10.944361] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   10.944365] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   10.944371] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   10.944376] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   10.944382] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   10.944389] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   10.944394] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   10.944399] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   10.944406] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[   10.944411] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   10.944416] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   10.944422] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[   10.944427] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   10.944433] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[   10.944438] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[   10.944445] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[   10.944450] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   10.944456] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   10.944465] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   10.944471] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   10.944476] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   10.944482] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   10.944491] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   10.944503] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   10.944507] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   10.944512] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[   10.944517] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[   10.944522] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   10.944525] ndiswrapper (load_sys_files:200): couldn't prepare driver 'bcmwlhigh6'
[   10.945059] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
[   10.945108] usbcore: registered new interface driver ndiswrapper
[   50.341705] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   50.341714] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   50.341719] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   50.341725] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   50.341729] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   50.341733] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   50.341737] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   50.341742] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   50.341746] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   50.341752] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   50.341758] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   50.341763] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   50.341767] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   50.341771] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[   50.341775] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   50.341779] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   50.341783] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[   50.341788] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   50.341792] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[   50.341796] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[   50.341801] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[   50.341805] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   50.341810] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   50.341818] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   50.341822] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   50.341826] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   50.341831] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   50.341838] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   50.341849] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   50.341852] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   50.341856] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[   50.341859] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[   50.341863] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   50.341864] ndiswrapper (load_sys_files:200): couldn't prepare driver 'bcmwlhigh6'
[   50.342382] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
```

I also followed the instruction at [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100)

Add the following to ntoskernal_io.c 
```
wstdcall NTSTATUS WIN_FUNC(IoUnregisterPlugPlayNotification,1) 
(void *tag)
{
      TRACE2("%p", tag);
      TODO(); /* Probably Not, legacy function abandoned in Windows 7 */
      IOEXIT(return STATUS_SUCCESS); /* Linux doesn't use it either */
}
```

---

### Post by chili555 on 2014-04-26
Yikes! Let's do some surgery here. First, is yours a 32- or 64-bit system?```
arch
```Don't install or modify or re-compile anything until we undo the problems here, puh-leeeeeze!

---

### Post by sidewalkcynic on 2014-04-26
x86_64

---

### Post by chili555 on 2014-04-26
Please check:```
ls /etc/ndiswrapper
```You should see directories called bcmn43xx32, bcmn43xx64 and bcmwlhigh6 . You have a 64-bit system, so we will remove the incorrect directories:```
sudo rm -rf bcmn43xx32
sudo rm -rf bcmwlhigh6
```Now reboot and show us again:```
sudo modprobe ndiswrapper > wifi2.txt
dmesg | grep ndis  >>  wifi2.txt
```

---

### Post by sidewalkcynic on 2014-04-26
```
lunaphiles@acer-pacer:~$ sudo modprobe ndiswrapper
lunaphiles@acer-pacer:~$ sudo dmesg | grep ndis >> wifi2.txt
lunaphiles@acer-pacer:~$ sudo dmesg | grep ndis
[   10.098267] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   10.099055] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   10.269282] usbcore: registered new interface driver ndiswrapper
[   29.798120] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   29.798130] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   29.798135] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   29.798141] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   29.798145] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   29.798149] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   29.798154] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   29.798158] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   29.798162] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   29.798168] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   29.798174] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   29.798179] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   29.798183] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   29.798187] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[   29.798191] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   29.798195] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   29.798199] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[   29.798204] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   29.798208] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[   29.798212] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[   29.798217] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[   29.798221] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   29.798226] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   29.798234] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   29.798238] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   29.798242] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   29.798247] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   29.798254] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   29.798265] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   29.798268] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   29.798272] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[   29.798275] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[   29.798279] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   29.798281] ndiswrapper (load_sys_files:200): couldn't prepare driver 'bcmwlhigh6'
[   29.798689] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
```

I ran the ```
ls /etc/ndiswrapper
```

and they were still there

---

### Post by sidewalkcynic on 2014-04-26
I am willing to reinstall Ubuntu, because I did not set up partitions, because it was the first time installing and I just wanted to seperate Windows and allow the Ubuntu installation to setup in one partition and SWAP; and to see if the WiFi would work.

---

### Post by chili555 on 2014-04-26
> (load_sys_files:200): couldn't prepare driver '[COLOR="#FF0000"]bcmwlhigh6[/COLOR]'Let's try this again, only better.```
cd /etc/ndiswrapper
sudo rm -rf bcmn43xx32
sudo rm -rf bcmwlhigh6
```Sorry for my mis-step.

---

### Post by sidewalkcynic on 2014-04-26
that got the WiFi connection going, but the FireFox connection only worked for the first page. I'll try the updater

---

### Post by chili555 on 2014-04-26
> **sidewalkcynic said:**
> that got the WiFi connection going, but the FireFox connection only worked for the first page. I'll try the updaterWe're getting there!

---

### Post by sidewalkcynic on 2014-04-26
I'll bet my WiFi host only allows my laptop and not the new PC desktop.

---

### Post by sidewalkcynic on 2014-04-26
No, I found the problem - I had to remove an edit in the networks menu that I tried before.

Thanks for your help, Senior Chili.

---

### Post by chili555 on 2014-04-26
Glad it's working! Have fun.

---

### Post by sidewalkcynic on 2014-04-26
I spoke too soon - it worked for a couple of pages, and I tried to download from the software app, and then it failed. Tried restarting. I wen to the Windows installation and browsed the Internet for an hour with no problems, and listened to a stream with no problem. Returned to the Ubuntu 14.04, and it loaded a couple of pages and failed.

```
lunaphiles@acer-pacer:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"dlink"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:21:91:13:A0:F9   
          Bit Rate=117 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:32  Invalid misc:3764   Missed beacon:0
```

```
unaphiles@acer-pacer:~$ dmesg | grep ndis
[    9.399175] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[    9.399967] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   10.011477] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   10.713050] usbcore: registered new interface driver ndiswrapper
```

---

### Post by chili555 on 2014-04-26
Any clues here?```
nm-tool
cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```Please tell us more about what failed. Does it appear to be connected but not load pages? Freeze? Drop? Or...??

---

### Post by sidewalkcynic on 2014-04-26
it seems to have difficulty connecting, but the network menu says it is connected
```
lunaphiles@acer-pacer:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:26:2D:16:52:08

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [dlink] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        10:0D:7F:32:B1:74

  Capabilities:
    Speed:           78 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    linksys-madina:  Infra, 00:22:6B:52:55:CB, Freq 2452 MHz, Rate 54 Mb/s, Strength 80 WEP
    belkin.a74:      Infra, 08:86:3B:7E:0A:74, Freq 2462 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    *dlink:          Infra, 00:21:91:13:A0:F9, Freq 2422 MHz, Rate 54 Mb/s, Strength 67
    optimumwifi:     Infra, 06:A1:51:CB:D0:51, Freq 2462 MHz, Rate 54 Mb/s, Strength 54
    E56CA2:          Infra, 04:A1:51:E5:6C:A1, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    186918:          Infra, 20:4E:7F:18:69:17, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    optimumwifi:     Infra, 22:4E:7F:18:69:18, Freq 2412 MHz, Rate 54 Mb/s, Strength 50
    2A5490:          Infra, 4C:60:DE:2A:54:8F, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA2
    IVAN:            Infra, E0:46:9A:7A:1F:0A, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA2
    807164:          Infra, 00:03:D8:80:71:6A, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    50B3B4:          Infra, 74:44:01:50:B3:B3, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    optimumwifi:     Infra, 06:A1:51:E5:6C:A2, Freq 2437 MHz, Rate 54 Mb/s, Strength 45
    optimumwifi:     Infra, 92:03:D8:83:5A:2A, Freq 2437 MHz, Rate 54 Mb/s, Strength 25

  IPv4 Settings:
    Address:         192.168.0.187
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1
```
```
lunaphiles@acer-pacer:~$ cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
Apr 26 13:52:32 acer-pacer NetworkManager[735]: <info>   nameserver '192.168.0.1'
Apr 26 13:52:32 acer-pacer NetworkManager[735]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr 26 13:52:32 acer-pacer NetworkManager[735]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Apr 26 13:52:33 acer-pacer NetworkManager[735]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Apr 26 13:52:33 acer-pacer NetworkManager[735]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Apr 26 13:52:33 acer-pacer NetworkManager[735]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Apr 26 13:52:33 acer-pacer NetworkManager[735]: <info> NetworkManager state is now CONNECTED_GLOBAL
Apr 26 13:52:33 acer-pacer NetworkManager[735]: <info> Policy set 'dlink' (wlan0) as default for IPv4 routing and DNS.
Apr 26 13:52:33 acer-pacer NetworkManager[735]: <info> DNS: starting dnsmasq...
Apr 26 13:52:33 acer-pacer NetworkManager[735]: <warn> dnsmasq not available on the bus, can't update servers.
Apr 26 13:52:33 acer-pacer NetworkManager[735]: <error> [1398534753.726541] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Apr 26 13:52:33 acer-pacer NetworkManager[735]: <warn> DNS: plugin dnsmasq update failed
Apr 26 13:52:33 acer-pacer NetworkManager[735]: <info> Writing DNS information to /sbin/resolvconf
Apr 26 13:52:34 acer-pacer NetworkManager[735]: <info> Activation (wlan0) successful, device activated.
Apr 26 13:52:34 acer-pacer NetworkManager[735]: <warn> dnsmasq appeared on DBus: :1.59
Apr 26 13:52:34 acer-pacer NetworkManager[735]: <info> Writing DNS information to /sbin/resolvconf
Apr 26 13:52:52 acer-pacer NetworkManager[735]: <info> (wlan0): IP6 addrconf timed out or failed.
Apr 26 13:52:52 acer-pacer NetworkManager[735]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 26 13:52:52 acer-pacer NetworkManager[735]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 26 13:52:52 acer-pacer NetworkManager[735]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
lunaphiles@acer-pacer:~$ 
```
[https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)
> Note that the package "dnsmasq" interferes with Network Manager which can use "dnsmasq-base" to provide DHCP services when sharing an internet connection. Therefore, if you use network manager (fine in simple set-ups only), then install dnsmasq-base, but not dnsmasq. If you have a more complicated set-up, uninstall network manager, use dnsmasq, or similar software (bind9, dhcpd, etc), and configure things by hand. 

---

### Post by sidewalkcynic on 2014-04-27
Since, I am able to connect and access a couple of pages after a reboot, I was able to download the dnsmasq package, and I did the editing of the files; but it does not seem to work any better - it still cannot load any pages after the first two or three.

```
lunaphiles@acer-pacer:~$ sudo apt-get install dnsmasq
[sudo] password for lunaphiles: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dnsmasq
0 upgraded, 1 newly installed, 0 to remove and 14 not upgraded.
Need to get 14.9 kB of archives.
After this operation, 114 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/universe dnsmasq all 2.68-1 [14.9 kB]
Fetched 14.9 kB in 0s (63.6 kB/s)
Selecting previously unselected package dnsmasq.
(Reading database ... 163205 files and directories currently installed.)
Preparing to unpack .../dnsmasq_2.68-1_all.deb ...
Unpacking dnsmasq (2.68-1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up dnsmasq (2.68-1) ...
 * Starting DNS forwarder and DHCP server dnsmasq                        [ OK ] 
Processing triggers for ureadahead (0.100.0-16) ...
lunaphiles@acer-pacer:~$ 


lunaphiles@acer-pacer:~$ sudo gedit
[sudo] password for lunaphiles: 

(gedit:2087): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:2087): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
lunaphiles@acer-pacer:~$ sudo /etc/init.d/dnsmasq restart
 * Restarting DNS forwarder and DHCP server dnsmasq                      [ OK ] 
lunaphiles@acer-pacer:~$ dig ubuntu.com

; <<>> DiG 9.9.5-3-Ubuntu <<>> ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10640
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4000
;; QUESTION SECTION:
;ubuntu.com.			IN	A

;; ANSWER SECTION:
ubuntu.com.		600	IN	A	91.189.94.156

;; Query time: 23 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sun Apr 27 12:38:24 EDT 2014
;; MSG SIZE  rcvd: 55

lunaphiles@acer-pacer:~$ 
```

---

### Post by sidewalkcynic on 2014-04-27
So I reinstalled Ubuntu 14.04 with a DVD image, because I thought I could access a ndiswrapper, but it did not happen; so I installed ndiswrapper from the download and used the inf. file you gave in the post 30. but it does not work

```
lunaphiles@SecularCircus:/media/lunaphiles/1G/ndiswrapper-1.59$ sudo make uninstall
[sudo] password for lunaphiles: 
rm -f /usr/share/man/man8/ndiswrapper.8
rm -f /usr/share/man/man8/loadndisdriver.8
make -C driver uninstall
make[1]: Entering directory `/media/lunaphiles/1G/ndiswrapper-1.59/driver'
rm -f /lib/modules/3.13.0-24-generic/misc/ndiswrapper.ko
/sbin/depmod -a 3.13.0-24-generic
make[1]: Leaving directory `/media/lunaphiles/1G/ndiswrapper-1.59/driver'
make -C utils uninstall
make[1]: Entering directory `/media/lunaphiles/1G/ndiswrapper-1.59/utils'
rm -f /sbin/loadndisdriver
rm -f /usr/sbin/ndiswrapper
rm -f /usr/sbin/ndiswrapper-buginfo
make[1]: Leaving directory `/media/lunaphiles/1G/ndiswrapper-1.59/utils'
lunaphiles@SecularCircus:/media/lunaphiles/1G/ndiswrapper-1.59$ sudo make
make -C utils
make[1]: Entering directory `/media/lunaphiles/1G/ndiswrapper-1.59/utils'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/media/lunaphiles/1G/ndiswrapper-1.59/utils'
make -C driver
make[1]: Entering directory `/media/lunaphiles/1G/ndiswrapper-1.59/driver'
make -C /usr/src/linux-headers-3.13.0-24-generic M=/media/lunaphiles/1G/ndiswrapper-1.59/driver
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/ntoskernel_io.o
In file included from /media/lunaphiles/1G/ndiswrapper-1.59/driver/ntoskernel_io.c:16:0:
/media/lunaphiles/1G/ndiswrapper-1.59/driver/ntoskernel_io.c:1163:28: error: redefinition of &#8216;IoUnregisterPlugPlayNotification&#8217;
 wstdcall NTSTATUS WIN_FUNC(IoUnregisterPlugPlayNotification,1) 
                            ^
/media/lunaphiles/1G/ndiswrapper-1.59/driver/ntoskernel.h:412:31: note: in definition of macro &#8216;WIN_FUNC&#8217;
 #define WIN_FUNC(name, argc) (name)
                               ^
/media/lunaphiles/1G/ndiswrapper-1.59/driver/ntoskernel_io.c:1132:28: note: previous definition of &#8216;IoUnregisterPlugPlayNotification&#8217; was here
 wstdcall NTSTATUS WIN_FUNC(IoUnregisterPlugPlayNotification,1)
                            ^
/media/lunaphiles/1G/ndiswrapper-1.59/driver/ntoskernel.h:412:31: note: in definition of macro &#8216;WIN_FUNC&#8217;
 #define WIN_FUNC(name, argc) (name)
                               ^
make[3]: *** [/media/lunaphiles/1G/ndiswrapper-1.59/driver/ntoskernel_io.o] Error 1
make[2]: *** [_module_/media/lunaphiles/1G/ndiswrapper-1.59/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/media/lunaphiles/1G/ndiswrapper-1.59/driver'
make: *** [driver] Error 2
lunaphiles@SecularCircus:/media/lunaphiles/1G/ndiswrapper-1.59$ sudo make install
make -C driver install
make[1]: Entering directory `/media/lunaphiles/1G/ndiswrapper-1.59/driver'
mkdir -p -m 755 /lib/modules/3.13.0-24-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/3.13.0-24-generic/misc
/sbin/depmod -a 3.13.0-24-generic
make[1]: Leaving directory `/media/lunaphiles/1G/ndiswrapper-1.59/driver'
make -C utils install
make[1]: Entering directory `/media/lunaphiles/1G/ndiswrapper-1.59/utils'
mkdir -p -m 755 /sbin
mkdir -p -m 755 /usr/sbin
install -m 755 loadndisdriver /sbin
install -m 755 ndiswrapper /usr/sbin
install -m 755 ndiswrapper-buginfo /usr/sbin
make[1]: Leaving directory `/media/lunaphiles/1G/ndiswrapper-1.59/utils'
mkdir -p -m 755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
lunaphiles@SecularCircus:/media/lunaphiles/1G/ndiswrapper-1.59$ cd ..
lunaphiles@SecularCircus:/media/lunaphiles/1G$ cd broadcom
lunaphiles@SecularCircus:/media/lunaphiles/1G/broadcom$ ndiswrapper -i bcmn43xx64.inf
couldn't create /etc/ndiswrapper: Permission denied at /usr/sbin/ndiswrapper line 129.
lunaphiles@SecularCircus:/media/lunaphiles/1G/broadcom$ ndiswrapper -l
ls: cannot access /etc/ndiswrapper: No such file or directory
lunaphiles@SecularCircus:/media/lunaphiles/1G/broadcom$ sudo ndiswrapper -i bcmn43xx64.inf
couldn't find SourceDisksFiles section - continuing anyway...
installing bcmn43xx64 ...
lunaphiles@SecularCircus:/media/lunaphiles/1G/broadcom$ ndiswrapper -l
bcmn43xx64 : driver installed
	device (0846:9020) present
lunaphiles@SecularCircus:/media/lunaphiles/1G/broadcom$ sudo modprobe ndiswrapper
lunaphiles@SecularCircus:/media/lunaphiles/1G/broadcom$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
lunaphiles@SecularCircus:~$ sudo modprobe ndiswrapper
[sudo] password for lunaphiles: 
lunaphiles@SecularCircus:~$ dmesg | grep ndis
[  248.645842] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[  248.648438] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  248.983309] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[  249.514910] usbcore: registered new interface driver ndiswrapper
lunaphiles@SecularCircus:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lunaphiles@SecularCircus:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             disconnected
  Default:           no
  HW Address:        10:0D:7F:32:B1:74

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    belkin.a74:      Infra, 08:86:3B:7E:0A:74, Freq 2462 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    DC40B3:          Infra, 84:1B:5E:DC:40:B2, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    CBD050:          Infra, 04:A1:51:CB:D0:4F, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    2A5490:          Infra, 4C:60:DE:2A:54:8F, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA2
    IVAN:            Infra, E0:46:9A:7A:1F:0A, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA2
    butt:            Infra, C0:C1:C0:B8:9F:8C, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    50B3B4:          Infra, 74:44:01:50:B3:B3, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    linksys-madina:  Infra, 00:22:6B:52:55:CB, Freq 2452 MHz, Rate 54 Mb/s, Strength 80 WEP
    dlink:           Infra, 00:21:91:13:A0:F9, Freq 2422 MHz, Rate 54 Mb/s, Strength 79
    optimumwifi:     Infra, 06:A1:51:CB:D0:51, Freq 2437 MHz, Rate 54 Mb/s, Strength 55
    butt-guest:      Infra, C0:C1:C0:B8:9F:8D, Freq 2462 MHz, Rate 54 Mb/s, Strength 40
    optimumwifi:     Infra, 92:03:D8:80:71:6A, Freq 2462 MHz, Rate 54 Mb/s, Strength 35
    186918:          Infra, 20:4E:7F:18:69:17, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    QuietCedar:      Infra, 48:F8:B3:1E:87:55, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    optimumwifi:     Infra, 22:4E:7F:18:69:18, Freq 2412 MHz, Rate 54 Mb/s, Strength 52
    QuietCedar-guest:Infra, 48:F8:B3:1E:87:57, Freq 2412 MHz, Rate 54 Mb/s, Strength 37
    E56CA2:          Infra, 04:A1:51:E5:6C:A1, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    optimumwifi:     Infra, 06:A1:51:E5:6C:A2, Freq 2437 MHz, Rate 54 Mb/s, Strength 40
    807164:          Infra, 00:03:D8:80:71:6A, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    NETGEAR33:       Infra, 74:44:01:7C:1C:4A, Freq 2417 MHz, Rate 54 Mb/s, Strength 47 WPA2
    Khan Network:    Infra, C0:C1:C0:44:E4:B2, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Khan Network-guest: Infra, C0:C1:C0:44:E4:B4, Freq 2412 MHz, Rate 54 Mb/s, Strength 32


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:26:2D:16:52:08

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


lunaphiles@SecularCircus:~$ cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
Apr 27 10:40:35 SecularCircus NetworkManager[939]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
Apr 27 10:40:35 SecularCircus NetworkManager[939]: <info> (wlan0): using WEXT for WiFi device control
Apr 27 10:40:35 SecularCircus NetworkManager[939]: <info> (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper' ifindex: 3)
Apr 27 10:40:35 SecularCircus NetworkManager[939]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 27 10:40:35 SecularCircus NetworkManager[939]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 27 10:40:35 SecularCircus NetworkManager[939]: <info> (wlan0): bringing up device.
Apr 27 10:40:35 SecularCircus NetworkManager[939]: <info> (wlan0): preparing device.
Apr 27 10:40:35 SecularCircus NetworkManager[939]: <info> (wlan0): deactivating device (reason 'managed') [2]
Apr 27 10:40:35 SecularCircus kernel: [  249.608179] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 27 10:40:35 SecularCircus kernel: [  249.608468] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 27 10:40:35 SecularCircus NetworkManager[939]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:02.1/usb1/1-1/1-1:1.0/net/wlan0, iface: wlan0)
Apr 27 10:40:35 SecularCircus NetworkManager[939]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:02.1/usb1/1-1/1-1:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Apr 27 10:40:35 SecularCircus NetworkManager[939]: <info> wpa_supplicant started
Apr 27 10:40:35 SecularCircus NetworkManager[939]: <info> (wlan0) supports 1 scan SSIDs
Apr 27 10:40:35 SecularCircus NetworkManager[939]: <warn> Trying to remove a non-existant call id.
Apr 27 10:40:35 SecularCircus NetworkManager[939]: <info> (wlan0): supplicant interface state: starting -> ready
Apr 27 10:40:35 SecularCircus NetworkManager[939]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Apr 27 10:40:35 SecularCircus NetworkManager[939]: <info> (wlan0): supplicant interface state: ready -> disconnected
Apr 27 10:40:35 SecularCircus NetworkManager[939]: <info> (wlan0) supports 1 scan SSIDs
Apr 27 10:40:45 SecularCircus NetworkManager[939]: <info> (wlan0): supplicant interface state: disconnected -> inactive
lunaphiles@SecularCircus:~$ 
```

the browser loads a page and then it has trouble.

---

### Post by chili555 on 2014-04-27
> because I thought I could access a ndiswrapper, but it did not happen;Why is that? Were you not able to hook up the ethernet and apt-get it?> make[3]: *** [/media/lunaphiles/1G/ndiswrapper-1.59/driver/ntoskernel_io.o] Error 1
make[2]: *** [_module_/media/lunaphiles/1G/ndiswrapper-1.59/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/media/lunaphiles/1G/ndiswrapper-1.59/driver'
make: *** [driver] Error 2When 'make' ends in any error, any further steps will be useless. With all the errors, etc., I am not surprised that this doesn't work.

Are you able to get a temporary wired ethernet connection?```
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndiswrapper-dkms dkms
```

---

### Post by sidewalkcynic on 2014-04-27
no temporary wired connection possible

So it looks like this time that it was the extra message at the end of the ntoskernel_io.c

```
:1132:28: note: previous definition of &#8216;IoUnregisterPlugPlayNotification&#8217; was here
 wstdcall NTSTATUS WIN_FUNC(IoUnregisterPlugPlayNotification,1)
                            ^
/media/lunaphiles/1G/ndiswrapper-1.59/driver/ntoskernel.h:412:31: note: in definition of macro &#8216;WIN_FUNC&#8217;
 #define WIN_FUNC(name, argc) (name)
```

So I remove that and re-make install ndiswrapper . . . and the same problem: browser loads a couple of pages it is familiar with and then it can't load anymore.

---

### Post by chili555 on 2014-04-27
> and re-make install ndiswrapperHow, exactly?```
make clean
make  [COLOR="#FF0000"]<--with *NO* errors[/COLOR]
sudo make install
```If not, please do.

---

### Post by sidewalkcynic on 2014-04-28
```
lunaphiles@SecularCircus:/media/lunaphiles/1G/ndiswrapper-1.59$ sudo make uninstall
[sudo] password for lunaphiles: 
rm -f /usr/share/man/man8/ndiswrapper.8
rm -f /usr/share/man/man8/loadndisdriver.8
make -C driver uninstall
make[1]: Entering directory `/media/lunaphiles/1G/ndiswrapper-1.59/driver'
rm -f /lib/modules/3.13.0-24-generic/misc/ndiswrapper.ko
/sbin/depmod -a 3.13.0-24-generic
make[1]: Leaving directory `/media/lunaphiles/1G/ndiswrapper-1.59/driver'
make -C utils uninstall
make[1]: Entering directory `/media/lunaphiles/1G/ndiswrapper-1.59/utils'
rm -f /sbin/loadndisdriver
rm -f /usr/sbin/ndiswrapper
rm -f /usr/sbin/ndiswrapper-buginfo
make[1]: Leaving directory `/media/lunaphiles/1G/ndiswrapper-1.59/utils'
lunaphiles@SecularCircus:/media/lunaphiles/1G/ndiswrapper-1.59$ sudo make clean
make -C driver clean
make[1]: Entering directory `/media/lunaphiles/1G/ndiswrapper-1.59/driver'
rm -f *.o *.ko .*.cmd *.mod.c *.symvers modules.order *~ .\#*
rm -f *_exports.h win2lin_stubs.h
rm -rf .tmp_versions
make[1]: Leaving directory `/media/lunaphiles/1G/ndiswrapper-1.59/driver'
make -C utils clean
make[1]: Entering directory `/media/lunaphiles/1G/ndiswrapper-1.59/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/media/lunaphiles/1G/ndiswrapper-1.59/utils'
rm -f *~
rm -fr ndiswrapper-1.59 ndiswrapper-1.59.tar.gz patch-stamp
lunaphiles@SecularCircus:/media/lunaphiles/1G/ndiswrapper-1.59$ sudo make
make -C utils
make[1]: Entering directory `/media/lunaphiles/1G/ndiswrapper-1.59/utils'
gcc -g -Wall -I../driver  -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/media/lunaphiles/1G/ndiswrapper-1.59/utils'
make -C driver
make[1]: Entering directory `/media/lunaphiles/1G/ndiswrapper-1.59/driver'
make -C /usr/src/linux-headers-3.13.0-24-generic M=/media/lunaphiles/1G/ndiswrapper-1.59/driver
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  LD      /media/lunaphiles/1G/ndiswrapper-1.59/driver/built-in.o
  MKEXPORT /media/lunaphiles/1G/ndiswrapper-1.59/driver/crt_exports.h
  MKEXPORT /media/lunaphiles/1G/ndiswrapper-1.59/driver/hal_exports.h
  MKEXPORT /media/lunaphiles/1G/ndiswrapper-1.59/driver/ndis_exports.h
  MKEXPORT /media/lunaphiles/1G/ndiswrapper-1.59/driver/ntoskernel_exports.h
  MKEXPORT /media/lunaphiles/1G/ndiswrapper-1.59/driver/ntoskernel_io_exports.h
  MKEXPORT /media/lunaphiles/1G/ndiswrapper-1.59/driver/rtl_exports.h
  MKEXPORT /media/lunaphiles/1G/ndiswrapper-1.59/driver/usb_exports.h
  MKSTUBS /media/lunaphiles/1G/ndiswrapper-1.59/driver/win2lin_stubs.h
  CC [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/crt.o
  CC [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/hal.o
  CC [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/iw_ndis.o
  CC [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/loader.o
  CC [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/ndis.o
  CC [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/ntoskernel.o
  CC [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/ntoskernel_io.o
  CC [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/pe_linker.o
  CC [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/pnp.o
  CC [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/proc.o
  CC [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/rtl.o
  CC [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/wrapmem.o
  CC [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/wrapndis.o
  CC [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/wrapper.o
  CC [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/usb.o
  AS [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/win2lin_stubs.o
  AS [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/lin2win.o
  LD [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /media/lunaphiles/1G/ndiswrapper-1.59/driver/ndiswrapper.mod.o
  LD [M]  /media/lunaphiles/1G/ndiswrapper-1.59/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make[1]: Leaving directory `/media/lunaphiles/1G/ndiswrapper-1.59/driver'
lunaphiles@SecularCircus:/media/lunaphiles/1G/ndiswrapper-1.59$ sudo make install
make -C driver install
make[1]: Entering directory `/media/lunaphiles/1G/ndiswrapper-1.59/driver'
mkdir -p -m 755 /lib/modules/3.13.0-24-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/3.13.0-24-generic/misc
/sbin/depmod -a 3.13.0-24-generic
make[1]: Leaving directory `/media/lunaphiles/1G/ndiswrapper-1.59/driver'
make -C utils install
make[1]: Entering directory `/media/lunaphiles/1G/ndiswrapper-1.59/utils'
mkdir -p -m 755 /sbin
mkdir -p -m 755 /usr/sbin
install -m 755 loadndisdriver /sbin
install -m 755 ndiswrapper /usr/sbin
install -m 755 ndiswrapper-buginfo /usr/sbin
make[1]: Leaving directory `/media/lunaphiles/1G/ndiswrapper-1.59/utils'
mkdir -p -m 755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
lunaphiles@SecularCircus:/media/lunaphiles/1G/ndiswrapper-1.59$ ndiswrapper -l
bcmn43xx64 : driver installed
	device (0846:9020) present
lunaphiles@SecularCircus:/media/lunaphiles/1G/ndiswrapper-1.59$ sudo modprobe ndiswrapper
lunaphiles@SecularCircus:/media/lunaphiles/1G/ndiswrapper-1.59$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
```
lunaphiles@SecularCircus:~$ dmesg | grep ndis
[  147.872263] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[  147.874855] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  148.176455] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[  148.709391] usbcore: registered new interface driver ndiswrapper
lunaphiles@SecularCircus:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"dlink"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:21:91:13:A0:F9   
          Bit Rate=117 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:24594   Missed beacon:0

lunaphiles@SecularCircus:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [dlink] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        10:0D:7F:32:B1:74

  Capabilities:
    Speed:           117 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    DC40B3:          Infra, 84:1B:5E:DC:40:B2, Freq 2437 MHz, Rate 54 Mb/s, Strength 85 WPA WPA2
    belkin.a74:      Infra, 08:86:3B:7E:0A:74, Freq 2462 MHz, Rate 54 Mb/s, Strength 82 WPA WPA2
    2A5490:          Infra, 4C:60:DE:2A:54:8F, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2
    CBD050:          Infra, 04:A1:51:CB:D0:4F, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    NETGEAR33:       Infra, 74:44:01:7C:1C:4A, Freq 2417 MHz, Rate 54 Mb/s, Strength 49 WPA2
    807164:          Infra, 00:03:D8:80:71:6A, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    835A24:          Infra, 00:03:D8:83:5A:2A, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    butt:            Infra, C0:C1:C0:B8:9F:8C, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    linksys-madina:  Infra, 00:22:6B:52:55:CB, Freq 2452 MHz, Rate 54 Mb/s, Strength 74 WEP
    optimumwifi:     Infra, 06:A1:51:CB:D0:51, Freq 2437 MHz, Rate 54 Mb/s, Strength 59
    optimumwifi:     Infra, 22:4E:7F:18:69:18, Freq 2412 MHz, Rate 54 Mb/s, Strength 55
    optimumwifi:     Infra, 92:03:D8:83:5A:2A, Freq 2437 MHz, Rate 54 Mb/s, Strength 40
    optimumwifi:     Infra, 06:A1:51:E5:6C:A2, Freq 2437 MHz, Rate 54 Mb/s, Strength 40
    butt-guest:      Infra, C0:C1:C0:B8:9F:8D, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    *dlink:          Infra, 00:21:91:13:A0:F9, Freq 2422 MHz, Rate 54 Mb/s, Strength 70
    IVAN:            Infra, E0:46:9A:7A:1F:0A, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA2
    186918:          Infra, 20:4E:7F:18:69:17, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    E56CA2:          Infra, 04:A1:51:E5:6C:A1, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    50B3B4:          Infra, 74:44:01:50:B3:B3, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    QuietCedar:      Infra, 48:F8:B3:1E:87:55, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    optimumwifi:     Infra, 92:03:D8:80:71:6A, Freq 2462 MHz, Rate 54 Mb/s, Strength 42

  IPv4 Settings:
    Address:         192.168.0.187
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:26:2D:16:52:08

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


lunaphiles@SecularCircus:~$ cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <info> NetworkManager state is now CONNECTED_GLOBAL
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <info> Policy set 'dlink' (wlan0) as default for IPv4 routing and DNS.
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <info> DNS: starting dnsmasq...
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <warn> dnsmasq not available on the bus, can't update servers.
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <error> [1398684101.708598] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <warn> DNS: plugin dnsmasq update failed
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <info> Writing DNS information to /sbin/resolvconf
Apr 28 07:21:41 SecularCircus avahi-daemon[801]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::120d:7fff:fe32:b174.
Apr 28 07:21:41 SecularCircus avahi-daemon[801]: New relevant interface wlan0.IPv6 for mDNS.
Apr 28 07:21:41 SecularCircus avahi-daemon[801]: Registering new address record for fe80::120d:7fff:fe32:b174 on wlan0.*.
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <info> Activation (wlan0) successful, device activated.
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <warn> dnsmasq appeared on DBus: :1.112
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <info> Writing DNS information to /sbin/resolvconf
Apr 28 07:22:00 SecularCircus NetworkManager[1019]: <info> (wlan0): IP6 addrconf timed out or failed.
Apr 28 07:22:00 SecularCircus NetworkManager[1019]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 28 07:22:00 SecularCircus NetworkManager[1019]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 28 07:22:00 SecularCircus NetworkManager[1019]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
lunaphiles@SecularCircus:~$ 
```
same problem - loads a page or two and then quits loading

---

### Post by chili555 on 2014-04-28
Please see:```
 <error> [1398684101.708598] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
```And also:> Note that the package "dnsmasq" interferes with Network Manager which can use "dnsmasq-base" to provide DHCP services when sharing an internet connection. Therefore, if you use network manager (fine in simple set-ups only), then install dnsmasq-base, but not dnsmasq. If you have a more complicated set-up, uninstall network manager, use dnsmasq, or similar software (bind9, dhcpd, etc), and configure things by hand.Which do you have installed?```
sudo dpkg -s dnsmasq | grep -i install
sudo dpkg -s dnsmasq-base | grep -i install
```If you have dnsmasq installed, please remove it:```
sudo apt-get purge dnsmasq
```If you do not have dnsmasq-base installed, please install it:```
sudo apt-get install dnsmasq-base
```I am concentrating on DNS because your logs show the error I quoted and also show no sign of disconnecting or similar distress. 

Have you checked the settings in Firefox? Does the system continue to ping even after it stops pulling web pages?```
ping -c10 www.google.com
```Your ndiswrapper redo looks just perfect!

---

### Post by sidewalkcynic on 2014-04-28
```
lunaphiles@SecularCircus:~$ sudo dpkg -s dnsmasq | grep -i install
[sudo] password for lunaphiles: 
dpkg-query: package 'dnsmasq' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
lunaphiles@SecularCircus:~$ sudo dpkg -s dnsmasq-base | grep -i install
Status: install ok installed
Installed-Size: 648
 that, install the dnsmasq package.
lunaphiles@SecularCircus:~$ ping -c10 www.google.com
ping: unknown host www.google.com
lunaphiles@SecularCircus:~$ 
```

---

### Post by chili555 on 2014-04-28
Excellent. What does this say?```
ping -c3 74.125.225.241
ping -c3 8.8.8.8
```

---

### Post by sidewalkcynic on 2014-04-28
```
lunaphiles@SecularCircus:~$ ping -c 74.125.225.241
Usage: ping [-aAbBdDfhLnOqrRUvV] [-c count] [-i interval] [-I interface]
            [-m mark] [-M pmtudisc_option] [-l preload] [-p pattern] [-Q tos]
            [-s packetsize] [-S sndbuf] [-t ttl] [-T timestamp_option]
            [-w deadline] [-W timeout] [hop1 ...] destination
lunaphiles@SecularCircus:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.0.187 icmp_seq=1 Destination Host Unreachable
From 192.168.0.187 icmp_seq=2 Destination Host Unreachable
From 192.168.0.187 icmp_seq=3 Destination Host Unreachable

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
pipe 3
lunaphiles@SecularCircus:~$ 


```
I just ran the first with the proper "-c3" and it gave the same statistics as the second string

---

### Post by chili555 on 2014-04-28
ping -c**[COLOR="#FF0000"]3[/COLOR]** 74.125.225.241> lunaphiles@SecularCircus:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.0.187 icmp_seq=1 Destination Host UnreachableCan you even ping the router??```
ping -c3 192.168.0.1
```If not, the connection has dropped and what shows in the log?```
cat /var/log/syslog | grep etwork | tail -n20
```

---

### Post by sidewalkcynic on 2014-04-28
```
lunaphiles@SecularCircus:~$ ping -c3 192.168.0.187
PING 192.168.0.187 (192.168.0.187) 56(84) bytes of data.
64 bytes from 192.168.0.187: icmp_seq=1 ttl=64 time=0.044 ms
64 bytes from 192.168.0.187: icmp_seq=2 ttl=64 time=0.053 ms
64 bytes from 192.168.0.187: icmp_seq=3 ttl=64 time=0.054 ms

--- 192.168.0.187 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.044/0.050/0.054/0.007 ms
lunaphiles@SecularCircus:~$ cat /var/log/syslog | grep etwork | tail -n20
Apr 28 07:21:40 SecularCircus NetworkManager[1019]: <info>   nameserver '192.168.0.1'
Apr 28 07:21:40 SecularCircus NetworkManager[1019]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr 28 07:21:40 SecularCircus NetworkManager[1019]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <info> NetworkManager state is now CONNECTED_GLOBAL
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <info> Policy set 'dlink' (wlan0) as default for IPv4 routing and DNS.
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <info> DNS: starting dnsmasq...
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <warn> dnsmasq not available on the bus, can't update servers.
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <error> [1398684101.708598] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <warn> DNS: plugin dnsmasq update failed
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <info> Writing DNS information to /sbin/resolvconf
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <info> Activation (wlan0) successful, device activated.
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <warn> dnsmasq appeared on DBus: :1.112
Apr 28 07:21:41 SecularCircus NetworkManager[1019]: <info> Writing DNS information to /sbin/resolvconf
Apr 28 07:22:00 SecularCircus NetworkManager[1019]: <info> (wlan0): IP6 addrconf timed out or failed.
Apr 28 07:22:00 SecularCircus NetworkManager[1019]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 28 07:22:00 SecularCircus NetworkManager[1019]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 28 07:22:00 SecularCircus NetworkManager[1019]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
```

Does that error need the special script at the end of the ntoskernal_io.c that I found before.

---

### Post by chili555 on 2014-04-28
> ping -c3 192.168.0.187What?? I thought the router was 192.168.0.1:>  IPv4 Settings:
    Address:         192.168.0.187
    Prefix:          24 (255.255.255.0)
    [COLOR="#FF0000"]Gateway:         192.168.0.1[/COLOR]

    DNS:             192.168.0.1If you pinged x.187, you just pinged yourself. You knocked on your own front door to see if you were at home and found out that you were!

---

### Post by sidewalkcynic on 2014-04-28
> **chili555 said:**
> What?? I thought the router was 192.168.0.1they gave the +3 error as the previous, so I tried

```
unaphiles@SecularCircus:~$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.187 icmp_seq=1 Destination Host Unreachable
From 192.168.0.187 icmp_seq=2 Destination Host Unreachable
From 192.168.0.187 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
pipe 3
```

---

### Post by sidewalkcynic on 2014-04-28
I just rechecked my neighborhood library, and they do not have a public network connection. I'll check the outer neighborhood branches this afternoon. I'm sure I have seen connections in the past, but they may have dismantled them. This is a small enough desktop, and I have seen people with home monitors in the library - so I can handle the embarrassment.

---

### Post by aaron_h2 on 2014-05-19
Hey, sorry for the slight necro, but seeing as I was able to get this far through your help, maybe you could help me finish this up.

After a few attempts, I was able to get linux to recognize the device. My problem, however, is that I can't authenticate. I am trying to conect to a WPA2. I know my password is correct.

arch:
```
x86_64
```

lsusb:
```
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 1532:0016 Razer USA, Ltd DeathAdder Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

ndiswrapper -l:
```
bcmn43xx64 : driver installed
    device (0846:9020) present

```

iwconfig:
```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Bit Rate:144 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

dmesg | grep ndis:
```
[   15.088867] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   15.460438] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   15.713981] usbcore: registered new interface driver ndiswrapper
[   80.292562] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  140.616858] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  290.037280] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  353.591711] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  403.502405] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  541.225705] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  589.815343] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  699.393283] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  726.775924] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[ 1276.993987] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[ 2090.556046] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[ 2161.593419] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[ 2483.758825] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)

```

I am guessing it is 'setting configuration failed'.

I used the bcmn43xx64.inf from post 89

Any help would be appreciated. This is my second stab at linux, quiting the first time due to an inability setting up wireless.

---

### Post by chili555 on 2014-05-20
This is probably the toughest device to get going in all of Linux! You can Google results reporting it works perfectly and that it never works, no way and no how. Some report the v2 files work; some report the v2_amended work. I'd certainly try the v2_amended: [https://dl.dropboxusercontent.com/u/58267392/Broadcom_bcm43xx_USB_32_64bit_v2_amended.zip](https://dl.dropboxusercontent.com/u/58267392/Broadcom_bcm43xx_USB_32_64bit_v2_amended.zip)

The fact that there are wildly varying results makes me wonder if there may be a router issue here. First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit 0, add the line:```
iw reg set IS
```Proofread carefully, save and close gedit.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Of course, you could also spend US$12-15 and get a fully supported USB wireless and be done!

---

### Post by steve134 on 2014-06-18
I am also having this problem. When I was young i used linux, but its been a while and i have lost it all. I have ran through this whole thread as well as a couple others. 
running Kubuntu 14.04. 
Netgear WNA3100

Here is some information 

wconfig: 
lo        no wireless extensions.


eth0      no wireless extensions.


usb0      no wireless extensions.


lsusb: 
Bus 002 Device 005: ID 04f3:01a4 Elan Microelectronics Corp. Wireless Keyboard
Bus 002 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 007: ID 0fca:8012 Research In Motion, Ltd. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 0e8d:1887 MediaTek Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

arch: 
i686

dmesg | grep ndis
[   17.469458] rndis_host 2-1.2:1.0: rndis media connect
[   17.493576] rndis_host 2-1.2:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.0-1.2, RNDIS device, 42:6f:2a:f5:2c:cd
[   17.493695] usbcore: registered new interface driver rndis_host
[   17.606443] usbcore: registered new interface driver rndis_wlan
[  409.571845] rndis_host 2-1.2:1.0 usb0: unregister 'rndis_host' usb-0000:00:1d.0-1.2, RNDIS device
[  411.415778] rndis_host 2-1.2:1.0: rndis media connect
[  411.440836] rndis_host 2-1.2:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.0-1.2, RNDIS device, 42:6f:2a:f5:2c:cd

if anyone could help it would be much appriciated

Steve

---

### Post by chili555 on 2014-06-18
> **steve134 said:**
> if anyone could help it would be much appriciated

SteveI assume you read my post just above. 

First, load the module:```
sudo modprobe ndiswrapper
```Any errors, complaints, etc.? Check for clues in the log:```
dmesg | grep ndis
iwconfig
```Once we have more information, we'll proceed.

---

### Post by joe7dust on 2014-10-18
I have followed the steps in this thread and my N300 is still not working in ubuntu. This error may make more sense to someone else here.

dmesg | grep ndis
[   36.089567] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel[   36.129476] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   42.225733] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[   43.618720] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[   43.619108] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   43.634338] ndiswrapper (mp_halt:254): device f69c6500 is not initialized - not halting
[   43.634640] ndiswrapper: device eth%d removed
[   43.646083] ndiswrapper: probe of 1-1:1.0 failed with error -22
[   43.665211] usbcore: registered new interface driver ndiswrapper
[ 2051.791671] usbcore: deregistering interface driver ndiswrapper
[ 2062.373278] module: ndiswrapper: Unknown relocation: 0

When I run modprobe ndiswrapper it says "could not insert 'ndiswrapper': Exec format error

More info: 

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by jeremy31 on 2014-10-18
> **joe7dust said:**
> I have followed the steps in this thread and my N300 is still not working in ubuntu. This error may make more sense to someone else here.

dmesg | grep ndis
[   36.089567] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel[   36.129476] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   42.225733] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[   43.618720] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[   43.619108] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   43.634338] ndiswrapper (mp_halt:254): device f69c6500 is not initialized - not halting
[   43.634640] ndiswrapper: device eth%d removed
[   43.646083] ndiswrapper: probe of 1-1:1.0 failed with error -22
[   43.665211] usbcore: registered new interface driver ndiswrapper
[ 2051.791671] usbcore: deregistering interface driver ndiswrapper
[ 2062.373278] module: ndiswrapper: Unknown relocation: 0

When I run modprobe ndiswrapper it says "could not insert 'ndiswrapper': Exec format error

More info: 

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Do you have any other options for wifi?  Maybe an internal wifi slot that could be used with a card supported by linux?

I have a very similar device, if not the exact same and the performance with ndiswrapper is less than stellar.  Check ```
lsusb
```  My device is as follows ```
Bus 003 Device 053: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
```

---

### Post by joe7dust on 2014-10-18
I have the exact same card you have. Can you please help me get ndiswrapper to work with it? Performance doesn't have to be great, this is my only option.

---

### Post by jeremy31 on 2014-10-18
Well you need to download and extract this file [http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz)
and then [code]sudo apt-get install ndisgtk[code]  Then look for a windows wlan program in your programs, once you run it you can choose to install driver and find location you extracted the Broadcom bcm43xx file and then everything should be automatic

---

### Post by veji on 2014-11-15
lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1267:0201 Logic3 / SpectraVideo plc A4Tech SWOP-3 Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
sudo modprobe ndiswrapper

dmesg | grep ndis
[   13.266577] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   13.267254] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   13.789489] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   13.789494] ndiswrapper (load_sys_files:200): couldn't prepare driver 'bcmn43xx32'
[   13.789837] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmn43xx32; check system log for messages from 'loadndisdriver'
[   13.789884] usbcore: registered new interface driver ndiswrapper


I've been working on this for so long now, that i'm prolly gonna need an 80's montage soon!  I've followed various threads to get Linux Mint 17 and the N300 adapater to work, but nothing is working.  I've installed every possible-related package there is and have tried over 4-5 various drivers, including my extracted Windows INF.

I was HOPING that Linux had changed from 10 years ago, when i had similar hardware issues, but i guess theres just no changing the fact that it will always have driver issues.  /sadpanda

---

### Post by chili555 on 2014-11-15
> I was HOPING that Linux had changed from 10 years ago, when i had similar hardware issues, but i guess theres just no changing the fact that it will always have driver issues.SLIGHTLY OFF-TOPIC EDITORIAL

Linux will, indeed, always have driver issues, but for several reasons that may not be apparent to all of us. First, new devices are developed and released every day. The manufacturers are in a constant arms race to have a better device with more features and, often, cheaper. In almost every case, they have no concern for the 1-2% of Linux users and therefor don't provide a working driver.

Second, most new Linux users come to the party with what they have now that they bought with working Windows drivers. That device may work well or not at all in Linux. Experienced Linux users always check the forums and are sure the device works in Linux. Mrs. Chili hates it when we walk through the store and I make remarks about items in the computer department; "Those Netgears are tricky even in ndiswrapper."

In your case, veji, the answer is in the log, as problems often are.> ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010BYou loaded bcmn43xx32 but, since you have a 64-bit system, you need bcmn43xx**64**. Erase the file you have now:```
sudo ndiswrapper -e bcmn43xx32
sudo rm -rf /etc/ndiswrapper/*
```Now load the 64-bit file from here: [http://ubuntuforums.org/showthread.php?t=1695036&page=9&p=11838453#post11838453](http://ubuntuforums.org/showthread.php?t=1695036&page=9&p=11838453#post11838453)

---

### Post by ray18 on 2014-11-29
Hello every one, I got one for the Savvys 
I have installed the drivers and the lsubs -l does list the NetGear addapter
in the Windows Wireless Drivers app, it does get the driver as installed
Why is it not connecting to ubuntu? I cant seem to get it detected by the OS

---

### Post by jeremy31 on 2014-11-29
Post terminal results from ```
uname -a
``````
lsusb
``` As there are quite a few of these adapters using different chipsets

---

