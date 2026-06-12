---
title: "howto create a dialup connection when can't detect modem"
date: 2006-02-14
forum: Networking &amp; Wireless
---

### Post by sulien on 2006-02-14
hi,

I have a compaq deskpro with a PII 128 MB RAM and 4.3 harddrive that I installed fully and it's the sole OS on the system. For some reason my modem is not detected. This computer is from 1998.

I managed to use ScanModem and the files it creates tells me that I don't have a USB modem. I am stuck at how to identify the chipset and drivers that I need to install to make the modem work with ubuntu 5.10 and connect by dialup to the internet. All my info was entered and I tried to use pon to connect but it didn't work. HELP !!!!! Please! 

Incidentally I'm doing this to intall the packages I need for gdesklets which I can't do and don't know where to put to make it function but that's another story.

thanks:-k

---

### Post by StefanoCole on 2006-02-15
Hello and welcome to the Ubuntu forum!

Is your modem an internal PCI WinModem? If you have run the ScanModem utility a file named "ModemData.txt" should be generated. What does it say? It should give you info about your modem chipset and possible available drivers. Also check the following wiki: [https://wiki.ubuntu.com/DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto")

Stefano

---

### Post by sulien on 2006-02-18
I am still stuck.The best I can guess is that my computer is a compaq desktop pro ep series either 6266,6300,6333,6350,6400,6450,6500. My research says this is a HCF pci modem by conexant but when I try scan modem or listmodem from their websites or linuxant's it refuses to give me anymore information about my system and won't install any drivers even with an auto installer. I'm starting to wonder if it is the correct modem type but that's what the internet says. Scan Modem mentions a UDEV device file system which indicant it's either conexnant or lucent thus either hcf or hsf but still no luck. Incidently can someone give me very detailed instructions about how and where to install these device drivers. I'm very frustrated. thanks

This is what I find for the modem online:
Deskpro EP Series 	Compaq Conexant HCF V90 Data Fax PCI
Microcom 415 External Data/Fax/Speakerphone
[http://www.modem-help.com/mfcs.php?mid=25](http://www.modem-help.com/mfcs.php?mid=25)

---

### Post by sulien on 2006-02-18
Just tried wvdialconf and it says it detects no modem on any ports or ttyS0 or ttyS1. What's the heck is the problem here?

---

### Post by sulien on 2006-02-18
okay, I pulled out of the computer the card that I think is a modem and I found this serial number under the bar code 721383-009 and by checking the internet it seems it might be a Intel PCI EtherExpress Pro100

HP / Compaq  	721383-009	INTEL PRO 10/100 BTX NETWORK CARD - 721383-009 - 721383009

Does this mean I can't use it for dialup as a modem?:cry:

---

### Post by bscbrit on 2006-02-18
This link will help you identify your modem type precisely:

[http://support.intel.com/support/network/sb/cs-012904.htm](http://support.intel.com/support/network/sb/cs-012904.htm)

Here is a link about your modem and linux:

[http://www.scyld.com/eepro100.html](http://www.scyld.com/eepro100.html)

However, a quick look suggests to me that it is not an win-modem but, without looking at the card itself I cannot be sure - however, you have the card and the first link should tell you what you need to know.  Do the detective work and then come back and I'll see if I am able to help.  :D

EDIT this is a network card - not a modem see my next post!

---

### Post by bscbrit on 2006-02-18
Sorry - are you trying to identify your network card (which is the one that you have in your hand....:-D ) or your modem, which you still have inside the computer presumably?

---

### Post by sulien on 2006-02-18
hi,

Thanks for your help! I'm trying to identify my modem but it seems that if that card I pulled out was only an ethernet card then perhaps I have no modem card at all??:confused:

---

### Post by bscbrit on 2006-02-18
Well its possible that the modem is built into the motherboard. Look for the connector to a telephone socket, which will be similar in appearance to the socket on the ethernet card but slightly smaller.  If it exists, it usually will be near to the other sockets on the motherboard.  If you find the socket, you have a built in modem. If not, then you probably only have a network card fitted and you will need to get a modem from somewhere else.

---

### Post by sulien on 2006-02-19
I'm investigating what type of modem I should buy for my setup. Must it be ISA V.90 or can I buy a PCI V.92?:-?

---

### Post by bscbrit on 2006-02-19
I wouldn't (personally) buy an ISA card if you have a PCI slot available unless there was something that the ISA card could do that you couldn't live without.  It might fit in your current computer but there a less and less motherboards with (E)ISA slots around nowadays.  If you have the choice, I would still buy a RS232 modem (i.e. one that connects using the serial connector) .  They work with any  software and this is next to no setup required (once you have told it which serial connector to use, its done!).  But PCI is fine provided that it is a 'real' modem and not a winmodem.  I have not had much success with the latter, but others seem to be able to make them work.

---

### Post by edopizza on 2006-03-23
[QUOTE=StefanoCole]Hello and welcome to the Ubuntu forum!

Is your modem an internal PCI WinModem? If you have run the ScanModem utility a file named "ModemData.txt" should be generated. What does it say? It should give you info about your modem chipset and possible available drivers. Also check the following wiki: [https://wiki.ubuntu.com/DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto")

Stefano[/QUOTE]


I have the same problem: in the network configuration window seems that the modem is installed, but when I click on autodetect no port is found. 
I am quite sure that the modem is a Creative Blaster V.92 PCI. 
Why is the modem not working? 
Here is the ModemData.txt I get with scanModem (the output is a little bit to technical for me!): 


 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-10-386  
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2006_March_14
------------ --------------  System information ------------------------
 Ubuntu 5.10 "Breezy Badger" 
 on System with processor: i686
 currently under kernel:   2.6.12-10-386
 [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) has good general guidance.
 Be sure to read the Ethernet section of Modem/YourSystem.txt 
A /dev/modem symbolic link is not present
 USB modem not detected.

 Checking for audio card 
0000:00:09.0 Multimedia audio controller: Yamaha Corporation YMF-724F [DS-1 Audio Controller] (rev 03)
	Reading /proc/asound/pcm 
00-00: YMFPCI : YMFPCI : playback 32 : capture 1
00-01: YMFPCI - IEC958 : YMFPCI - IEC958 : playback 1
00-02: YMFPCI - Rear : YMFPCI - Rear PCM : playback 1
00-03: YMFPCI - PCM2 : YMFPCI - AC'97 : capture 1


 The kernel was assembled with compiler:  3.4.5
 a gcc-3.4.5  package must be installed to support driver compiling
To support compiling, get the  BreezyGCC_3.4_i386.tar.gz from [http://phep2.technion.ac.il/linmodems/packages/smartlink/](http://phep2.technion.ac.il/linmodems/packages/smartlink/) 

 Compiling utility   make   Not found.

Checking for kernel-headers needed for compiling.
 Kernel-header resources needed for compiling are not manifestly ready!

Modem candidates are at PCI_buses:  0000:00:0a.0
    
Providing detail for device at  0000:00:0a.0
  with vendor-ID:device-ID
	    ----:----
Class 0780: 125d:2898   Communication controller: ESS Technology ES2898 Modem (rev 03)
  SubSystem 148d:1063  DIGICOM Systems, Inc.: Unknown device 1063
	Flags: fast devsel, IRQ 5
 Checking for IRQ 5 sharing with modem.

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 125d:2898 148d:1063 debian_version 2.6.12-10-386  3.4.5 none    i686
      
 Information on several modem chipset providers is provided below,
 because ambiguities remain on the correct choice of supporting software.
            
 == Checking PCI IDs through modem chip suppliers ==

 Vendor=125d is ESS Technologies, making devices:
 There has been no formal support for Linux since kernels 2.2.2
 There is no hope for support under 2.6.n kernels.
 See InfoGeneral.txt about alternatives.

 Only under 2.4.n Linux kernels and are there some kludges of fadding utility:
   [http://linmodems.technion.ac.il/archive-fourth/msg00317.html](http://linmodems.technion.ac.il/archive-fourth/msg00317.html)   (2004Feb08)
   [http://andrew.cait.org/ess/](http://andrew.cait.org/ess/)
   [http://sidlo.penguin.cz/ES2838/index_en.html](http://sidlo.penguin.cz/ES2838/index_en.html)
   [http://tx.technion.ac.il/~raindel/](http://tx.technion.ac.il/~raindel/)
   [http://phep2.technion.ac.il/linmodems/archive/msg04424.html](http://phep2.technion.ac.il/linmodems/archive/msg04424.html)


  ======= PCI_ID checking completed ====== 
 Update=2006_March_14
A PCMCIA CardBus is not detected on this System.
drwxr-xr-x  2 root root 0 2006-03-23 12:02 /dev/.udevdb

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


Checking the /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) breezy main restricted

deb [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) breezy-updates main restricted



deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted






deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free 
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) breezy universe main restricted


A package kernel-kbuild-2.6-3 or later version must be installed to support compiling


      
 The Major.Minor versions differ in the designated compiler none and the 3.4.5 used in kernel assembly!!"
But there must be a match on the target for driver installation, 
of gcc Major.Minor versions or kernel and drivers!!
Otherwise the drivers will fail to load with warning:
  Invalid module format!!"
See [http://linmodems.technion.ac.il/archive-fifth/msg04252.html](http://linmodems.technion.ac.il/archive-fifth/msg04252.html) 
 
Kernel-header resources needed for compiling are not manifestly ready!
Checking /usr/src/ for compressed compressed headers or kernel-source

Kernel-header resources needed for compiling are not manifestly ready!
If compressed resources are present, expand and then configure them following DriverCompiling.txt
They may have to be installed.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName			OnLine
  ----------------------------------------------------------------------
 Debian  		kernel-headers-2.6.12-10-386    	[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) or install CD
 Ubuntu 		linux-headers-2.6.12-10-386		[http://http://packages.ubuntu.com/](http://http://packages.ubuntu.com/) or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  Debian, Ubuntu and Xandros
 Mandrake 	kernel-source-2.6.12-10-386	   If not present on install CDs search
 	[http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/](http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/) 
	[http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html](http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html), or other mirrors.
  SuSE		kernel-source-2.6.12-10-386		 , kernels are named k_deflt
  FedoraCore4  kernel-devel-2.6.12-10-386 or kernel-smp-devel-2.6.12-10-386 on install CD1 or CD4
One of which must be installed if compiling drivers to match kernel 2.6.12-10-386 proves necessary.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
   

 A /dev/modem symbolic link is not set.

The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe_mppc
-------------------------------------
 Resident PPP support modules are properly uncompressed .
----active COMM services are ------------
eth0      Link encap:Ethernet  HWaddr 00:E0:7D:8B:EB:EA  
          inet6 addr: fe80::2e0:7dff:fe8b:ebea/64 Scope:Link
This COMM mode should be closed before using the modem, or DNS services may fail.
Be sure to read the section about ppp related modules and aliases in Modem/YourSystem.txt
 ---- dmesg queries -------

  pppd version 2.4.2 may not be fully compatible with 2.6.8 kernel releases.
  If an initial CONNECT is achieved without PPP being subsequently established,
  drop back to a 2.4.1 version.  This has worked for PCTEL AMR modem users,
  supported by the [http://www.smlink.com](http://www.smlink.com)  slmodem software.
  Check pppd version with:
    pppd --version
  See  [http://linmodems.technion.ac.il/archive-fourth/msg03167.html](http://linmodems.technion.ac.il/archive-fourth/msg03167.html)
    
  debian_version is not yet providing pre-compiled drivers for WinModems

---

### Post by nielowait on 2006-04-08
I've recently installed ubuntu on my mom's computer (she's over 60) and she's much happier with it than with windows already (no more crashes, no more spyware, no more viruses etc :D - so I'm happy too!)

The last thing I need to get working is faxing facilities - which is where I hit my snag. (I've got her hooked up to ADSL through the local network, so no need for ppp)

I've got an ES2898 modem in the computer, same as edopizza - but I am having difficulty getting it working - maybe I'm just thick. I've also put in a HPS MicroModem 56 (PCtel), but for some reason scanModem is not picking it up - maybe I have to remove the other modem first.

If anyone has come up with a solution to exactly the same situation as that of edopizza - please let me know, as I'd be really pleased if my mom doesn't have to boot up into windows ever again - and I, therefore, won't have to bother with things crashing or freezing on her computer ever again! (and even in the highly unlikely event of something like that happening at least I'd be able to figure out why or ask good people like you on the internet. ;) )

(oh, one thing different from edopizza - I installed Hoary Hedgehog)

---

### Post by helmut_hed on 2006-05-01
edopizza, nielowait: both your modems have support under Linux.

The PCTel driver is here:

[http://linmodems.technion.ac.il/pctel-linux/pctel-0.9.7-9-rht-5.tar.gz](http://linmodems.technion.ac.il/pctel-linux/pctel-0.9.7-9-rht-5.tar.gz)

The ESS driver is here:

[http://tx.technion.ac.il/~raindel/ess_2.6-v0.1.tar.gz](http://tx.technion.ac.il/~raindel/ess_2.6-v0.1.tar.gz)

For installation procedure, check out this new HOWTO (written for PCTel, but the ESS procedure is analogous):

[http://ubuntuforums.org/showthread.php?t=171163](http://ubuntuforums.org/showthread.php?t=171163)

Jeff Trull
(presently doing maintenance on both drivers)

---

