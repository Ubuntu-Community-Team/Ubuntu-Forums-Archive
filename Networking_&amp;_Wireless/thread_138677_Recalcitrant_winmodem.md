---
title: "Recalcitrant winmodem"
date: 2006-03-02
forum: Networking &amp; Wireless
---

### Post by Grégoire_Neuville on 2006-03-02
[SIZE="6"]Hi,
 
I've got problems to get my modem working with ubuntu. May I ask anybody some help ?
(I join (below) the scanModem Modemdata.txt file)
 
Thanks a lot.
[/SIZE]



 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-10-k7
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2006_Feb_14
------------ --------------  System information ------------------------
 Ubuntu 5.10 "Breezy Badger" 
 on System with processor: i686
 currently under kernel:   2.6.12-10-k7
 USB modem not detected.


 The kernel was assembled with compiler:  3.4.5
 with current System compiler GCC=3.4.5

 Found make utility.

Checking for kernel-headers needed for compiling.
 Kernel-headers supporting compiling are resident: 

Modem candidates are at PCI_buses:  0000:02:01.0
    
Providing detail for device at  0000:02:01.0
  with vendor-ID:device-ID
	    ----:----
Class 0780: 11c1:048c   Communication controller: Lucent Microelectronics V.92 56K WinModem (rev 03)
  SubSystem 11c1:044c  Lucent Microelectronics: Unknown device 044c
	Flags: bus master, medium devsel, latency 64, IRQ 21
 Checking for IRQ 21 sharing with modem.
O-APIC-level  acpi, ohci1394

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 11c1:048c 11c1:044c ubuntu 2.6.12-10-k7  3.4.5 3.4.5    i686
 == Checking PCI IDs through modem chip suppliers ==

 Vendor 11c1 corresponds to Lucent Technologies or subsidiary Agere Systems, Inc.
 Information is at:  [http://www.agere.com/client/modem_dsp.html](http://www.agere.com/client/modem_dsp.html). Produced are both:
   1) modems identifiable from their primary PCI IDs and 
   2) soft modem Subystem chips requiring identification through codec readouts.
   
 Lucent/Agere Mars/WinModem drivers from version 8.30 onwards have
 the necessary fix for SMP machines which includes machines with
 hyperthreading turned on (virtually acting as two CPUs).
 

  Class 0703:  11c1:048c is still NOT supported under Linux, as of 2006_Feb_14
  It is a "software" modem without a digital signal processing (DSP) chipset.
  The ltmodem drivers from [http://ltmodem.heby.de](http://ltmodem.heby.de) resources for DSP modems do NOT provide support,
    A dialout terminates with "No Carrier" or a Hang if usage of the ltmodem drivers is attempted. See InfoGeneral.txt about alternatives.


  ======= PCI_ID checking completed ====== 
 Update=2006_Feb_14
A PCMCIA CardBus is not detected on this System.
drwxr-xr-x  2 root root 0 2006-03-02 02:44 /dev/.udevdb

There is an active UDEV file system, creating device nodes in volatile RAM.
For SmartLink modems using the slamr.ko or slusb.ko drivers an /etc/init.d/ script
will be necessary to create /dev/slamr0 or /dev/slusb0 ports, or manually by:
#  mknod -m 600 /dev/slamr0 c 242 0
#  mknod -m 600 /dev/slusb0 c 243 0
upon each bootup.

For information on modem port creation under the UDEV device file system see:
   [http://linmodems.technion.ac.il/archive-fourth/msg03299.html](http://linmodems.technion.ac.il/archive-fourth/msg03299.html)  for Conexnant modems
   [http://linmodems.technion.ac.il/archive-fifth/msg01177.html](http://linmodems.technion.ac.il/archive-fifth/msg01177.html)  for Lucent/Agere DSP modems
   
 Checking for modem symbolic link support lines within /etc/udev/ files
	/etc/udev/rules.d/ltmodem.rules
#
# UDEV rule for ltmodem, in  /etc/udev/rules.d/ltmodem.rules
#  creates symlink /dev/modem to /dev/ttyLTM0, and sets permissions.
KERNEL="ttyLTM[0-9]", NAME="%k", MODE="0660", GROUP="dialout", SYMLINK="modem"
# to restrict to a single USER add above , OWNER="USERNAME" 



Checking the /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe





A package kernel-kbuild-2.6-3 or later version must be installed to support compiling


    /usr/bin/gcc -> /usr/bin/gcc-3.4
 dequate match of gcc versions of the compiler and kernel.
 A /dev/modem symbolic link is not set.

The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe_mppc
/etc/modprobe.d/eagle-usb:install eagle-usb /sbin/modprobe ppp-async; /sbin/modprobe --ignore-install eagle-usb
/etc/modprobe.d/devfsd:alias /dev/ppp*		ppp_generic
-------------------------------------
 Resident PPP support modules are properly uncompressed .
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/YourModem.txt
A /dev/modem symbolic link is not present
DEVFSD=/etc/devfs/devfsd.conf
 ---- dmesg queries -------
  ubuntu is not yet providing pre-compiled drivers for WinModems

---

### Post by Matchless on 2006-03-03
Grégoire_Neuville,
                       Have a look at the wiki dialupmodemhowto, it is very clear and covers both Lucent and Smartlink.

---

### Post by towsonu2003 on 2006-03-03
You just killed my eyes... can you deacrease the fonts by any chance? [QUOTE=Grégoire_Neuville]
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test **11c1:048c** 11c1:044c ubuntu 2.6.12-10-k7  3.4.5 3.4.5    i686
  **Class 0703:  11c1:048c is still NOT supported under Linux**, as of 2006_Feb_14
  It is a "software" modem without a digital signal processing (DSP) chipset.
  The ltmodem drivers from [http://ltmodem.heby.de](http://ltmodem.heby.de) resources for DSP modems do NOT provide support,
    A dialout terminates with "No Carrier" or a Hang if usage of the ltmodem drivers is attempted. **See InfoGeneral.txt about alternatives.**[/quote]
I guess it won't work... sorry... file a bug to ubuntu (last link in my signature). 
> ubuntu is not yet providing pre-compiled drivers for WinModemswhat a shame... :cry: [-( :evil:

---

### Post by Grégoire_Neuville on 2006-03-04
Thanks to both of you, gentlemen, but I think that I've tried every existing solutions for winmodems - and I just received a pessimistic answer from a guy at [email]discuss@linmodems.org[/email] -; I now just have to buy an external modem...

---

