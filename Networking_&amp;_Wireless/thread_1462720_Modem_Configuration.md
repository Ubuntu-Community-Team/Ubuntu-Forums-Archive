---
title: "Modem Configuration"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by MughalShahzad on 2010-04-26
Following is my modem data, extracted from ModemData.txt. I am trying to configure my modem, kindly go through the following information and give me guide line to figure it out.

Thanks & Regards

```

 Only plain text email is forwarded by the  Discuss@Linmodems.org List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.31-14-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: http://www.linux.org/groups/index.html.
They will know your Country's modem code, which may be essential for dialup service.
Responses from Discuss@Linmodems.org are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org 
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu ,  ALSA_version=1.0.20
Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009
 scanModem update of:  2010_03_18

Distrib_ID=Ubuntu
DistribCodeName=karmic
AptRepositoryStem=http://pk.archive.ubuntu.com/ubuntu/


Presently install your Linux Distributions dkms package. It provides for automated driver updates,
following upgrade of your kernel.  For details see http://linux.dell.com/projects.shtml#dkms

 There are no blacklisted modem drivers in /etc/modprobe*  files 

 Potentially useful modem drivers now loaded are:
                  

Attached USB devices are:
 ID 0951:1607 Kingston Technology Data Traveler 2.0
If a cellphone is not detected, see http://ubuntuforums.org/archive/index.php/t-878554.html
A sample report is:  http://linmodems.technion.ac.il/bigarch/archive-nineth/msg00578.html

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to discuss@linmodems.org

Candidate PCI devices with modem chips are:
01:08.0 Communication controller: Agere Systems 56k WinModem (rev 01)
High Definition Audio cards can host modem chips.

For candidate card in slot 01:08.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 01:08.0	11c1:0440	11c1:0440	Communication controller: Agere Systems 56k WinModem 

 Modem interrupt assignment and sharing: 
 --- Bootup diagnostics for card in PCI slot 01:08.0 ----
[    0.193214] pci 0000:01:08.0: reg 10 32bit mmio: [0xff8ff400-0xff8ff4ff]
[    0.193224] pci 0000:01:08.0: reg 14 io port: [0xecf8-0xecff]
[    0.193234] pci 0000:01:08.0: reg 18 io port: [0xe800-0xe8ff]
[    0.193276] pci 0000:01:08.0: supports D2
[    0.193280] pci 0000:01:08.0: PME# supported from D2 D3hot D3cold
[    0.193287] pci 0000:01:08.0: PME# disabled

 The PCI slot 01:08.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to discuss@linmodems.org
 if help is needed.
 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 01:08.0:
	Modem chipset  detected on
NAME="Communication controller: Agere Systems 56k WinModem "
CLASS=0780
PCIDEV=11c1:0440
SUBSYS=11c1:0440
IRQ=11
IDENT=Agere.DSP

 For candidate modem in:  01:08.0
   0780 Communication controller: Agere Systems 56k WinModem 
      Primary device ID:  11c1:0440
 Support type needed or chipset:	Agere.DSP
 


 The modem has a Lucent/Agere/LSI Mars or Apollo DSP (digital signal processing) chipset. 
Support packages for 2.6.n kernels are at:
 http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/ 
 http://packages.debian.org/sid/martian-modem-source/
Always use the most update for kernels after 2.6.20, currently martian-full-20080625.tar.gz
For kernels 2.6.20 and less, usr martian-full-20080407.tar.gz.

 See DOCs/AgereDSP.txt for Details.

 At http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/ get the martian-full-20080625.tar.gz and follow Readme-NOW.html
 0x0440 -- Mars 2 - data/fax/voice
-------------- end Agere Systems section -------------------

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.4.1
             and the compiler used in kernel assembly: 4.4.1

 The patch utility is needed for compiling ALSA drivers, and possibly others. 

 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.4
   linuc_headers base folder /lib/modules/2.6.31-14-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are needed. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at http://packages.ubuntu.com
 or comparable Repository for other Linux distros.
 When compiling ALSA drivers, the utility "patch" will also be needed.




If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through http://packages.ubuntu.com
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 277352 2009-02-20 22:25 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html

For guidance on FAX usage, get from http://linmodems.technion.ac.il/packages/  get faxing.tar.gz
It has samples for a modem using port /dev/ttySL0, which must be changed to match your modem's port.

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------



```

---

### Post by bapoumba on 2010-04-26
Moved to Networking.

---

