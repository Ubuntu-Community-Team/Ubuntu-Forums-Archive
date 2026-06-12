---
title: "Lustre file system"
date: 2012-07-30
forum: Networking &amp; Wireless
---

### Post by sushy on 2012-07-30
I am trying to setup a lustre file system. But when I try to do mkfs.lustre I get the error saying command not found. I tried looking for mkfs.lustre file in both /sbin and /usr/sbin but it does not exist. Is there a package that can install this for me?

So as to make it more understandable. How does mkfs.lustre get installed in /sbin or /usr/sbin? I cannot find it in either of those locations on my system.

---

### Post by bakegoodz on 2012-07-31
```
sudo apt-get install lustre-utils
```

---

### Post by sushy on 2012-07-31
I get the error saying 

E: Couldn't find package lustre-utils

---

### Post by bakegoodz on 2012-07-31
Comment out universe and multiverse. If you can't figure it out show your sources.list
```
cat /etc/apt/sources.list
```

---

### Post by sushy on 2012-08-07
Hi this is my new sources.list

root@ubuntu:/# cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/ lucid main restricted

#deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

But I still get the same error message.

Thanks in advance for your help.

---

### Post by bakegoodz on 2012-08-07
Yup, Universe and Multiverse is commented out. Remove the '##' in the lines with Universe and Multivere. You can leave the deb-src lines commented out and certainly leave the back ported lines commented out. Save and update Apt and then you can install
```
apt-get update
```

BTW, the sources list is very verbose, which probably makes it look complicated. You can actually combine Universe and Multivere on one line. Here is my sources.list:
```
deb http://mirror.xmission.com/ubuntu/ precise main universe multiverse
deb http://mirror.xmission.com/ubuntu/ precise-updates main universe multiverse
deb http://mirror.xmission.com/ubuntu/ precise-security main universe multiverse
```

---

### Post by sushy on 2012-08-08
Hi Bakegoodz,

Thanks for your reply. I did what you mentioned. I removed the ## lines and combined everything into one line. Here is my sources.list file


# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/ lucid main restricted
#deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
**deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main universe multiverse**
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
**deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main universe multiverse**
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
**deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security main universe multiverse**


After that I did

#apt-get update

And then tried to install the lustre-utils 

#apt-get install lustre-utils

but I still get the same error.

---

### Post by bakegoodz on 2012-08-09
Sorry, I didn't check out the Lucid packages. I turns out lustre-utils is just a source package on Lucid. So you would uncomment the deb-src lines in sources.list. Then you would have to compile the luste-utils package which is a little involved but not too bad with this guide. [http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/](http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/)

---

### Post by sushy on 2012-08-09
Thank you the above mentioned link. I get this error while I type in 

sudo apt-get source lustre-utils

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Could not open file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_main_source_Sources -open (2: No such file or directory)

I cannot find us.archive.ubuntu.com_ubuntu_dists_lucid_main_source_Sources
under /var/lib/apt/lists/(There is no space between "_source_" but I dont know why this is being shown)

Im not sure about resolving this.

---

### Post by sushy on 2012-08-09
I tried installing everything again as per the link sent by you. But again when I type in mkfs.lustre .....

it says mkfs.lustre:command not found

The steps I followed are:


sushy@sushy:/$ cd /etc/apt/sources.list
-bash: cd: /etc/apt/sources.list: Not a directory
sushy@sushy:/$ cat /etc/apt/sources.list
#
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/ lucid main restricted

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

----------------------------------------------------------------------------------------------------------------------------------
sushy@sushy:/$ sudo apt-get install build-essential fakeroot dpkg-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
fakeroot is already the newest version.
dpkg-dev is already the newest version.
dpkg-dev set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 202 not upgraded.

sushy@sushy:/$ mkdir build
sushy@sushy:~$ cd build

sushy@sushy:~/build$ sudo apt-get source lustre-utils
Reading package lists... Done
Building dependency tree
Reading state information... Done
NOTICE: 'lustre-utils' packaging is maintained in the 'Cvs' version control system at:
-d :pserver:anonymous@cvs.lustre.org:/lustre
Need to get 5,583kB of source archives.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe lustre 1.6.7.2-1 (dsc) [1,517B]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe lustre 1.6.7.2-1 (tar) [4,943kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe lustre 1.6.7.2-1 (diff) [638kB]
Fetched 5,583kB in 18s (297kB/s)
gpgv: Signature made Mon 10 Aug 2009 01:39:05 AM PDT using DSA key ID B913143A
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./lustre_1.6.7.2-1.dsc
dpkg-source: info: extracting lustre in lustre-1.6.7.2
dpkg-source: info: unpacking lustre_1.6.7.2.orig.tar.gz
dpkg-source: info: applying lustre_1.6.7.2-1.diff.gz
dpkg-source: info: upstream files that have been modified:
 lustre-1.6.7.2/ldiskfs/kernel_patches/patches/ext3-fiemap-2.6.18-vanilla.patch
 lustre-1.6.7.2/ldiskfs/kernel_patches/series/ldiskfs-2.6.18-debian.series
sushy@sushy:~/build$ sudo apt-get build-dep lustre-utils
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  automake1.7 dh-kpatches diffstat dpatch dvipng libaiksaurus-1.2-0c2a
  libaiksaurus-1.2-data libboost-regex1.40.0 libboost-signals1.40.0 libreadline-dev
  libreadline6-dev libsnmp-dev libsnmp-perl libssl-dev libt1-5 libwrap0-dev lyx lyx-common
  patchutils preview-latex-style quilt texlive-latex-extra texlive-latex-extra-doc
  texlive-pictures texlive-pictures-doc zlib1g-dev
The following packages will be upgraded:
  libsnmp-base libsnmp15 libssl0.9.8
3 upgraded, 26 newly installed, 0 to remove and 199 not upgraded.
Need to get 232MB of archives.
After this operation, 377MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libssl0.9.8 0.9.8k-7ubuntu8.13 [3,018kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe automake1.7 1.7.9-9.1 [352kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main diffstat 1.47-1build1 [23.6kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main dpatch 2.0.31 [88.4kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libt1-5 5.1.2-3ubuntu0.10.04.2 [156kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main dvipng 1.12-3ubuntu0.1 [85.3kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe libaiksaurus-1.2-data 1.2.1+dev-0.12-6build1 [318kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe libaiksaurus-1.2-0c2a 1.2.1+dev-0.12-6build1 [23.6kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libboost-regex1.40.0 1.40.0-4ubuntu4 [379kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libboost-signals1.40.0 1.40.0-4ubuntu4 [54.2kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libreadline6-dev 6.1-1 [234kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libreadline-dev 6.1-1 [904B]
Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libsnmp-base 5.4.2.1~dfsg0ubuntu1-0ubuntu2.2 [1,346kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libsnmp15 5.4.2.1~dfsg0ubuntu1-0ubuntu2.2 [2,058kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libsnmp-perl 5.4.2.1~dfsg0ubuntu1-0ubuntu2.2 [142kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libwrap0-dev 7.6.q-18 [35.4kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main zlib1g-dev 1:1.2.3.3.dfsg-15ubuntu1 [162kB]
Get:18 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libssl-dev 0.9.8k-7ubuntu8.13 [2,007kB]
Get:19 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libsnmp-dev 5.4.2.1~dfsg0ubuntu1-0ubuntu2.2 [1,580kB]
Get:20 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe lyx-common 1.6.5-1ubuntu1 [5,669kB]
Get:21 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe lyx 1.6.5-1ubuntu1 [3,187kB]
Get:22 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main patchutils 0.3.1-2build1 [101kB]
Get:23 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main preview-latex-style 11.85-1ubuntu1 [123kB]
Get:24 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main quilt 0.48-5 [318kB]
Get:25 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main texlive-pictures 2009-7 [865kB]
Get:26 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main texlive-latex-extra 2009-7ubuntu3 [4,723kB]
Get:27 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main texlive-latex-extra-doc 2009-7ubuntu3 [193MB]
50% [27 texlive-latex-extra-doc 90.9MB/193MB 47%]                           204kB/s 9min 17sWrite failed: Connection reset by peer

Lost connection so it started again

Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main texlive-latex-extra-doc 2009-7ubuntu3 [193MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main texlive-pictures-doc 2009-7 [11.9MB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe dh-kpatches 0.99.36 [68.3kB]
Fetched 205MB in 33min 10s (103kB/s)
Preconfiguring packages ...
(Reading database ... 270348 files and directories currently installed.)
Preparing to replace libssl0.9.8 0.9.8k-7ubuntu8.6 (using .../libssl0.9.8_0.9.8k-7ubuntu8.13_i386.deb) ...
Unpacking replacement libssl0.9.8 ...
Setting up libssl0.9.8 (0.9.8k-7ubuntu8.13) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package automake1.7.
(Reading database ... 270348 files and directories currently installed.)
Unpacking automake1.7 (from .../automake1.7_1.7.9-9.1_all.deb) ...
Selecting previously deselected package diffstat.
Unpacking diffstat (from .../diffstat_1.47-1build1_i386.deb) ...
Selecting previously deselected package dpatch.
Unpacking dpatch (from .../archives/dpatch_2.0.31_all.deb) ...
Selecting previously deselected package libt1-5.
Unpacking libt1-5 (from .../libt1-5_5.1.2-3ubuntu0.10.04.2_i386.deb) ...
Selecting previously deselected package dvipng.
Unpacking dvipng (from .../dvipng_1.12-3ubuntu0.1_i386.deb) ...
Selecting previously deselected package libaiksaurus-1.2-data.
Unpacking libaiksaurus-1.2-data (from .../libaiksaurus-1.2-data_1.2.1+dev-0.12-6build1_all.deb) ...
Selecting previously deselected package libaiksaurus-1.2-0c2a.
Unpacking libaiksaurus-1.2-0c2a (from .../libaiksaurus-1.2-0c2a_1.2.1+dev-0.12-6build1_i386.deb) ...
Selecting previously deselected package libboost-regex1.40.0.
Unpacking libboost-regex1.40.0 (from .../libboost-regex1.40.0_1.40.0-4ubuntu4_i386.deb) ...
Selecting previously deselected package libboost-signals1.40.0.
Unpacking libboost-signals1.40.0 (from .../libboost-signals1.40.0_1.40.0-4ubuntu4_i386.deb) ...
Selecting previously deselected package libreadline6-dev.
Unpacking libreadline6-dev (from .../libreadline6-dev_6.1-1_i386.deb) ...
Selecting previously deselected package libreadline-dev.
Unpacking libreadline-dev (from .../libreadline-dev_6.1-1_i386.deb) ...
Preparing to replace libsnmp-base 5.4.2.1~dfsg0ubuntu1-0ubuntu2.1 (using .../libsnmp-base_5.4.2.1~dfsg0ubuntu1-0ubuntu2.2_all.deb) ...
Unpacking replacement libsnmp-base ...
Preparing to replace libsnmp15 5.4.2.1~dfsg0ubuntu1-0ubuntu2.1 (using .../libsnmp15_5.4.2.1~dfsg0ubuntu1-0ubuntu2.2_i386.deb) ...
Unpacking replacement libsnmp15 ...
Selecting previously deselected package libsnmp-perl.
Unpacking libsnmp-perl (from .../libsnmp-perl_5.4.2.1~dfsg0ubuntu1-0ubuntu2.2_i386.deb) ...
Selecting previously deselected package libwrap0-dev.
Unpacking libwrap0-dev (from .../libwrap0-dev_7.6.q-18_i386.deb) ...
Selecting previously deselected package zlib1g-dev.
Unpacking zlib1g-dev (from .../zlib1g-dev_1%3a1.2.3.3.dfsg-15ubuntu1_i386.deb) ...
Selecting previously deselected package libssl-dev.
Unpacking libssl-dev (from .../libssl-dev_0.9.8k-7ubuntu8.13_i386.deb) ...
Selecting previously deselected package libsnmp-dev.
Unpacking libsnmp-dev (from .../libsnmp-dev_5.4.2.1~dfsg0ubuntu1-0ubuntu2.2_i386.deb) ...
Selecting previously deselected package lyx-common.
Unpacking lyx-common (from .../lyx-common_1.6.5-1ubuntu1_all.deb) ...
Selecting previously deselected package lyx.
Unpacking lyx (from .../lyx_1.6.5-1ubuntu1_i386.deb) ...
Selecting previously deselected package patchutils.
Unpacking patchutils (from .../patchutils_0.3.1-2build1_i386.deb) ...
Selecting previously deselected package preview-latex-style.
Unpacking preview-latex-style (from .../preview-latex-style_11.85-1ubuntu1_all.deb) ...
Selecting previously deselected package quilt.
Unpacking quilt (from .../archives/quilt_0.48-5_all.deb) ...
Selecting previously deselected package texlive-pictures.
Unpacking texlive-pictures (from .../texlive-pictures_2009-7_all.deb) ...
Selecting previously deselected package texlive-latex-extra.
Unpacking texlive-latex-extra (from .../texlive-latex-extra_2009-7ubuntu3_all.deb) ...
Selecting previously deselected package texlive-latex-extra-doc.
Unpacking texlive-latex-extra-doc (from .../texlive-latex-extra-doc_2009-7ubuntu3_all.deb) ...
Selecting previously deselected package texlive-pictures-doc.
Unpacking texlive-pictures-doc (from .../texlive-pictures-doc_2009-7_all.deb) ...
Selecting previously deselected package dh-kpatches.
Unpacking dh-kpatches (from .../dh-kpatches_0.99.36_all.deb) ...
Processing triggers for doc-base ...
Processing 4 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up automake1.7 (1.7.9-9.1) ...

Setting up diffstat (1.47-1build1) ...
Setting up dpatch (2.0.31) ...
Setting up libt1-5 (5.1.2-3ubuntu0.10.04.2) ...

Setting up dvipng (1.12-3ubuntu0.1) ...
Setting up libaiksaurus-1.2-data (1.2.1+dev-0.12-6build1) ...
Setting up libaiksaurus-1.2-0c2a (1.2.1+dev-0.12-6build1) ...

Setting up libboost-regex1.40.0 (1.40.0-4ubuntu4) ...

Setting up libboost-signals1.40.0 (1.40.0-4ubuntu4) ...

Setting up libreadline6-dev (6.1-1) ...
Setting up libreadline-dev (6.1-1) ...
Setting up libsnmp-base (5.4.2.1~dfsg0ubuntu1-0ubuntu2.2) ...
Setting up libsnmp15 (5.4.2.1~dfsg0ubuntu1-0ubuntu2.2) ...

Setting up libsnmp-perl (5.4.2.1~dfsg0ubuntu1-0ubuntu2.2) ...
Setting up libwrap0-dev (7.6.q-18) ...
Setting up zlib1g-dev (1:1.2.3.3.dfsg-15ubuntu1) ...
Setting up libssl-dev (0.9.8k-7ubuntu8.13) ...
Setting up libsnmp-dev (5.4.2.1~dfsg0ubuntu1-0ubuntu2.2) ...
Setting up lyx-common (1.6.5-1ubuntu1) ...

Setting up patchutils (0.3.1-2build1) ...
Setting up preview-latex-style (11.85-1ubuntu1) ...
mktexlsr: Updating /usr/local/share/texmf/ls-R...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE...
mktexlsr: Updating /var/lib/texmf/ls-R...
mktexlsr: Done.

Setting up quilt (0.48-5) ...
Setting up texlive-pictures (2009-7) ...

Setting up texlive-latex-extra-doc (2009-7ubuntu3) ...

Setting up texlive-pictures-doc (2009-7) ...

Setting up dh-kpatches (0.99.36) ...

Processing triggers for tex-common ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.
Setting up lyx (1.6.5-1ubuntu1) ...

Setting up texlive-latex-extra (2009-7ubuntu3) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for tex-common ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.

----------------------------------------------------------------------------------------------------------------------------------

sushy@sushy:~/build$ ls
lustre-1.6.7.2  lustre_1.6.7.2-1.diff.gz  lustre_1.6.7.2-1.dsc  lustre_1.6.7.2.orig.tar.gz
sushy@sushy:~/build$ ls -l
total 5460
drwxr-xr-x 10 root root    4096 2012-08-09 13:36 lustre-1.6.7.2
-rw-r--r--  1 root root  638023 2009-11-05 03:06 lustre_1.6.7.2-1.diff.gz
-rw-r--r--  1 root root    1517 2009-11-05 03:06 lustre_1.6.7.2-1.dsc
-rw-r--r--  1 root root 4943268 2009-11-05 03:06 lustre_1.6.7.2.orig.tar.gz
----------------------------------------------------------------------------------------------------------------------------------

sushy@sushy:~/build$ sudo dpkg-source -x lustre_1.6.7.2-1.dsc
gpgv: Signature made Mon 10 Aug 2009 01:39:05 AM PDT using DSA key ID B913143A
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./lustre_1.6.7.2-1.dsc
dpkg-source: info: extracting lustre in lustre-1.6.7.2
dpkg-source: info: unpacking lustre_1.6.7.2.orig.tar.gz
dpkg-source: info: applying lustre_1.6.7.2-1.diff.gz
dpkg-source: info: upstream files that have been modified:
 lustre-1.6.7.2/ldiskfs/kernel_patches/patches/ext3-fiemap-2.6.18-vanilla.patch
 lustre-1.6.7.2/ldiskfs/kernel_patches/series/ldiskfs-2.6.18-debian.series
----------------------------------------------------------------------------------------------------------------------------------
sushy@sushy:~/build$ sudo dpkg-buildpackage -rfakeroot -b
dpkg-buildpackage: warning: using a gain-root-command while being root
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value:
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
tail: cannot open `debian/changelog' for reading: No such file or directory
dpkg-buildpackage: error: tail of debian/changelog gave error exit status 1

-----------------------------------------------------------------

sushy@sushy:/$ mkfs.lustre
mkfs.lustre: command not found

----------------------------------------------------------------------------------------------------------------------------------
sushy@sushy:~$ sudo dpkg -i lustre-utils
dpkg: error processing lustre-utils (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 lustre-utils
----------------------------------------------------------------------------------------------------------------------------------
sushy@sushy:/usr/sbin$ which mkfs.lustre
sushy@sushy:/usr/sbin$ which lustre

Sorry for a long post. Thanks in advance.

---

### Post by bakegoodz on 2012-08-11
I don't know why the package won't install. I don't have Lucid on a computer right now, but when I have some time I would like to try to duplicate what you are doing.

---

### Post by bakegoodz on 2012-08-12
You can get farther by going into the bulid/lustre-1.6.7.2 before issuing dpkg-buildpackage
It doesn't matter though, the build process dies with build problems I couldn't resolve. I guess that explains why they didn't build a binary package for Lucid.

---

### Post by sushy on 2012-08-13
Thank you so much for being patient with me. Since we cannot find the binaries while installing lustre on ubuntu 10.04 we are unable to go forward with Lustre. Is there some other distributed file system that could successfully be installed on ubuntu 10.04?

Regards,
Sushy

---

### Post by bakegoodz on 2012-08-14
GlusterFS
[http://www.howtoforge.com/high-availability-storage-with-glusterfs-on-ubuntu-10.04-automatic-file-replication-mirror-across-two-storage-servers](http://www.howtoforge.com/high-availability-storage-with-glusterfs-on-ubuntu-10.04-automatic-file-replication-mirror-across-two-storage-servers)

---

### Post by sushy on 2012-08-14
Thank you so much for that link. I was able to setup Gluster on my existing machines. I am really at peace now. :) But I have one question, what is the recovery mechanism of Gluster like?

---

### Post by sushy on 2012-08-14
I have a new found problem this time.

I am not able to either delete a file, delete a directory or delete a few lines from a file. When I delete any existing file/directory the files at location /data/export(as in the link) do not get updated but the files on mount /mnt/glusterfs/ get updated. I tried rebooting the system but now the /mnt/glusterfs/ show the deleted files as well. So basically I am unable to delete anything. My version of gluster is 3.0.4

Is there a workaround this?

Thanks for your help.

---

### Post by sushy on 2012-08-20
Solved this and posting it for benefit of others. The gluster version 3.0.4 had a bug which prevents deletion of files and has been fixed in version 3.1.2. This gluster is unavailable with Ubuntu 10.04 so had to upgrade to Ubuntu 11.10.

Thanks for your help.

---

### Post by bakegoodz on 2012-08-21
So you were able to go to a newer Ubuntu? Why not 12.04?

---

### Post by sushy on 2012-08-21
The default gluster with Ubuntu 12.04 seemed to have some bugs as I read on a few forums. I might be wrong. So I left it at 11.10. The gluster works as expected. Currently I am working on testing this gluster setup. 

Thank you so much for your inputs.

---

