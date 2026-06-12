---
title: "HP Mini 1116 &amp; Wireless driver"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by fractonimbus on 2010-05-23
Hey, I'm a totally rookie at all this. I installed Ubuntu 10.4 Netbook edition in an HP Mini 1116 NR computer--I used an SD card & UNetbootin) and the wireless router is not recognized. I've been pretty much googling and troubleshooting this problem for most of the day. I always get stuck at a dead end.

This netbook does not have an ethernet adapter nor a CD-Rom drive, so I have no way of connecting to the internet w/out wireless. I am able to download things from my other laptop to the SD card.

1. When I enter 
sudo apt-get install build-essential at the terminal, I get "package not found."

2. When I try to install b43-fwcutter or bcmwl-kernel-source, it either won't work because I can't connect to the net or I get a "dkms dependency" issue.

3. So I tried to install the dkms pacakge and got a "gcc dependency" issue.  After that, I come up with a dead end.

An alternative option, so I read, is to use ndiswrapper and download the HP wireless broadcom driver, but that driver is a .exe file and I read that ndiswrapper needs a .inf file and I can't seem to find one. Does it matter?

Any help would be appreciated.

---

### Post by purelinuxuser on 2010-05-23
Hello!  In order for us to help you, we'll need some information about your system.  Post the output of the following commands (since you don't have an Internet connection, you can just copy/paste to a text file and save it on your SD card).
```
lspci
lshw -c network
iwconfig
```Best of luck :)

Edit: By the way, your netbook doesn't have an Ethernet adapter!?  What kind of computer does NOT have an Ethernet adapter!!!

---

### Post by kandydish on 2010-05-24
Hey, I have the EXACT same problem. Here are my specs:

kandy-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

kandy@kandy-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:feafc000-feafffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:25:56:88:64:98
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


kandy@kandy-laptop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by purelinuxuser on 2010-05-24
> **kandydish said:**
> Hey, I have the EXACT same problem. Here are my specs:

Please do not hijack threads.  But anyway, here's a fix that might work for fractonimbus too.

[LIST=1]
[*][S]Since neither of you have an Internet connection, download the b43-fwcutter package manually at [http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_012-1build1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_012-1build1_i386.deb).  Let me know if there are any problems.
[*]Install it, and you will get a prompt asking if you want to download and install firmware.  Be sure this is **UNCHECKED**, or the installation will fail.[/S]
[/LIST]

[LIST=1]
[*]**Build fwcutter manually (see two posts down).**
[*]Now download the firmware here: [http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2) and save it to your Downloads folder.  Right-click on it in the File Browser and click Extract.
[*]Open a Terminal (Applications > Accessories > Terminal) and type in the following commands:
```
cd Downloads/broadcom-wl-4.178.10.4/linux
sudo b43-fwcutter -w /lib/firmware wl_apsta.o
```**IMPORTANT: That last command will ask you for your "sudo" password.  Just type in your login password- however, you will NOT be able to see any characters as you type (not even *s).  This is normal, just keep typing.**
[*]After that operation completes, browse into /lib/firmware and see if there are two folders named b43 and b43legacy.
[*]If so, reboot, and hopefully your wireless will be working.
[/LIST]
Note that this card has been temperamental in my experience.  Wireless tends to be slow... constant disconnects... weird DMA errors... but your mileage may vary ;)

---

### Post by fractonimbus on 2010-05-24
I did the commands you first suggested and got this:

No command 'lpsci' found, did you mean:
 Command 'lspci' from package 'pciutils' (main)
lpsci: command not found


WARNING: you should run this program as super-user.
  

*-network description: Network controller
       

product: BCM4312 802.11b/g
       

vendor: 
Broadcom Corporation
       
physical id: 0
       
bus info: pci@0000:01:00.0
       
version: 01
       
width: 64 bits
       
clock: 33MHz
       
capabilities: bus_master cap_list
       
configuration: driver=b43-pci-bridge latency=0
       

resources: irq:16 memory:feafc000-feafffff
  
*-network
       

description: Ethernet interface
       

product: 88E8040 PCI-E Fast Ethernet Controller
       

vendor: Marvell Technology 
Group Ltd.
       
physical id: 0
       
bus info: pci@0000:02:00.0
       
logical name: eth0
       
version: 00
       

serial: 
00:25:b3:52:e5:8c
       
width: 64 bits
       
clock: 33MHz
       
capabilities: bus_master cap_list ethernet physical
       


configuration: broadcast=yes 
driver=sky2 
driverversion=1.25 
firmware=N/A latency=0 
multicast=yes
      
resources: irq:26 memory:febfc000-febfffff ioport:ec00(size=256)
  


*-network DISABLED
       
description: Wireless interface
       
physical id: 2
       logical name: wlan0
       
serial: 00:25:56:97:86:6c
       
capabilities: ethernet physical wireless
       
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

emily@emily-laptop:~$ lwconfig

No command 'lwconfig' found, did you mean:
 Command 'iwconfig' from package 
'wireless-tools' (main)
 Command 'ldconfig' from package 'libc-bin' (main)
lwconfig: command not found

I did what you suggested in your second email and got this:

Sorry, the input file is either wrong or not supported by b43-fwcutter.
This file has an unknown MD5sum bb8537e3204a1ea5903fe3e66b5e2763.

---

### Post by purelinuxuser on 2010-05-24
You misspelled 2 of the commands- they are *lspci* and [I]iwconfig. :P

[/I]Hmm... retry my second post, but instead of installing b43-fwcutter via *.deb package, try building it instead:

[LIST=1]
[*]Download [http://bu3sch.de/b43/fwcutter/b43-fwcutter-013.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-013.tar.bz2) and save it to your Downloads folder.
[*]Extract the archive.
[*]Open a Terminal and type in the following commands:
```
cd Downloads/b43-fwcutter-013
make
```
Hopefully there won't be any problems- should you encounter any, however, post back with terminal output.
[*]After b43-fwcutter is built, you can try my second post instructions again- **however, on the last command, replace "b43-fwcutter" with "~/Downloads/b43-fwcutter-013/b43-fwcutter" (without the quotes of course).**
[/LIST]
Let me know how it all goes! :)

---

### Post by fractonimbus on 2010-05-25
Here we go :) Thanks for your help. This is what I got:

emily@emily-laptop:~$ cd Downloads/b43-fwcutter-013
emily@emily-laptop:~/Downloads/b43-fwcutter-013$ make
     DEPEND   dep/md5.d
/bin/sh: cc: not found
     DEPEND   dep/fwcutter.d
/bin/sh: cc: not found
     CC       obj/fwcutter.o
/bin/sh: cc: not found
make: *** [obj/fwcutter.o] Error 127
emily@emily-laptop:~/Downloads/b43-fwcutter-013$

---

### Post by purelinuxuser on 2010-05-25
> **fractonimbus said:**
> Here we go :) Thanks for your help. This is what I got:

emily@emily-laptop:~$ cd Downloads/b43-fwcutter-013
emily@emily-laptop:~/Downloads/b43-fwcutter-013$ make
     DEPEND   dep/md5.d
/bin/sh: cc: not found
     DEPEND   dep/fwcutter.d
/bin/sh: cc: not found
     CC       obj/fwcutter.o
/bin/sh: cc: not found
make: *** [obj/fwcutter.o] Error 127
emily@emily-laptop:~/Downloads/b43-fwcutter-013$

[S]You are missing some dependencies.  Download the following packages and install them:
[http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-defaults/gcc_4.4.3-1ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-defaults/gcc_4.4.3-1ubuntu1_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-defaults/cpp_4.4.3-1ubuntu1_i386.deb]("http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.4/gcc-4.4_4.4.3-4ubuntu5_i386.deb")
[http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.4/gcc-4.4_4.4.3-4ubuntu5_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.4/gcc-4.4_4.4.3-4ubuntu5_i386.deb)
Then start back from step 3.  BTW, you're welcome! :)[/S]

Edit: Okay, that is weird.  I just booted a fresh live cd and the same commands worked out fine for me, no extra dependencies required.  Show me the output of:
```
gcc
```Also, try step 3 again but this time run
```
bash
```as your very first command before you do anything.

---

### Post by kandydish on 2010-05-25
Hey, sorry for hijacking. I thought that she would probably have the same problems as me (she was) and we can move about this faster with two people working on it and posting responses versus one.

I got the same errors when I tried to make b43-cutter
So I skipped it ( I don't know why) and I went to the next step and I get this:(I extracted it to my home folder)

kandy@kandy-laptop:~$ cd broadcom-wl-4.178.10.4/linux
kandy@kandy-laptop:~/broadcom-wl-4.178.10.4/linux$ sudo b43-fwcutter -w /lib/firmware wl_apsta.o
[sudo] password for kandy: 
Sorry, the input file is either wrong or not supported by b43-fwcutter.
This file has an unknown MD5sum bb8537e3204a1ea5903fe3e66b5e2763.

I also got errors when I tried to install the gcc packages:

gcc_4.4.3-1ubuntut1

Error: Dependency is not satisfiable: gcc-4.4 (>= 4.4.3-1)

gcc_4.4_4.4.3-4ubuntu5

Error: Dependency is not satisfiable: binutils (>=2.20)

Apparently the ones I have are more updated?

---

### Post by purelinuxuser on 2010-05-25
> **kandydish said:**
> Hey, sorry for hijacking.

It's alright... just being clear! :P

> **kandydish said:**
> I also got errors when I tried to install the gcc packages:

gcc_4.4.3-1ubuntut1

Error: Dependency is not satisfiable: gcc-4.4 (>= 4.4.3-1)

gcc_4.4_4.4.3-4ubuntu5

Error: Dependency is not satisfiable: binutils (>=2.20)

Apparently the ones I have are more updated?

You MUST build b43-fwcutter.  The version in the Ubuntu repos. is not up-to-date enough to take the firmware files required.  Also, don't install those packages (see my edited last post), just move on to make.

---

### Post by kandydish on 2010-05-26
kandy@kandy-laptop:~$ bash
kandy@kandy-laptop:~$ cd b43-fwcutter-013
kandy@kandy-laptop:~/b43-fwcutter-013$ make
     DEPEND   dep/md5.d
/bin/sh: cc: not found
     DEPEND   dep/fwcutter.d
/bin/sh: cc: not found
     CC       obj/fwcutter.o
/bin/sh: cc: not found
make: *** [obj/fwcutter.o] Error 127
kandy@kandy-laptop:~/b43-fwcutter-013$ cd
kandy@kandy-laptop:~$ gcc
The program 'gcc' can be found in the following packages:
 * gcc
 * pentium-builder
Try: sudo apt-get install <selected package>
kandy@kandy-laptop:~$ sudo apt-get install gcc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gcc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gcc has no installation candidate
kandy@kandy-laptop:~$ sudo apt-get install pentium-builder
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pentium-builder

I was looking at other places and I found this thread: 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

The problems I had were installing dkms and bcmwl-kernel-source.

When I checked my synaptics manager after that, it said they were both broken.

---

### Post by purelinuxuser on 2010-05-26
> **kandydish said:**
> The problems I had were installing dkms and bcmwl-kernel-source.

When I checked my synaptics manager after that, it said they were both broken.

Just remove those packages.  That should clear things up.

> **kandydish said:**
> kandy@kandy-laptop:~$ gcc
The program 'gcc' can be found in the following packages:
 * gcc
 * pentium-builder
Try: sudo apt-get install <selected package>
kandy@kandy-laptop:~$ sudo apt-get install gcc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gcc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gcc has no installation candidate

Uhmm... that is... weird.  It may be that you have to run "sudo apt-get update," but you need Internet access for that. #-oI have absolutely no idea how to proceed from here, sorry.  Man, it's a bummer that neither of you guys have an Ethernet port on your netbook, that would have made things a heck of a lot easier.

---

### Post by cariboo on 2010-05-26
It looks like you are going about this completely the wrong way,  you can download and install the wl driver using System->Administration->Hardware Drivers, look for the sta driver. If you have the B43 driver installed, you will either have to blacklist it in /etc/modprobe.d/blacklist.conf or uninstall it.

You have to have a working wired internet in order to install the driver via Hardware Drivers. If you don't you can download the driver [here]("http:///packages.ubuntu.com/lucid/bcmwl-kernel-source"), then use gdebi to install it.

---

### Post by fractonimbus on 2010-05-26
Okay, I tried the gcc command:

emily@emily-laptop:~$ gcc
The program 'gcc' can be found in the following packages:
 * gcc
 * pentium-builder
Try: sudo apt-get install <selected package>
emily@emily-laptop:~$ sudo apt-get install gcc
[sudo] password for emily: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gcc
emily@emily-laptop:~$

---

### Post by kandydish on 2010-05-26
I get an error when I try to install the driver:
Error: Dependency not satisfiable: dkms

and it just domino's to gcc. and that gets stuck also where I try to manual build it. I posted it earlier. Looks like the HP Mini 1116nr is just not meant to have wireless...

---

### Post by fractonimbus on 2010-05-26
Haha, kandydish, that's exactly what happened to me in my first message of this thread. The gcc is killing us.

---

### Post by purelinuxuser on 2010-05-26
> **cariboo907 said:**
> It looks like you are going about this completely the wrong way,  you can download and install the wl driver using System->Administration->Hardware Drivers, look for the sta driver. If you have the B43 driver installed, you will either have to blacklist it in /etc/modprobe.d/blacklist.conf or uninstall it.

You have to have a working wired internet in order to install the driver via Hardware Drivers. If you don't you can download the driver [here]("http:///packages.ubuntu.com/lucid/bcmwl-kernel-source"), then use gdebi to install it.

Yeah, I probably should have just given up on b43 a LONG time ago. :) The problem with the STA driver is that they can't install it manually. :confused: Also the fact that apt-get can't find the gcc package is weird, which leads me to suspect that apt-get update is required.  Alas, a functional Internet connection is required...

---

### Post by fractonimbus on 2010-05-27
Is there a place to find an apt-get update?

---

### Post by purelinuxuser on 2010-05-27
> **fractonimbus said:**
> Is there a place to find an apt-get update?

It's a command that you run to update your package database. :P But of course you need a functional Internet connection...

---

### Post by fractonimbus on 2010-05-29
So is it hopeless? Is there anything else I can do?

---

### Post by purelinuxuser on 2010-05-29
> **fractonimbus said:**
> So is it hopeless? Is there anything else I can do?

AFAIK nothing that doesn't involve spending some more cash (and no, I'm not talking about buying a new netbook).

---

### Post by fractonimbus on 2010-05-29
I went out and bought an Apple USB Ethernet adapter, so I have internet on the netbook now. I still seem to be stuck at the same spot though. dkms dependency . . .

---

### Post by purelinuxuser on 2010-05-30
Oh, good, that was my idea (buy a USB wireless stick :)).

Anyway, see if the following commands resolve any problems:
```
sudo apt-get update
sudo apt-get -f install
sudo dpkg-reconfigure -a
sudo apt-get upgrade
```Then go to System > Administration > Hardware Drivers and install the "Broadcom Proprietary STA Wireless Driver."  Finally, reboot.

Hope this helps! :KS

Edit: Also, if you STILL have errors, post EXACT command output/error messages.

*Note: The driver you will be installing is proprietary and thus does not support some of the more advanced features of Linux wireless, such as Monitor mode (passive monitoring of wireless networks) and Master mode (using your card as an access point, basically).  It will be fine for everyday use however, and is reliable.*

---

### Post by namluc on 2010-06-15
I'm at the same position, after doing a fresh install of lucid on my hp mini. I have got to say this thing is a joke. The netbook edition doesn't even have the stuff required for a major netbook. This was not a problem last year, why is it a problem this year. 

I've downloaded dkms, but then couldn't install that as it has another dependency, gcc. After I've installed all of these things, it will take me more time to get everything sorted out.

What a joke.

Just found that gcc depends on something else.

---

### Post by paul_harris on 2010-06-15
> **purelinuxuser said:**
> Please do not hijack threads. But anyway, here's a fix that might work for fractonimbus too.

[LIST=1]
[*][S]Since neither of you have an Internet connection, download the b43-fwcutter package manually at [http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_012-1build1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_012-1build1_i386.deb). Let me know if there are any problems.
[*]Install it, and you will get a prompt asking if you want to download and install firmware. Be sure this is **UNCHECKED**, or the installation will fail.[/S]
[/LIST][LIST=1]
[*]**Build fwcutter manually (see two posts down).**
[*]Now download the firmware here: [http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2) and save it to your Downloads folder. Right-click on it in the File Browser and click Extract.
[*]Open a Terminal (Applications > Accessories > Terminal) and type in the following commands:
```
cd Downloads/broadcom-wl-4.178.10.4/linux
sudo b43-fwcutter -w /lib/firmware wl_apsta.o
```**IMPORTANT: That last command will ask you for your "sudo" password. Just type in your login password- however, you will NOT be able to see any characters as you type (not even *s). This is normal, just keep typing.**
[*]After that operation completes, browse into /lib/firmware and see if there are two folders named b43 and b43legacy.
[*]If so, reboot, and hopefully your wireless will be working.
[/LIST]Note that this card has been temperamental in my experience. Wireless tends to be slow... constant disconnects... weird DMA errors... but your mileage may vary ;)
 
 i got to step 3 and did the sudo bit but it came up as.
Sorry, the input file is either wrong or not supported by b 43-fwcutter. this file has an unknown MD5sum bb blah blah blah. what does that mean

---

### Post by paul_harris on 2010-06-15
neither of the b43 firmware files are about anyway.

---

### Post by paul_harris on 2010-06-15
> **paul_harris said:**
> neither of the b43 firmware files are about anyway.
the previous message was for the post before the last post

---

### Post by Ub4me on 2010-07-08
Suffered the same problem for three day. I am new to this too. Your best bet is to Ethernet connect (use the ethernet port) and run all the 'update' and 'upgrade' commands. It will take about an hour but will solve most of the domino dependency problem.

I am coming from three days of consecutive download to usb from my apple and run on my Window/Ubuntu. I feel your pain

---

### Post by projectalarum on 2010-07-27
I hope it's not too late, but I have had the same exact issue, although, my HP Mini 1116 DOES have an ethernet port, just nothing to connect to as wireless is my only option at the moment.  I've had similiar issues with wireless and this netbook + Ubuntu in the past, but have always been able to resolve it, with a bit of time and A LOT of time digging through google.  On top of the wireless, I had another interesting problem today with 10.04 where it would mount my external cdrom as a floppy, and luckily it ended up solving my problem in a round about way.  But I imagine that problem was unique and not the same as yours.  The following steps worked for me as extremely simple as it sounds, it was the quickest solution and made me feel a little stupid in the end.  It will require an external cdrom or possibly a work around with the .iso used to install.
 
Open Synaptic Package Manager, under Edit, select 'Add CD-ROM'.  With the installation disc in the drive, the package manager will mount the drive as a local resource for additional restricted packages.  This is where I discovered my problem with the floppy issue which was cured by reinstalling using a USB drive instead of the external CDROM.  But anyways, once it's done, reload package manager to refresh it, and search for [FONT=Courier New]bcmwl-kernel-source[/FONT] and install it.
 
After that, open terminal and do:
 
~$ sudo modprobe -r b43 ssb wl
~$ sudo modprobe wl
 
and restart for giggles, lemme know if this helps!!!

---

### Post by Animal0307 on 2010-10-08
I'm not sure if it was said. And I'm aware this thread is most likely dead but for the sake of sharing knowledge. The HP mini 1000 series **DOES** have an ethernet port. It's hidden under a rubber plug on the front left corner next to the headphone jack. also on the right side under the cap looks to be a USB port that I think is for a BT or 3G adaptor.

Cheers,
Animal0307

---

