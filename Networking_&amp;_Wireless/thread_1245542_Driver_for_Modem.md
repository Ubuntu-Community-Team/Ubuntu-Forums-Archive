---
title: "Driver for Modem"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by Willn21 on 2009-08-20
I am trying to set up a fax server
I am having some trouble finding the driver for my modem
Can someone tell me where to find the driver and how to install it

Here is my modemdata.txt

 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.28-11-server 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.28-11-server (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 02:48:10 UTC 2009
 scanModem update of:  2009_08_15

The dialer utility package WVDIAL does not appear to be installed on your System. 
For Ubuntu Jaunty users, there are at the bottom of [http://linmodems.technion.ac.il/packages/:](http://linmodems.technion.ac.il/packages/:)
     wvdial_jaunty_amd64.zip   for x86_64, 64 bit bus systems.
     wvdial_jaunty_i386.zip    for 32 bit systems.
These are about 1 MB in size.  After downloaded and copied into your Linux partition:
$ unzip wv*.zip
Within the new folder:
$ sudo dpkg -i *.deb
will  complete the wvdial installation
Please read Modem/DOCs/wvdial.txt for usage information.
 There are no blacklisted modem drivers in /etc/modprobe*  files 
 Potentially useful modem drivers now loaded are:
                

Attached USB devices are:
 ID 07cc:0200 Carry Computer Eng., Co., Ltd 6-in-1 Card Reader
 ID 413c:2003 Dell Computer Corp. Keyboard
If a cellphone is not detected, see [http://ubuntuforums.org/archive/index.php/t-878554.html](http://ubuntuforums.org/archive/index.php/t-878554.html)
A sample report is:  [http://linmodems.technion.ac.il/bigarch/archive-nineth/msg00578.html](http://linmodems.technion.ac.il/bigarch/archive-nineth/msg00578.html)

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to [email]discuss@linmodems.org[/email]

For candidate card in slot 00:08.0, firmware information and bootup diagnostics are:
 PCI slot    PCI ID        SubsystemID    Name
 ----------    ---------    ---------    --------------
 00:08.0    16ec:2f00    16ec:010a    Communication controller: U.S. Robotics USR5660A 

 Modem interrupt assignment and sharing: 
 11:      28510    XT-PIC-XT        uhci_hcd:usb2, eth0
 --- Bootup diagnostics for card in PCI slot 00:08.0 ----
[    0.846693] pci 0000:00:08.0: reg 10 32bit mmio: [0xee000000-0xee00ffff]
[    0.846702] pci 0000:00:08.0: reg 14 io port: [0xd000-0xd007]
[    0.846740] pci 0000:00:08.0: PME# supported from D0 D3hot
[    0.846746] pci 0000:00:08.0: PME# disabled

 The PCI slot 00:08.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:08.0:
    Modem chipset  detected on
NAME="Communication controller: U.S. Robotics USR5660A "
CLASS=0780
PCIDEV=16ec:2f00
SUBSYS=16ec:010a
IRQ=11
IDENT=hsfmodem
Driver=hsfmodem-drivers

 For candidate modem in:  00:08.0
   0780 Communication controller: U.S. Robotics USR5660A 
      Primary device ID:  16ec:2f00
 Support type needed or chipset:    hsfmodem
 


For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read DOCs/Conexant.txt

 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem-7.80.02.02full_k2.6.28_11_server_ubuntu_i386.deb.zip 
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See DOCs/Testing.txt  for details.
 
 The directions following below need only be pursued, if the above procedures are not adequate.

Start at [http://www.linuxant.com/drivers/hsf/downloads-license.php](http://www.linuxant.com/drivers/hsf/downloads-license.php) to find the
hsfmodem package matching your System. For several Linux distros, there are
precompiled drivers matched to specific kernels. These have within the FileName,
your KernelVersion:    2.6.28_11_server
They can be found through [http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php) 
A more precise location may be given a few paragraphs below.
If an EXACT Match with your your KernelVersion is not found, one of the 
"Generic packages with source" near the bottom of the page must be used.
Downloaded packages must be moved into the Linux partition (home folder is OK)
and unzipped with:
    unzip hsf*.zip
The installation command for a .deb suffic packages is, with root/adm permission:
  sudo dpkg -i hsf*.deb
while for .rpm suffix it is, with:
  rpm -i hsf*.rpm
 Read DOCs/Conexant.txt

Writing DOCs/Conexant.txt


 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.3.3
             and the compiler used in kernel assembly: 4.3.3

 linux-headers-2.6.28-11-server resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
     linux-headers-2.6.28-11-server


If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
    -rwsr-xr-- 1 root dip 277352 2009-02-20 12:25 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
    $ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
    sudo chmod a+x /usr/sbin/pppd

Checking settings of:    /etc/ppp/options
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
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0 virbr0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:

     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by Willn21 on 2009-08-20
bump

---

