---
title: "libdvd-pkg: cannot install: broken packages?"
date: 2021-11-01
forum: Multimedia Software
---

### Post by tcpip on 2021-11-01
Hi,

I'm using Ubuntu 20.04.3 LTS on my Intel i5 laptop. I'm moderately familiar with Ubuntu, Linux, and Unix, having used and installed and managed Unix systems since about 1990.

I am unable to install libdvd-pkg successfully. (I've been using previous versions of Ubuntu on my older laptops, and I've always been able to install these DVD CSS tools and packages before, with or without problems.)

This time, when I do an apt install libdvd-pkg, I know I'm supposed to do a dpkg-reconfigure libdvd-pkg afterwards. That's when I hit a problem. This is the message I'm getting:


libdvd-pkg: Checking orig.tar integrity...
/usr/src/libdvd-pkg/libdvdcss_1.4.2.orig.tar.bz2: OK
libdvd-pkg: Unpacking and configuring...
libdvd-pkg: Building the package... (it may take a while)
libdvd-pkg: Build log will be saved to /usr/src/libdvd-pkg/libdvdcss2_1.4.2-1~local_amd64.build
WARNING: libcap needs an update (cap=40 should have a name).
Current: =ep
Bounding set =cap_chown,cap_dac_override,cap_fowner,cap_wake_alarm,cap_block_suspend,cap_audit_read,38,39,40
Ambient set =
Securebits: 024/0x14/5'b10100
 secure-noroot: no (unlocked)
 secure-no-suid-fixup: yes (unlocked)
 secure-keep-caps: yes (unlocked)
 secure-no-ambient-raise: no (unlocked)
uid=0(root) euid=0(root)
gid=1000(shuvam)
groups=4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),120(lpadmin),131(lxd),132(sambashare),1000(shuvam)
Guessed mode: UNCERTAIN (0)


I've seen this other thread which is just a few months old: [https://ubuntuforums.org/showthread.php?t=2463371](https://ubuntuforums.org/showthread.php?t=2463371)   but the symptoms reported there are different.

Can you please help?

---

### Post by Frogs Hair on 2021-11-01
Try the following and make sure all packages are up to date and then reconfigure again. Please post the full output of the second attempt.   
```
sudo apt update && sudo apt upgrade

```
```
sudo dpkg-reconfigure libdvd-pkg
```

---

### Post by tcpip on 2021-11-02
I do apt update and apt dist-upgrade as a matter of course every week or two. I've done it at least thrice since I installed libdvd-pkg and tried the dpkg-reconfigure.

The output I have posted is the output I see after doing all of these.

---

### Post by Frogs Hair on 2021-11-02
> WARNING: libcap needs an update (cap=40 should have a name This stands out , are you running docker and do you have any 3rd party PPA's installed as noted on the post you linked ?

The following command was used to address the quoted warning above in another post though I seem to have no need for it on my system and have libdvd installed.    
```
sudo apt-get install libpcap-dev
```

---

### Post by tcpip on 2021-11-06
> **Frogs Hair said:**
> This stands out , are you running docker and do you have any 3rd party PPA's installed as noted on the post you linked ?
This is the list of files in my /etc/apt/sources.list.d/  -- I haven't checked the actual /etc/apt/sources.list for added lines, but the sources.list.d itself tells me I have two "non-standard" PPAs.

```

/etc/apt/sources.list.d/:
total 20
-rw-rw-r-- 1 root shuvam  68 Jun 24 15:26 signal-xenial.list
-rw-rw-r-- 1 root root    68 Jun 24 15:26 signal-xenial.list.save
-rw-r--r-- 1 root root    58 Jun 24 15:26 skype-stable.list
-rw-r--r-- 1 root root    58 Jun 24 15:26 skype-stable.list.save
-rw-r--r-- 1 root root   203 Jun 24 15:27 vscode.list

```

> The following command was used to address the quoted warning above in another post though I seem to have no need for it on my system and have libdvd installed.    
```
sudo apt-get install libpcap-dev
```
Thanks for this tip, I tried it, but the error remained.

---

### Post by Frogs Hair on 2021-11-06
Please run and post the output to check for outdated software sources. 

> cat /etc/apt/sources.list

---

### Post by tcpip on 2021-11-07
> **Frogs Hair said:**
> Please run and post the output to check for outdated software sources.

Here it is:
```

deb http://in.archive.ubuntu.com/ubuntu/ focal main restricted


deb http://in.archive.ubuntu.com/ubuntu/ focal-updates main restricted


deb http://in.archive.ubuntu.com/ubuntu/ focal universe
deb http://in.archive.ubuntu.com/ubuntu/ focal-updates universe


deb http://in.archive.ubuntu.com/ubuntu/ focal multiverse
deb http://in.archive.ubuntu.com/ubuntu/ focal-updates multiverse


deb http://in.archive.ubuntu.com/ubuntu/ focal-backports main restricted univers


deb http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse


deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main

```

I have removed all commented lines for brevity.

---

### Post by Frogs Hair on 2021-11-08
Post the entire output of each command.

```
sudo dpkg --configure -a 
```

> sudo apt -f install


---

### Post by tcpip on 2021-11-22
> **Frogs Hair said:**
> Post the entire output of each command.

```
sudo dpkg --configure -a 
```

Absolutely no output. No error message either. I just get the hash prompt back.

And ```
apt -f install
``` gives me

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

In the meantime, I have done ```
apt update; apt dist-upgrade
``` once or twice, all of which work fine.

I tried running ```
dpkg-reconfigure libdvd-pkg
``` once again just now, and it gave me the usual long error message which I have already posted in my thread starter post. But this time, I went to the file which has the build log and here are its contents:
```

dpkg-buildpackage: info: source package libdvdcss
dpkg-buildpackage: info: source version 1.4.2-1~local
dpkg-buildpackage: info: source distribution UNRELEASED
dpkg-buildpackage: info: source changed by Sebastian Ramacher <sramacher@debian.org>
dpkg: error: cannot set primary group ID to root: Operation not permitted
dpkg-architecture: error: dpkg --print-architecture failed: 
dpkg-buildpackage: error: dpkg-architecture subprocess returned exit status 25

```

I don't know what it means by "cannot set primary group ID to root" because I am running the program as root.

Does this have anything to do with the fact that I have some directory remounts? This is my /etc/fstab (stripped of comments).

```

UUID=3589bbd8-7d13-461d-aedd-ce21ab26eabd /               btrfs   defaults,subvol=@ 0       1
UUID=BE29-5106  /boot/efi       vfat    umask=0077      0       1
UUID=3589bbd8-7d13-461d-aedd-ce21ab26eabd /home           btrfs   defaults,subvol=@home 0       2
UUID=827362e0-e6e3-4dfc-a0df-2a3964377929 /second-root    btrfs   defaults        0       2
UUID=292e7c88-8c5b-42e0-82d8-da78be390f36 /warehouse      ext4    defaults        0       2
UUID=01D4B0DB966EFED0 /windows        ntfs    defaults,umask=007,gid=46 0       0
UUID=6ef66c37-440b-46af-9b46-3971795c8148 none            swap    sw              0       0
#
# bind mounts
#
/warehouse/var-log    /var/log        none    bind
/warehouse/var-cache    /var/cache        none    bind
/warehouse/usr-src    /usr/src        none    bind
/warehouse/home/shuvam    /home/shuvam        none    bind

```


The last four lines are hand inserted by me, the ones above them were by the Ubuntu installer. The hand-inserted lines are to let me keep a lot of larger directories in a partition called /warehouse, and then mount them in their proper places so that various applications can find what they need in expected places. Till about a year ago, I used to use soft-links for this, but soft-links break snaps, so I have resorted to this. Does this have an impact on why the dpkg-reconfigure is failing?

---

