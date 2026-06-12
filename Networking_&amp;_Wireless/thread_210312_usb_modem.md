---
title: "usb modem"
date: 2006-07-06
forum: Networking &amp; Wireless
---

### Post by eilker1917 on 2006-07-06
Hello everybody...

Today since morning, i try to install my pikatel usb modem. I cant be succesfull.
Ubuntu is my first linux experienment. **And i am getting crazy**.](*,) 
From terminal , i write sudo pppoeconf , it scans and at the and, it says not detected, sorry i scanned 1 interface bla bla, may be it is used by other program etc..

i checked, i have package ins. for pppoe.

i try from networking too, it doesnt detect modem.

i write to firefox some ip's, it doesnt work.

I installed ubuntu 6.06 . I have ms winXP pro. 

even i tried the command ipconfig /release when i was at xp. It doent work again in ubuntu.

PLeaseeeeeee help, i am gonna be crazy here.](*,)

---

### Post by golfbuf on 2006-07-06
[QUOTE=eilker1917]
PLeaseeeeeee help, i am gonna be crazy here.](*,)[/QUOTE]

I don't know, but I did see a wiki on usb broadband modems .. check out wiki.ubuntu.com for it.

IIRC it was bad news.

regards,

---

### Post by eilker1917 on 2006-07-06
Thank you very much for the link..i found my medicine..but people , is it that much difficult to install a driver in linux?? this kills me...i dont know how to do all of  these...](*,) 


******************
1 Introduction

    * Description
    * Pre-requisites 

Next: Pre-requisites, Previous: Introduction, Up: Introduction
1.1 Description

EciAdsl is a free Linux driver for connecting your computer to the internet, if you have a Globespan based ADSL USB modem.
Other operating systems like *BSD are under development (please contact authors for more information - See Authors / Support.)

EciAdsl driver homepage is there:
[http://eciadsl.flashtux.org](http://eciadsl.flashtux.org)

An up-to-date list of supported modems is available on this page:
[http://eciadsl.flashtux.org/modems.php?lang=en&supported=yes](http://eciadsl.flashtux.org/modems.php?lang=en&supported=yes)

Previous: Description, Up: Introduction
1.2 Pre-requisites
1.2.1 Packages

In order to install EciAdsl driver, you need the following programs/packages:

    * A running GNU/Linux system (x86 architecture) with standard tools (MDK9/RH8/top-recent/exotic ones may have (solvable) problems, BSD and other systems are not officially supported yet)
    * USB 1.1 hardware support
    * Linux kernel 2.4.x (>=2.4.18-pre3 or <2.4.18-pre3+N_HDLC patch in order to get automatic pppd reconnection feature working, which is recommended)
    * USB support (as modules):
          o general USB support
          o USB preliminary fs
          o your HUB USB controller AS MODULE
          o no DABUSB module enabled 
    * PPP support (including usermode pppd package >=2.4.0)
    * installation from the sources: standard development packages (Linux sources in /usr/src/linux, GNU software like gcc>=2.91.66, GNU make, etc.)
    * USB modem (*only* GlobeSpan chipset inside)
    * bash (>=2.x.x)
    * optionally: tcl/tk >= 8.x.x, perl
    * root privileges (at least to install the driver) 

1.2.2 Kernel

If you have latest Mandrake/Redhat with default kernel you can skip this chapter.
According to your distribution, some options may lack in your kernel. If eciadsl-doctor detects missing options, then you need to recompile your kernel.

You MUST include these options (“*” stands for “in the kernel”, “M” stands for “module”):

USB support —>
<M> Support for USB
[ ] USB verbose debug messages
— Miscellaneous USB options
[*] Preliminary USB device filesystem
[ ] Enforce USB bandwidth allocation (EXPERIMENTAL)
[ ] Long timeout for slow-responding devices (some MGE Ellipse UPSes)
— USB Host Controller Drivers
< > EHCI HCD (USB 2.0) support (EXPERIMENTAL)
<M> UHCI (Intel PIIX4, VIA, ...) support
<M> UHCI Alternate Driver (JE) support
<M> OHCI (Compaq, iMacs, OPTi, SiS, ALi, ...) support
..
— USB Multimedia devices
..
< > DABUSB driver
..

Character devices —>
..
[*] Non-standard serial port support
<M> HDLC line discipline support
..

Network device support —>
..
<M> PPP (point-to-point protocol) support
[ ] PPP multilink support (EXPERIMENTAL)
[ ] PPP filtering
<M> PPP support for async serial ports
<M> PPP support for sync tty ports
<M> PPP Deflate compression
<M> PPP BSD-Compress compression
< > PPP over Ethernet (EXPERIMENTAL)
< > PPP over ATM (EXPERIMENTAL)

Next: Configuration, Previous: Introduction, Up: Top
2 Installation

    * Removing dabusb
    * Driver installation
    * Compilation 

Next: Driver installation, Previous: Installation, Up: Installation
2.1 Removing dabusb

If modem is powered on at Linux startup, then you need to remove dabusb.
Otherwise, skip this section.

Hotplug is probably enabled, and it wrongly detects your modems as an audio device and loads dabusb module in order to add support for this audio device.
If /etc/hotplug/blacklist exists, edit it and add a line containing the word 'dabusb' (without the quotes) to it. Restart Linux.

If you cannot find such file whereas hotplug is installed and enabled, there must be another way to configure it, but you can also apply the following method (a bit rough):

    * Boot your Linux machine with your modem unplugged
    * You can remove the dabusb module from your system using eciadsl-config-tk or eciadsl-config-text.
      You can also directly call eciadsl-remove-dabusb (in /usr/local/bin by default).
      Or, manually type the following command:
      modprobe -r dabusb && rm -f $(modprobe -l | grep dabusb) && depmod -a

If the kernel has been compiled by hand, don't forget to remove dabusb support from the kernel configuration too.

Next: Compilation, Previous: Removing dabusb, Up: Installation
2.2 Driver installation

Download the latest stable usermode package (source code or a package for your distrubution) on this page:
[http://eciadsl.flashtux.org/download.php?lang=en](http://eciadsl.flashtux.org/download.php?lang=en)

Depending of the package you get, issue one of these commands:

    * Sources (.tar.gz): tar xvzf /path/eciadsl-usermode-x.y.tar.gz
    * Sources (.tar.bz2): tar xvjf /path/eciadsl-usermode-x.y.tar.bz2
    * RedHat/Mandrake (.rpm): rpm -i /path/eciadsl-usermode-x.y-1.i386.rpm
    * Debian (.deb): dpkg -i /path/eciadsl-usermode_x.y-1_i386.deb
    * Slackware (.tgz): installpkg /path/eciadsl-usermode-x.y-i386-1.tgz
    * Gentoo (.ebuild):
      see [http://doc.gentoofr.org/Members/BeTa/eciadsl-gentoo-howto/view](http://doc.gentoofr.org/Members/BeTa/eciadsl-gentoo-howto/view) 

where x.y is the version (for example 0.8)

Previous: Driver installation, Up: Installation
2.3 Compilation

If you installed distro specific package (Redhat/Mandrake, Debian, Slackware, Gentoo), you can skip this step.

All you have to do is to run in a console or a terminal:
./configure
make
As "root": make install

Check ./configure –help to get a list of optional settings. You may want to install the software in a different place than the default one (/usr/local), using --prefix=/opt for instance.
Driver's config files can also be installed in a directory you may prefer (default is in /etc/eciadsl), using the –conf-prefix (default is /) AND –conf-fir (default is etc/eciadsl) parameters. For instance:
--conf-prefix=/opt --conf-dir=etc/eciadsl
or --conf-prefix=/opt/eciadsl --conf-dir=etc

Be careful, –etc-prefix can be changed too (defaut is /, so /etc is used), but it is used to get system config files like resolv.conf or the pppd config files. Use –etc-prefix only if you know what you are doing.

See other options using ./configure –help.

Next: Connection, Previous: Installation, Up: Top
3 Configuration

    * Configuration tool
    * Detail of parameters 

Next: Detail of parameters, Previous: Configuration, Up: Configuration
3.1 Configuration tool

    * If Tcl/Tk is installed on your system, you can run graphical configuration tool:
      eciadsl-config-tk

      Enter all parameters without checking “Change synch .bin file”.
    * Otherwise, run text mode configuration:
      eciadsl-config-text
      Just follow steps to configure the driver. 

Previous: Configuration tool, Up: Configuration
3.2 Detail of parameters

user
    Username given by your provider
    For example: username@clubadsl1

password
    Password given by your provider


VPI
    First number of “dialed number”
    For example if you “dial” 8,35 with Windows driver then your VPI is 8.

VCI
    Second number of “dialed number”
    For example if you “dial” 8,35 with Windows driver then your VCI is 35.

Provider DNS
    Check the box “Update provider DNS” and choose your provider in the list.
    If your provider is not in the list, enter manually your DNS servers in the fields below the list.
    If you don't know your DNS servers, read this question in FAQ:
    [http://eciadsl.flashtux.org/faq.php?lang=en#1.6](http://eciadsl.flashtux.org/faq.php?lang=en#1.6)

Modem
    Select your modem in the list.
    If your modem is not in the list, check on modems page:
    [http://eciadsl.flashtux.org/modems.php?lang=en](http://eciadsl.flashtux.org/modems.php?lang=en)
    - If your modem is “not supported”, the driver will never work with your modem (please don't ask for support to developers, you've to look for another driver).
    - If your modem is “maybe supported”, then ask to developers for detail. See Authors / Support.

Modem chipset
    [value is automatically setted by choosing Modem model].
    For any doubt please check on modems page:
    [http://eciadsl.flashtux.org/modems.php?lang=en](http://eciadsl.flashtux.org/modems.php?lang=en)

Alt synch
    [value is automatically setted by choosing Modem model].
    It is the USB alt interface used by eciadsl to comunicate with modems during synch phase.
    Standard values: 4 for GS7070 (old modem models) - 5 or 0 for GS7470 chipset (new modem models)
    For any doubt please check on modems page:
    [http://eciadsl.flashtux.org/modems.php?lang=en](http://eciadsl.flashtux.org/modems.php?lang=en)

Alt pppoeci
    [value is automatically setted by choosing Modem model].
    It is the USB alt interface used by eciadsl to comunicate with modems during pppoeci phase.
    Standard values: 4 for GS7070 (old modem models) - 1 or 0 for GS7470 chipset (new modem models)
    For any doubt please check on modems page:
    [http://eciadsl.flashtux.org/modems.php?lang=en](http://eciadsl.flashtux.org/modems.php?lang=en)

Synch .bin file
    Check this option only if eciadsl-start fails with synchronization.

PPP mode
    - For users in France, choose default PPP mode (VCM_RFC2364).
    - For other users, check the appropriate ppp mode with your provider.
    Look at this question in the FAQ:
    [http://eciadsl.flashtux.org/faq.php?lang=en#5.4](http://eciadsl.flashtux.org/faq.php?lang=en#5.4)

DHCP
    Check this only if your provider uses DHCP.
    If you don't know, leave this option unchecked.

Static IP
    Check this only if you have static IP.
    If so, enter IP address and gateway below.
    If you don't know, leave this option unchecked. 

Next: Synch .bin creation, Previous: Configuration, Up: Top
4 Connection

    * Eciadsl-start
    * Other scripts 

Next: Other scripts, Previous: Connection, Up: Connection
4.1 Eciadsl-start

To connect to the internet, issue this command as root:
eciadsl-start | tee log.txt
4.1.1 Synch problem

If you've problems with synch (eciadsl-synch timeout/error or lcp timeouts after synch), then follow instructions below:

    * Download .bin package there:
      [http://eciadsl.flashtux.org/download.php?lang=en&view=sync](http://eciadsl.flashtux.org/download.php?lang=en&view=sync)
    * Unpack the package into /etc/eciadsl (as root):
      cd /etc/eciadsl && tar xvzf /path/eciadsl-synch_bin.tar.gz
    * Run eciadsl-config-tk or eciadsl-config-text and choose another .bin file
    * Shut down the modem: either with modprobe -r usb-uhci (or usb-ohci), either unplugging/replugging the modem (USB cable).
    * Run eciadsl-start again.
      If you still have synch problems, then try another synch .bin file.
      Important: you can try ALL synch .bin files, don't look at place or provider of .bin.
      If no .bin works, then you'll have to create your own .bin file under Windows. See Synch .bin creation. 

For other problems with eciadsl-start, please look at the FAQ:
[http://eciadsl.flashtux.org/faq.php?lang=en](http://eciadsl.flashtux.org/faq.php?lang=en)
4.1.2 PPPoE users

If you're using PPPoE, you have to configure and use a standard PPPoE client as rp-pppoe ([http://www.roaringpenguin.com/pppoe](http://www.roaringpenguin.com/pppoe)) to connect to your ADSL modem through tap0.

Previous: Eciadsl-start, Up: Connection
4.2 Other scripts
4.2.1 eciadsl-probe-device

Use this script if eciadsl-start doesn't find your modem. This script looks for VID/PID of your modem and display them. For detail, please contact us. See Authors / Support.
4.2.2 eciadsl-doctor

Use this script (with --usb-init option) if eciadsl-start fails with other problem than “Modem not found” or synchronization.
4.2.3 eciadsl-probe-synch

Use this script to test automatically all .bin files, if you have synch problems.

Next: Authors / Support, Previous: Connection, Up: Top
5 Synch .bin creation

    * Eci Windows driver
    * USB Sniffer
    * Snif USB packets under Windows
    * Convert log to .bin under Linux 

If you've synch problems and tried all .bin files with no success, then you have to create your own .bin file under Windows.

Otherwise, you can skip this chapter.

Next: USB Sniffer, Previous: Synch .bin creation, Up: Synch .bin creation
5.1 Eci Windows driver

[Skip this section if your modem has a GS7470 chipset, YOU MUST USE YOUR OWN WINDOWS DRIVER.
For any doubt please check your modem chipset at: [http://eciadsl.flashtux.org/modems.php?lang=en]](http://eciadsl.flashtux.org/modems.php?lang=en]).
5.1.1 Download

Download Eci windows driver version 1.06 (otherwise your .bin file will not work under linux):
[http://eciadsl.flashtux.org/download/eci_drv_106_win.zip](http://eciadsl.flashtux.org/download/eci_drv_106_win.zip)
5.1.2 Driver modification

If your modem has not one of these VID/PID, you've to modify two files in Eci Windows:
- VID1/PID1: 0547/2131, VID2/PID2: 0915/8000
- VID1/PID1: 0915/0001, VID2/PID2: 0915/0002
To check your VID/PID, please look at:
[http://eciadsl.flashtux.org/modems.php?lang=en](http://eciadsl.flashtux.org/modems.php?lang=en).

Modifications you've to do:

- file gafwload.inf, line 24 :
ExcludeFromSelect = USB\VID_0547&PID_2131
replace 0547 by your VID1 and 2131 by your PID1

- file gafwload.inf, line 30 :
%GSILOAD.DeviceDescAnchor% = GSIUSBLDRANCHOR, USB\VID_0547&PID_2131
replace 0547 by your VID1 and 2131 by your PID1

- file gwausb.inf, line 34 :
ExcludeFromSelect = USB\VID_0915&PID_8000
replace 0915 by your VID2 and 8000 by your PID2

- file gwausb.inf, line 42 :
%ADSLUSB.DeviceDesc% = ADSLUSB.gspnDefault, USB\VID_0915&PID_8000
replace 0915 by your VID2 and 8000 by your PID2

- file gwausb.inf, line 58 :
HKR, Ndi, DeviceID, 0, "USB\VID_0915&PID_8000"
replace 0915 by your VID2 and 8000 by your PID2
5.1.3 Installation

Launch setup.exe and follow instructions.

Next: Snif USB packets under Windows, Previous: Eci Windows driver, Up: Synch .bin creation
5.2 USB Sniffer

Download and install latest USB sniffer package there:
[http://benoit.papillault.free.fr/usbsnoop/](http://benoit.papillault.free.fr/usbsnoop/)

Documentation for Snoopy (USB sniffer) is available there:
[http://benoit.papillault.free.fr/usbsnoop/doc.php](http://benoit.papillault.free.fr/usbsnoop/doc.php)

Next: Convert log to .bin under Linux, Previous: USB Sniffer, Up: Synch .bin creation
5.3 Sniff USB packets under Windows

Disable auto-connection to the internet and unplug all USB devices (except the modem).

Start the sniffer and install the filter on the “Wan modem”, then unplug and replug the modem.
As soon as both red and green leds are fixed, uninstall filters.
The sniffed packets should be in the file C:\WINxxx\usbsnoop.log
Reboot under Linux.

Previous: Snif USB packets under Windows, Up: Synch .bin creation
5.4 Convert log to .bin under Linux

Mount windows partition containing the usbsnoop log file so as to copy it where you want.
Issue this command:
eciadsl-vendor-device.pl usbsnoop.log -chipset=#YOUR_MODEM_CHISPET#
substitute #YOUR_MODEM_CHISPET# with your modem chipset (GS7070 or GS7470).
For help, issue this command: eciadsl-vendor-device.pl -h
This perl script parses the log file and generates a new bin file (script provided with usermode package).
Issue this command:
mv #BIN_FILENAME_CREATED# /etc/eciadsl/my_synch.bin
substitute #BIN_FILENAME_CREATED with bin file name created.
and then run eciadsl-config-text to use this .bin

Run eciadsl-start...
...and cross your fingers :-)

---

### Post by eilker1917 on 2006-07-07
Anyone could you tell me , how to do things below?? how will i put those things into kernel??? two days trying with a modem :-k  

***********
You MUST include these options (“*” stands for “in the kernel”, “M” stands for “module”):

USB support —>
<M> Support for USB
[ ] USB verbose debug messages
— Miscellaneous USB options[*] Preliminary USB device filesystem
[ ] Enforce USB bandwidth allocation (EXPERIMENTAL)
[ ] Long timeout for slow-responding devices (some MGE Ellipse UPSes)
— USB Host Controller Drivers
< > EHCI HCD (USB 2.0) support (EXPERIMENTAL)
<M> UHCI (Intel PIIX4, VIA, ...) support
<M> UHCI Alternate Driver (JE) support
<M> OHCI (Compaq, iMacs, OPTi, SiS, ALi, ...) support
..
— USB Multimedia devices
..
< > DABUSB driver
..

Character devices —>
..[*] Non-standard serial port support
<M> HDLC line discipline support
..

Network device support —>
..
<M> PPP (point-to-point protocol) support
[ ] PPP multilink support (EXPERIMENTAL)
[ ] PPP filtering
<M> PPP support for async serial ports
<M> PPP support for sync tty ports
<M> PPP Deflate compression
<M> PPP BSD-Compress compression
< > PPP over Ethernet (EXPERIMENTAL)
< > PPP over ATM (EXPERIMENTAL)

---

### Post by eilker1917 on 2006-07-07
noone knows it???

---

