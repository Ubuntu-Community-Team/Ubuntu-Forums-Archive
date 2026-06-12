---
title: "no eth0 in 10.10, Intel 82566DC"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by Static-XJ on 2010-10-11
I've played around with Linux before, but still consider myself a beginner.  

I am currently trying to dual boot Win XP Pro and Ubuntu 10.10.  Ubuntu is a new instal, not upgrading from a previous version.  I connect to the internet wirelessly, Ubuntu picked this up flawlessly, and works great.  I use internet connection sharing in Windows to connect an Xbox360 via the motherboards onboard NIC, in Windows this works just fine.  My motherboard has an Intel 82566DC gigabit ethernet connection built in.  

ifconfig shows loopback and wlan0, no eth0.  

Searching here, and through Intel's support pages shows the e1000e driver is needed.  

results of dmesg | grep e1000e:
```
[    0.856008] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[    0.856013] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
[    0.856071] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.856084] e1000e 0000:00:19.0: setting latency timer to 64
[    0.856240] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[    1.136652] e1000e 0000:00:19.0: (unregistered net_device): The NVM Checksum Is Not Valid
[    1.158681] e1000e 0000:00:19.0: PCI INT A disabled
[    1.158700] e1000e: probe of 0000:00:19.0 failed with error -5

```trimmed results of lspci:
```
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
```As I understand this, the ethernet controller is detected, and the e1000e driver loaded, right?

I was planning to use Firestarter to setup internet connection sharing, but with no eth0, but I can't move past square one.  I even tried physically removing the wireless card, connecting direct to the router, and booting up the install cd, but still no eth0 (wireless worked throughout the install).

---

### Post by Static-XJ on 2010-10-12
bump

---

### Post by Iowan on 2010-10-12
**ifconfig -a** should show all available interfaces. You might also check **sudo lshw -C network**.

---

### Post by wnelson on 2010-10-12
Please post you output from dmesg.

---

### Post by Static-XJ on 2010-10-12
> **Iowan said:**
> **ifconfig -a** should show all available interfaces. You might also check **sudo lshw -C network**.
**ifconfig -a:**
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr ****
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: ****
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:257 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:217021 (217.0 KB)  TX bytes:43692 (43.6 KB)
```**sudo lshw -C network:**
```
*-network UNCLAIMED     
       description: Ethernet controller
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:92200000-9221ffff memory:92224000-92224fff ioport:20e0(size=32)
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:07:02.0
       logical name: wlan0
       version: 00
       serial: ****
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=2.6.35-22-generic firmware=N/A ip=192.168.1.104 latency=32 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:92000000-92007fff
```
> **wnelson said:**
> Please post you output from dmesg.
Any specific part you'd like to see?  I did post "dmesg | grep e1000e" output in the first post.  The results have not changed.

---

### Post by Static-XJ on 2010-10-14
bump

---

### Post by Nighthog on 2010-10-14
I had trouble with 10.04.1 similar to yours - wireless was fine and dandy, but eth0 was conspicuous by its absence.

The fix for me was to remove Network-Manager and install wicd.  If you do this, you will lose all connectivity when network-manager is removed (remove it BEFORE installing wicd), so check all the dependencies for wicd (python-support etc) and download the packages first.  Wicd is a big improvement over network manager IMO.

Good luck ...

---

### Post by Static-XJ on 2010-10-15
> **Nighthog said:**
> I had trouble with 10.04.1 similar to yours - wireless was fine and dandy, but eth0 was conspicuous by its absence.

The fix for me was to remove Network-Manager and install wicd.  If you do this, you will lose all connectivity when network-manager is removed (remove it BEFORE installing wicd), so check all the dependencies for wicd (python-support etc) and download the packages first.  Wicd is a big improvement over network manager IMO.

Good luck ...

Just tried this.  Got wicd working just fine with the wireless, but still no eth0 to be found.  Tried connecting to the router via ethernet, still nothing.  Using wicd to connect via wired, it just times out with no connection.

---

### Post by chili555 on 2010-10-15
> e1000e 0000:00:19.0: (unregistered net_device): The NVM ***Checksum Is Not Valid***
e1000e 0000:00:19.0: PCI INT A disabled
e1000e: probe of 0000:00:19.0 failed with error -5That's the problem. I have searched many times for an answer and suggest you do so as well. I do not have an answer yet.

---

### Post by Static-XJ on 2010-10-16
I found this information:

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=5f3eed6fe0e36e4b56c8dd9160241a868ee0de2a](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=5f3eed6fe0e36e4b56c8dd9160241a868ee0de2a)

I have no idea how to apply those patches.

---

### Post by chili555 on 2010-10-16
> I have no idea how to apply those patches.Neither do I. I do not see any reference to invalid checksum. Do you believe this is related?

---

### Post by boydude on 2010-10-19
> **chili555 said:**
> Neither do I. I do not see any reference to invalid checksum. Do you believe this is related?

i think i have the same problem, anyone know how to apply the patch?

---

### Post by chamilton on 2011-01-28
Hi,
I'm not sure if anyone still has this problem, but I came up with a fix. I have the same ethernet controller as the OP (Intel 82566DC) and was getting no indication from my modem that it was receiving valid data packets. My fresh install of 64 bit 10.10 didn't allow me to connect (I never got a DHCP lease). I tried re-inserting the module e1000e using ```
sudo modprobe -f e1000e
``` which returned told me that the e1000e.ko had an error with the kernel (or something to that effect). My fix was to go to search the intel site and download their latest e1000e linux drivers supported by the kernel and apply them.

Direct link to drivers: [HTML]http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=2775&lang=eng[/HTML]then I extracted the contents and installed the driver(I assume you can extract with the GUI tool yourself).
```
cd ./e1000e-1.2.20/src 
make
sudo make install
sudo rmmod -f e100*
sudo modprobe e1000e
sudo ifconfig eth0 up
sudo dhclient eth0

```Which gave me a working internet connection. I hope this helps anyone with similar issues.

Cheers

---

### Post by 2manyhobbeez on 2011-02-12
I have an Intel 82567LM ethernet adapter which does not work for me in Kubuntu 10.4 (or any other distro that I have tried, including Suse). I downloaded the Intel driver from their website and then tried to build/install it but am having fundamental problems. Hopefully it's just my unfamiliarity with with the bird that is the problem.

The basic issue is that I can't run make. It says some headers are missing. I read somewhere that you have to do a 
sudo apt-get install build-essential

and a 
sudo apt-get install linux-headers-server

first. Of course I have to get these from the cd since I have no network, so I preceeded these commands with a 
sudo apt-cdrom add

command which looks like it works. However the subsequent apt-get install commands don't look like they work. There's a lot of error messages pertaining to not being able to connect with the http sources that must be in /etc/apt/sources.lst of course. But it really doesn't look like anything significant happens and anyways the make command still complains about the missing headers.

Am I doing something wrong here?

thanks, george

---

### Post by chili555 on 2011-02-12
Let's see why the native driver is not doing its job. Please run and post:```
sudo modprobe e1000e
dmesg | grep e100
```Thanks.

---

### Post by 2manyhobbeez on 2011-02-13
Here you go. Since I have no network on the linux side of my dual boot sys it is very difficult to communicate.

Modprobe returned nothing at all.

george@Kubuntu:~$ sudo modprobe e1000e
[sudo] password for george: 
george@Kubuntu:~$ sudo modprobe e1000e
george@Kubuntu:~$ dmesg | grep e100

[    0.187080] pci 0000:00:1f.5: reg 24: [io  0xe100-0xe10f]
[    4.579824] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[    4.579827] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
[    4.579868] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.579877] e1000e 0000:00:19.0: setting latency timer to 64
[    4.579972] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[    4.811352] e1000e 0000:00:19.0: (unregistered net_device): The NVM Checksum Is Not Valid
[    4.821687] e1000e 0000:00:19.0: PCI INT A disabled
[    4.821693] e1000e: probe of 0000:00:19.0 failed with error -5
george@Kubuntu:~$

---

### Post by chili555 on 2011-02-13
> 4.811352] e1000e 0000:00:19.0: (unregistered net_device): The NVM Checksum Is Not ValidThis is a well known issue: [https://bugzilla.kernel.org/show_bug.cgi?id=11382](https://bugzilla.kernel.org/show_bug.cgi?id=11382)

Here is a fix: [http://ubuntuforums.org/showthread.php?t=1276211&page=4](http://ubuntuforums.org/showthread.php?t=1276211&page=4)

See post #35 and following.

I had actually thought it was fixed in later Ubuntu versions. What does this tell us?```
modinfo e1000e | grep -i version
```

---

### Post by 2manyhobbeez on 2011-02-13
george@Kubuntu:~$ modinfo e1000e | grep -i version
version:        1.0.2-k4
srcversion:     A664BFB98E9F21DA03E6A17
vermagic:       2.6.35-22-generic-pae SMP mod_unload modversions 686 
george@Kubuntu:~$ ^C
george@Kubuntu:~$

---

### Post by 2manyhobbeez on 2011-02-14
I note that the thread you referred to ('Here is a fix') does a make in the middle of it. My original post above says that I can't do a make, apparently make is not installed. I need to know how to install it from the dvd since I can't connect to the Internets.

Thanks for the advice so far.

george.

---

### Post by 2manyhobbeez on 2011-02-14
Actually make is working. I failed to notice that it is getting part way thru the intel makefile before it fails on something in there. I'll try the other ('Here is a fix') solution suggested by chili555.

---

### Post by chili555 on 2011-02-14
How are you getting along? Is it building? Do you need some more help?

---

### Post by 2manyhobbeez on 2011-02-14
Nope. The fact is I have to compile the Intel code and I can't do that. It fails in the makefile, I think on trying to execute gcc. The error message I see doing make is 'Compiler not found' at line 124 which is the next to last line in the code segment below.


```
# pick a compiler
ifneq (,$(findstring egcs-2.91.66, $(shell cat /proc/version)))
  CC := kgcc gcc cc
else
  CC := gcc cc
endif
test_cc = $(shell $(cc) --version > /dev/null 2>&1 && echo $(cc))
CC := $(foreach cc, $(CC), $(test_cc))
CC := $(firstword $(CC))
ifeq (,$(CC))
  $(error Compiler not found)
endif
```

If I try to run gcc at the command line I get this.

```
george@Kubuntu:~/Downloads/e1000e-1.2.20/src$ sudo gcc
sudo: gcc: command not found
```

But if I try to install gcc I get errors from the package manager pgm (I forget the name) that says it can't find the necessary parts on the DVD. I get similar results if I try to install from the command line after doing apt-cdrom add. There's something fundamentally wrong here and I'm beginning to run out of patience with it.

---

### Post by chili555 on 2011-02-14
Generally, to compile, you need build-essential and linux-headers-generic. I thought they were on the install DVD. Once you have added the DVD as a source, open System > Administration > Synaptic and see if they are there to install. gcc is a component of build-essential.

We might be able to figure out how to get them if you have a USB key.


Before you try again, preceed your commands with 'make clean.'  It will, as the name suggests, wipe the slate clean and give you a fresh start.

---

### Post by 2manyhobbeez on 2011-02-14
I'm thinkin the files just don't exist on the dvd. I can't find synaptic but I am running KPackageKit and it complains:

Package download failed. Please check your network connectivity. Then under details...

E: Error cdrom://Kubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101008)/ maverick/main libc-dev-bin i386 2.12.1-0ubuntu6
File not found

Where would these files (for build-essential, et. al.) be located on the dvd? I could browse and see if they are on there.

---

### Post by chili555 on 2011-02-14
I am not sure where it is on the DVD; I don't have that particular one. However, if it's on the DVD, you ought to be able to do, in a terminal:```
sudo apt-cdrom add
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

You might also get the packages and their dependencies here: [http://packages.ubuntu.com/maverick/build-essential](http://packages.ubuntu.com/maverick/build-essential)

[http://packages.ubuntu.com/maverick/devel/linux-headers-2.6.35-22-generic](http://packages.ubuntu.com/maverick/devel/linux-headers-2.6.35-22-generic)

If your kernel version is not 2.6.35-22-generic, look around in packages/ubuntu.com for the correct version. Check with:```
uname -r
```

Of course, apt-get will complain loudly when it can't get on line, but, if it's available, it should grab the files off the DVD.

---

### Post by 2manyhobbeez on 2011-02-15
I made progress. I downloaded the Ubuntu 32 bit live cd image and loaded it in place of the Kubuntu os. Now I can compile the driver just fine. But now I'm to the point where I'm supposed to be able to do:
sudo ifconfig eth0 <ip adr>

but it says no such device because it doesn't know about eth0 I guess. I tried a reboot but that made no diff. I'll go look around and see how to configure that unless you know a way. I really have no clue.

Ya gotta wonder why the Kubuntu disk would be different than the Ubuntu disk. I downloaded the K DVD so it's not like they ran out of room.

Thanks for the help.

george

---

### Post by chili555 on 2011-02-15
Let's see if it got compiled correctly:```
modinfo e1000e | grep -i version
```We are looking for a later version than before:> modinfo e1000e | grep -i version
version: 1.0.2-k4Let's also look for kernel messages:```
dmesg | grep e100
```I have my fingers crossed!

---

### Post by 2manyhobbeez on 2011-02-16
I finally got the network up, running Ub* 10.10 by following the instructions in the link in post 17 above. But I really wanted the KDE interface in Kub* so I installed Kub* 10.10 in place of the working Ub*. Then I tried to replicate the steps that worked in Ub* to compile and install the new driver, but trying to use the Ub* CD in the drive (since I couldn't make any progress using the proper Kub* DVD). All hell broke loose (msgs indicating wrong disk, can't find files, etc.).

Alright, workaround #2 then. I already had the precompiled e1000e.ko file saved from the Ub* successful compile. I'll just cp it into wherever the driver file lives (can't remember the path now) and fake it out. Nope. System doesn't like that file. I don't know how to do a proper install without using make so if somebody knows if that can be done using the cross-compiled ko file let me know.

OK, then. Workaround #3. I reinstalled Ub* 10.10, reestablished the network, and then loaded the kde interface. That went OK until I tried to use it. When booted the the KDE interface came up all the way through the login screen and then it flipped back to the gnome desktop. All the kde apps are there (along with the gnome apps). but the i'face is wrong. I just don't get it.

Maybe I need to go to the Kub* forum to fix the make issue. Otherwise, I give up.

Thanks to Chili555 for the assistance. I appreciate that.
g

---

