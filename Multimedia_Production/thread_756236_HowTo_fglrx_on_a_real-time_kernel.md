---
title: "HowTo: fglrx on a real-time kernel"
date: 2008-04-15
forum: Multimedia Production
---

### Post by angryfirelord on 2008-04-15
For a while, Ubuntu users who needed a real-time kernel couldn't get 3D working properly on it due to issues. However, after some trial and error I appear to have found a solution. Please note that I forgot to write this down, so there may be mistakes. 

I got my info from the following sites:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually)
[http://64studio.com/node/150#comment-1148](http://64studio.com/node/150#comment-1148)

Ok, first thing, open up a terminal and create a folder for the ati driver:
```
mkdir ati; cd ati
```
We're now inside the ati folder. Let's download the driver and save it in the *ati* folder:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-3-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-3-x86.x86_64.run)

Ok, before we do anything else, let's download the necessary packages that'll allow us to build the deb packages later on:
```
sudo apt-get update
sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-2.6.22-14-rt
```
At this point, I'm not sure if dkms will create problems. You may have to not install it right now and install it later on.

Ok, now here's where it gets a little messy. If we try to build and install the deb packages as usual, we're going to get an error like this:
```
FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol '__rcu_read_lock'
```
Fortunately, there's a fix. Whether or not this fix is legal can be disputed, but as far as I can see I don't think anyone is going to run into legal issues. If you're cautious, read the rest of the guide before proceeding.

We need to change the license header in order for this check to go away. Still in the ati folder, run the following:
```
sudo sh ati-driver-installer-8-3-x86.x86_64.run --extract fglrx
```
What this command will do is extract all of the files into a new folder called fglrx. If you run the ls command, you can spot it. However, I'm going to work in the ati folder.

Now we must edit two files. One is called drm_compat.h and the other is called firegl_public.c. So, let's open up the first one: (please change the text editor as necessary)
```
gksu gedit fglrx/common/lib/modules/fglrx/build_mod/drm_compat.h
```
Find this line (it should be at the beginning):
[php]#define MODULE_LICENSE(x)[/php]
Change it to this:
[php]#define MODULE_LICENSE("GPL")[/php]
Save and exit. Go to the second file:
```
gksu gedit fglrx/common/lib/modules/fglrx/build_mod/firegl_public.c
```
Find this line:
[php]MODULE_LICENSE("Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY")[/php]
Change it to this:
[php]MODULE_LICENSE("GPL")[/php]
Save and exit. Now we can generate the deb packages. Run:
```
sudo sh fglrx/packages/Debian/ati-packager.sh --buildpkg gutsy
```
Again, I'm not sure if that's the correct syntax, so double-check on that. The ati-packager.sh is the script to run.

If the debs are generated successfully, then install them:
```
sudo dpkg --force-overwrite -i fglrx-amdcccle_8.471-0ubuntu1_amd64.deb fglrx-kernel-source_8.471-0ubuntu1_amd64.deb xorg-driver-fglrx_8.471-0ubuntu1_amd64.deb xorg-driver-fglrx-dev_8.471-0ubuntu1_amd64.deb
```
The reason for the --force-overwrite is that otherwise this command would conflict with the ia32-libs package on a 64-bit system. For 32-bit systems, the force may not be necessary.

After the command completes, dkms should handle the building of the kernel module. If you did not install it, install dkms now.

Open this file:
```
gksu gedit /etc/default/linux-restricted-modules-common
```
Make it look like this:
```
DISABLED_MODULES="fglrx"
```
Finally, edit your xorg.conf. You do it manually or two other ways:
```
sudo dpkg-reconfigure xserver-xorg
```
or
```
sudo aticonfig --initial
```
Reboot. The fglrx driver should be installed and running.

As I stated before, **I MAKE MISTAKES!!!** Please, if you find something incorrect or that it doesn't work, report it below.

I hope this guide cures some Ubuntu Studio user's frustration with ATI.

---

### Post by Stochastic on 2008-04-15
Really? I had absolutely no issues with getting fglrx and compiz to run on a fresh install of Ubuntu Studio Gutsy with the automated installer on my ATI Radeon Xpress 200m graphics card.  Everything ran smooth and clean.

---

### Post by angryfirelord on 2008-04-15
> **Stochastic said:**
> Really? I had absolutely no issues with getting fglrx and compiz to run on a fresh install of Ubuntu Studio Gutsy with the automated installer on my ATI Radeon Xpress 200m graphics card.  Everything ran smooth and clean.
Do you have the 32-bit or 64-bit edition? I don't know, maybe they fixed it and I didn't realize it. :)

I have a Radeon X1600.

---

### Post by Stochastic on 2008-04-15
I'm running 32bit now, but when I installed the 64bit version of gutsy back in tha day, everything went smooth too.  I hadn't heard of anyone having issues, but this also isn't the multimedia & video forum so maybe everyone who had issues posted elsewhere?  Actually I do remember hearing murmurs during the beta testing of the realtime kernel that fglrx wasn't happy with it, but come the full release no further mention until now.

---

### Post by leilei on 2008-05-24
> **Stochastic said:**
> Really? I had absolutely no issues with getting fglrx and compiz to run on a fresh install of Ubuntu Studio Gutsy with the automated installer on my ATI Radeon Xpress 200m graphics card.  Everything ran smooth and clean.

Well that's not really using the Real-time kernel now is it?


I followed the instructions here and the ati-packager.sh command failed, so I did
```
cd fglrx
sudo sh packages/Debian/ati-packager.sh --buildpkg etch
```
And it built the packages. I continued from there and woo, accelleration on rt kernel on Hardy 8.04 :D
The wacky license change step is sure easier than recompiling the kernel to drop that paravirtualization support

---

