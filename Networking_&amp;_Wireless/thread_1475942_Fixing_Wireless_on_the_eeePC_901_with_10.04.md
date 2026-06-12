---
title: "Fixing Wireless on the eeePC 901 with 10.04"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by xianthax on 2010-05-07
My 901 has a ralink RT2860 wireless card which wouldn't connect to any wifi network with 10.04, all the "how to fix" posts i found were rather lacking or involved excess work, hopefully this will help someone out.

Heres how i fixed it YMMV and i take no responsibility if you mess up your install.

Download the newest driver from: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

I used 2.3.0.0 dated 1/29/2010, i haven't noticed any bugs in this version _yet_.

Unzip this file (right click and extract here).

Make sure you have the build-essential package installed (use synaptic or apt-get install build-essential)

All you really have to do is follow the readme in the driver folder for the most part but for completeness:

In the drivers folder, which should be /home/<username>/Downloads/2010_01_29_RT2860_Linux_STA_v2.3.0.0/ if you haven't changed your default download settings, navigate to os/linux and open the file named config.mk

Find these lines:

```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
```

Change them to 

```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```

open a terminal and navigate to the driver folder:

cd /home/<username>/Downloads/2010_01_29_RT2860_Linux_STA_v2.3.0.0/

type: make     

and push enter.

The driver should compile, if its ends in an error, stop and figure it out :)  I did this on a stock 10.04 install so all you should need is the build-essential package and it should work.  IF you get header errors you may be missing the linux-headers package.

Now copy the .dat file over, i'm not 100% sure this is required but the driver read me said to do it and it can't hurt

cd /etc/
sudo mkdir Wireless
cd Wireless
sudo mkdir RT2860STA
sudo cp /home/<username>/Downloads/2010_01_29_RT2860_Linux_STA_v2.3.0.0/RT2860STA.dat /etc/Wireless/RT2860STA/RT2860STA.dat

Now test the driver:

Turn off your wireless with the network manager then in a terminal:

sudo rmmod rt2860sta
sudo insmod /home/<username>/Downloads/2010_01_29_RT2860_Linux_STA_v2.3.0.0/os/linux/rt2680sta.ko

Try connecting to some networks, should work fine at this point ( i even get full N speed now)

If all is well then:

cd /lib/modules/'uname -r'/kernel/drivers/staging/rt2860
cp rt2860sta.ko ~/rt2860sta.ko.bak  <---creates a backup of the default driver in your home directory
sudo rm rt2860sta.ko
sudo cp /home/<username>/Downloads/2010_01_29_RT2860_Linux_STA_v2.3.0.0/os/linux/rt2680sta.ko rt2680sta.ko

After that it should load whenever you reboot, etc, **this will break when a kernel update happens.**

What i did to solve that was to setup DKMS to rebuild it automatically when the kernel updates, thats kind of out of the scope of this post but you can find info on DKMS from the DKMS man page or this wiki covers the basics: [http://wiki.centos.org/HowTos/BuildingKernelModules](http://wiki.centos.org/HowTos/BuildingKernelModules)

---

### Post by emilinz on 2010-05-09
It works!!! Thank you

---

### Post by gsoundsgood on 2010-08-19
now it's very easy to solve this issue (wireless not working on some models of eee-pc):

if you can get a functioning connection via LAN, you can simply download the package *linux-backports-modules-wireless-2.6.32-24-generic* from the repositories:

```
sudo apt-get install linux-backports-modules-wireless-2.6.32-24-generic
```

or you can download it from here on any computer and just install on your eee-PC:
[http://packages.ubuntu.com/lucid/linux-backports-modules-wireless-2.6.32-24-generic]("http://packages.ubuntu.com/lucid/linux-backports-modules-wireless-2.6.32-24-generic")

tested on eee pc-901, wireless now working flawlessly

---

### Post by Light-kun on 2011-10-02
> **gsoundsgood said:**
> now it's very easy to solve this issue (wireless not working on some models of eee-pc):

if you can get a functioning connection via LAN, you can simply download the package *linux-backports-modules-wireless-2.6.32-24-generic* from the repositories:

```
sudo apt-get install linux-backports-modules-wireless-2.6.32-24-generic
```

or you can download it from here on any computer and just install on your eee-PC:
[http://packages.ubuntu.com/lucid/linux-backports-modules-wireless-2.6.32-24-generic]("http://packages.ubuntu.com/lucid/linux-backports-modules-wireless-2.6.32-24-generic")

tested on eee pc-901, wireless now working flawlessly

Hello,
I tried  previous post: maked, installed drivers from official RA site, insmodded, can ses a mod in lsmod:
 rt2860sta             756669  0 
but still can't see my wireless interface in ifconfig.

Do I need to install backports? And what after it? reboot?

---

### Post by nothingspecial on 2011-10-02
Hi,

Please make new thread for your issue rather than digging up an old one.

Closed

---

