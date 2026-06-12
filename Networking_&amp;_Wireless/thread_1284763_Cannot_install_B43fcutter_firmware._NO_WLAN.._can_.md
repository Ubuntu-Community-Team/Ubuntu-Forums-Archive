---
title: "Cannot install B43fcutter firmware. NO WLAN.. can anyone help ??"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by scrypt on 2009-10-07
Hi everyone.

I caannot enable or use my wlan card.

My card is a bcm4312 wlan card.

here is the output from sudo lshw -C network

laptop:~$ sudo lshw -C network
*-network UNCLAIMED
description: Network controller
product: BCM4312 802.11b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:04:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
*-network

As you can see my wlan card driver is UNCLAIMED and this is really where my probelms really start...

I have tried to reinstall b43fwcutter from synaptics and also from my teminal 

BUT i get this error:

laptop:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postgresql-8.3 (8.3.8-0ubuntu8.10) ...
Starting PostgreSQL 8.3 database server: main* The PostgreSQL server failed to start. Please check the log output:
2009-10-07 04:25:00 BST FATAL: could not load server certificate file "server.crt": No such file or directory
failed!
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: error processing postgresql-8.3 (--configure):
subprocess post-installation script returned error exit status 1
No apport report written because the error message indicates its a followup error from a previous failure.
dpkg: dependency problems prevent configuration of postgresql:
postgresql depends on postgresql-8.3; however:
Package postgresql-8.3 is not configured yet.
dpkg: error processing postgresql (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
postgresql-8.3
postgresql
E: Sub-process /usr/bin/dpkg returned an error code (1)

B43fcutter seems to be installed but no matter what i have tried I cannot seem to install the Firmware.

Can somebody help me with this please.
I have been trying to fix this for nearly two days now...

Cheers for now

scrypt

---

### Post by arumator on 2009-10-07
hello scrypt , you have 2 options to get the wireless card working if you have not already. one option and the best option is the official broadcom-sta-driver 

uninstall b43 fw cutter. I have the same model card on one of my laptops and tried that method once. never got it to work.

[http://ppa.launchpad.net/albertomilone/broadcom-sta/ubuntu/pool/main/b/bcmwl/](http://ppa.launchpad.net/albertomilone/broadcom-sta/ubuntu/pool/main/b/bcmwl/)

should get you both .debs for the driver if not attempt to compile and install the tar.gz at the same website [bcmwl_5.10.91.9+bdcom.orig.tar.gz]("http://ppa.launchpad.net/albertomilone/broadcom-sta/ubuntu/pool/main/b/bcmwl/bcmwl_5.10.91.9+bdcom.orig.tar.gz") 

[http://ubuntuforums.org/showthread.php?t=1229614](http://ubuntuforums.org/showthread.php?t=1229614) this webpage explains more about the broadcom-sta-driver

the broadcom-sta driver is considered a non-free package. if you dont want a nonfree package, you need a program called ndiswrapper. in order to use ndiswrapper one will need the original microsoft windows xp wifi firmware executable. According to what i have read on this program, windows vista binarys dont work. from the executable you will need two files:

bcmwl5.inf
bcmwl5.sys

stick these together in a folder on the desktop then once ndiswrapper is installed on your machine type the following commands into terminal

sudo ndiswrapper -i (drag-drop the .inf file here) it will install the .inf and .sys file for your computer if its the right one. to know if you have installed the correct one:
sudo ndiswrapper -l should tell you if its recongizing the card.

once the card is recongzed run ndiswrapper -m
to write modprobe configuration.

finally, sudo modprobe ndiswrapper should allow you to use your wifi if everything has gone smoothly.

---

### Post by scrypt on 2009-10-07
Hello amurator

Thank-you for your reply.

I am still new to Ubuntu

Could you please post me the correct commands.

I then can study them and learn how to download, extract and install the correct firmware.

So I will be a couple of good starter lessons for me to learn in one go.

I look forward to your replies

scrypt

---

### Post by arumator on 2009-10-07
download these 2 files :  [http://ppa.launchpad.net/albertomilone/broadcom-sta/ubuntu/pool/main/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu1_i386.deb](http://ppa.launchpad.net/albertomilone/broadcom-sta/ubuntu/pool/main/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu1_i386.deb)  [http://ppa.launchpad.net/albertomilone/broadcom-sta/ubuntu/pool/main/b/bcmwl/bcmwl-modaliases_5.10.91.9+bdcom-0ubuntu1_i386.deb](http://ppa.launchpad.net/albertomilone/broadcom-sta/ubuntu/pool/main/b/bcmwl/bcmwl-modaliases_5.10.91.9+bdcom-0ubuntu1_i386.deb)  copy and paste those links one at a time into your browser. it should ask you each time if you want to download a file the file. the file will have end of .deb   how to install:  these newly downloded files will appear in one of 2 locations: in your home folder under downloads or right on your desktop. just double clicking the newly downloaded file should start the installation procedure.  EDIT: if you really want to fix postgresql open up synaptic package manager   click on the status button  if theres a broken package it will list where the categories of packages was. click on &quot;broken&quot; and remove the packages listed to the right.they will have a little red box next to them.  heres a link to the dependecy your missing: [http://packages.ubuntu.com/jaunty/postgresql-8.3](http://packages.ubuntu.com/jaunty/postgresql-8.3)

---

### Post by scrypt on 2009-10-08
Okay.

I shall take a look and give it a go.

I'll post back how things went.

Cheers for now  scrypt

---

### Post by scrypt on 2009-10-08
These are the correct commands i need to run, download, extract and install the appropriate firmware

Code:

wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-012.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-012.tar.bz2)
tar xjf b43-fwcutter-012.tar.bz2
cd b43-fwcutter-012
make
cd ..

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-012/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o

I ran these commands as is.

is there anything i need to change with any of these commands?

My firmware is installed and kept in /lib/firmware.

Im am not sure what to do next can you help??

---

### Post by scrypt on 2009-10-08
are these the right commands i should be running???

export /lib/firmware


sudo ../../b43-fwcutter-012/b43-fwcutter -w /lib/firmware wl_apsta_mimo.o

---

### Post by scrypt on 2009-10-08
I have no wireless can someone help me out please?

---

