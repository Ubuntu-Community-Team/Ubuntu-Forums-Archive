---
title: "dial up connection"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by m.h.shams on 2006-06-16
dear friends, 

i have a external usb modem on my pc (my os is ubuntu 6.0.6)
it seems that ubuntu cant detect this modem

i WISH (really WISH) that one day i can connect internet with my modem, :(

here is lsusb commands result :

```

root@ubuntu-desktop:~# lsusb
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0483:7554 SGS Thomson Microelectronics 56k SoftModem
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

```

and this is scanmodem test result : (modmemData.txt)

```



 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 6.06 LTS  kernel 2.6.15-23-386
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at DISCUSS@linmodems.org
Code updated on:  2006_Jan_11
------------ --------------  System information ------------------------
 Ubuntu 6.06 LTS 
 on System with processor: i686
 currently under kernel:   2.6.15-23-386
 USB modem not detected.

--------- lspci scan ----------------
 PCI_bus
0000:00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
0000:00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
0000:00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
0000:00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 ?? [Radeon 9550] (Secondary)
0000:02:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
-------------------------------------

 A modem was not detected among the above PCI devices.
 This indicates that the modem, if present has a non-standard or ISA bridge.
 Please follow the directions in Modem/SoftModem.txt  for identifying the modem properties
 when booting under Microsoft Windows. Also access any documentation sources
 on yourchipset.  Guidance can only be provided AFTER
 the chipset and/or its drivers have been identified.
 
 The IBM mwave modem does have a driver within 2.6.n kernel+module releases.  If is at:
 	 /lib/modules/2.6.15-23-386/kernel/drivers/char/mwave/mwave.ko
and can be loaded only if Mwave hardware is present  Test with:	
 #  su - root
 followed by
 # modprobe wmave
 If successful see: 
 	http://tedfelix.com/Mwave/
 	http://www.linuxdocs.org/HOWTOs/mini/ACP-Modem/   , section 2.4 and later.
 	http://www.freenetpages.co.uk/hp/mjbou/dwtpul.html
	http://tedfelix.com/Mwave/
	
 A failure response has output like:
 	FATAL: Error inserting mwave (/lib/modules/2.6.10-1-686/kernel/drivers/char/mwave/mwave.ko): Input/output error
indicating absence of an Mwave modem


 The kernel was assembled with compiler:  4.0.3
 a gcc-4.0.3  package must be installed to support driver compiling
Modem candidates are at PCI_buses:  
  ======= PCI_ID checking completed ====== 
 Update=2006_Jan_11
A PCMCIA CardBus is not detected on this System.
 Checking for modem symbolic link support lines within /etc/udev/ files


Checking the /etc/apt/sources.list

deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://au.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

A package kernel-kbuild-2.6-3 or later version must be installed to support compiling


      
 The Major.Minor versions differ in the designated compiler none and the 4.0.3 used in kernel assembly!!"
But there must be a match on the target for driver installation, 
of gcc Major.Minor versions or kernel and drivers!!
Otherwise the drivers will fail to load with warning:
  Invalid module format!!"
See http://linmodems.technion.ac.il/archive-fifth/msg04252.html 
 
Checking for kernel-headers needed for compiling.
Checking /usr/src/ for compressed compressed headers or kernel-source

Kernel-header resources needed for compiling are not manifestly ready!
If compressed resources are present, expand and then configure them following DriverCompiling.txt
They may have to be installed.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName			OnLine
  ----------------------------------------------------------------------
 Debian  		kernel-headers-2.6.15-23-386    	http://www.debian.org/distrib/packages or install CD
 Ubuntu 		linux-headers-2.6.15-23-386		http://http://packages.ubuntu.com/ or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  Debian, Ubuntu and Xandros
 Mandrake 	kernel-source-2.6.15-23-386	   If not present on install CDs search
 	http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/ 
	http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html, or other mirrors.
  SuSE		kernel-source-2.6.15-23-386		 , kernels are named k_deflt
  FedoraCore4  kernel-devel-2.6.15-23-386 or kernel-smp-devel-2.6.15-23-386 on install CD1 or CD4
One of which must be installed if compiling drivers to match kernel 2.6.15-23-386 proves necessary.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
   

 A /dev/modem symbolic link is not set.

The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
-------------------------------------
 Resident PPP support modules are properly uncompressed .
----active COMM services are ------------
eth0      Link encap:Ethernet  HWaddr 00:11:2F:E0:01:D0  
This COMM mode should be closed before using the modem, or DNS services may fail.
Be sure to read the section about ppp related modules and aliases in Modem/YourModem.txt
 Be sure to read the Ethernet section of Modem/YourModem.txt 
DEVPPP=crw------- 1 root root 108, 0 2006-05-31 04:45 /dev/ppp
A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294668.327000] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[4294668.328000] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[4294668.328000] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[4294668.331000] ACPI: PCI Interrupt Link [LKMO] (IRQs 20 21 22) *0, disabled.
[4294668.331000] ACPI: PCI Interrupt Link [LKSM] (IRQs 20 21 22) *0, disabled.
[4294668.332000] ACPI: PCI Interrupt Link [LTID] (IRQs 20 21 22) *0, disabled.
[4294668.332000] ACPI: PCI Interrupt Link [LTIE] (IRQs 20 21 22) *0, disabled.
[4294668.342000]   PREFETCH window: disabled.
[4294668.343000] audit: initializing netlink socket (disabled)
[4294695.753000] ibm_acpi: ec object not found
[4294695.773000] pcc_acpi: loading...
[4294701.123000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294701.124000] apm: overridden by ACPI.

  pppd version 2.4.2 may not be fully compatible with 2.6.8 kernel releases.
  If an initial CONNECT is achieved without PPP being subsequently established,
  drop back to a 2.4.1 version.  This has worked for PCTEL AMR modem users,
  supported by the http://www.smlink.com  slmodem software.
  Check pppd version with:
    pppd --version
  See  http://linmodems.technion.ac.il/archive-fourth/msg03167.html
    
  ubuntu is not yet providing pre-compiled drivers for WinModems

```

please help meeeeeeeeeeeeeeee


regards.
shams

---

### Post by zxee on 2006-06-17
> See  [http://linmodems.technion.ac.il/archive-fourth/msg03167.html](http://linmodems.technion.ac.il/archive-fourth/msg03167.html)
    
  ubuntu is not yet providing pre-compiled drivers for WinModems

There are threads here in the networking forum on using apt-get to install a driver for certain winmodems (which is what you have-unfortunately many usb modems are winmodem i.e they require windows to operate)  There are work arounds and the sl-modem driver but I have no idea if that would work on your modem. There is a modem check tool you can download from linmodem and then see if it's possible to get it working. For me the easier way is just to go out and get a controllor type modem-most serial port (com port) external modems are compatible with linux.

---

### Post by m.h.shams on 2006-06-20
[QUOTE=zxee]There are threads here in the networking forum on using apt-get to install a driver for certain winmodems (which is what you have-unfortunately many usb modems are winmodem i.e they require windows to operate)  There are work arounds and the sl-modem driver but I have no idea if that would work on your modem. There is a modem check tool you can download from linmodem and then see if it's possible to get it working. For me the easier way is just to go out and get a controllor type modem-most serial port (com port) external modems are compatible with linux.[/QUOTE]

when i run lsusb, i got this property for my modem :

SGS Thomson Microelectronics 56k SoftModem

i search this term, and found some info about this modem 

[ hare  ]("http://www.qbik.ch/usb/devices/showdev.php?id=2637")

they said that this type of modems can work correctly with **[B]slmdm **[/B] driver.  but i can't find this driver on internet. there is some old links
for download this driver, but they are all invalid now.

:(

---

### Post by zxee on 2006-06-21
There are several modems listed under that designation at the usb section of linmodems.org [http://www.qbik.ch/usb/devices/search_res.php?pattern=SGS+Thomson](http://www.qbik.ch/usb/devices/search_res.php?pattern=SGS+Thomson)
You're correct drivers when available are listed for the 2.4.X series kernel.
Can you get a serial (com port) external modem?

---

