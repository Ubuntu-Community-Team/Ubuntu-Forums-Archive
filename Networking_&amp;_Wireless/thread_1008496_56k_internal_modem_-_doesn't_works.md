---
title: "56k internal modem - doesn't works"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by zococo on 2008-12-11
Hello,

I would like to use the 56K internal modem on my asus M50 Sv laptop working with Ubuntu Hardy Heron and it doesn't works.

I looked for the solution on many web pages, I intended to install and reinstall alsa and nothing happened. When I run  GNOME PPP the soft says that it doesn't find any modem.

I used scanmodem and the file modemData says :
>  Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.24-22-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.24-22-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Nov 24 18:32:42 UTC 2008
 scanModem update of:  2008_11_06

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
 ID 056a:0062 Wacom Co., Ltd 
 ID 04b8:0802 Seiko Epson Corp. Stylus CX3200
 ID 174f:5a31  
 ID 04cc:1521 Philips Semiconductors USB 2.0 Hub
 ID 08ff:1600 AuthenTec, Inc. 

USB modems not recognized

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:284b	1043:1763	Audio device: Intel Corporation 82801H 

 Modem interrupt assignment and sharing: 
 23:     444999     363694   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[   27.385331] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   27.385347] PCI: Setting latency timer of device 0000:00:1b.0 to 64


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.16
The modem cards detected by "aplay -l"  are: 
carte  0: Intel [HDA Intel], périphérique 6 : Si3054 Modem [Si3054 Modem]

The /proc/asound/pcm file reports:
-----------------------
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
00-02: ALC883 Analog : ALC883 Analog : capture 1
00-01: ALC883 Digital : ALC883 Digital : playback 1
00-00: ALC883 Analog : ALC883 Analog : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebf8000 irq 23

 PCI slot 00:1b.0 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.24-22-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
 The modem codec file for the HDA card is: /proc/asound/card0/codec#1
--------------------------------------------------------
Codec: Motorola Si3054
Address: 1
Vendor Id: 0x10573055
Subsystem Id: 0x10431316
Revision Id: 0x100700
Modem Function Group: 0x1

 The audio card hosts a softmodem chip:  0x10573055

The softmodem chip 0x10573055 is in principle supported by the COMM support of slmodemd 
and the joint snd-hda-intel audio+modem driver, begun with ALSA version 1.0.13.  
For HDA cards with ALC883 chips, an upgrade to ALSA verions 1.0.15 way be necessary. Instructions for Upgrading snd-hda-intel and its dependent driver set are at:
[http://linmodems.technion.ac.il/bigarch/archive-eighth/msg00838.html](http://linmodems.technion.ac.il/bigarch/archive-eighth/msg00838.html)

If not a Conexant modem, the driver snd-hda-intel with its dependent drivers:
snd_hda_intel         344856  6 
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd                    56996  21 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
----------
provide audio + modem support with the modem chip residing on the subsystem.
Any particular card can host any one of several soft modem chips. 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:1b.0:
	Modem chipset  detected on
NAME="Audio device: Intel Corporation 82801H "
CLASS=0403
PCIDEV=8086:284b
SUBSYS=1043:1763
IRQ=23
HDA=8086:284b
SOFT=8086:284b.HDA
CHIP=0x10573055
IDENT=slmodemd
SLMODEMD_DEVICE=hw:0,6
Driver=snd-hda-intel

 For candidate modem in:  00:1b.0
   0403 Audio device: Intel Corporation 82801H 
      Primary device ID:  8086:284b
    Subsystem PCI_id  1043:1763 
    Softmodem codec or chipset from diagnostics: 0x10573055
                               from    Archives: 
                        The HDA card softmodem chip is 0x10573055
      

Support type needed or chipset:	slmodemd supporting the snd-hda-intel audio+modem driver

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-hda-intel
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) 
 the package SLMODEMD.gcc4.2.tar.gz having a compiled slmodemd. Unpack under Linux with:
 	$ tar zxf SLMODEMD.gcc4.2.tar.gz
 and read instructions therein. But briefly, the modem is setup with command:
 	sudo slmodemd -c YOUR_COUNTRY --alsa hw:0,6
 reporting dynamic creation of ports:
	/dev/ttySL0 --> /dev/pts/N   , with N some number
 Read DOCs/Smartlink.txt and Modem/DOCs/YourSystem.txt for follow through guidance.

----------------end Softmodem section --------------

Writing DOCs/Intel.txt
Writing DOCs/Smartlink.txt
============ end Smartlink section =====================

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.2.3
             and the compiler used in kernel assembly: 4.2.4


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.2
   linuc_headers base folder /lib/modules/2.6.24-22-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are needed. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at [http://packages.ubuntu.com](http://packages.ubuntu.com)
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

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269256 2007-10-04 21:57 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

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
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

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
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------


the file /etc/default/sl-modem-daemon says :
> # NOTE: settings in /etc/defautls/slmodemd are used too

# set this to 1 to never run the daemon from the init script
# you can set it if you have an USB device, than the init script won't
# be started at boot (but when the USB device is plugged on)
DONTSTART=0

# This is the default configuration for the slmodem driver daemon
# running on Debian systems.
#	
# Edit device node and country code here ... 
#
# possible country codes are:
#
#   USA
#   GERMANY
#   BELGIUM
#   etc.
#   
#  use 'slmodemd --countrylist' to check out other countries
#
#
#SLMODEMD_DEVICE=slamr0
#SLMODEMD_COUNTRY=GERMANY

SLMODEMD_DEVICE=auto
#SLMODEMD_COUNTRY=USA
#USA enlevé et remplacé par France
SLMODEMD_COUNTRY=FRANCE
#
# Additional options for slmodemd, see "slmodemd -h" output for details.
# Do NOT set country or device name here!

OPTS=""

# force the start of the daemon even if old type modules seem to be
# installed (set it to 1)

FORCESTART=0

# set this to not see any hints of the init script on startup

# BEQUIET=1

# set this to not create the /dev/modem symlink

# NOSYMLINK=1

I really don't know what I can do to make work the modem.

Could somebody help me ? Thank you.

---

### Post by lingenfr on 2008-12-23
I have the same problem. There is no precompiled version for 2.6.24-22-generic on the linmodems site. I started with the slmodem and daemon package in the repositories and as noted elsewhere the modules will not build. I want to get this modem working to use with NCID. Thanks.

---

### Post by Perkins on 2009-01-28
A couple of the links in the instructions you posted go to pages which have more detailed instructions.

If you're having trouble compiling, start by installing the package build-essential.  If it still fails, read the compiler output.  It should give tell you what headers are missing.  You should be able to find them in the repository.

---

### Post by lingenfr on 2009-04-11
> **Perkins said:**
> A couple of the links in the instructions you posted go to pages which have more detailed instructions.

If you're having trouble compiling, start by installing the package build-essential.  If it still fails, read the compiler output.  It should give tell you what headers are missing.  You should be able to find them in the repository.

Obviously we have build-essential or we wouldn't have gotten this far. If we were able to interpret the compiler output and figure it out, we wouldn't be posting here. We still need help.

---

