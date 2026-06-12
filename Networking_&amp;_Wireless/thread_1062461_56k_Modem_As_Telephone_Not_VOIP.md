---
title: "56k Modem As Telephone Not VOIP"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by CaptainBuntu on 2009-02-06
Hello,

As the title says, I'm trying to use the integrated 56k Voice/Data/Fax modem in my laptop to make Telephone calls over standard phone networks. I would Ideally like to use my Headset /w mic to make such calls. 

Ubuntu 8.04 LTS
Here is the output of lspci

```
kao@hal9000:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
06:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
06:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

```

---

### Post by Shazaam on 2009-02-06
Have you been here yet?...
[https://help.ubuntu.com/8.10/internet/C/modem.html](https://help.ubuntu.com/8.10/internet/C/modem.html)

---

### Post by CaptainBuntu on 2009-02-06
No, I have not. Though this seems to just explain how to Dial-Up to a ISP for internet access, This is not what I'm trying to do. I already have an Internet connection via WiFi. I'm trying to use the Dial Up Modem to Make phone calls over my Home Phone Landline Through my PC.

I ran the scanModem program on the "Identifying your Modem" section of the aforementioned website. Below is the contents;

```
 Only plain text email is forwarded by the  Discuss@Linmodems.org List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.24-23-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: http://www.linux.org/groups/index.html.
They will know your Country's modem code, which may be essential for dialup service.
Responses from Discuss@Linmodems.org are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.24-23-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jan 26 00:13:11 UTC 2009
 scanModem update of:  2009_02_04

 There are no blacklisted modem drivers in /etc/modprobe*  files 
 Potentially useful modem drivers now loaded are:
         snd_hda_intel       

Attached USB devices are:
 ID 0830:127e Palm, Inc. 
 ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
 ID 0b05:1712 ASUSTek Computer, Inc. 
 ID 05a4:9862 Ortek Technology, Inc. 
 ID 05a4:9837 Ortek Technology, Inc. 
 ID 0402:5602 ALi Corp. Video Camera Controller
If a cellphone is not detected, see http://ubuntuforums.org/archive/index.php/t-878554.html

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to discuss@linmodems.org

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:27d8	1043:1343	Audio device: Intel Corporation 82801G 

 Modem interrupt assignment and sharing: 
 16:     961003          0   IO-APIC-fasteoi   uhci_hcd:usb5, ohci1394, HDA Intel, fglrx
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[   34.972531] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.972558] PCI: Setting latency timer of device 0000:00:1b.0 to 64


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.16
The modem cards detected by "aplay -l"  are: 
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]

The /proc/asound/pcm file reports:
-----------------------
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
00-04: ALC882 Analog : ALC882 Analog : capture 2
00-00: ALC882 Analog : ALC882 Analog : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xffaf8000 irq 16

 PCI slot 00:1b.0 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.24-23-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
 The modem codec file for the HDA card is: /proc/asound/card0/codec#1
--------------------------------------------------------
Codec: Motorola Si3054
Address: 1
Vendor Id: 0x10573055
Subsystem Id: 0x104310c6
Revision Id: 0x100700
Modem Function Group: 0x1

 The audio card hosts a softmodem chip:  0x10573055

The softmodem chip 0x10573055 is in principle supported by the COMM support of slmodemd 
and the joint snd-hda-intel audio+modem driver, begun with ALSA version 1.0.13.  
For HDA cards with ALC883 chips, an upgrade to ALSA verions 1.0.15 way be necessary. Instructions for Upgrading snd-hda-intel and its dependent driver set are at:
http://linmodems.technion.ac.il/bigarch/archive-eighth/msg00838.html

If not a Conexant modem, the driver snd-hda-intel with its dependent drivers:
snd_hda_intel         346136  6 
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
NAME="Audio device: Intel Corporation 82801G "
CLASS=0403
PCIDEV=8086:27d8
SUBSYS=1043:1343
IRQ=16
HDA=8086:27d8
SOFT=8086:27d8.HDA
CHIP=0x10573055
IDENT=slmodemd
SLMODEMD_DEVICE=hw:0,6
Driver=snd-hda-intel

 For candidate modem in:  00:1b.0
   0403 Audio device: Intel Corporation 82801G 
      Primary device ID:  8086:27d8
    Subsystem PCI_id  1043:1343 
    Softmodem codec or chipset from diagnostics: 0x10573055
                               from    Archives: 
                        The HDA card softmodem chip is 0x10573055
      

Support type needed or chipset:	slmodemd supporting the snd-hda-intel audio+modem driver

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-hda-intel
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from http://linmodems.technion.ac.il/packages/smartlink/ 
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
   linuc_headers base folder /lib/modules/2.6.24-23-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are needed. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at http://packages.ubuntu.com
 or comparable Repository for other Linux distros.
 When compiling ALSA drivers, the utility "patch" will also be needed.


Compressed files at: /usr/src/gspca.tar.bz2


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
	-rwsr-xr-- 1 root dip 269256 2007-10-04 14:57 /usr/sbin/pppd

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

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0 ppp0 wlan0 wmaster0
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

```

---

### Post by cariboo on 2009-02-06
What you want to do is possible, but you have to install the modem before you can use it. 

I did something similar back in Win95. I haven't looked lately, but the dialer was installed in early versions of Windows XP. If it is possible to do something in Windows, then someone has written a howto for Linux. 

Jim

---

### Post by CaptainBuntu on 2009-02-06
> **cariboo907 said:**
> What you want to do is possible, but you have to install the modem before you can use it. 

I did something similar back in Win95. I haven't looked lately, but the dialer was installed in early versions of Windows XP. If it is possible to do something in Windows, then someone has written a howto for Linux. 

Jim
Yes, I also used to do this in Earlier versions of MS Windows but have not tried it in *nix. 

As for you stating that I need to install my modem. I'm assuming you mean drivers for the modem as the actual Modem is integrated.

If so, how do I go about acquiring these drivers and installing them, or should I start another thread?

---

### Post by Shazaam on 2009-02-07
As cariboo907 posted you need to install the modem drivers first before you can do anything else. It looks like you have a SmartLink (slmodem) modem by the scanmodem printout. It lists the drivers that you need.
Before you install any drivers run this in terminal if you have not done it already (pulls in the header files for your kernel)...
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by CaptainBuntu on 2009-02-07
> **Shazaam said:**
> As cariboo907 posted you need to install the modem drivers first before you can do anything else. It looks like you have a SmartLink (slmodem) modem by the scanmodem printout. It lists the drivers that you need.
Before you install any drivers run this in terminal if you have not done it already (pulls in the header files for your kernel)...
```
sudo apt-get install linux-headers-$(uname -r)
```
Thank you, I attempted to do the following

```
sudo apt-get install slmodem
```

And got the following output,

```
kao@hal9000:~$ sudo apt-get install slmodem
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting sl-modem-daemon instead of slmodem
The following NEW packages will be installed:
  sl-modem-daemon
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 510kB of archives.
After this operation, 1163kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy/restricted sl-modem-daemon 2.9.10+2.9.9d+e-pre2-5ubuntu4 [510kB]
Fetched 510kB in 16s (30.5kB/s)                                                
Preconfiguring packages ...
Selecting previously deselected package sl-modem-daemon.
(Reading database ... 126590 files and directories currently installed.)
Unpacking sl-modem-daemon (from .../sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5ubuntu4_i386.deb) ...
Setting up sl-modem-daemon (2.9.10+2.9.9d+e-pre2-5ubuntu4) ...
Adding system user `Slmodemd' (UID 112) ...
Adding new group `Slmodemd' (GID 126) ...
Adding new user `Slmodemd' (UID 112) with group `Slmodemd' ...
Not creating home directory `/'.
FATAL: Module ungrab_winmodem not found.
FATAL: Module slamr not found.
Starting SmartLink Modem driver for: auto.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.
```

---

### Post by filipejps on 2009-03-24
I've got the same problem with my modem... 
I would like to use my modem as a Fax.

---

### Post by solitaire on 2009-04-08
Anyone else got any ideas to get Ubuntu program to work as a SoftPhone for Landlines?

---

### Post by cody1233 on 2010-08-10
This would be very useful...for fax have you tried efax?

---

### Post by grahammechanical on 2010-08-11
I use to be able to do this on my very old pc running Win98. I used a program given away free by a magazine. It provided fax and dialing. I have not been able to find anything on Linux that seems to do the same. It is a shame as it was a great way to talk to my sister who lives on the coast when I was working on the computer. You have got me wondering if such a program would work under Wine or in a virtual machine. I do have Virtual Box installed.

regards

---

### Post by cody1233 on 2010-08-15
I never thought of using wine...was this program from a website or a cd in the magazine?

---

