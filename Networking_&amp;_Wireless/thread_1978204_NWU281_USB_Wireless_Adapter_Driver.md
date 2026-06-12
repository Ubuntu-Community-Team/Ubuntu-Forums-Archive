---
title: "NWU281 USB Wireless Adapter Driver"
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by Quail2 on 2012-05-11
I recently got a new laptop and discovered that the wireless card wasn't compatible with linux so I bought an Addon NWU281 802.11n USB adapter to get online. It provides instructions on a CD on how to set up the driver, but for some reason I can't figure out what I'm meant to do. I wondered if someone could help me, perhaps explain in more detail what I'm meant to do? I've searched online to see if there was a driver I could download but couldn't find one.

Anyway, here are the instructions:
> 
Part 1: make 8192C USB Linux driver quickly
execute shell script “install.sh”
>./install.sh
> 
Part 1: make 8192C USB Linux driver step by step
(1) step1: uncompress the “rtl8192cu_linux_v2.0.xxxx.2010xxxx.tar.gz” file. (in “driver” directory)
    > tar zxvf rtl8192CU_linux_v2.0.1170.20101112.tar.gz
(2) step2: make 8192C USB driver module
    > make
(3) step3: clean the operation environment
    > ./clean
(4) step4: insert 8192C USB modules 
    > insmod 8192cu.ko


I know this probably seems like a stupid question, so sorry for asking but I want to get wireless on Ubuntu so I don't have to boot up in Windows 7 for internet and Ubuntu for everything else.

---

### Post by chili555 on 2012-05-11
> I recently got a new laptop and discovered that the wireless card wasn't compatible with linux Do you mind if the doctor looks at your internal card first? I love a challenge; I love a mystery and I hate to lose. Please unplug the USB device and open a terminal and run and post:```
lsb_release -a
lspci -nn | grep 0280
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.> I know this probably seems like a stupid question, so sorry for asking but I want to get wireless on Ubuntu so I don't have to boot up in Windows 7 for internet and Ubuntu for everything else. That's perfectly reasonable; no apologies needed.

---

### Post by Quail2 on 2012-05-11
> No LSB modules are available.
Distributor ID: Ubuntu
Description 10.04.2 LTS
Release: 10.04
Codename: lucid
> 01:00.0 Network controller [[COLOR=Red]0280[/COLOR]]: Ralink Device [1814:5390]
The third command doesn't return anything. Annoyingly I can't find a cable for a wired connection so I'm using my old laptop to connect to the internet.

To add some more information to the orignial post, I've figured out how to run everything, but it keeps telling me the files don't exist.

---

### Post by chili555 on 2012-05-11
Your internal device is certainly not incompatible with Ubuntu. In the latest version, 12.04, it is driven by the driver rt2800pci out of the box. You could consider an upgrade to 12.04.

Here is a good tutorial on installing it if you refer not to install 12.04. It will require a temporary ethernet connection: [http://ubuntuforums.org/showthread.php?t=1928740](http://ubuntuforums.org/showthread.php?t=1928740)

I'll be very happy to help in either case.

---

### Post by Quail2 on 2012-05-11
Thanks, I obviously didn't do enough research before I bought a USB adapter. I have a portable hard drive with me so if there's a way of downloading the files I need onto this laptop (running ubuntu 11.10) and installing them without an ethernet connection I could do it now.

---

### Post by chili555 on 2012-05-11
> if there's a way of downloading the files I need onto this laptop (running ubuntu 11.10) and installing them without an ethernet connection I could do it now.It could be done, however the compiling tools, build-essential, linux-headers-generic and dkms are complex with a lot of other packages as dependencies. Downloading separately is a couple of hours of frustration and possible mis-steps. With an ethernet connection on the computer in question is three minutes and it's done correctly. 

I'm reasonably adept at such things and I'd wait.

---

### Post by chamber on 2012-05-11
Small note.

I am using a USB wireless that uses the same chipset.

Cd'ing to the unzipped folder in the teminal and then running 

```
sudo bash install.sh 
```

installs the driver for me on my arch laptop.  I have to do this for each new kernal release but it does work.

Have you tried running the shell script?

---

