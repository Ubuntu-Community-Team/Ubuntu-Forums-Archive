---
title: "Modem Driver for Laptop"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by 9a8sy on 2009-03-26
I wasn't sure if Networking or Hardware was the best place for this post so I hope this is alright.

I have a Gateway laptop which I need to get an internal modem setup for dialup networking. I ran a utility to identify the modem which I will post below. After running it I downloaded what I thought was the correct driver then tried to configure KPPP dialer application. However it appears I have done something wrong. Any help here would be appreciated. The driver link I used was [http://linmodems.technion.ac.il/packages/smartlink/]("http://linmodems.technion.ac.il/packages/smartlink/")

I used the file SLMODEMD_gcc4.3_alsa1.0.17.tar.gz

My modem data was as follows:

--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009
 scanModem update of:  2009_02_21

 There are no blacklisted modem drivers in /etc/modprobe*  files 
 Potentially useful modem drivers now loaded are:
         snd_hda_intel       

Attached USB devices are:
 ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
 ID 046d:0991 Logitech, Inc. QuickCam Pro for Notebooks
If a cellphone is not detected, see [http://ubuntuforums.org/archive/index.php/t-878554.html](http://ubuntuforums.org/archive/index.php/t-878554.html)

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to [email]discuss@linmodems.org[/email]

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:27d8	107b:0366	Audio device: Intel Corporation 82801G 

 Modem interrupt assignment and sharing: 
 22:       1496          0   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[    0.608295] PCI: 0000:00:1b.0 reg 10 64bit mmio: [d4240000, d4243fff]
[    0.608353] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.608360] pci 0000:00:1b.0: PME# disabled
[   14.230149] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.230193] HDA Intel 0000:00:1b.0: setting latency timer to 64

 The PCI slot 00:1b.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.17
The modem cards detected by "aplay -l"  are: 
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]

The /proc/asound/pcm file reports:
-----------------------
01-00: USB Audio : USB Audio : capture 1
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
00-00: STAC92xx Analog : STAC92xx Analog : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd4240000 irq 22
 1 [U0x46d0x991    ]: USB-Audio - USB Device 0x46d:0x991
                      USB Device 0x46d:0x991 at usb-0000:00:1d.7-1, high speed

 PCI slot 00:1b.0 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.27-7-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.27-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko
 The modem codec file for the HDA card is: /proc/asound/card0/codec#1
--------------------------------------------------------
Codec: Motorola Si3054
Address: 1
Vendor Id: 0x10573057
Subsystem Id: 0x10001
Revision Id: 0x100100
Modem Function Group: 0x1

 The audio card hosts a softmodem chip:  0x10573057

The softmodem chip 0x10573057 is in principle supported by the COMM support of slmodemd 
and the joint snd-hda-intel audio+modem driver, begun with ALSA version 1.0.13.  
For HDA cards with ALC883 chips, an upgrade to ALSA verions 1.0.15 way be necessary. Instructions for Upgrading snd-hda-intel and its dependent driver set are at:
[http://linmodems.technion.ac.il/bigarch/archive-eighth/msg00838.html](http://linmodems.technion.ac.il/bigarch/archive-eighth/msg00838.html)

If not a Conexant modem, the driver snd-hda-intel with its dependent drivers:
snd_hda_intel         384176  3 
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss,snd_usb_audio
snd                    63268  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_usb_audio,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
----------
provide audio + modem support with the modem chip residing on the subsystem.
Any particular card can host any one of several soft modem chips. 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:1b.0:
	Modem chipset  detected on
NAME="Audio device: Intel Corporation 82801G "
CLASS=0403
PCIDEV=8086:27d8
SUBSYS=107b:0366
IRQ=22
HDA=8086:27d8
SOFT=8086:27d8.HDA
CHIP=0x10573057
IDENT=slmodemd
SLMODEMD_DEVICE=hw:0,6
Driver=snd-hda-intel

 For candidate modem in:  00:1b.0
   0403 Audio device: Intel Corporation 82801G 
      Primary device ID:  8086:27d8
    Subsystem PCI_id  107b:0366 
    Softmodem codec or chipset from diagnostics: 0x10573057
                               from    Archives: 
                        The HDA card softmodem chip is 0x10573057
      

Support type needed or chipset:	slmodemd supporting the snd-hda-intel audio+modem driver


 Pending fixes to gcc-4.3, temporarily use instead of SLMODEMD.gcc4.3.tar.gz, use
 	SLMODEMD_gcc4.2_alsa1.0.17.tar.gz

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-hda-intel
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) 
 the package SLMODEMD_gcc4.2_alsa1.0.17.tar.gz having a compiled slmodemd. Unpack under Linux with:
 	$ tar zxf SLMODEMD_gcc4.2_alsa1.0.17.tar.gz
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

 Versions adequately match for the compiler installed: 4.3.2
             and the compiler used in kernel assembly: 4.3.2


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.3
   linuc_headers base folder /lib/modules/2.6.27-11-generic/build

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
	-rwsr-xr-- 1 root dip 277160 2008-11-20 15:58 /usr/sbin/pppd

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

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0 wlan1 wmaster0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by Maxlite on 2009-04-02
Frugal: I have the same softmodem different version (Intel 82802H). It's actually a High Definition Audio (HDA) card with a softmodem chip on board. I haven't been able to get mine to work.  However, there are several other files generated by "Scanmodem" that may help you. When you ran scanmodem, it created several other folders containing several documents with a lot of information.  Go through them and see if they help. Some examples: /media/cdrom0/linux/readme, /etc/ppp/options, /home/(your ID)/modem/docs/Intel.txt & /home/(your ID)/Modem/modemdata/txt and others. If I ever get mine working, I'll post the 'howtos' results, etc.  Good Luck.

---

### Post by alimooghashang on 2009-04-27
when i try to install
i get an error says:

warning: hsfmodem-7.80.02.04full_k2.6.27.19_3.2_pae-1suse.i586.rpm: Header V3 DSA signature: NOKEY, key ID 5dfbf7dc
error: Failed dependencies:
        alsa-driver-linuxant is needed by hsfmodem-7.80.02.04full_k2.6.27.19_3.2_pae-1suse.i586

what to do?

---

