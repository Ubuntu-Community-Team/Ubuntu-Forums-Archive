---
title: "upgrade kernel from 2.6.38 to 2.6.39"
date: 2011-07-05
forum: Networking &amp; Wireless
---

### Post by biswa on 2011-07-05
Hi all
now i am using linux ubuntu image having version 11.04.It has kernel version as 2.6.38 
i want to make  WL 1271 as a AP(access point).For this i need to upgrade the kernel version to 2.6.39 which support AP in WL 1271.
For this i have used the following commands:

1.) Add the kernel ppa and update your system:

sudo add-apt-repository ppa:kernel-ppa/ppa

sudo apt-get update

2.) Check available kernels with the command:

apt-cache showpkg linux-headers

kernel 2.6.39.0 should be in list.

sudo apt-get install linux-headers-2.6.39-0 linux-headers-2.6.39-0-generic linux-image-2.6.39-0-generic --fix-missing

After running the above commands i am getting the following message:
Unable to locate package linux-headers-2.6.39-0


please help how to solve this problem

---

### Post by varunendra on 2011-07-05
> **biswa said:**
> 
2.) Check available kernels with the command:

apt-cache showpkg linux-header

kernel 2.6.39.0 should be in list.
As per above, did you see version 2.6.39.0 in the list that is created by apt-cache showpkg linux-header command?

I manually checked the site that ppa:kernel-ppa/ppa actually points to, and there were no packages there ([http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/natty/main/](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/natty/main/)). Perhaps they have been removed from there. Same is also suggested in the last two comments on the tutorial page that perhaps you followed: [http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0](http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0)

---

### Post by biswa on 2011-07-08
i checked that version 2.6.39.0 kernel was not in the list.But how to bring this kernel version to this list or any other process to upgrade kernel from version 2.6.38 to 2.6.39.please help.

---

### Post by terrykiwi83 on 2011-07-10
Having same problem here kernel 2.6.39 isn't showing after adding the PPA and updating above, is there another way to upgrade?

**Edit:** Found the Kernel here [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Just need to work out which one to install and in what order :\

---

