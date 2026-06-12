---
title: "Wireless does not work, Broadcom BCM4312"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by kuraykillua on 2010-07-28
So I've just installed Ubuntu on 2 computers, and I'm new to it. However I'm not new to computers. The problem I'm currently running into on one of the computers is that the wireless will not detect any connections, despite there being many.
The computer is a HP Compaq v6203AU using the wireless card Broadcom BCM4312 [14e4:4312].
I've went through dozens of walkthroughs, encountering errors in every single one of them, I've spent 8 hours on this one problem and extremely frustrated. It seem to be a problem with the driver that comes as default, and I'm lost at what to do. I've searched this forum many times and tried quite a few of the suggestions.
The terminal command "lspci -nn | grep 14e4" returns the following:
03:00.0 Network Controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312]

ifconfig returns the following

eth0      Link encap:Ethernet  HWaddr 00:23:8b:b2:ab:d3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7072 (7.0 KB)  TX bytes:7072 (7.0 KB)


So, what other information should I provide? I've read the guidelines  and don't seem to see anything else relevant. The computer has no  internet access as there is nowhere to connect except through wireless. Thanks for your time, have a good day.

---

### Post by snowpine on 2010-07-28
Welcome to the forums!

Best source of information is always the official Ubuntu documentation:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

If you get stuck at a particular step, post back with the details, and I'll try my best to help! :)

---

### Post by kuraykillua on 2010-07-28
Yep, I've tried that page before.
Under B43/STA No internet access, step 1, while installing the package bcmwl-kernel-source, Synaptic package manager returns the following:
An error occurred
THe following details are provided:
E: b43-fwcutter: subprocess installed post-installation script returned error exit status 4
E: bcmwl-kernel-source: subprocess installed post-installation script returned error exit status 6

ADDITIONAL INFO:
So even if I ignore that, and go to system, admin, hardware drivers, one for Broadcom STA wireless driver shows up, however when I click activate, I get the following message:
SystemError: installArchives() failed

---

### Post by snowpine on 2010-07-28
Have you tried the b43 instructions? (I was under the impression the b43/sta hybrid was for Dell only.)

Any chance you can temporarily connect via wired?

If the Ubuntu documentation is inaccurate :( you could always try Broadcom's own instructions: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by drpjkurian on 2010-07-28
Hi
See the instructions in [this]("http://linuxwireless.org/en/users/Drivers/b43") page for ubuntu

---

### Post by kuraykillua on 2010-07-28
BCM4312 says mostly found on Dell, didn't say exclusively. Also, even with the B43 instructions before step 1, while installing b43-fwcutter, it fails. it says: Failed to install package 'b43-fwcutter_012-1build1_i386.deb'
And the terminal goes something like
Resolving downloads.openwrt.org... failed: Name or service not known.
Wget: unable to resolve host address 'download.openwrt.org'

It seems like it needs internet thus I don't understand why it's under the "no internet" section.

With Broadcom's instructions, I've followed it to the point where it says activate the drivers under hardware drivers, which I've done. It returns the error I mentioned earlier.

---

### Post by snowpine on 2010-07-28
> **kuraykillua said:**
> And the terminal goes something like
Resolving downloads.openwrt.org... failed: Name or service not known.
Wget: unable to resolve host address 'download.openwrt.org'

It seems like it needs internet thus I don't understand why it's under the "no internet" section.

Sounds like a bug. :( 

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by kuraykillua on 2010-07-28
Following instructions from drpjkurian, on [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

It says my card is supported and I need B43 drivers.
It also says for Ubuntu, simply installing B43-fwcutter will solve everything. The following is what the prompt gave me.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up b43-fwcutter (1:012-1build1) ...
--2010-07-28 21:29:34--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--configure):
 subprocess installed post-installation script returned error exit status 4
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Removing old bcmwl-5.60.48.36+bdcom DKMS files...

------------------------------
Deleting module version: 5.60.48.36+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-21-generic
Building for architecture i686
Building initial module for 2.6.32-21-generic
/usr/sbin/dkms: line 35: patch: command not found

Error! Application of patch 0001-MODULE_LICENSE.patch failed.
Check /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
 b43-fwcutter
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
kuray@Vega:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up b43-fwcutter (1:012-1build1) ...
--2010-07-28 21:34:38--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--configure):
 subprocess installed post-installation script returned error exit status 4
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Removing old bcmwl-5.60.48.36+bdcom DKMS files...

------------------------------
Deleting module version: 5.60.48.36+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-21-generic
Building for architecture i686
Building initial module for 2.6.32-21-generic
/usr/sbin/dkms: line 35: patch: command not found

Error! Application of patch 0001-MODULE_LICENSE.patch failed.
Check /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
 b43-fwcutter
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)



So, more errors. This baffles me...

---

### Post by snowpine on 2010-07-28
I think you are skipping a couple of important steps:

> Step 1.

On a computer with Internet access, download the required firmware files from [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

Step 2.

Copy the downloaded files to your home folder and execute the following commands consecutively in a terminal to extract and install the firmware:

~$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2
~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

I should add, however, I've never had to do this personally--I've always just connected my BCM4312 netbook through a wired connection, problem solved in 2 minutes.

---

### Post by kuraykillua on 2010-07-28
I've tried those steps before, it gave me an error last time, so just in case I re-downloaded the files on another computer... and it worked.
I think what happened is when I did those steps the first time the file was corrupt, thus not working. I am SOO glad with all your help this problem was solved after I worked on this for hours. Thank you all for your time and efforts... now if you don't mind I'm going to go enjoy the awesomeness of Ubuntu. Hopefully with no more errors :)

---

### Post by wobert on 2010-07-28
I have the same issue, 
I also have a thread for this... The only difference is I do have a dell laptop...
Hopefully someone can help

---

### Post by drpjkurian on 2010-07-29
Hi
Please mark this thread as solved

---

### Post by GriffiN on 2010-10-19
well, as i could not find the solution even on a marked as solved ill put the solution i had

first

sudo apt-get remove --purge firmware-b43-installer

then

sudo apt-get install firmware-b43-lpphy-installer

worked inmediately

taken from:
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/655111](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/655111)

---

