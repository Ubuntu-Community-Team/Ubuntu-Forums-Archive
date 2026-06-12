---
title: "Winmodem--&gt;Linmodem"
date: 2005-03-17
forum: Networking &amp; Wireless
---

### Post by StefanoCole on 2005-03-17
Hello, I am new in Linux and I have installed Ubuntu Warthy a couple of weeks ago. I have a Winmodem that I would like to use with Ubuntu.
I have run the scanModem utility. I include here the content of modemData.txt file.
Since I am a Linux beginner it is not clear the content of such file, in particular about the process to follow to get a Linmodem (installing kernel headers and so on). Can you help me? Thanks in advance!


 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 4.10 kernel 2.6.8.1-3-386
 Occassionally reponses are blocked by an Internet Providers mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_March_3
------------ --------------  System information ------------------------
Ubuntu 4.10 "Warty Warthog" 
 on System with processor: i686
 currently under kernel:   2.6.8.1-3-386
 The kernel was assembled with compiler:  3.3.4
 a gcc package must be installed to support driver compiling

Checking for kernel-headers needed for compiling.
Kernel-header resources are not evident.
Within your Linux distributions resources, search for package names with:
  linux-headers-2.6.8.1-3-386
  kernel-source-2.6.8.1-3-386
  linux-2.6.8.1-3-386
One of which must be installed if compiling drivers to match kernel 2.6.8.1-3-386 proves necessary.
This is necessary for most modem drivers, through some Linux distributions provide some compiled drivers.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
  

 A /dev/modem symbolic link is not set.
 Checking for USB modems
 None found

Modem candidates are at PCI_buses:  0000:00:0b.0
    
Providing detail for device at PCI_bus 0000:00:0b.0
  with vendor-ID:device-ID
	    ----:----
Class 0780: 11c1:0440   Communication controller: Lucent Microelectronics 56k WinModem (rev 01)
  SubSystem 11c1:0440   Lucent Microelectronics LT WinModem 56k Data+Fax+Voice+Dsvd
	Flags: bus master, medium devsel, latency 0, IRQ 10
	Memory at da000000 (32-bit, non-prefetchable)
	I/O ports at bc00 [size=8]
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 11c1:0440 11c1:0440 debian 2.6.8.1-3-386 3.3.4     i686

 == Checking PCI IDs through modem chip suppliers ==

 The modem has a supported Lucent/Agere DSP (digital signal processing) chipset
  with primary PCI_ID:  11c1:0440
 DSP=1

 Vendor 11c1 corresponds to Lucent Technologies or subsidiary Agere Systems, Inc.
 Information is at:  [http://www.agere.com/client/modem_dsp.html](http://www.agere.com/client/modem_dsp.html). Produced are both:
   1) modems identifiable from their primary PCI IDs and 
   2) soft modem Subystem chips requiring identification through codec readouts.
 
 Call waiting specified by, +pcw=1, is not implmented in the ltmodem drivers.
Configuration with forcing is described in: [http://linmodems.technion.ac.il/archive-fifth/msg00055.html](http://linmodems.technion.ac.il/archive-fifth/msg00055.html)
 0x0440 -- Mars 2 - data/fax/voice

 Support has been extended to 2.6.n kernels by Rajesh K. Balan and
 Aleksey Kondratenko <alk@tut.by>, with official support from AgereSystems later following.
 Functionality requires serial_core support, either as a module or integral to the kernel.
 
 The ltmodem-2.6-alk-7.tar.bz2 can be downloaded from:
   [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/) 
   with low bandwidth alternate: [http://alk.at.tut.by/ltmodem-2.6-alk-7.tar.bz2](http://alk.at.tut.by/ltmodem-2.6-alk-7.tar.bz2)
   There are detailed instructions in  [http://linmodems.technion.ac.il/archive-fifth/msg00584.html](http://linmodems.technion.ac.il/archive-fifth/msg00584.html)
   
   For kernels prior to 2.6.11, the resources at [http://ltmodem.heby.de](http://ltmodem.heby.de) can be utilized.



 Add either of the following lines to the Debian  /etc/apt/sources.list
 to enable automatic updates on installer availability:
   deb [http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/](http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/) ./
   deb [http://www.sfu.ca/~cth/ltmodem/dists/debian/](http://www.sfu.ca/~cth/ltmodem/dists/debian/) ./


  The desired installer name is like:
========================================
ltmodem-2.6.8.1-3-386_8.nn_i386.deb
----------------------------------------
 ltmodem-kv-Kernel_FL-LTver--.CPU.rpm   explains the versioning.
 For your System
            Kernel_FL is 2.6.8.1-3-386 , the full kernel version displayed by: uname -r
                      LTver is 8.31a9, the release of the compiler kit
                               8.nn is the Agere core code designation.
       The proccesor type or CPU is:  i686      dispayed by:  uname -m
 used in compiling and assembling driver packages.

      
 A suitable installer is not available as of this 2005_March_3 update.
 Check in the section debian at  [http://ltmodem.heby.de/](http://ltmodem.heby.de/)
   for a subsequent Installer submission.
 Older releases have been archived at:
   [http://linmodems.technion.ac.il/packages/ltmodem/archive/](http://linmodems.technion.ac.il/packages/ltmodem/archive/)
 Also there is a RPM search engine at:   [http://rpm.pbone.net](http://rpm.pbone.net)
 The closest match to your   i686=CPU   is recommended.
   The closest match to your   i686=CPU   is recommended.
   For example replacements in order of preference for an
     i686 would be i586, i486 and i386
 If not present use the  ltmodem-8.31a9.tar.gz compiler kit.

 The list of available Installers for debian as of this 2005_March_3
 is inserted into to Modem/General.txt
  ======= PCI_ID checking completed ====== 
 Update=2005_March_3
A PCMCIA CardBus is not detected on this System.
GCCversion=
The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias char-major-108 ppp_generic
/etc/modprobe.d/aliases:alias tty-ldisc-3  ppp_async  
/etc/modprobe.d/aliases:alias tty-ldisc-14 ppp_synctty
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe
/etc/modprobe.d/aliases:alias ppp-compress-21 bsd_comp   
/etc/modprobe.d/aliases:alias ppp-compress-24 ppp_deflate
/etc/modprobe.d/aliases:alias ppp-compress-26 ppp_deflate
-------------------------------------
 Resident PPP support modules are properly uncompressed .
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/General.txt

  A port needed for the PPP protocol is absent!!!
  echo "  crw-------    1 root     root     108,   0 Dec 31  1969 /dev/ppp"

A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
Local APIC disabled by BIOS -- reenabling.
ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
  debian is not yet providing pre-compiled drivers for WinModems

---

### Post by Maniak on 2005-03-20
Stephano,

First step is to run up Synaptic and search for:
1. build-essentials
2. linux-headers (find the one that matches 'uname -r')
Install both of those.

Search on the internet for 'ltmodem deb files'. You should find at least one deb file that may work in loading up the drivers you need....otherwise - 

I went to the [http://linmodems.technion.ac.il/pac...dem/kernel-2.6/](http://linmodems.technion.ac.il/pac...dem/kernel-2.6/) site and used that. Follow the udev instructions, then simply follow on with the readme or the example in the doc folder.

I also searched for and downloaded a deb for 'gnome-ppp' which installed without a problem. This is a front-end to wvdial, which is the program that actually connects you to the internet. 

The final step is to enable your user to actually get wvdial/gnome-ppp to work. Use the Computer menu, go to System Configuration, Users and Groups. Open that and for your username click on the properties tab, Other Groups tab. Add the dip group to your users groups.  

Try all that and see how you go. That is what I have just been thru to get my new Ubuntu system connecting to the net with a PCI LT modem.

---

### Post by StefanoCole on 2005-03-22
Hi, I have downloaded a 'gnome-ppp' (filename gnome-ppp-0.3.21.tar.gz). Can you tell me how to install it? (As I wrote in my first post I am new to Linux and so, even simply operations for me are not so easy!)

Thank you, Stefano

---

### Post by Maniak on 2005-03-23
I also tried the gnome-ppp-0.3.21.tar.gz but had trouble getting it to install properly.

Do a google search for 'gnome-ppp deb'. It should find several  gnome-ppp-0.3.17-2.deb mirrors. Once you have it, open a terminal and 'dpkg -i gnome-ppp-0.3.17-2.deb' to install it.

Go from there with the dip group stuff to get it to work properly.

Simon BC

---

### Post by bored2k on 2005-03-23
[QUOTE=Maniak]I also tried the gnome-ppp-0.3.21.tar.gz but had trouble getting it to install properly.

Do a google search for 'gnome-ppp deb'. It should find several  gnome-ppp-0.3.17-2.deb mirrors. Once you have it, open a terminal and 'dpkg -i gnome-ppp-0.3.17-2.deb' to install it.

Go from there with the dip group stuff to get it to work properly.

Simon BC[/QUOTE]
 Gnome PPP Hoary : [http://higgs.djpig.de/ubuntu/www/hoary/net/gnome-ppp](http://higgs.djpig.de/ubuntu/www/hoary/net/gnome-ppp)
Warty: [http://higgs.djpig.de/cgi-ubuntu/search_packages.pl?keywords=ppp&searchon=names&subword=1&version=warty&release=all](http://higgs.djpig.de/cgi-ubuntu/search_packages.pl?keywords=ppp&searchon=names&subword=1&version=warty&release=all)

There is always a README file in .tgz, use it wisely.

Usually its

./configure
make
sudo make install .

---

### Post by Maniak on 2005-03-23
I can't remember where but the ./configure would error out (XML parser in Perl seems to ring bells in the depths of the mind). I could not see an easy solution so went for the .deb file and it is working fine.

---

### Post by bored2k on 2005-03-23
[QUOTE=Maniak]I can't remember where but the ./configure would error out (XML parser in Perl seems to ring bells in the depths of the mind). I could not see an easy solution so went for the .deb file and it is working fine.[/QUOTE]
 Compiling is a b!7[# compared to .deb files. That is why they say debian has supercow powers :roll: .

---

### Post by Maniak on 2005-03-23
[QUOTE=bored2k]Compiling is a b!7[# compared to .deb files. That is why they say debian has supercow powers :roll: .[/QUOTE]

Supercow eh.......knew it was good - but that is really good!!

---

### Post by StefanoCole on 2005-03-24
O.K., I have downloaded modem drivers, compiled and installed following the instructions. Then I have downloaded and installed the gnome-ppp deb and added the dip group to my user groups.
I have tried all but something goes wrong. I try to explain (I use italian as language for Ubuntu, so now I try to translate in english the messages that I receive):
- I start gnome-ppp and fill in username, password and phone number
- I push the connect button and select log to see in the log window what is happening
- the log window says: modem initialized, waiting for carrier, then something else about username and password 
- the gnome-ppp window says 'connected'
- if I see the details it says: state = inactive, speed=0 Kb/s.
- I start Mozilla Firefox and select a website but it tells me that it cannot reach it.
- After about 10 seconds of connection gnome-ppp disconnects and it prompts me for a new connection!

Thank you for any hints, Stefano

---

### Post by Maniak on 2005-03-24
Stephano,

Your problem sounds like an issue with the setting for the default gateway. Your machine cannot find it. I had this problem when I was Mandrake and cannot remember how exactly to fix it. 

1.   Check that under 'Computer, Network Settings' for the Modem PPP adapter that in the interface properties, advanced tab -'Set modem as default route to internet' is checked.

2.   If you have a network card as well - I cannot help you as I only have the modem installed.

---

### Post by mesocool on 2005-03-25
[QUOTE=bored2k]Gnome PPP Hoary : [http://higgs.djpig.de/ubuntu/www/hoary/net/gnome-ppp](http://higgs.djpig.de/ubuntu/www/hoary/net/gnome-ppp)
Warty: [http://higgs.djpig.de/cgi-ubuntu/search_packages.pl?keywords=ppp&searchon=names&subword=1&version=warty&release=all](http://higgs.djpig.de/cgi-ubuntu/search_packages.pl?keywords=ppp&searchon=names&subword=1&version=warty&release=all)

There is always a README file in .tgz, use it wisely.

Usually its

./configure
make
sudo make install .[/QUOTE]

I dpkg that package and add the dig even though I dont know what is that dig for.
But it still cannot find the modem. 
I got the message saying "cannot open modem" and "cannot open /dev/modem: No such file or directory".

Help Help~~ ](*,)

---

### Post by Maniak on 2005-03-25
[QUOTE=mesocool]I dpkg that package and add the dig even though I dont know what is that dig for.
But it still cannot find the modem. 
I got the message saying "cannot open modem" and "cannot open /dev/modem: No such file or directory".

Help Help~~ ](*,)[/QUOTE]

I had that for a while until I did the following - 

Add new udev rule. Copy the following to /etc/udev/udev.rules/. 

#
# UDEV rule for ltmodem
#  creates symlink /dev/modem to /dev/ttyLT?, and takes care of permissions

KERNEL="ttyLTM[0-9]", NAME="%k", MODE="0660", GROUP="dialout", SYMLINK="modem"

You may want to fix group owner if your distro is not Debian. Just make sure that GROUP parameter matches group owner of /dev/ttyS0 (ls -l /dev/ttyS0 is your friend).

After installation and setup, restart hotplug or reboot to check that all works.
(the above is ripped from the ltmodem-2.6-alk-7.tar.bz2 package documents)

At least that's what I think I did. In the end I went back to a blank box and started again......

Hope it comes together.

---

### Post by StefanoCole on 2005-03-29
I found a DialupModemHowto and followed the instructions (use of pppconfig and of modem lights panel-application). It worked fine! Now I am able to connect to internet using Ubuntu!!!

Bye bye, Stefano

---

### Post by The_Living_Linux on 2005-05-19
[QUOTE=Maniak]I also tried the gnome-ppp-0.3.21.tar.gz but had trouble getting it to install properly.

Do a google search for 'gnome-ppp deb'. It should find several  gnome-ppp-0.3.17-2.deb mirrors. Once you have it, open a terminal and 'dpkg -i gnome-ppp-0.3.17-2.deb' to install it.

Go from there with the dip group stuff to get it to work properly.

Simon BC[/QUOTE]

I tried downloading both gnome-ppp-gz 0.3.21.tar.and gnome-ppp-0.3.17-2.deb,and i copied onto a USB key from my PC running windows and then transferred it onto my laptop which is running linux.....and whenever i try the following,this is what happens  :

$ tar -zxpvf gnome-ppp-0.3.21.tar.gz

gzip: stdin:not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

#dpkg -i gnome-ppp-0.3.17-2.deb
 
dpkg-deb: gnome-ppp-0.3.17-2.deb is not a debian format archive

I was wondering whether the errors were due to the fact that i downloaded the files onto windows first and then transferred it to linux....(i'm not sure,i'm rather new to linux)

---

