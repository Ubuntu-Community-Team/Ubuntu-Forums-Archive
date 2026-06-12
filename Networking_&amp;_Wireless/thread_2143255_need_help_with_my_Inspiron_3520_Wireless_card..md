---
title: "need help with my Inspiron 3520 Wireless card."
date: 2013-05-08
forum: Networking &amp; Wireless
---

### Post by komrad3006 on 2013-05-08
Hi there, I installed U.Studio 13.04 today and it show my proprietery driver is in use but still not read wireless networks, but does read a wired connection.

[[http://i1351.photobucket.com/albums/p794/Komrad3006/wirelssdirver_zpsec8cd2ad.png](http://i1351.photobucket.com/albums/p794/Komrad3006/wirelssdirver_zpsec8cd2ad.png)]("http://s1351.photobucket.com/user/Komrad3006/media/wirelssdirver_zpsec8cd2ad.png.html")

i have tried numberous task from different website i found like

```


sudo apt-get remove bcmwl-kernel-source 
sudo apt-get install bcmwl-kernel-source


```

and even did

```


Please verify your pci.id with a terminal command:

  
    lspci -nn   Is it 14e4:4365? I am not sure it is even possible in a 32-bit  system. If you have a 64-bit system and the device I mentioned, then I  suggest this package: [http://jas.gemnetworks.com/debian/pool/main/w/wireless-bcm43142/wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb](http://jas.gemnetworks.com/debian/pool/main/w/wireless-bcm43142/wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb)
  First install the prerequisites:
  
    sudo apt-get install linux-headers-generic build-essential dkms   Then install the package with:
  
    cd Desktop   <--or wherever you downloaded the deb    
    sudo dpkg -i wire*.deb    
    sudo modprobe wl


``` 

the 
```


sudo modprobe wl


```

gives me this 

```


FATAL: Module wl not found.


```

and my lspci -nn

```


komrad@krash-LT:~$ lspci -vvnn | grep 14e4
07:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)


```

---

### Post by chili555 on 2013-05-08
Please try:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-headers-generic
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```Any improvement?

---

### Post by komrad3006 on 2013-05-08
> **chili555 said:**
> Please try:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-headers-generic
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```Any improvement?

nope here is what i got:

```

komrad@krash-LT:~$ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for komrad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-lowlatency linux-image-lowlatency
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 4,279 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 241791 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-19-lowlatency

```

```

komrad@krash-LT:~$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-lowlatency linux-image-lowlatency
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
komrad@krash-LT:~$ 

```

```

komrad@krash-LT:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-lowlatency linux-image-lowlatency
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,346 kB of archives.
After this operation, 4,279 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  bcmwl-kernel-source
Install these packages without verification [y/N]? y
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 241724 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_amd64.deb) ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu6) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-19-lowlatency
Building for architecture x86_64
Building initial module for 3.8.0-19-lowlatency
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module>
    import apport
ImportError: No module named apport
Error! Bad return status for module build on kernel: 3.8.0-19-lowlatency (x86_64)
Consult /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log for more information.
FATAL: Module wl not found.    <----------------------------------------------------------------------------------noticed that still shows up
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-19-lowlatency


```

```

komrad@krash-LT:~$ sudo modprobe wl
FATAL: Module wl not found.

```

I dont know, i wana say it was working fine before my computer was going whack.  12.10 it worked fine when i follow the steps above.

---

### Post by komrad3006 on 2013-05-08
i just ran
```

$ sudo lshw -C network

```

and got

```

komrad@krash-LT:~$ sudo lshw -C network
[sudo] password for komrad: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7c00000-f7c07fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 05
       serial: e0:db:55:82:3c:b8
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.8 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
komrad@krash-LT:~$ 

```

idk if it being unclaimed has anything to do with it?

---

### Post by chili555 on 2013-05-08
> **komrad3006 said:**
> idk if it being unclaimed has anything to do with it?Unclaimed, in this context, means no driver claims it. wl can't claim it because it won't yet build correctly:> Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module>
    import apport
ImportError: No module named apport
[COLOR="#FF0000"]Error! Bad return status for module build on kernel: 3.8.0-19-lowlatency [/COLOR](x86_64)
Consult /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log for more information.Please try:```
sudo apt-get install python-apport
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```How about now?

---

### Post by komrad3006 on 2013-05-12
> **chili555 said:**
> Unclaimed, in this context, means no driver claims it. wl can't claim it because it won't yet build correctly:Please try:```
sudo apt-get install python-apport
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```How about now?

if i do all this from live usb it should still work unless i shutdown or restart right?  this was ran from backbox but even when i run in studio i get same exact messages. Here is what i type and the results, in order:

```
sudo apt-get install python-apport
```
i get
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-apport is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Duplicate sources.list entry cdrom://BackBox Linux 3.0/ precise/main i386 Packages (/var/lib/apt/lists/BackBox%20Linux%203.0_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://BackBox Linux 3.0/ precise/multiverse i386 Packages (/var/lib/apt/lists/BackBox%20Linux%203.0_dists_precise_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://BackBox Linux 3.0/ precise/restricted i386 Packages (/var/lib/apt/lists/BackBox%20Linux%203.0_dists_precise_restricted_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://BackBox Linux 3.0/ precise/universe i386 Packages (/var/lib/apt/lists/BackBox%20Linux%203.0_dists_precise_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

```
sudo apt-get install linux-headers-generic
```
i get
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Duplicate sources.list entry cdrom://BackBox Linux 3.0/ precise/main i386 Packages (/var/lib/apt/lists/BackBox%20Linux%203.0_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://BackBox Linux 3.0/ precise/multiverse i386 Packages (/var/lib/apt/lists/BackBox%20Linux%203.0_dists_precise_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://BackBox Linux 3.0/ precise/restricted i386 Packages (/var/lib/apt/lists/BackBox%20Linux%203.0_dists_precise_restricted_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://BackBox Linux 3.0/ precise/universe i386 Packages (/var/lib/apt/lists/BackBox%20Linux%203.0_dists_precise_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

```
sudo apt-get install bcmwl-kernel-source
```
i get
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms
The following NEW packages will be installed:
  bcmwl-kernel-source dkms
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,224 kB of archives.
After this operation, 3,862 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
W: Duplicate sources.list entry cdrom://BackBox Linux 3.0/ precise/main i386 Packages (/var/lib/apt/lists/BackBox%20Linux%203.0_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://BackBox Linux 3.0/ precise/multiverse i386 Packages (/var/lib/apt/lists/BackBox%20Linux%203.0_dists_precise_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://BackBox Linux 3.0/ precise/restricted i386 Packages (/var/lib/apt/lists/BackBox%20Linux%203.0_dists_precise_restricted_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://BackBox Linux 3.0/ precise/universe i386 Packages (/var/lib/apt/lists/BackBox%20Linux%203.0_dists_precise_universe_binary-i386_Packages)
Selecting previously unselected package dkms.
(Reading database ... 146600 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Selecting previously unselected package bcmwl-kernel-source.
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6.1_amd64.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6.1) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-36-generic
Building for architecture x86_64
Building initial module for 3.2.0-36-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-36-generic/updates/dkms/

depmod.....

DKMS: install completed.
update-initramfs is disabled since running on read-only media
W: Duplicate sources.list entry cdrom://BackBox Linux 3.0/ precise/main i386 Packages (/var/lib/apt/lists/BackBox%20Linux%203.0_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://BackBox Linux 3.0/ precise/multiverse i386 Packages (/var/lib/apt/lists/BackBox%20Linux%203.0_dists_precise_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://BackBox Linux 3.0/ precise/restricted i386 Packages (/var/lib/apt/lists/BackBox%20Linux%203.0_dists_precise_restricted_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://BackBox Linux 3.0/ precise/universe i386 Packages (/var/lib/apt/lists/BackBox%20Linux%203.0_dists_precise_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

```
sudo modprobe wl
```
i get
```

FATAL: Error inserting wl (/lib/modules/3.2.0-36-generic/updates/dkms/wl.ko): Invalid argument

```

---

### Post by komrad3006 on 2013-05-12
ok, so i went ahead and installed backbox. Everything went so smooth went to install all the steps above and the only thing that was the same was the "sudo modprobe wl"  i checked my additional drivers and here is what it shows?

****EDIT***
Ok so i found this post that you were in Chili555.  [http://ubuntuforums.org/showthread.php?t=2052124](http://ubuntuforums.org/showthread.php?t=2052124)  

I followed the steps deleted all the "linux-backports-modules-cw"

restarted computer and it is now closer then it was before, it is now ready my card but still disabled.  another screen shot:
[[http://i1351.photobucket.com/albums/p794/Komrad3006/network_zpsbc886275.png](http://i1351.photobucket.com/albums/p794/Komrad3006/network_zpsbc886275.png)](http://s1351.photobucket.com/user/Komrad3006/media/network_zpsbc886275.png.html)

---

### Post by komrad3006 on 2013-05-12
LMAO, ok so i feel smart after posting that i push "FN" + "F2" and it enabled my wireless. i restarted computer and unpluged my cable and here i am posting from my wireless connection,  thank you so much for all your help.

i tried to mark as solved, thread tools only shows, print, email, and subscribe?

---

### Post by chili555 on 2013-05-12
Awesome! Glad it's working!

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by wildmanne39 on 2013-05-13
Hi, please use thumbnails or url's for images because many people have a slow connection and large images make it very hard for them to load the page.
Thanks

---

