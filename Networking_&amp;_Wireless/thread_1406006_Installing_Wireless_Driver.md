---
title: "Installing Wireless Driver"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by mcmullen on 2010-02-13
I have just installed Ubuntu 9.10 netbook remix for my new laptop. I've tried at great length to install the correct drivers to get my wireless up and running. I'm currently trying to install the Broadcom driver for my 802.11g wireless card. I have downloaded the headers and tools for ubuntu and am proceeding with the instructions given on

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

but when i get to these steps i come unstuck
# mkdir hybrid_wl
# cd hybrid_wl
# tar xzf <path>/hybrid-portsrc.tarI can make the directory and open it but when it comes to the third step I get a message saying that there is no such file or directory.

Any help you could offer would be much appreciated as I am completely stuck.

---

### Post by chili555 on 2010-02-13
Have you tried the easy way? Connect an ethernet cable, get an internet connection and do:```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```

---

### Post by mcmullen on 2010-02-13
Yes I've tried this it says 

FATAL module wl not found

---

### Post by chili555 on 2010-02-13
What, if anything, shows up in System -> Administration -> Hardware Drivers?

---

### Post by mcmullen on 2010-02-13
It says that there are no proprietary drivers active in this system, it says there is a Broadcom STA proprietary wireless driver but it is inactive. When I try to activate it says sorry installation of this driver has failed. It says to look at a log which then shows:

2010-02-13 17:59:43,230 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-02-13 17:59:49,765 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-02-13 17:59:49,766 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-02-13 17:59:49,858 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-02-13 17:59:55,829 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-02-13 17:59:55,880 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-02-13 17:59:55,954 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

---

### Post by sacher on 2010-02-13
Why don' t you try to istall the drivers using **Ndiswrapper** 
 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
 
 
or **b43-fwcutter** 
[LIST=1]
[*]Install b43-fwcutter. You can find it here [http://packages.debian.org/sid/b43-fwcutter](http://packages.debian.org/sid/b43-fwcutter)

[*]Get the drivers:
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)     and  [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2). 
[/LIST]     3. Execute the following commands to extract the firmware
	sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o	tar xfvj broadcom-wl-4.80.53.0.tar.bz2	sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o

---

### Post by chili555 on 2010-02-13
> but when i get to these steps i come unstuck
# mkdir hybrid_wl
# cd hybrid_wl
# tar xzf <path>/hybrid-portsrc.tarI can make the directory and open it but when it comes to the third step I get a message saying that there is no such file or directory.Please try this.

By default, downloads are placed on the desktop. I assume that's where the hybrid-portsrc file is. Since you have already created a directory hybrid_wl, let's move the hybrid-portsrc file there:```
mv Desktop/hybrid-portsrc.tar hybrid_wl
```Now, let's change to the correct directory:```
cd hybrid_wl
```And unpack the tar file:```
tar xzf hybrid-portsrc.tar
```A folder will be created and we need to change to that directory:```
cd hybrid-portsrc
```Now, we will make and install the module:```
make
```Now follow the remaining instructions in the README.

---

### Post by Pragmatik on 2010-02-13
I had exactly the same problem last weekend.  Before connecting to ethernet (and I read that you can do it via USB/CD also if you can't -- somewhere else on the forums) and entering....

sudo apt-get install bcmwl-kernel-source

....you might have luck reinstalling first.  I tried a bunch of solutions on my Dell Mini 10v with Netbook Remix, and then the solution didn't work for me, simply installing the Broadcom driver.  Something was amiss.  I reinstalled Remix again (the install only took a few minutes anyway).  Ran sudo apt-get install bcmwl-kernel-source (or you could get it via Synaptic), and all was well on the fresh install.  Restart after installing the driver, and you're good.  

I installed Netbook Remix on two machines that night, with only the driver added.  Restarted, and all was well.

---

### Post by Pragmatik on 2010-02-13
Sorry, that was garbled.  I mean:

1) Reinstall UNR again.  
2) Hook up to ethernet.
3) Run sudo apt-get install bcmwl-kernel-source
4) Restart system.
5) Enjoy your wireless! :)

---

