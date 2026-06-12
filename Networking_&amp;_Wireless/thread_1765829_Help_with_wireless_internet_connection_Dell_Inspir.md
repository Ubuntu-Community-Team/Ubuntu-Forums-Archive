---
title: "Help with wireless internet connection Dell Inspiron N7010"
date: 2011-05-23
forum: Networking &amp; Wireless
---

### Post by gurpreet9 on 2011-05-23
Hello All

I recently installed ubuntu 10.04 on my dell inspiron N7010 laptop. I installed it as a software on windows. So it is a dual boot system now.

Since the time I installed ubuntu, I am facing following problems:

1. No wireless networks are detected. Hence, not able to access internet
2. Touch pad not working

In my understanding, drivers need to be installed for wireless connection and for touch pad. I tried contacting Dell support. They refused saying that they have given Windows 7 and won't provide me with the drivers.

Can anyone help me solve these problems? I would love to shift completely to open source and that was the reason for installing ubuntu. Any help would be much appreciated.

Thanks and Regards
GS

---

### Post by chili555 on 2011-05-23
First, let's see what kind of wireless device you have. Please open Applications > Accessories > Terminal and run and post:```
lspci -nn
```My karma and mojo are very poor today; I'll bet it's a Broadcom. Do you have wired ethernet access if we need it?

---

### Post by gurpreet9 on 2011-05-25
Here is the output when I enter the code:


   gurpreet@ubuntu:~$ lspci -nn
  00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 18)
  00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 18)
  00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
  00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
  00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
  00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
  00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
  00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
  00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
  00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
  00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b0b] (rev 06)
  00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06)
  00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
  00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
  03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
  04:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
  ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 05)
  ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 05)
  ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 05)
  ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 05)
  ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 05)
  ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 05)
  [FONT=&quot]gurpreet@ubuntu:~$[/FONT]



I have tried using wired LAN, but it didn't work by default. Do I have to do change setting to be able to use it?

Also, I have installed ubuntu on windows. Is that a hindrance and is it better to create separate partition and install ubuntu as a standalone OS?

---

### Post by chili555 on 2011-05-26
> 03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)> My karma and mojo are very poor today; I'll bet it's a Broadcom.What do you know! Your Broadcom works with the module *wl*. It is very easy to get with a wired ethernet connection and very tough without. 

Your wired ethernet works with the driver atl1c which is very difficult to download and install in 10.04 but is included by default in 11.04. However, 11.04 has difficulties with Broadcom drivers, especially on Dells! Quite a Catch 22, isn't it?!

Since either the wired or wireless will be equally hard, let's try wireless, unless you disagree.

Here is where you will be getting the packages you need: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) Notice that the search tool at the bottom asks for the Distribution; you want Lucid, which is 10.04.

You may find some of them on the installation CD. Browse the CD, and look in pool > main > <letter the package name begins with>. For example, if you were looking for dkms, you would look in pool > Main > d > dkms.

I assume you can download all these to your windows partition and transfer them on a USB key or otherwise to your Ubuntu install. Please get: [http://packages.ubuntu.com/lucid/bcmwl-kernel-source](http://packages.ubuntu.com/lucid/bcmwl-kernel-source)

Be sure to download the architecture; that is, 32- or 64-bit to match what you have installed.

Notice the red bullets that indicate the packages that are required to install bcmwl-kernel-source. Download those, too. When you download linux-headers-generic, you will find that it depends on linux headers matching your running kernel, so you might as well grab that now. Open a terminal and run the command:```
uname -r
```That will tell you the kernel version you are running. Download the matching kernel headers, for example, linux-headers-2.6.32-14-generic. Substitute your details here.

Once you have all the packages on the USB key, drag and drop them to your Ubuntu desktop. Install them in a terminal with:```
sudo dpkg -i dkms*.deb
```The wildcard * means you don't have to type out all the version information each time.

Of course, there may be even more packages that are dependencies, get them and install them, too, until it all goes perfectly. Obviously, post back if I can help you.> Also, I have installed ubuntu on windows. Is that a hindrance and is it better to create separate partition and install ubuntu as a standalone OS? It's not really a hindrance. It ought to be all the same.

I know this sounds very complicated, but if you go slowly and carefully, you will have wireless working easily. Ask if you get stuck. I'm here for you.

---

### Post by gurpreet9 on 2011-05-26
The kernel version is 2.6.32-24-generic.

Here is the output from running the code:
   [FONT=&quot]gurpreet@ubuntu:~/Desktop$ sudo dpkg -i dkms*.deb[/FONT]
  [FONT=&quot](Reading database ... 122375 files and directories currently installed.)[/FONT]
  [FONT=&quot]Preparing to replace dkms 2.1.1.2-2fakesync1 (using dkms_2.1.1.2-2fakesync1_all.deb) ...[/FONT]
  [FONT=&quot]Unpacking replacement dkms ...[/FONT]
  [FONT=&quot]Setting up dkms (2.1.1.2-2fakesync1) ...[/FONT]
   
  [FONT=&quot]Processing triggers for man-db ...[/FONT]
  [FONT=&quot]gurpreet@ubuntu:~/Desktop$ [/FONT]
  

What next?

---

### Post by chili555 on 2011-05-27
> **gurpreet9 said:**
> The kernel version is 2.6.32-24-generic.

Here is the output from running the code:
   [FONT=&quot]gurpreet@ubuntu:~/Desktop$ sudo dpkg -i dkms*.deb[/FONT]
  [FONT=&quot](Reading database ... 122375 files and directories currently installed.)[/FONT]
  [FONT=&quot]Preparing to replace dkms 2.1.1.2-2fakesync1 (using dkms_2.1.1.2-2fakesync1_all.deb) ...[/FONT]
  [FONT=&quot]Unpacking replacement dkms ...[/FONT]
  [FONT=&quot]Setting up dkms (2.1.1.2-2fakesync1) ...[/FONT]
   
  [FONT=&quot]Processing triggers for man-db ...[/FONT]
  [FONT=&quot]gurpreet@ubuntu:~/Desktop$ [/FONT]
  

What next?Go back to the link I gave you and download bcmwl-kernel-source and all its dependencies; the ones with the red bullets. Install them just as you did dkms. You've done a perfect job so far. Keep going.> The kernel version is 2.6.32-24-generic.Then you will also need linux-headers-2.6.32-24-generic. Grab it and install it; you're doing very well.

---

### Post by gurpreet9 on 2011-05-28
Please see attachments for the packages installed and the packages which I was unable to install.

The following error message was coming:


   [FONT=&quot]gurpreet@ubuntu:~/Desktop$ sudo dpkg -i linux-libc-dev_2.6.32-30.59_i386.deb [/FONT]
  [FONT=&quot][sudo] password for gurpreet: [/FONT]
  [FONT=&quot]dpkg: error processing linux-libc-dev_2.6.32-30.59_i386.deb (--install):[/FONT]
  [FONT=&quot] package architecture (i386) does not match system (amd64)[/FONT]
  [FONT=&quot]Errors were encountered while processing:[/FONT]
  [FONT=&quot] linux-libc-dev_2.6.32-30.59_i386.deb[/FONT]
  [FONT=&quot]gurpreet@ubuntu:~/Desktop$[/FONT]
  

Can you suggest a solution for this error?

Thanks in advance...

---

### Post by chili555 on 2011-05-28
> Can you suggest a solution for this error?It appears you have a 64-bit system but downloaded a 32-bit package. Go back and download the 64-bit package.

That little i386 refers to 32-bit.

---

### Post by gurpreet9 on 2011-05-29
Hi...thanks for the reply..I downloaded 'amd64" packages. Here is a list of what I have installed besides the two packages earlier installed:  

gcc_4.4.3-1ubuntu1_amd64.deb
libc-dev-bin_2.11.1-0ubuntu7.7_amd64.deb
linux-libc-dev_2.6.32-30.59_amd64.deb


Packages not installed:
libc6_2.11.1-0ubuntu7.7_amd64.deb
libc6-dev_2.11.1-0ubuntu7.7_amd64.deb

These packages could not be installed as an error message was coming:
   gurpreet@ubuntu:~/Desktop/New 64-bit$ sudo dpkg -i libc6-dev_2.11.1-0ubuntu7.7_amd64.deb
  (Reading database ... 122375 files and directories currently installed.)
  Preparing to replace libc6-dev 2.11.1-0ubuntu7.2 (using libc6-dev_2.11.1-0ubuntu7.7_amd64.deb) ...
  Unpacking replacement libc6-dev ...
  dpkg: dependency problems prevent configuration of libc6-dev:
   libc6-dev depends on libc6 (= 2.11.1-0ubuntu7.7); however:
    Package libc6 is not configured yet.
  dpkg: error processing libc6-dev (--install):
   dependency problems - leaving unconfigured
  Errors were encountered while processing:
   libc6-dev
  gurpreet@ubuntu:~/Desktop/New 64-bit$
  

Now after I was done with all this, an alert was coming in the tray area saying that I need to run apt-get/package manager for the inconsistencies. I don't know whether that is relevant to what I am doing, but I didn't get that alert earlier.

Can you let me know what more packages need to be installed or what is the next course of action?

---

### Post by chili555 on 2011-05-29
> libc6-dev depends on libc6 (= 2.11.1-0ubuntu7.7); however:
Package libc6 is not configured yet.That's sort of Linux-speak for "we can't install the development headers for a package that's not yet installed." So go get libc6-[COLOR="Red"]**2.11.1-0ubuntu7.7**[/COLOR] *ONLY* (not libc6-2.11.1-0ubuntu7.6 or any other version but what it asked for exactly) and install it. Then go on forward with the libc6-dev package.

If you get any other dependency issues, you know what to do; get what it says it's missing in the exact version and AMD64.
You're getting close!

---

### Post by gurpreet9 on 2011-05-30
See the attached file. I spent roughly 4 hours trying to resolve this. Went back and forth into windows to download dependencies and then coming back to linux. But all efforts went in vain as there is a consistent error. I have started to lose hope that this will ever work :(

I don't whether I should be asking for any more of your time as I am not heading anywhere with this...you have helped a lot so far.......

---

### Post by chili555 on 2011-05-30
> I don't whether I should be asking for any more of your time as I am not heading anywhere with thisThat's entirely up to you. I'm in this forum for the long pull. If I'm not spending my time helping you, I'll be spending my time helping someone else. I have time. Your document lists several packages that need to be downloaded and installed. Every time you see "Package *whatever* is not configured yet" that is another package you need to install. Make a big list and get them all in one trip.

---

### Post by clayday27 on 2011-07-06
may you please help me? i am having a very simliar issue. I installed 11.04 out of the box and the wireless wont work.

---

### Post by chili555 on 2011-07-06
> **clayday27 said:**
> may you please help me? i am having a very simliar issue. I installed 11.04 out of the box and the wireless wont work.Please start your own new thread and post:```
lspci -nn | grep 0280
rfkill list all
```Reply here with a link to your thread and I'll be very happy to help.

---

