---
title: "Broadcom 802.11 Linux STA wireless driver problem?"
date: 2013-02-01
forum: Networking &amp; Wireless
---

### Post by WaNaBePi on 2013-02-01
Hello forums.

I'm on 12.04.1.

It's 64 bit

My problem is that I can't connect to wireless Internet.

I can see networks fine.

I can connect ONLY with a Ethernet cord.

This all started when I did some upgrade, something like "wireless driver update" (the most recent one I would imagine). 

Ever since then I've had this problem.

Going back to an older kernal doesn't help.

I tried following various guides to no avail. 

I'm sure there are specifics that I need to show via some command, please let me know.

I can tell you that I'm on a Samsung rf510.

This is the driver for the wireless that shows up under settings:

This package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-, BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based hardware.

This used to work just fine, and seems to be half working since I can see networks.

I believe I have multiple wireless divers installed or something, but who knows.

I don't know what to do, I'm stumped.

Thank you.

---

### Post by dnr1128 on 2013-02-01
This seems to be an on going problem.  I did the same thing with my broadcom 4313, and I'm having continual ongoing problems, even after upgrading my system to 12.10.  

[This thread]("http://ubuntuforums.org/showthread.php?t=2111077") is the most recent problem thread.  

If you find a solution, please post it!!  :)

---

### Post by Hadaka on 2013-02-01
Hi, lets take a look at what driver you need.
please post..
```
lspci -nnk | grep AN | sed 's/Controller/PCID --->/g' | grep PCID
 
```

thanks

---

### Post by WaNaBePi on 2013-02-03
```
lspci -nnk | grep AN | sed 's/Controller/PCID --->/g' | grep PCID
default@default-laptop:~$ lspci -nnk | grep AN | sed 's/Controller/PCID --->/g' | grep PCID
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN PCID ---> [14e4:4727] (rev 01)
default@default-laptop:~$ 

```

Thank you...

---

### Post by carl4926 on 2013-02-03
Can I refer you to
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

The parts important to you are

Broadcom Corporation BCM4313 802.11b/g/n  [14e4:4727]

---

### Post by WaNaBePi on 2013-02-03
I have seen that site before and was using the driver from it, but I don't know how it got replaced or whatever.

If you could guide me through the setup that would be wonderful.

This is what I get when I use there code...
```

default@default-laptop:~$ sudo apt-get install firmware-b43-installer
[sudo] password for default: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  libgtkspell-3-0 libllvm3.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

There is defiantly a problem, I know there is a driver installed. I know its the right one, to some degree, but some setting has gotten messed up I think.

It does say "no (WIP)" under the supported section. My guess is that means wireless ip... Does that mean I'm screwed or what?

---

### Post by carl4926 on 2013-02-03
firmware-b43-installer

Will not work with your device

You need to

```
sudo apt-get remove firmware-b43-installer
```You may still have to rename the folder b43 in /lib/firmware to b43-old

```
sudo apt-get install bcmwl-kernel-source
```should install the 'wl' driver which should work

I think....

---

### Post by 23senick on 2013-02-03
There definitely seems to be some new problem with Broadcom 4313 after a recent update. I had been using the proprietary driver for months (12.04 64-bit). Then a week or so ago it just stopped connecting.  It sees the wifi networks, but will not connect to them. The wireless seems to have loaded the "wl" driver but as I say, it just won't connect.  Tried all sorts of apt-get purges and re-loads, and using "additional drivers." to do the same  

Only "solution" I have found is to purge [FONT=Arial][SIZE=2]bcmwl kernel source and un-blacklist [/SIZE][/FONT][FONT=Arial][SIZE=2]brmcsmac. This at least gives a weak wifi you can connect[SIZE=2].[/SIZE]

[SIZE=2]It woul[SIZE=2]d[/SIZE] be great if [SIZE=2]we could have some guidance from one of the f[SIZE=2]orum staff/moderators [SIZE=2]about whether there's some ge[SIZE=2]neral (and new) pro[SIZE=2]b[SIZE=2]l[SIZE=2]e[/SIZE]m with[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE] Broad[SIZE=2]com 4[SIZE=2]313 cards. [SIZE=2]They [SIZE=2]seem to be installed quite widely, so come on guys, [/SIZE][/SIZE][/SIZE][/SIZE]what about [SIZE=2]a heads up?

[SIZE=2]Or even better a [SIZE=2]ste[SIZE=2]p[/SIZE]-by-ste[SIZE=2]p[SIZE=2] guide to overcoming this new issue[SIZE=2], for existing installs.[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
[/SIZE][/SIZE][/FONT]

---

### Post by iMac71 on 2013-02-03
the following guide may help:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by mikewhatever on 2013-02-03
Check out this bug report [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809).
Comment #25 seems relevant, and offeres a workaround.

---

### Post by Hadaka on 2013-02-03
Hi, try this...post #4


```
http://ubuntuforums.org/showthread.php?t=2111181 
```

as the post suggests...copy and paste the commands.

---

### Post by 23senick on 2013-02-03
Hmm tried that without success. After restart lshw -c network showed wireless is unclaimed.  

Looking at this link [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809) (see post #25) suggests we need to revert to the old version of bcmwl-kernel-source (version 5.100.82.112). Can anyone give a step by step of how to get that?  And wouldn't it make sense for Ubuntu Software Centre to offer both?

---

### Post by Hadaka on 2013-02-03
@23senic, while the link i suggest didnt work for you, for
whatever reason, doesnt mean it wont work with WaNaBePi,
the person who originated this thread.

---

### Post by mikewhatever on 2013-02-03
> **23senick said:**
> Hmm tried that without success. After restart lshw -c network showed wireless is unclaimed.  

Looking at this link [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809) (see post #25) suggests we need to revert to the old version of bcmwl-kernel-source (version 5.100.82.112). Can anyone give a step by step of how to get that?  And wouldn't it make sense for Ubuntu Software Centre to offer both?

I've posted a step by step here [http://askubuntu.com/questions/250858/broadcom-wireless-bcm4313-on-12-04-lts/250896#250896](http://askubuntu.com/questions/250858/broadcom-wireless-bcm4313-on-12-04-lts/250896#250896)

---

### Post by WaNaBePi on 2013-02-04
Mikewhatever,

I dig the guide. Going to give it a shot in a second.

In the future, when there is an update that I do want for the wireless, how would I disable the stop upgrade?

Gave it a shot seems like it works, but I have to restart and unplug ethernet to be sure.

```
default@default-laptop:~$ sudo apt-get remove bcmwl-kernel-source
[sudo] password for default: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtkspell-3-0 libllvm3.0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 4,274 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 525331 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-37-generic
default@default-laptop:~$ sudo apt-get install bcmwl-kernel-source=5.100.82.38+bdcom-0ubuntu6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtkspell-3-0 libllvm3.0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,151 kB of archives.
After this operation, 3,514 kB of additional disk space will be used.
Err http://us.archive.ubuntu.com/ubuntu/ precise/restricted bcmwl-kernel-source amd64 5.100.82.38+bdcom-0ubuntu6
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_amd64.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
default@default-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
default@default-laptop:~$ sudo apt-get update
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://us.archive.ubuntu.com precise InRelease                             
Ign http://archive.canonical.com precise InRelease                             
Err http://security.ubuntu.com precise-security Release.gpg                    
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com precise Release.gpg                               
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Err http://us.archive.ubuntu.com precise Release.gpg                           
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.canonical.com precise Release.gpg                           
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign http://security.ubuntu.com precise-security Release                        
Ign http://extras.ubuntu.com precise Release                                   
Ign http://security.ubuntu.com precise-security/main Sources/DiffIndex         
Err http://us.archive.ubuntu.com precise-updates Release.gpg                   
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://security.ubuntu.com precise-security/restricted Sources/DiffIndex   
Ign http://security.ubuntu.com precise-security/universe Sources/DiffIndex     
Ign http://security.ubuntu.com precise-security/multiverse Sources/DiffIndex   
Ign http://security.ubuntu.com precise-security/main amd64 Packages/DiffIndex  
Ign http://security.ubuntu.com precise-security/restricted amd64 Packages/DiffIndex
Ign http://security.ubuntu.com precise-security/universe amd64 Packages/DiffIndex
Ign http://security.ubuntu.com precise-security/multiverse amd64 Packages/DiffIndex
Ign http://security.ubuntu.com precise-security/main i386 Packages/DiffIndex   
Ign http://security.ubuntu.com precise-security/restricted i386 Packages/DiffIndex
Ign http://security.ubuntu.com precise-security/universe i386 Packages/DiffIndex
Ign http://security.ubuntu.com precise-security/multiverse i386 Packages/DiffIndex
Get:1 http://security.ubuntu.com precise-security/main TranslationIndex [74 B] 
Get:2 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:3 http://security.ubuntu.com precise-security/restricted TranslationIndex [71 B]
Get:4 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:5 http://security.ubuntu.com precise-security/main Sources [62.8 kB]       
Get:6 http://security.ubuntu.com precise-security/restricted Sources [1,950 B] 
Get:7 http://security.ubuntu.com precise-security/universe Sources [20.0 kB]   
Get:8 http://security.ubuntu.com precise-security/multiverse Sources [1,379 B] 
Get:9 http://security.ubuntu.com precise-security/main amd64 Packages [225 kB] 
Get:10 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:11 http://security.ubuntu.com precise-security/universe amd64 Packages [62.7 kB]
Get:12 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,184 B]
Get:13 http://security.ubuntu.com precise-security/main i386 Packages [233 kB] 
Get:14 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:15 http://security.ubuntu.com precise-security/universe i386 Packages [64.2 kB]
Get:16 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,366 B]
Get:17 http://security.ubuntu.com precise-security/main Translation-en [110 kB]
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Hit http://us.archive.ubuntu.com precise Release                               
Get:18 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]          
Ign http://us.archive.ubuntu.com precise/main Sources/DiffIndex                
Ign http://us.archive.ubuntu.com precise/restricted Sources/DiffIndex       
Ign http://us.archive.ubuntu.com precise/universe Sources/DiffIndex            
Ign http://us.archive.ubuntu.com precise/multiverse Sources/DiffIndex          
Ign http://us.archive.ubuntu.com precise/main amd64 Packages/DiffIndex         
Ign http://us.archive.ubuntu.com precise/restricted amd64 Packages/DiffIndex   
Ign http://us.archive.ubuntu.com precise/universe amd64 Packages/DiffIndex     
Ign http://us.archive.ubuntu.com precise/multiverse amd64 Packages/DiffIndex   
Ign http://us.archive.ubuntu.com precise/main i386 Packages/DiffIndex          
Ign http://us.archive.ubuntu.com precise/restricted i386 Packages/DiffIndex    
Ign http://us.archive.ubuntu.com precise/universe i386 Packages/DiffIndex      
Ign http://us.archive.ubuntu.com precise/multiverse i386 Packages/DiffIndex    
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Ign http://us.archive.ubuntu.com precise-updates/main Sources/DiffIndex        
Ign http://us.archive.ubuntu.com precise-updates/restricted Sources/DiffIndex  
Ign http://us.archive.ubuntu.com precise-updates/universe Sources/DiffIndex    
Ign http://us.archive.ubuntu.com precise-updates/multiverse Sources/DiffIndex  
Ign http://us.archive.ubuntu.com precise-updates/main amd64 Packages/DiffIndex 
Ign http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com precise-updates/universe amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com precise-updates/main i386 Packages/DiffIndex  
Ign http://us.archive.ubuntu.com precise-updates/restricted i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com precise-updates/universe i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages/DiffIndex
Get:19 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:20 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:21 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:22 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                   
Hit http://us.archive.ubuntu.com precise/multiverse Sources                 
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Get:23 http://us.archive.ubuntu.com precise-updates/main Sources [218 kB]      
Get:24 http://us.archive.ubuntu.com precise-updates/restricted Sources [5,118 B]
Get:25 http://us.archive.ubuntu.com precise-updates/universe Sources [76.4 kB] 
Get:26 http://us.archive.ubuntu.com precise-updates/multiverse Sources [4,737 B]
Get:27 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [483 kB]
Get:28 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [9,531 B]
Get:29 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [175 kB]
Ign http://extras.ubuntu.com precise/main amd64 Packages/DiffIndex             
Err http://archive.canonical.com precise Release.gpg                           
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Get:30 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [9,425 B]
Get:31 http://us.archive.ubuntu.com precise-updates/main i386 Packages [492 kB]
Hit http://archive.canonical.com precise Release                               
Ign http://extras.ubuntu.com precise/main i386 Packages/DiffIndex              
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://archive.canonical.com precise/partner amd64 Packages/DiffIndex      
Ign http://archive.canonical.com precise/partner i386 Packages/DiffIndex       
Ign http://archive.canonical.com precise/partner TranslationIndex              
Ign http://archive.canonical.com precise/partner amd64 Packages/DiffIndex      
Ign http://archive.canonical.com precise/partner i386 Packages/DiffIndex       
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Get:32 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [9,483 B]
Get:33 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [177 kB]
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Get:34 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [10.4 kB]
Get:35 http://us.archive.ubuntu.com precise-updates/main Translation-en [234 kB]
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Fetched 2,759 kB in 1min 19s (34.9 kB/s)                                       
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/dists/precise/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
default@default-laptop:~$ sudo apt-get install bcmwl-kernel-source=5.100.82.38+bdcom-0ubuntu6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtkspell-3-0 libllvm3.0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 1,151 kB of archives.
After this operation, 3,514 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  bcmwl-kernel-source
Install these packages without verification [y/N]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/restricted bcmwl-kernel-source amd64 5.100.82.38+bdcom-0ubuntu6 [1,151 kB]
Fetched 1,151 kB in 8s (138 kB/s)                                              
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 525266 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_amd64.deb) ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building only for 3.2.0-37-generic
Building for architecture x86_64
Building initial module for 3.2.0-37-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-37-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-37-generic
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ precise-security/restricted amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ precise-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ precise-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_dists_precise_partner_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_dists_precise_partner_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_dists_precise_partner_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
default@default-laptop:~$
```

The terminal output has a lot of "something wicked went wrong in it," do I have some other problems i should address as well?

But first I must test to see if it even works, thank you.

It in fact did work, thank you again.

I did not do the stop update part because i do the notify but don't download for my updates i figured i could just deselect the STA driver until i know there is one that works better.

My problem is Solved!

---

### Post by 23senick on 2013-02-04
Mikewhatever, thanks - will give it a go later. Off to work (wrong time zone I guess!)

---

### Post by mikewhatever on 2013-02-04
Glad it worked for you WaNaBePi.

> In the future, when there is an update that I do want for the wireless, how would I disable the stop upgrade?

You just delete the /etc/apt/preferences.d/bcmwl-kernel-source file.
```
sudo rm /etc/apt/preferences.d/bcmwl-kernel-source
```

The "something wicked went wrong in it" is unrelated to our topic here. We can look at your /etc/apt/sources list if you want, but that's probably a topic for another thread.

23senick, have a nice day. Hope it works for you too.

---

### Post by 23senick on 2013-02-04
Not there yet, sadly.  Successfully installed the old version using apt-get method, but lshw -c network shows wireless is still unclaimed.   Have re-booted a couple of times.  

Is it to do with version number?  Latest is apparently 5.100.82.112, but the step-by-step version is 5.100.82.38

Anything else anyone can suggest to get the wireless association sorted?

---

### Post by mikewhatever on 2013-02-04
> **23senick said:**
> Not there yet, sadly.  Successfully installed the old version using apt-get method, but lshw -c network shows wireless is still unclaimed.   Have re-booted a couple of times.  

Is it to do with version number?  Latest is apparently 5.100.82.112, but the step-by-step version is 5.100.82.38

Anything else anyone can suggest to get the wireless association sorted?

If the wireless is unclaimed, it usually means that the correct module isn't loaded. Try loading it manually with 

```
sudo modprobe wl
```

If it works, add it to /etc/modules for autoloading.

The 5.100.82.112 version is only available for 12.10. You can, of cause, download and install it, but keep in mind that it hasn't been tested with 12.04, and that the one you had before the upgrade was version 5.100.82.38.

---

### Post by 23senick on 2013-02-04
Appreciate your help.  Tried sudo modprobe wl, got

FATAL: Error inserting wl (/lib/modules/3.2.0-37-generic/updates/dkms/wl.ko): Invalid argument

...any thoughts?

---

### Post by mikewhatever on 2013-02-04
Hm..., interesting. Can you post the outputs of the following:

```
dpkg -l | grep bcmwl

dmesg | grep wl

lsmod
```

---

### Post by 23senick on 2013-02-04
```
$ dpkg -l | grep bcmwl
ii  bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu6 Broadcom 802.11 Linux STA wireless driver source


$ dmesg | grep wl
[    0.000000] DMI: Hewlett-Packard HP Pavilion dm1 Notebook PC/3387, BIOS F.01 08/04/2011
[   21.916906] wl: disagrees about version of symbol lib80211_get_crypto_ops
[   21.916916] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
[ 1329.827074] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 1329.827091] wl: Unknown symbol lib80211_get_crypto_ops (err -22)
[ 1487.284945] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 1487.284964] wl: Unknown symbol lib80211_get_crypto_ops (err -22)

$ lsmod
Module                  Size  Used by
vesafb                 13844  1 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
ip6t_LOG               16974  4 
xt_hl                  12521  6 
ip6t_rt                12558  3 
snd_seq_midi           13324  0 
nf_conntrack_ipv6      13906  7 
nf_defrag_ipv6         13412  1 nf_conntrack_ipv6
snd_rawmidi            30748  1 snd_seq_midi
snd_hda_codec_idt      70795  1 
ipt_REJECT             12576  1 
ipt_LOG                12919  5 
xt_limit               12711  12 
xt_tcpudp              12603  18 
snd_hda_codec_hdmi     32474  1 
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                97485  0 
xt_addrtype            12713  4 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
xt_state               12578  14 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
btusb                  18291  0 
ip6table_filter        12815  1 
ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12704  0 
nf_nat                 25891  1 nf_nat_ftp
nf_conntrack_ipv4      19716  9 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack_ftp       13452  1 nf_nat_ftp
nf_conntrack           81926  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12810  1 
uvcvideo               72627  0 
ip_tables              27473  1 iptable_filter
serio_raw              13211  0 
fglrx                4713410  151 
x_tables               29891  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
k10temp                13166  0 
videodev               98259  1 uvcvideo
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29990  2 snd_seq,snd_pcm
sp5100_tco             13791  0 
v4l2_compat_ioctl32    17128  1 videodev
lib80211               14381  0 
i2c_piix4              13301  0 
snd                    79041  20 snd_hda_codec_idt,snd_rawmidi,snd_hda_codec_hdmi,snd_seq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer
soundcore              15091  1 snd
wmi                    19256  1 hp_wmi
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
rfcomm                 46747  12 
parport_pc             32866  0 
bnep                   18139  2 
bluetooth             205289  24 btusb,rfcomm,bnep
ppdev                  17113  0 
compat                 20099  5 btusb,lib80211,rfcomm,bnep,bluetooth
hp_accel               25976  0 
lis3lv02d              19876  1 hp_accel
video                  19596  0 
input_polldev          13896  1 lis3lv02d
binfmt_misc            17540  1 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62154  0
```

---

### Post by mikewhatever on 2013-02-04
OK, thanks for the outputs. If you've followed the thread suggested by Hadaka, try removing the linux-backports-modules-cw-3.6-precise-generic package, then reboot:

```
sudo apt-get purge linux-backports-modules-cw-3.6-precise-generic
```

It caused the same problem for others with the wl module.

---

### Post by 23senick on 2013-02-04
Thanks Mikewhatever - I'll give it a go in a bit and post back.  Just had to surrender the laptop to someone with homework to do!

---

### Post by 23senick on 2013-02-04
Success!! Thanks mikewhatever.  

When I did the sudo apt-get purge, I got this message:

  	 	 	 	 	 	   The following package was automatically installed and is no longer required:  
   linux-backports-modules-cw-3.6-3.2.0-37-generic  
 Use 'apt-get autoremove' to remove them.  
  
I first of all tried rebooting without doing this, and got back to where I had started (seeing wifi network but not connecting). So I did apt-get autoremove and on startup, again, it wouldn't connect. I disconnected from wifi network, left it a few minutes, and when I tried again it connected. Tried a reboot...immediate connection.  

Hope others find this helpful. Should the thread be marked solved, I wonder?

---

### Post by varunendra on 2013-02-05
So we got two happy campers here :)

Nicely done mike!

***@ 23senick,***
Next time you have to post some command output, please consider enclosing them in 'Code' tags. It preserves the output's formatting and makes it more readable. I've edited your above post as an example. You may follow the '[COLOR="Navy"]example[/COLOR]' link in my signature to see an example of how to do it yourself :)

***@ WaNaBePi,***
If you believe you are satisfied with the solution, please consider marking it as **[Solved] **to help others.

---

