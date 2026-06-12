---
title: "HP Photosmart D110 scanning trouble"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by pseudocube on 2011-02-02
My computer recognizes the printer and has no trouble printing out any documents. The printer can scan papers to a memory card and makes copies just fine too. But when I select "Scan to PC" I get the message "Try scan from computer or see documentation. Press OK." Of course, the printer included next to no documentation, only the basic plug-it-in-and-turn-it-on instructions. Simple Scan said that it did not find a scanner.

**Edit:** Shoot, I probably should have posted this in "General Help."

---

### Post by erilidon on 2011-02-02
Is it hooked up USB directly to the computer or to the network?

---

### Post by pseudocube on 2011-02-02
It is connected by a USB cable.

Also, I installed hplip. Here's its output:
```
user@user-desktop:~$ hp-check

HP Linux Imaging and Printing System (ver. 3.10.2)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the
HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies
are installed to successfully compile HPLIP.                                    
2. Run-time check mode (-r or --run): Use this mode to determine if a distro    
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball   
has the proper dependencies installed to successfully run.                      
3. Both compile- and run-time check mode (-b or --both) (Default): This mode    
will check both of the above cases (both compile- and run-time dependencies).   

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux user-desktop 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686 GNU/Linux

Distribution:
ubuntu 10.04

Checking Python version...
OK, version 2.6.5 installed

Checking PyQt 4.x version...
OK, version 4.7.2 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.3
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.83.0


------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).

Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: CUPS devel- Common Unix Printing System development files...
OK, found.

Checking for dependency: CUPS image - CUPS image development files...
OK, found.

Checking for dependency: DBus - Message bus system...
OK, found.

Checking for dependency: gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency: libjpeg - JPEG library...
OK, found.

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
OK, found.

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
OK, found.

Checking for dependency: libusb - USB library...
OK, found.

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: PolicyKit - Administrative policy framework...
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
OK, found.

Checking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...
OK, found.

Checking for dependency: Python XML libraries...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
OK, found.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 3.10.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.10.2

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hplip/HP
ppdbase=/usr/share/ppd/hplip
doc=/usr/share/doc/hplip-doc/HTML
icon=no
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=yes
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=yes
foomatic-drv-install=yes
foomatic-ppd-install=yes
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.10.2rc1.9
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=yes
hpijs-only-build=no
lite-build=no
udev-acl-rules=yes
hpcups-only-build=no
hpijs-only-build=no


Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0



Current contents of '~/.hplip/hplip.conf' file:
[installation]
version = 3.10.2rc1.9
date_time = 02/02/2011 17:52:26



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
HP-Photosmart-D110-series
-------------------------
Type: Unknown
Device URI: usb://HP/Photosmart%20D110%20series?serial=CN0C8G43WP05N9
PPD: /etc/cups/ppd/HP-Photosmart-D110-series.ppd
PPD Description: HP Photosmart d5060 Series hpijs, 3.10.2
Printer status: printer HP-Photosmart-D110-series is idle.  enabled since Wed 02 Feb 2011 05:06:12 PM PST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
'hpaio' in '/etc/sane.d/dll.d/hplip'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
 
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cup***t' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
OK, found.


 
-----------------
| USB I/O SETUP |
-----------------

Checking for permissions of USB attached printers...

HP Device 0x8d11 at 001:003: 
    Device URI: hp:/usb/Photosmart_D110_series?serial=CN0C8G43WP05N9

HP Linux Imaging and Printing System (ver. 3.10.2)
System Tray Status Service ver. 2.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
error: Unsupported model: Photosmart_D110_series

---------------
| USER GROUPS |
---------------

user adm lp dialout cdrom plugdev lpadmin admin sambashare

User member of group 'lp'. Enables print/ scan/ fax.
User member of group 'lpadmin'.

-----------
| SUMMARY |
-----------

error: 1 error or warning.

Please refer to the installation instructions at:
http://hplip.sourceforge.net/install/index.html


Done.
user@user-desktop:~$ 

```

---

### Post by pseudocube on 2011-02-16
I figured out a workaround: I can still scan to an SD card, so I can use my camera to transfer the files from the printer to my PC.

Meanwhile, if anyone has any help they can offer to solve the problem I would be very grateful. :D

---

### Post by pormenese on 2011-02-18
> **pseudocube said:**
> I figured out a workaround: I can still scan to an SD card, so I can use my camera to transfer the files from the printer to my PC.

Meanwhile, if anyone has any help they can offer to solve the problem I would be very grateful. :D

I bought the same printer, some days ago, and I'm also using ubuntu 10.04. The problem is that the hplip version of lucid is 3.10.2. The support for HP D110  was added in hplip version 3.10.5.

To correct it, add the [Till Kamppeter's PPA]("https://launchpad.net/%7Etill-kamppeter/+archive/ppa") to your repositories list and update hplip (the current version is 3.11.1). Then, check that the driver used for your printer is the correct one.

My printer is working perfectly :)

---

### Post by nealaustin on 2011-02-28
Went out and bought a HP Photoscan D110 today. Downloaded and installed the from HP site: "hplip-3.11.1.run" and saved the very simple instructions to my Ubuntu 10.04 32bit netbook (system76) and then copied the file via thumb drive to my wife's Ubuntu 10.04 64bit desktop machine and installed it there. SimpleScan works!, printing works! Wireless works! Awesome printer indeed. :popcorn: I first tried to use a similar printer to set it up but the scanner didn't work. I am by no means an expert, but reading this forum before I bought this printer guided me to the right product for Linux. Thanks everyone!

---

### Post by pseudocube on 2011-03-01
> **pormenese said:**
> To correct it, add the [Till Kamppeter's PPA]("https://launchpad.net/%7Etill-kamppeter/+archive/ppa") to your repositories list and update hplip (the current version is 3.11.1). Then, check that the driver used for your printer is the correct one.

Awesome, thanks! It's working! :) 2 Internet points to you!

---

### Post by Adler on 2011-06-25
pormenese,

YOU ARE THE MAN! Thanks for that.

You get 4 Internet points from me!

JJMacey
Tempe, Arizona

---

### Post by leandromartinez98 on 2011-07-29
Do I need to reboot or something else? I've done the PPA thing and the driver is correct, with the 3.11.1 version, but the scanner still doesn't work.

---

