---
title: "Trying to get dial up working"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by dennyx13 on 2009-07-24
Hey i'm trying to get dial up working on a compaq presario f500. i have the newest distro of crunchbang based off of jaunty. 
I ran scanModem, and i have the results, but unfortunately the email i'm supposed to send it to doesn't seem to be valid. can someone figure out what i need to do from the results?
i'm kinda new to linux so no clue about any of this. 
liking it so far. i'm dual booting in windows 7 to use the net atm
but here's the results from scanmodem:

>  Only plain text email is forwarded by the  [EMAIL="Discuss@Linmodems.org"]Discuss@Linmodems.org[/EMAIL] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.28-13-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [EMAIL="Discuss@Linmodems.org"]Discuss@Linmodems.org[/EMAIL] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.28-13-generic (buildd@vernadsky) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009
 scanModem update of:  2009_07_17

The dialer utility package WVDIAL does not appear to be installed on your System. 
Please read Modem/DOCs/wvdial.txt

 There are no blacklisted modem drivers in /etc/modprobe*  files 
 Potentially useful modem drivers now loaded are:
         snd_hda_intel       

Attached USB devices are:
 ID 0718:0492 Imation Corp. 
 ID 1058:0704 Western Digital Technologies, Inc. 
If a cellphone is not detected, see [http://ubuntuforums.org/archive/index.php/t-878554.html](http://ubuntuforums.org/archive/index.php/t-878554.html)
A sample report is:  [http://linmodems.technion.ac.il/bigarch/archive-nineth/msg00578.html](http://linmodems.technion.ac.il/bigarch/archive-nineth/msg00578.html)

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to [EMAIL="discuss@linmodems.org"]discuss@linmodems.org[/EMAIL]

For candidate card in slot 00:10.1, firmware information and bootup diagnostics are:
 PCI slot    PCI ID        SubsystemID    Name
 ----------    ---------    ---------    --------------
 00:10.1    10de:026c    103c:30b7    Audio device: nVidia Corporation MCP51 High Definition Audio 

 Modem interrupt assignment and sharing: 
 18:          2        375   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:10.1 ----
[    0.504277] pci 0000:00:10.1: reg 10 32bit mmio: [0xb0000000-0xb0003fff]
[    0.504301] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.504305] pci 0000:00:10.1: PME# disabled
[    1.541413] pci 0000:00:10.1: Enabling HT MSI Mapping
[   15.121224] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 18 (level, high) -> IRQ 18
[   15.121366] HDA Intel 0000:00:10.1: setting latency timer to 64

 The PCI slot 00:10.1 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [EMAIL="discuss@linmodems.org"]discuss@linmodems.org[/EMAIL]
 if help is needed.
 


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.18
The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-00: CONEXANT Analog : CONEXANT Analog : playback 1 : capture 1
00-01: Conexant Digital : Conexant Digital : playback 1

about /proc/asound/cards:
------------------------
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xb0000000 irq 18

 PCI slot 00:10.1 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-intel.ko
UNEXPECTED HDA diagnostic outcome.
=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:10.1:
    Modem chipset  detected on
NAME="Audio device: nVidia Corporation MCP51 High Definition Audio "
CLASS=0403
PCIDEV=10de:026c
SUBSYS=103c:30b7
IRQ=18
HDA=10de:026c
SOFT=10de:026c.HDA
ArchivedChip=0x14f12bfa
CodecClass=14f1
IDENT=hsfmodem
Driver=hsfmodem-drivers

 For candidate modem in:  00:10.1
   0403 Audio device: nVidia Corporation MCP51 High Definition Audio 
      Primary device ID:  10de:026c
    Subsystem PCI_id  103c:30b7 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: 0x14f12bfa
                        
      

Support type needed or chipset:    hsfmodem


For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read DOCs/Conexant.txt

 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem-7.80.02.02full_k2.6.28_13_generic_ubuntu_i386.deb.zip 
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
your KernelVersion:    2.6.28_13_generic
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

Support for Conexant chips hosted on High Definition Audio cards may require
installation of additional packages, one of the alsa-driver-linuxant packages
on  [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)  At the same time download the 
alsa-driver-1.0.17-1.patch , in case it prove to be later needed. During the
hsfmodem install, there will be a message if there is necessary installation of
alsa-driver-linuxant

The installation command for a .deb suffic packages is, with root/adm permission:
  sudo dpkg -i hsf*.deb
while for .rpm suffix it is, with:
  rpm -i hsf*.rpm

There may a message that "Dependencies" are not satisfied.  In this case the Ubuntu/Debian packages to be installed are linux-libc-dev & libc6-dev. Package
names may be different for other Linuxes. If not on your install CD, these
packages can be searched for at [http://packages.ubuntu.com](http://packages.ubuntu.com).  After download,
they can be coinstalled with:
    sudo dpkg -i li*.deb
Again try the alsa-driver-linuxant

There may be a message that the patch must be applied.  In this case get the
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.17.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.17.tar.bz2) 
Under Linux, this package is unpacked with:
$ tar jxf alsa*.tar.bz2
Next the patch is applied with:
$ patch -p0 < alsa-driver-1.0.17-1.patch

See [http://linmodems.technion.ac.il/bigarch/archive-eighth/msg00838.html](http://linmodems.technion.ac.il/bigarch/archive-eighth/msg00838.html)
for details on compiling and installing replacement snd-hda-intel + its
dependent drivers.
After the installation is completed, rerun the hsfmodem installation.
Reboot and try to detect the modem with Root permission:
    sudo wvdialconf  /etc/wvdial.conf

 Read DOCs/Conexant.txt

Writing DOCs/Conexant.txt


 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 The kernel was compiled with gcc version 4.3.3 and a compiler is not installed

 The code linking utility, ld, may be needed and is provided in the binutils package 
 The patch utility is needed and is needed for compiling ALSA drivers, and possibly others. 

 If compiling is necessary packages must be installed, providing:
    gcc-4.3 


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
    -rwsr-xr-- 1 root dip 277352 2009-02-20 11:25 /usr/sbin/pppd

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

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0 eth1
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------


---

