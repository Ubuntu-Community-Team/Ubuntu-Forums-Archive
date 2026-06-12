---
title: "kernel 2.6.36"
date: 2010-11-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by egrpioneer on 2010-11-27
Please don't lose patience with me for posting in this forum, but before I launch into testing Natty, I need to learn how to install 2.6.36. Currently running perfect installs of Maverick 64 bit on 2, computers. Want to run new kernel in the laptop.

Thanks in advance, for any direction that can be offered!!

---

### Post by efflandt on 2010-11-27
Do you need kernel 2.6.36 in maverick or natty for something?  The current kernel in natty (at least as of yesterday) is 2.6.37-6-generic #17-Ubuntu.

---

### Post by benjamimgois on 2010-11-27
Just add the Kernel-PPA to your system and it will appear on your software-center:

Open a terminal and type this command:
sudo add-apt-repository ppa:kernel-ppa/ppa

---

### Post by egrpioneer on 2010-11-27
> **efflandt said:**
> Do you need kernel 2.6.36 in maverick or natty for something?  The current kernel in natty (at least as of yesterday) is 2.6.37-6-generic #17-Ubuntu.

I've read that in Maverick, updating to 2.6.36, from 2.6.35.23, will improve performance. Maybe yes, maybe no! Just want to learn and try it out!!

Thanks for responding!!

---

### Post by egrpioneer on 2010-11-27
> **benjamimgois said:**
> Just add the Kernel-PPA to your system and it will appear on your software-center:

Open a terminal and type this command:
sudo add-apt-repository ppa:kernel-ppa/ppa

Thank you! OK, followed your instructions. What is next?

---

### Post by benjamimgois on 2010-11-27
> **egrpioneer said:**
> Thank you! OK, followed your instructions. What is next?

Now it's avaiable on your software center. Go to applications, software center and search for "2.6.36" and install 3 files:

linux-headers-2.6.36-1
linux-headers-2.6.36-1-generic
linux-image-2.6.36-1-generic


Now just reboot your system and you will be running the new kernel

---

### Post by efflandt on 2010-11-27
If you did not do **sudo apt-get update** after adding the ppa you might have to refresh Synaptic (curly Reload icon) to see that kernel version.

---

### Post by egrpioneer on 2010-11-27
> **efflandt said:**
> If you did not do **sudo apt-get update** after adding the ppa you might have to refresh Synaptic (curly Reload icon) to see that kernel version.

Thanks, but doing reload, then searching for 2.6.36.1, in synaptic/software center doesn't show 2.6.36.1
Will keep trying to figure it out.

Thanks all!!

---

### Post by terry_gardener on 2010-11-27
> **egrpioneer said:**
> Thanks, but doing reload, then searching for 2.6.36.1, in synaptic/software center doesn't show 2.6.36.1
Will keep trying to figure it out.

Thanks all!!

you will properly find that the latest kernel will appear in the ppa which is .37-6

if you have added the ppa and then reloaded it. it should be in the list of upgrades available.

either click mark all upgrade and it should be in the list or run update manager and it should be in that list. 

you may find that the .36 has been backported or purposed for maverick, to activate these updates goto sources and then click updates tab and then tick the top 4 sections, the following should be selected. security, recommended, purposed and unsupported.

you might have to disable the kernel ppa as synaptic will only show the latest package available. 

hope this makes sense 

ps you can also use kernel-check application to search for kernel updates and install the latest.

---

### Post by egrpioneer on 2010-11-28
> **terry_gardener said:**
> you will properly find that the latest kernel will appear in the ppa which is .37-6

if you have added the ppa and then reloaded it. it should be in the list of upgrades available.

either click mark all upgrade and it should be in the list or run update manager and it should be in that list. 

you may find that the .36 has been backported or purposed for maverick, to activate these updates goto sources and then click updates tab and then tick the top 4 sections, the following should be selected. security, recommended, purposed and unsupported.

you might have to disable the kernel ppa as synaptic will only show the latest package available. 

hope this makes sense 

ps you can also use kernel-check application to search for kernel updates and install the latest.

Thanks for the suggestions! This is what is now recommended: "linux-backports-modules-compat-wireless-2.6.36-2.6.35.23-generic", but directs install of its meta-package.
I'll search for the "meta package", install it and see how it works.

Thank again for your assistance.

---

### Post by Starks on 2010-11-28
The kernel ppa is not a normal ppa and I don't understand why people keep treating it like one.

---

### Post by zika on 2010-11-28
```
mkdir zika28112010
cd zika28112010
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-headers-2.6.36-020636-generic_2.6.36-020636.201010210905_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-headers-2.6.36-020636_2.6.36-020636.201010210905_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-image-2.6.36-020636-generic_2.6.36-020636.201010210905_amd64.deb
sudo dpkg -i linux*.deb
cd ..
rm -rf zika28112010
```

---

### Post by egrpioneer on 2010-11-30
> **zika said:**
> ```
mkdir zika28112010
cd zika28112010
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-headers-2.6.36-020636-generic_2.6.36-020636.201010210905_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-headers-2.6.36-020636_2.6.36-020636.201010210905_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-image-2.6.36-020636-generic_2.6.36-020636.201010210905_amd64.deb
sudo dpkg -i linux*.deb
cd ..
rm -rf zika28112010
```

Thank you!! I'll take a run at it, and get back to you!

---

### Post by Turgon_Noldor on 2011-02-15
> **zika said:**
> ```
mkdir zika28112010
cd zika28112010
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-headers-2.6.36-020636-generic_2.6.36-020636.201010210905_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-headers-2.6.36-020636_2.6.36-020636.201010210905_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-image-2.6.36-020636-generic_2.6.36-020636.201010210905_amd64.deb
sudo dpkg -i linux*.deb
cd ..
rm -rf zika28112010
```

Worked like a charm with me. Thank you zika :)

---

